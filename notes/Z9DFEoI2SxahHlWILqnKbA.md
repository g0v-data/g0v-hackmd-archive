

🎯 **Background**
Currently, `voice.py` is a Streamlit UI — it doesn’t expose a REST API, so I can’t connect it to my React frontend (even if the UI looks the same, there’s no URL to call).
Also, my own PC can’t run Ollama, so pls try to run this on your machine.

Please follow the steps below to wrap the three core classes from `voice.py` (`AthleteProfile`, `DatabaseManager`, `ConversationalVoiceCoach`) into FastAPI endpoints.
Once running, the React frontend can point to `http://localhost:8000` to make the whole flow work on your PC — including text interaction, STT (speech-to-text), and TTS (text-to-speech).

---

## 🛠 Step 1 — Install dependencies

```bash
pip install fastapi uvicorn pydantic python-multipart aiofiles
pip install faster-whisper av soundfile   # STT (offline Whisper)
pip install pyttsx3                       # Offline TTS (average quality, no internet needed)
pip install elevenlabs                    # Optional: Cloud TTS (better quality, requires API Key)
```

Install **ffmpeg** (for decoding WebM/OGG):

* **Windows:** `winget install ffmpeg`
* **Mac:** `brew install ffmpeg`

---

## 🛠 Step 2 — Create `api.py`

Place this file in the same folder as `voice.py`.
It will:

* Import the three core classes from `voice.py`
* Provide API endpoints for creating a session, step-by-step data collection, free-form Q\&A, and generating a summary
* Add `/voice/utterance` (upload audio → STT)
* Add `/voice/tts` (text → audio file)
* For all major APIs, passing `tts=true` will automatically return an `audio_url`

```bash
# api.py
import os, uuid, io
from typing import List, Optional
from fastapi import FastAPI, UploadFile, File, Query
from fastapi.middleware.cors import CORSMiddleware
from fastapi.responses import FileResponse, JSONResponse
from pydantic import BaseModel

from voice import AthleteProfile, DatabaseManager, ConversationalVoiceCoach

# 可選 TTS/STT 模組
try:
    from elevenlabs import ElevenLabs
    elevenlabs = ElevenLabs(api_key=os.getenv("ELEVENLABS_API_KEY"))
except:
    elevenlabs = None

try:
    import pyttsx3
except:
    pyttsx3 = None

try:
    from faster_whisper import WhisperModel
    import av, soundfile as sf, numpy as np
    whisper = WhisperModel("base", device="cpu")
except:
    whisper = None

MEDIA_DIR = os.path.join(os.getcwd(), "media")
os.makedirs(MEDIA_DIR, exist_ok=True)

app = FastAPI(title="PsyCoach API")
app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],  # 開發全開，之後可收斂
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)

db = DatabaseManager()
coach = ConversationalVoiceCoach()

# ---------- Utilities ----------
def decode_to_wav(raw: bytes) -> str:
    container = av.open(io.BytesIO(raw), format="webm")
    stream = container.streams.audio[0]
    resampler = av.audio.resampler.AudioResampler(format="s16", layout="mono", rate=16000)
    pcm = []
    for packet in container.demux(stream):
        for frame in packet.decode():
            pcm.append(resampler.resample(frame).to_ndarray())
    audio = np.concatenate(pcm, axis=1).T.astype(np.int16)
    path = os.path.join(MEDIA_DIR, f"{uuid.uuid4().hex}.wav")
    sf.write(path, audio, 16000, subtype="PCM_16")
    return path

def stt(path: str) -> str:
    if not whisper:
        raise RuntimeError("No STT engine installed.")
    segments, _ = whisper.transcribe(path, language="zh", vad_filter=True)
    return "".join(s.text for s in segments).strip()

def tts(text: str, voice: Optional[str] = None) -> str:
    path = os.path.join(MEDIA_DIR, f"{uuid.uuid4().hex}.mp3")
    if elevenlabs:
        audio = elevenlabs.text_to_speech.convert(
            voice_id=voice or os.getenv("TTS_VOICE") or "Rachel",
            optimize_streaming_latency="0",
            output_format="mp3_44100_128",
            text=text,
        )
        with open(path, "wb") as f:
            for chunk in audio:
                if chunk:
                    f.write(chunk)
        return path
    if pyttsx3:
        engine = pyttsx3.init()
        engine.save_to_file(text, path)
        engine.runAndWait()
        return path
    raise RuntimeError("No TTS engine installed.")

def maybe_tts(message: str, enable: bool, voice: Optional[str]) -> Optional[str]:
    if not enable or not message:
        return None
    try:
        return tts(message, voice)
    except:
        return None

# ---------- Schemas ----------
class CreateSessionReq(BaseModel):
    name: str
    age: int
    weight: float
    height: float
    sport_type: Optional[str] = None
    athlete_level: Optional[str] = None
    training_frequency: int = 3
    goals: List[str] = []
    preferences: dict = {"voice_interaction": "Text Only"}

class StepReq(BaseModel):
    session_id: str
    step: str
    user_input: str

class ChatReq(BaseModel):
    session_id: str
    user_message: str
    history: List[dict] = []

class TTSReq(BaseModel):
    text: str
    voice: Optional[str] = None

# ---------- API ----------
@app.post("/voice/session")
def create_session(body: CreateSessionReq, tts: bool = Query(False), voice: Optional[str] = Query(None)):
    sid = uuid.uuid4().hex
    profile = AthleteProfile(
        session_id=sid, name=body.name, age=body.age, weight=body.weight,
        height=body.height, primary_goals=body.goals,
        training_frequency=body.training_frequency, preferences=body.preferences
    )
    db.save_athlete_profile(profile)
    start = coach.start_vocal_data_collection(profile)
    audio_path = maybe_tts(start.get("message"), tts, voice)
    return {"sessionId": sid, "next": {**start, "audio_url": f"/media/{os.path.basename(audio_path)}" if audio_path else None}}

@app.post("/voice/step")
def process_step(body: StepReq, tts: bool = Query(False), voice: Optional[str] = Query(None)):
    p = db.load_athlete_profile(body.session_id)
    if not p: return {"error": "not found"}
    r = coach.process_conversation_step(p, body.user_input, body.step)
    audio_path = maybe_tts(r.get("message"), tts, voice)
    return {**r, "audio_url": f"/media/{os.path.basename(audio_path)}" if audio_path else None}

@app.post("/voice/question")
def gen_question(session_id: str, tts: bool = Query(False), voice: Optional[str] = Query(None)):
    p = db.load_athlete_profile(session_id)
    if not p: return {"error": "not found"}
    q = coach.generate_coaching_question(p)
    audio_path = maybe_tts(q.get("question"), tts, voice)
    return {**q, "audio_url": f"/media/{os.path.basename(audio_path)}" if audio_path else None}

@app.post("/voice/respond")
def coach_respond(body: ChatReq, tts: bool = Query(False), voice: Optional[str] = Query(None)):
    p = db.load_athlete_profile(body.session_id)
    if not p: return {"error": "not found"}
    r = coach.generate_coaching_response(p, body.user_message, body.history)
    audio_path = maybe_tts(r.get("response"), tts, voice)
    return {**r, "audio_url": f"/media/{os.path.basename(audio_path)}" if audio_path else None}

@app.post("/voice/summary")
def final_summary(session_id: str, tts: bool = Query(False), voice: Optional[str] = Query(None)):
    p = db.load_athlete_profile(session_id)
    if not p: return {"error": "not found"}
    s = coach.generate_final_coaching_summary(p, [])
    audio_path = maybe_tts(s.get("summary"), tts, voice)
    return {**s, "audio_url": f"/media/{os.path.basename(audio_path)}" if audio_path else None}

@app.post("/voice/utterance")
async def upload_voice(audio: UploadFile = File(...)):
    raw = await audio.read()
    path = decode_to_wav(raw) if not audio.filename.endswith(".wav") else os.path.join(MEDIA_DIR, audio.filename)
    if not audio.filename.endswith(".wav"):
        with open(path, "wb") as f: f.write(raw)
    try:
        text = stt(path)
        return {"text": text}
    except Exception as e:
        return {"error": str(e)}

@app.post("/voice/tts")
def tts_endpoint(req: TTSReq):
    try:
        path = tts(req.text, req.voice)
        return {"audio_url": f"/media/{os.path.basename(path)}"}
    except Exception as e:
        return {"error": str(e)}

@app.get("/media/{filename}")
def serve_media(filename: str):
    path = os.path.join(MEDIA_DIR, filename)
    if not os.path.exists(path):
        return {"error": "not found"}
    return FileResponse(path)
```

---

### Start the API server:

```bash
uvicorn api:app --reload --port 8000
```

---

### Test the API:

Open:
[http://localhost:8000/docs](http://localhost:8000/docs)

* **`/voice/session`** → Create a session, confirm it returns `sessionId`
* **`/voice/utterance`** → Upload `.webm` / `.ogg` / `.wav`, check if it returns text
* **`/voice/tts`** → Send text, see if it returns `audio_url` (playable)

---

## 🛠 Step 3 — Create React frontend

```bash
npm create vite@latest psycoach-ui -- --template react
cd psycoach-ui
npm i axios
```

Create `.env`:

```ini
VITE_API_URL=http://localhost:8000
```

`src/utils/api.js`:

```javascript
import axios from "axios";
const api = axios.create({
  baseURL: import.meta.env.VITE_API_URL || "http://localhost:8000",
  timeout: 15000,
});
export default api;
```

the `public/index.html`: just fill it in the one u see in ur file: 
```ini
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8" />
    <link rel="icon" href="%PUBLIC_URL%/favicon.ico" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <meta name="theme-color" content="#000000" />
    <meta
      name="description"
      content="Web site created using create-react-app"
    />
    <link rel="apple-touch-icon" href="%PUBLIC_URL%/logo192.png" />
    <!--
      manifest.json provides metadata used when your web app is installed on a
      user's mobile device or desktop. See https://developers.google.com/web/fundamentals/web-app-manifest/
    -->
    <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />
    <!--
      Notice the use of %PUBLIC_URL% in the tags above.
      It will be replaced with the URL of the `public` folder during the build.
      Only files inside the `public` folder can be referenced from the HTML.

      Unlike "/favicon.ico" or "favicon.ico", "%PUBLIC_URL%/favicon.ico" will
      work correctly both with client-side routing and a non-root public URL.
      Learn how to configure a non-root public URL by running `npm run build`.
    -->
    <title>React App</title>
  </head>
  <body>
    <noscript>You need to enable JavaScript to run this app.</noscript>
    <div id="root"></div>
    <!--
      This HTML file is a template.
      If you open it directly in the browser, you will see an empty page.

      You can add webfonts, meta tags, or analytics to this file.
      The build step will place the bundled scripts into the <body> tag.

      To begin the development, run `npm start` or `yarn start`.
      To create a production bundle, use `npm run build` or `yarn build`.
    -->
  </body>
  <script src="https://cdn.tailwindcss.com"></script>
</html>

```
the `src/App.jsx`: just fill it in the one u see in ur file: 


```bash
import React, { useEffect, useRef, useState } from "react";
import axios from "axios";
import { motion, AnimatePresence } from "framer-motion";
import { Mic, Square, Send, MessageCircle, Sparkles, History, Headphones, Settings, CheckCircle2 } from "lucide-react";

/**
 * PsyCoach — React UI (Tailwind-polished, framer-motion, bottom mic)
 * Setup (once):
 *   npm i axios framer-motion lucide-react
 *   Tailwind: https://tailwindcss.com/docs/guides/vite  (content: ./index.html, ./src/**/*.{js,ts,jsx,tsx})
 *   .env  VITE_API_URL=http://localhost:8000
 */

const API_BASE = import.meta.env.VITE_API_URL || "http://localhost:8000";
const api = axios.create({ baseURL: API_BASE, timeout: 20000 });

export default function App() {
  const [ready, setReady] = useState(false);
  const [error, setError] = useState("");

  // session / flow state
  const [sessionId, setSessionId] = useState("");
  const [stepInfo, setStepInfo] = useState(null); // { message, step, audio_url? }
  const [history, setHistory] = useState([]);     // [{ question, response, coach }]

  // TTS prefs
  const [enableTTS, setEnableTTS] = useState(true);
  const [voiceName, setVoiceName] = useState("Rachel");

  // inputs
  const [stepInput, setStepInput] = useState("");
  const [chatInput, setChatInput] = useState("");

  // audio playback history
  const [audioHistory, setAudioHistory] = useState([]); // [{url, ts}]

  // loading flags
  const [loadingStep, setLoadingStep] = useState(false);
  const [loadingChat, setLoadingChat] = useState(false);
  const [creating, setCreating] = useState(false);

  // demo profile
  const [profile, setProfile] = useState({
    name: "Demo",
    age: 22,
    weight: 60,
    height: 170,
    sport_type: "Endurance Sports",
    athlete_level: "Intermediate",
    training_frequency: 3,
    goals: ["reduce stress"],
    preferences: { voice_interaction: "Text Only" },
  });

  // health check
  useEffect(() => {
    (async () => {
      try {
        await api.get("/media/does-not-exist");
      } catch (_) {
        setReady(true); // 404 means server reachable
      }
    })().catch(() => setError("Backend not reachable"));
  }, []);

  const playIfAny = (audioUrl) => {
    if (!audioUrl) return;
    const src = audioUrl.startsWith("http") ? audioUrl : API_BASE + audioUrl;
    const a = new Audio(src);
    a.play().catch(() => {});
    setAudioHistory((h) => [...h, { url: src, ts: Date.now() }]);
  };

  const createSession = async () => {
    setError("");
    setCreating(true);
    try {
      const { data } = await api.post(`/voice/session?tts=${enableTTS}&voice=${encodeURIComponent(voiceName || "")}`, profile);
      setSessionId(data.sessionId);
      setStepInfo(data.next);
      setHistory([]);
      setStepInput("");
      playIfAny(data?.next?.audio_url);
    } catch (e) {
      setError(msgOf(e));
    } finally {
      setCreating(false);
    }
  };

  const submitStep = async () => {
    if (!sessionId || !stepInfo) return;
    const payload = { session_id: sessionId, step: stepInfo.step, user_input: stepInput };
    setError("");
    setLoadingStep(true);
    try {
      const { data } = await api.post(`/voice/step?tts=${enableTTS}&voice=${encodeURIComponent(voiceName || "")}`, payload);
      setStepInfo(data);
      setStepInput("");
      playIfAny(data?.audio_url);
    } catch (e) {
      setError(msgOf(e));
    } finally {
      setLoadingStep(false);
    }
  };

  const askQuestion = async () => {
    if (!sessionId) return;
    setError("");
    setLoadingChat(true);
    try {
      const { data } = await api.post(`/voice/question?tts=${enableTTS}&voice=${encodeURIComponent(voiceName || "")}`, null, { params: { session_id: sessionId } });
      setHistory((h) => [...h, { question: data.question }]);
      playIfAny(data?.audio_url);
    } catch (e) {
      setError(msgOf(e));
    } finally {
      setLoadingChat(false);
    }
  };

  const sendChat = async () => {
    if (!sessionId || !history.length) return;
    const last = history[history.length - 1];
    const optimistic = [...history.slice(0, -1), { ...last, response: chatInput }];
    setHistory(optimistic);
    const toSend = chatInput; // store before clearing
    setChatInput("");
    setLoadingChat(true);
    try {
      const { data } = await api.post(`/voice/respond?tts=${enableTTS}&voice=${encodeURIComponent(voiceName || "")}`, {
        session_id: sessionId,
        user_message: toSend,
        history: optimistic,
      });
      setHistory((h) => {
        const base = [...h];
        base[base.length - 1] = { ...base[base.length - 1], coach: data.response };
        return base;
      });
      playIfAny(data?.audio_url);
    } catch (e) {
      setError(msgOf(e));
    } finally {
      setLoadingChat(false);
    }
  };

  const getSummary = async () => {
    if (!sessionId) return;
    setError("");
    setLoadingChat(true);
    try {
      const { data } = await api.post(`/voice/summary?tts=${enableTTS}&voice=${encodeURIComponent(voiceName || "")}`, null, { params: { session_id: sessionId } });
      alert(data.summary || "No summary returned");
      playIfAny(data?.audio_url);
    } catch (e) {
      setError(msgOf(e));
    } finally {
      setLoadingChat(false);
    }
  };

  // Floating mic should auto-target whichever input is relevant
  const onFloatingTranscript = (t) => {
    if (stepInfo && stepInfo.step && stepInfo.step !== "complete") {
      setStepInput((s) => (s ? s + " " + t : t));
    } else {
      setChatInput((s) => (s ? s + " " + t : t));
    }
  };

  return (
    <div className="relative min-h-screen overflow-hidden bg-gradient-to-b from-indigo-50 via-violet-50 to-white text-slate-800">
      {/* Decorative blobs */}
      <div className="pointer-events-none absolute -top-24 left-1/2 -z-10 h-80 w-80 -translate-x-1/2 rounded-full bg-gradient-to-tr from-indigo-300/50 to-fuchsia-300/40 blur-3xl" />
      <div className="pointer-events-none absolute -bottom-24 right-10 -z-10 h-72 w-72 rounded-full bg-gradient-to-tr from-cyan-300/40 to-emerald-300/40 blur-3xl" />

      <div className="mx-auto max-w-3xl px-4 pb-36">
        <Header ready={ready} />

        {error && (
          <motion.div initial={{ opacity: 0, y: -6 }} animate={{ opacity: 1, y: 0 }} className="mt-4 rounded-xl border border-red-200 bg-red-50 px-4 py-3 text-sm text-red-700 shadow">
            {error}
          </motion.div>
        )}

        {/* Preferences */}
        <Card className="mt-6">
          <div className="flex flex-wrap items-center gap-3">
            <Pill icon={<Headphones className="h-4 w-4" />} text="Speech Options" />
            <label className="inline-flex items-center gap-2 text-sm">
              <input type="checkbox" className="h-4 w-4 accent-indigo-600" checked={enableTTS} onChange={(e) => setEnableTTS(e.target.checked)} />
              Enable TTS in responses
            </label>
            <div className="flex items-center gap-2">
              <input
                className="rounded-xl border border-slate-200 bg-white/80 px-3 py-2 text-sm shadow-sm backdrop-blur focus:outline-none focus:ring focus:ring-indigo-200"
                placeholder="Voice name (e.g., Rachel)"
                value={voiceName}
                onChange={(e) => setVoiceName(e.target.value)}
                style={{ minWidth: 220 }}
              />
              <span className="text-xs text-slate-400">ElevenLabs name or local TTS</span>
            </div>
          </div>
        </Card>

        {/* Session */}
        <Card className="mt-6">
          <div className="flex items-center justify-between gap-4">
            <h2 className="text-lg font-semibold">Session</h2>
            <div className="flex items-center gap-2 text-xs text-slate-500"><Settings className="h-3.5 w-3.5" /> API: {API_BASE}</div>
          </div>
          {!sessionId ? (
            <div className="mt-4 grid grid-cols-1 gap-3 md:grid-cols-2">
              <LabeledInput label="Name" value={profile.name} onChange={(v) => setProfile((p) => ({ ...p, name: v }))} />
              <LabeledInput label="Age" type="number" value={profile.age} onChange={(v) => setProfile((p) => ({ ...p, age: Number(v) }))} />
              <LabeledInput label="Weight (kg)" type="number" value={profile.weight} onChange={(v) => setProfile((p) => ({ ...p, weight: Number(v) }))} />
              <LabeledInput label="Height (cm)" type="number" value={profile.height} onChange={(v) => setProfile((p) => ({ ...p, height: Number(v) }))} />
              <LabeledInput label="Sport Type" value={profile.sport_type} onChange={(v) => setProfile((p) => ({ ...p, sport_type: v }))} />
              <LabeledInput label="Athlete Level" value={profile.athlete_level} onChange={(v) => setProfile((p) => ({ ...p, athlete_level: v }))} />
              <LabeledInput label="Goals (comma separated)" value={profile.goals.join(", ")} onChange={(v) => setProfile((p) => ({ ...p, goals: splitComma(v) }))} className="md:col-span-2" />
              <Button onClick={createSession} loading={creating} iconLeft={<Sparkles className="h-4 w-4" />}>Create Session</Button>
            </div>
          ) : (
            <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className="mt-3 text-sm">
              <div className="flex items-center gap-2 rounded-lg bg-slate-50 px-3 py-2">
                <CheckCircle2 className="h-4 w-4 text-emerald-500" />
                <span className="font-mono text-slate-700">sessionId</span>: {sessionId}
              </div>
            </motion.div>
          )}
        </Card>

        {/* Step-by-step */}
        {sessionId && stepInfo && stepInfo.step !== "complete" && (
          <Card className="mt-6">
            <h2 className="text-lg font-semibold">Guided Setup</h2>
            <p className="mt-2 text-sm text-slate-600">Coach asks:</p>
            <motion.div initial={{ opacity: 0, y: 6 }} animate={{ opacity: 1, y: 0 }} className="mt-2 rounded-xl bg-white/80 px-4 py-3 text-slate-800 shadow-inner ring-1 ring-slate-100 backdrop-blur">
              {stepInfo.message}
            </motion.div>

            <div className="mt-3 flex flex-col gap-3 md:flex-row md:items-center">
              <input
                className="flex-1 rounded-xl border border-slate-200 bg-white/80 px-4 py-2 shadow-sm backdrop-blur focus:outline-none focus:ring focus:ring-indigo-200"
                placeholder="Type your answer or use the mic…"
                value={stepInput}
                onChange={(e) => setStepInput(e.target.value)}
              />
              <div className="flex items-center gap-2">
                <InlineRecorder onTranscript={(t) => setStepInput((s) => (s ? s + " " + t : t))} />
                <Button onClick={submitStep} loading={loadingStep} intent="primary" iconLeft={<Send className="h-4 w-4" />}>Send</Button>
              </div>
            </div>
          </Card>
        )}

        {/* Chat */}
        {sessionId && (
          <Card className="mt-6">
            <div className="flex items-center justify-between">
              <h2 className="text-lg font-semibold">Coaching Chat</h2>
              <div className="flex items-center gap-2">
                <Button onClick={askQuestion} intent="ghost" iconLeft={<MessageCircle className="h-4 w-4" />}>Ask Question</Button>
                <Button onClick={getSummary} intent="ghost">Get Summary</Button>
              </div>
            </div>

            <div className="mt-4 space-y-3">
              {history.length === 0 && (
                <div className="rounded-xl border border-dashed border-slate-200 p-6 text-center text-sm text-slate-500">No messages yet. Click <b>Ask Question</b> to begin.</div>
              )}
              {history.map((row, i) => (
                <div key={i} className="space-y-2">
                  {row.question && <Bubble role="coach" text={row.question} />}
                  {row.response && <Bubble role="you" text={row.response} />}
                  {row.coach && <Bubble role="coach" text={row.coach} />}
                </div>
              ))}
              <AnimatePresence>
                {loadingChat && <TypingBubble />}
              </AnimatePresence>
            </div>

            <div className="mt-4 flex flex-col gap-3 md:flex-row md:items-center">
              <input
                className="flex-1 rounded-xl border border-slate-200 bg-white/80 px-4 py-2 shadow-sm backdrop-blur focus:outline-none focus:ring focus:ring-indigo-200"
                placeholder="Type your reply or use the mic…"
                value={chatInput}
                onChange={(e) => setChatInput(e.target.value)}
              />
              <div className="flex items-center gap-2">
                <InlineRecorder onTranscript={(t) => setChatInput((s) => (s ? s + " " + t : t))} />
                <Button onClick={sendChat} intent="dark" iconLeft={<Send className="h-4 w-4" />}>Send</Button>
              </div>
            </div>
          </Card>
        )}

        {/* Audio History */}
        {audioHistory.length > 0 && (
          <Card className="mt-6">
            <div className="flex items-center justify-between">
              <h2 className="text-lg font-semibold">Audio Playback History</h2>
              <Button onClick={() => setAudioHistory([])} intent="ghost" iconLeft={<History className="h-4 w-4" />}>Clear</Button>
            </div>
            <ul className="mt-3 space-y-2 text-sm">
              {[...audioHistory].reverse().slice(0, 10).map((item, idx) => (
                <li key={idx} className="flex items-center justify-between rounded-xl border border-slate-200 bg-white/80 px-3 py-2 shadow-sm">
                  <div className="truncate pr-3">
                    <div className="truncate text-slate-700">{item.url}</div>
                    <div className="text-xs text-slate-400">{new Date(item.ts).toLocaleTimeString()}</div>
                  </div>
                  <Button onClick={() => new Audio(item.url).play()} intent="dark">Replay</Button>
                </li>
              ))}
            </ul>
          </Card>
        )}

        <div className="mt-10 text-center text-xs text-slate-400">Built for local demo · API at {API_BASE}</div>
      </div>

      {/* Bottom Navigation with Press & Hold Mic */}
      <BottomBar onTranscript={onFloatingTranscript} onAsk={askQuestion} onSummary={getSummary} />
    </div>
  );
}

// ---------- UI helpers ----------
function Header({ ready }) {
  return (
    <div className="sticky top-0 z-10 -mx-4 mb-4 border-b border-slate-100/80 bg-white/70 backdrop-blur">
      <div className="mx-auto max-w-3xl px-4">
        <div className="flex items-center justify-between py-4">
          <div className="flex items-center gap-3">
            <div className="grid h-9 w-9 place-items-center rounded-2xl bg-gradient-to-tr from-slate-900 to-indigo-700 font-semibold text-white shadow">P</div>
            <div>
              <div className="text-base font-semibold leading-none">PsyCoach</div>
              <div className="text-xs text-slate-500">React + FastAPI (local)</div>
            </div>
          </div>
          <div className="flex items-center gap-2 text-xs">
            <span className={`inline-block h-2 w-2 rounded-full ${ready ? "bg-emerald-500" : "bg-slate-300"}`} />
            {ready ? "Backend reachable" : "Checking…"}
          </div>
        </div>
      </div>
    </div>
  );
}

function Card({ children, className = "" }) {
  return <div className={`rounded-2xl border border-slate-200/80 bg-white/80 p-4 shadow-sm backdrop-blur ${className}`}>{children}</div>;
}

function Pill({ icon, text }) {
  return (
    <div className="inline-flex items-center gap-2 rounded-full border border-slate-200 bg-white/80 px-3 py-1 text-xs text-slate-600 shadow-sm">
      {icon}
      <span>{text}</span>
    </div>
  );
}

function Button({ children, onClick, intent = "light", loading = false, iconLeft }) {
  const styles = {
    light: "bg-white text-slate-800 border border-slate-200 hover:bg-slate-50",
    primary: "bg-indigo-600 text-white hover:bg-indigo-500",
    dark: "bg-slate-900 text-white hover:bg-slate-800",
    ghost: "border border-slate-200 text-slate-700 hover:bg-slate-50",
  };
  return (
    <button onClick={onClick} disabled={loading} className={`inline-flex items-center gap-2 rounded-xl px-4 py-2 text-sm shadow-sm transition ${styles[intent]} ${loading ? "opacity-60" : ""}`}>
      {iconLeft}
      {loading ? "Please wait…" : children}
    </button>
  );
}

function LabeledInput({ label, className = "", type = "text", value, onChange }) {
  return (
    <label className={`flex flex-col gap-1 ${className}`}>
      <span className="text-xs font-medium text-slate-600">{label}</span>
      <input type={type} value={value} onChange={(e) => onChange(e.target.value)} className="rounded-xl border border-slate-200 bg-white/80 px-3 py-2 text-sm shadow-sm backdrop-blur focus:outline-none focus:ring focus:ring-indigo-200" />
    </label>
  );
}

function Bubble({ role, text }) {
  const isMe = role === "you";
  return (
    <motion.div initial={{ opacity: 0, y: 4 }} animate={{ opacity: 1, y: 0 }} className={`max-w-[85%] rounded-2xl px-4 py-2 text-sm shadow-sm ${isMe ? "ml-auto bg-indigo-600 text-white" : "mr-auto bg-white/90 text-slate-800 ring-1 ring-slate-100"}`}>
      {!isMe && <div className="mb-0.5 text-[10px] uppercase tracking-wide text-slate-500">Coach</div>}
      {isMe && <div className="mb-0.5 text-[10px] uppercase tracking-wide text-white/70">You</div>}
      <div className="whitespace-pre-wrap">{text}</div>
    </motion.div>
  );
}

function TypingBubble() {
  return (
    <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} exit={{ opacity: 0 }} className="mr-auto max-w-[85%] rounded-2xl bg-white/90 px-4 py-2 text-sm shadow-sm ring-1 ring-slate-100">
      <div className="mb-0.5 text-[10px] uppercase tracking-wide text-slate-500">Coach</div>
      <div className="flex items-center gap-1">
        <span className="h-1.5 w-1.5 animate-bounce rounded-full bg-slate-400 [animation-delay:-0.2s]" />
        <span className="h-1.5 w-1.5 animate-bounce rounded-full bg-slate-400" />
        <span className="h-1.5 w-1.5 animate-bounce rounded-full bg-slate-400 [animation-delay:0.2s]" />
      </div>
    </motion.div>
  );
}

// ---------- Recorder buttons (inline) ----------
function InlineRecorder({ onTranscript }) {
  const [recording, setRecording] = useState(false);
  const mediaRecorderRef = useRef(null);
  const chunksRef = useRef([]);

  const start = async () => {
    if (recording) return;
    const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
    const mr = new MediaRecorder(stream, { mimeType: "audio/webm" });
    chunksRef.current = [];
    mr.ondataavailable = (e) => e.data.size && chunksRef.current.push(e.data);
    mr.onstop = async () => {
      const blob = new Blob(chunksRef.current, { type: "audio/webm" });
      chunksRef.current = [];
      onTranscript && onTranscript(await sttUpload(blob));
      stream.getTracks().forEach((t) => t.stop());
    };
    mr.start();
    mediaRecorderRef.current = mr;
    setRecording(true);
  };

  const stop = () => {
    if (!recording || !mediaRecorderRef.current) return;
    mediaRecorderRef.current.stop();
    setRecording(false);
  };

  const sttUpload = async (blob) => {
    try {
      const fd = new FormData();
      fd.append("audio", blob, "clip.webm");
      const { data } = await api.post("/voice/utterance", fd, { headers: { "Content-Type": "multipart/form-data" } });
      return data?.text || "";
    } catch (e) {
      console.error(e);
      return "";
    }
  };

  return (
    <div className="flex items-center gap-2">
      {!recording ? (
        <button onClick={start} className="inline-flex items-center gap-2 rounded-xl border border-slate-200 bg-white/80 px-3 py-2 text-sm shadow-sm hover:bg-slate-50">
          <Mic className="h-4 w-4" /> Record
        </button>
      ) : (
        <button onClick={stop} className="inline-flex items-center gap-2 rounded-xl bg-rose-600 px-3 py-2 text-sm text-white shadow-sm hover:bg-rose-500">
          <Square className="h-4 w-4" /> Stop
        </button>
      )}
    </div>
  );
}

function BottomBar({ onTranscript, onAsk, onSummary }) {
  const [recording, setRecording] = useState(false);
  const mediaRecorderRef = useRef(null);
  const chunksRef = useRef([]);

  const start = async () => {
    if (recording) return;
    const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
    const mr = new MediaRecorder(stream, { mimeType: "audio/webm" });
    chunksRef.current = [];
    mr.ondataavailable = (e) => e.data.size && chunksRef.current.push(e.data);
    mr.onstop = async () => {
      const blob = new Blob(chunksRef.current, { type: "audio/webm" });
      chunksRef.current = [];
      onTranscript && onTranscript(await sttUpload(blob));
      stream.getTracks().forEach((t) => t.stop());
    };
    mr.start();
    mediaRecorderRef.current = mr;
    setRecording(true);
  };

  const stop = () => {
    if (!recording || !mediaRecorderRef.current) return;
    mediaRecorderRef.current.stop();
    setRecording(false);
  };

  const sttUpload = async (blob) => {
    try {
      const fd = new FormData();
      fd.append("audio", blob, "clip.webm");
      const { data } = await api.post("/voice/utterance", fd, { headers: { "Content-Type": "multipart/form-data" } });
      return data?.text || "";
    } catch (e) {
      console.error(e);
      return "";
    }
  };

  // Press & Hold handlers (desktop + mobile)
  const downProps = {
    onMouseDown: start,
    onMouseUp: stop,
    onMouseLeave: stop,
    onTouchStart: (e) => { e.preventDefault(); start(); },
    onTouchEnd: (e) => { e.preventDefault(); stop(); },
  };

  return (
    <div className="fixed inset-x-0 bottom-0 z-20 border-t border-slate-200/80 bg-white/80 backdrop-blur">
      <div className="mx-auto flex max-w-3xl items-center justify-between gap-4 px-4 py-3">
        <Button onClick={onAsk} intent="ghost" iconLeft={<MessageCircle className="h-4 w-4" />}>Ask</Button>
        <div className="relative">
          {recording && <span className="absolute -inset-3 animate-ping rounded-full bg-rose-400/60" />}
          <button
            {...downProps}
            className={`grid h-14 w-14 place-items-center rounded-full shadow-lg transition-colors ${recording ? "bg-rose-600 text-white" : "bg-slate-900 text-white hover:bg-slate-800"}`}
            title={recording ? "Release to stop" : "Press & hold to record"}
          >
            {recording ? <Square className="h-5 w-5" /> : <Mic className="h-5 w-5" />}
          </button>
        </div>
        <Button onClick={onSummary} intent="ghost">Summary</Button>
      </div>
    </div>
  );
}

function splitComma(v) {
  return (v || "").split(",").map((s) => s.trim()).filter(Boolean);
}

function msgOf(e) {
  if (e?.response?.data?.error) return e.response.data.error;
  if (typeof e?.message === "string") return e.message;
  try { return JSON.stringify(e?.response?.data || {}); } catch { return "Unknown error"; }
}
```



below is another version of src/App.jsx u can try this instead if u want(this is a complex version with some fake dashboard in quiz)

```bash
import React, { useEffect, useRef, useState } from "react";
import axios from "axios";
import { motion, AnimatePresence } from "framer-motion";
import {
  Mic,
  Square,
  Send,
  MessageCircle,
  Sparkles,
  History,
  Headphones,
  Settings,
  CheckCircle2,
  Activity,
  Gauge,
  Users,
  HeartHandshake,
  Smile
} from "lucide-react";

/**
 * PsyCoach — Deluxe React UI (Tailwind + Framer Motion)
 * - Bottom bar mic with press & hold
 * - Enhanced cards (coach board, quick actions, quick state check)
 * - Self-Assessment modal with progress + diagnosis (fake until backend adds /assessment/submit)
 *
 * Setup:
 *   npm i axios framer-motion lucide-react
 *   Tailwind per docs; .env -> VITE_API_URL=http://localhost:8000
 */

const API_BASE = import.meta.env.VITE_API_URL || "http://localhost:8000";
const api = axios.create({ baseURL: API_BASE, timeout: 20000 });

export default function App() {
  const [ready, setReady] = useState(false);
  const [error, setError] = useState("");

  // session / flow state
  const [sessionId, setSessionId] = useState("");
  const [stepInfo, setStepInfo] = useState(null); // { message, step, audio_url? }
  const [history, setHistory] = useState([]); // [{ question, response, coach }]

  // assessment state
  const [assessmentOpen, setAssessmentOpen] = useState(false);
  const [assessmentStep, setAssessmentStep] = useState(0);
  const [assessmentAnswers, setAssessmentAnswers] = useState({});
  const [assessmentLoading, setAssessmentLoading] = useState(false);
  const [assessmentResult, setAssessmentResult] = useState(null); // {summary, score, plan, audio_url?}

  // TTS prefs
  const [enableTTS, setEnableTTS] = useState(true);
  const [voiceName, setVoiceName] = useState("Rachel");

  // inputs
  const [stepInput, setStepInput] = useState("");
  const [chatInput, setChatInput] = useState("");

  // audio playback history
  const [audioHistory, setAudioHistory] = useState([]); // [{url, ts}]

  // loading flags
  const [loadingStep, setLoadingStep] = useState(false);
  const [loadingChat, setLoadingChat] = useState(false);
  const [creating, setCreating] = useState(false);

  // demo profile
  const [profile, setProfile] = useState({
    name: "Demo",
    age: 22,
    weight: 60,
    height: 170,
    sport_type: "Endurance Sports",
    athlete_level: "Intermediate",
    training_frequency: 3,
    goals: ["reduce stress"],
    preferences: { voice_interaction: "Text Only" },
  });

  // health check
  useEffect(() => {
    (async () => {
      try {
        await api.get("/media/does-not-exist");
      } catch (_) {
        setReady(true); // 404 means server reachable
      }
    })().catch(() => setError("Backend not reachable"));
  }, []);

  const playIfAny = (audioUrl) => {
    if (!audioUrl) return;
    const src = audioUrl.startsWith("http") ? audioUrl : API_BASE + audioUrl;
    const a = new Audio(src);
    a.play().catch(() => {});
    setAudioHistory((h) => [...h, { url: src, ts: Date.now() }]);
  };

  const createSession = async () => {
    setError("");
    setCreating(true);
    try {
      const { data } = await api.post(
        `/voice/session?tts=${enableTTS}&voice=${encodeURIComponent(voiceName || "")}`,
        profile
      );
      setSessionId(data.sessionId);
      setStepInfo(data.next);
      setHistory([]);
      setStepInput("");
      playIfAny(data?.next?.audio_url);
    } catch (e) {
      setError(msgOf(e));
    } finally {
      setCreating(false);
    }
  };

  const submitStep = async () => {
    if (!sessionId || !stepInfo) return;
    const payload = { session_id: sessionId, step: stepInfo.step, user_input: stepInput };
    setError("");
    setLoadingStep(true);
    try {
      const { data } = await api.post(
        `/voice/step?tts=${enableTTS}&voice=${encodeURIComponent(voiceName || "")}`,
        payload
      );
      setStepInfo(data);
      setStepInput("");
      playIfAny(data?.audio_url);
    } catch (e) {
      setError(msgOf(e));
    } finally {
      setLoadingStep(false);
    }
  };

  const askQuestion = async () => {
    if (!sessionId) return;
    setError("");
    setLoadingChat(true);
    try {
      const { data } = await api.post(
        `/voice/question?tts=${enableTTS}&voice=${encodeURIComponent(voiceName || "")}`,
        null,
        { params: { session_id: sessionId } }
      );
      setHistory((h) => [...h, { question: data.question }]);
      playIfAny(data?.audio_url);
    } catch (e) {
      setError(msgOf(e));
    } finally {
      setLoadingChat(false);
    }
  };

  const sendChat = async () => {
    if (!sessionId || !history.length) return;
    const last = history[history.length - 1];
    const optimistic = [...history.slice(0, -1), { ...last, response: chatInput }];
    setHistory(optimistic);
    const toSend = chatInput; // store before clearing
    setChatInput("");
    setLoadingChat(true);
    try {
      const { data } = await api.post(
        `/voice/respond?tts=${enableTTS}&voice=${encodeURIComponent(voiceName || "")}`,
        {
          session_id: sessionId,
          user_message: toSend,
          history: optimistic,
        }
      );
      setHistory((h) => {
        const base = [...h];
        base[base.length - 1] = { ...base[base.length - 1], coach: data.response };
        return base;
      });
      playIfAny(data?.audio_url);
    } catch (e) {
      setError(msgOf(e));
    } finally {
      setLoadingChat(false);
    }
  };

  const getSummary = async () => {
    if (!sessionId) return;
    setError("");
    setLoadingChat(true);
    try {
      const { data } = await api.post(
        `/voice/summary?tts=${enableTTS}&voice=${encodeURIComponent(voiceName || "")}`,
        null,
        { params: { session_id: sessionId } }
      );
      alert(data.summary || "No summary returned");
      playIfAny(data?.audio_url);
    } catch (e) {
      setError(msgOf(e));
    } finally {
      setLoadingChat(false);
    }
  };

  // ---------- Assessment flow ----------
  const assessmentQuestions = [
    {
      key: "execution",
      title: "How well did you follow your plan?",
      options: ["Never", "Rarely", "Sometimes", "Often", "Very Often"],
    },
    {
      key: "mood",
      title: "How did you feel overall today?",
      options: ["Very Low", "Low", "Neutral", "Good", "Great"],
    },
    {
      key: "fatigue",
      title: "How fatigued are you now?",
      options: ["None", "Mild", "Moderate", "High", "Extreme"],
    },
  ];

  const openAssessmentWithState = (stateLabel) => {
    setAssessmentOpen(true);
    setAssessmentStep(0);
    setAssessmentAnswers((a) => ({ ...a, quick_state: stateLabel }));
    setAssessmentResult(null);
  };

  const submitAssessment = async () => {
    setAssessmentLoading(true);
    setError("");
    try {
      const payload = {
        session_id: sessionId || null,
        answers: assessmentAnswers,
      };
      const url = `/assessment/submit?tts=${enableTTS}&voice=${encodeURIComponent(voiceName || "")}`;
      let data;
      try {
        const res = await api.post(url, payload);
        data = res.data;
      } catch (err) {
        // Backend not ready — synthesize a local diagnosis
        const score = pseudoScore(assessmentAnswers);
        data = {
          summary:
            score >= 75
              ? "You're in a strong performance state. Keep volume steady and prioritize sleep hygiene."
              : score >= 50
              ? "Moderate readiness. Reduce intensity 10–15% and add a breathing reset between sets."
              : "Low readiness today. Switch to technique drills and a 12‑minute mindfulness reset.",
          score,
          plan: [
            "Warm‑up: 6 min nasal breathing + mobility",
            "Main: technique/low‑impact intervals (20–30m)",
            "Cooldown: box breathing 4‑4‑6‑2 (5m)",
          ],
          audio_url: null,
        };
      }
      setAssessmentResult(data);
      playIfAny(data?.audio_url);
    } catch (e) {
      setError(msgOf(e));
    } finally {
      setAssessmentLoading(false);
    }
  };

  // Floating mic should auto-target whichever input is relevant
  const onFloatingTranscript = (t) => {
    if (stepInfo && stepInfo.step && stepInfo.step !== "complete") {
      setStepInput((s) => (s ? s + " " + t : t));
    } else {
      setChatInput((s) => (s ? s + " " + t : t));
    }
  };

  return (
    <div className="relative min-h-screen overflow-hidden bg-gradient-to-b from-indigo-50 via-violet-50 to-white text-slate-800">
      {/* Decorative blobs */}
      <div className="pointer-events-none absolute -top-24 left-1/2 -z-10 h-80 w-80 -translate-x-1/2 rounded-full bg-gradient-to-tr from-indigo-300/50 to-fuchsia-300/40 blur-3xl" />
      <div className="pointer-events-none absolute -bottom-24 right-10 -z-10 h-72 w-72 rounded-full bg-gradient-to-tr from-cyan-300/40 to-emerald-300/40 blur-3xl" />

      <div className="mx-auto max-w-3xl px-4 pb-36">
        <Header ready={ready} />

        {error && (
          <motion.div
            initial={{ opacity: 0, y: -6 }}
            animate={{ opacity: 1, y: 0 }}
            className="mt-4 rounded-xl border border-red-200 bg-red-50 px-4 py-3 text-sm text-red-700 shadow"
          >
            {error}
          </motion.div>
        )}

        {/* Coach board & quick actions */}
        <CoachBoard onQuickState={openAssessmentWithState} />

        {/* Preferences */}
        <Card className="mt-6">
          <div className="flex flex-wrap items-center gap-3">
            <Pill icon={<Headphones className="h-4 w-4" />} text="Speech Options" />
            <label className="inline-flex items-center gap-2 text-sm">
              <input
                type="checkbox"
                className="h-4 w-4 accent-indigo-600"
                checked={enableTTS}
                onChange={(e) => setEnableTTS(e.target.checked)}
              />
              Enable TTS in responses
            </label>
            <div className="flex items-center gap-2">
              <input
                className="rounded-xl border border-slate-200 bg-white/80 px-3 py-2 text-sm shadow-sm backdrop-blur focus:outline-none focus:ring focus:ring-indigo-200"
                placeholder="Voice name (e.g., Rachel)"
                value={voiceName}
                onChange={(e) => setVoiceName(e.target.value)}
                style={{ minWidth: 220 }}
              />
              <span className="text-xs text-slate-400">ElevenLabs name or local TTS</span>
            </div>
          </div>
        </Card>

        {/* Session */}
        <Card className="mt-6">
          <div className="flex items-center justify-between gap-4">
            <h2 className="text-lg font-semibold">Session</h2>
            <div className="flex items-center gap-2 text-xs text-slate-500">
              <Settings className="h-3.5 w-3.5" /> API: {API_BASE}
            </div>
          </div>
          {!sessionId ? (
            <div className="mt-4 grid grid-cols-1 gap-3 md:grid-cols-2">
              <LabeledInput label="Name" value={profile.name} onChange={(v) => setProfile((p) => ({ ...p, name: v }))} />
              <LabeledInput label="Age" type="number" value={profile.age} onChange={(v) => setProfile((p) => ({ ...p, age: Number(v) }))} />
              <LabeledInput label="Weight (kg)" type="number" value={profile.weight} onChange={(v) => setProfile((p) => ({ ...p, weight: Number(v) }))} />
              <LabeledInput label="Height (cm)" type="number" value={profile.height} onChange={(v) => setProfile((p) => ({ ...p, height: Number(v) }))} />
              <LabeledInput label="Sport Type" value={profile.sport_type} onChange={(v) => setProfile((p) => ({ ...p, sport_type: v }))} />
              <LabeledInput label="Athlete Level" value={profile.athlete_level} onChange={(v) => setProfile((p) => ({ ...p, athlete_level: v }))} />
              <LabeledInput
                label="Goals (comma separated)"
                value={profile.goals.join(", ")}
                onChange={(v) => setProfile((p) => ({ ...p, goals: splitComma(v) }))}
                className="md:col-span-2"
              />
              <Button onClick={createSession} loading={creating} iconLeft={<Sparkles className="h-4 w-4" />}>Create Session</Button>
            </div>
          ) : (
            <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} className="mt-3 text-sm">
              <div className="flex items-center gap-2 rounded-lg bg-slate-50 px-3 py-2">
                <CheckCircle2 className="h-4 w-4 text-emerald-500" />
                <span className="font-mono text-slate-700">sessionId</span>: {sessionId}
              </div>
            </motion.div>
          )}
        </Card>

        {/* Step-by-step */}
        {sessionId && stepInfo && stepInfo.step !== "complete" && (
          <Card className="mt-6">
            <h2 className="text-lg font-semibold">Guided Setup</h2>
            <p className="mt-2 text-sm text-slate-600">Coach asks:</p>
            <motion.div
              initial={{ opacity: 0, y: 6 }}
              animate={{ opacity: 1, y: 0 }}
              className="mt-2 rounded-xl bg-white/80 px-4 py-3 text-slate-800 shadow-inner ring-1 ring-slate-100 backdrop-blur"
            >
              {stepInfo.message}
            </motion.div>

            <div className="mt-3 flex flex-col gap-3 md:flex-row md:items-center">
              <input
                className="flex-1 rounded-xl border border-slate-200 bg-white/80 px-4 py-2 shadow-sm backdrop-blur focus:outline-none focus:ring focus:ring-indigo-200"
                placeholder="Type your answer or use the mic…"
                value={stepInput}
                onChange={(e) => setStepInput(e.target.value)}
              />
              <div className="flex items-center gap-2">
                <InlineRecorder onTranscript={(t) => setStepInput((s) => (s ? s + " " + t : t))} />
                <Button onClick={submitStep} loading={loadingStep} intent="primary" iconLeft={<Send className="h-4 w-4" />}>Send</Button>
              </div>
            </div>
          </Card>
        )}

        {/* Chat */}
        {sessionId && (
          <Card className="mt-6">
            <div className="flex items-center justify-between">
              <h2 className="text-lg font-semibold">Coaching Chat</h2>
              <div className="flex items-center gap-2">
                <Button onClick={askQuestion} intent="ghost" iconLeft={<MessageCircle className="h-4 w-4" />}>Ask Question</Button>
                <Button onClick={getSummary} intent="ghost">Get Summary</Button>
              </div>
            </div>

            <div className="mt-4 space-y-3">
              {history.length === 0 && (
                <div className="rounded-xl border border-dashed border-slate-200 p-6 text-center text-sm text-slate-500">
                  No messages yet. Click <b>Ask Question</b> to begin.
                </div>
              )}
              {history.map((row, i) => (
                <div key={i} className="space-y-2">
                  {row.question && <Bubble role="coach" text={row.question} />}
                  {row.response && <Bubble role="you" text={row.response} />}
                  {row.coach && <Bubble role="coach" text={row.coach} />}
                </div>
              ))}
              <AnimatePresence>{loadingChat && <TypingBubble />}</AnimatePresence>
            </div>

            <div className="mt-4 flex flex-col gap-3 md:flex-row md:items-center">
              <input
                className="flex-1 rounded-xl border border-slate-200 bg-white/80 px-4 py-2 shadow-sm backdrop-blur focus:outline-none focus:ring focus:ring-indigo-200"
                placeholder="Type your reply or use the mic…"
                value={chatInput}
                onChange={(e) => setChatInput(e.target.value)}
              />
              <div className="flex items-center gap-2">
                <InlineRecorder onTranscript={(t) => setChatInput((s) => (s ? s + " " + t : t))} />
                <Button onClick={sendChat} intent="dark">Send</Button>
              </div>
            </div>
          </Card>
        )}

        {/* Audio History */}
        {audioHistory.length > 0 && (
          <Card className="mt-6">
            <div className="flex items-center justify-between">
              <h2 className="text-lg font-semibold">Audio Playback History</h2>
              <Button onClick={() => setAudioHistory([])} intent="ghost" iconLeft={<History className="h-4 w-4" />}>Clear</Button>
            </div>
            <ul className="mt-3 space-y-2 text-sm">
              {[...audioHistory].reverse().slice(0, 10).map((item, idx) => (
                <li
                  key={idx}
                  className="flex items-center justify-between rounded-xl border border-slate-200 bg-white/80 px-3 py-2 shadow-sm"
                >
                  <div className="truncate pr-3">
                    <div className="truncate text-slate-700">{item.url}</div>
                    <div className="text-xs text-slate-400">{new Date(item.ts).toLocaleTimeString()}</div>
                  </div>
                  <Button onClick={() => new Audio(item.url).play()} intent="dark">Replay</Button>
                </li>
              ))}
            </ul>
          </Card>
        )}

        <div className="mt-10 text-center text-xs text-slate-400">Built for local demo · API at {API_BASE}</div>
      </div>

      {/* Bottom Navigation with Press & Hold Mic */}
      <BottomBar onTranscript={onFloatingTranscript} onAsk={askQuestion} onSummary={getSummary} />

      {/* Assessment Modal */}
      <AssessmentModal
        open={assessmentOpen}
        onClose={() => setAssessmentOpen(false)}
        step={assessmentStep}
        setStep={setAssessmentStep}
        answers={assessmentAnswers}
        setAnswers={setAssessmentAnswers}
        questions={assessmentQuestions}
        onSubmit={submitAssessment}
        loading={assessmentLoading}
        result={assessmentResult}
      />
    </div>
  );
}

// ---------- UI helpers ----------
function Header({ ready }) {
  return (
    <div className="sticky top-0 z-10 -mx-4 mb-4 border-b border-slate-100/80 bg-white/70 backdrop-blur">
      <div className="mx-auto max-w-3xl px-4">
        <div className="flex items-center justify-between py-4">
          <div className="flex items-center gap-3">
            <div className="grid h-9 w-9 place-items-center rounded-2xl bg-gradient-to-tr from-slate-900 to-indigo-700 font-semibold text-white shadow">
              P
            </div>
            <div>
              <div className="text-base font-semibold leading-none">PsyCoach</div>
              <div className="text-xs text-slate-500">React + FastAPI (local)</div>
            </div>
          </div>
          <div className="flex items-center gap-2 text-xs">
            <span className={`inline-block h-2 w-2 rounded-full ${ready ? "bg-emerald-500" : "bg-slate-300"}`} />
            {ready ? "Backend reachable" : "Checking…"}
          </div>
        </div>
      </div>
    </div>
  );
}

function CoachBoard({ onQuickState }) {
  const chips = [
    { label: "Energized", color: "from-emerald-400 to-teal-500" },
    { label: "Focused", color: "from-indigo-400 to-violet-500" },
    { label: "Balanced", color: "from-sky-400 to-cyan-500" },
    { label: "Fatigued", color: "from-orange-400 to-rose-500" },
    { label: "Burned Out", color: "from-rose-400 to-pink-500" },
  ];
  return (
    <Card className="mt-4">
      <div className="flex items-start justify-between gap-3">
        <div className="flex items-center gap-3">
          <div className="grid h-12 w-12 place-items-center rounded-2xl bg-gradient-to-tr from-indigo-600 to-fuchsia-600 text-white shadow">
            <Smile className="h-6 w-6" />
          </div>
          <div>
            <div className="text-base font-semibold">Coach Motin</div>
            <div className="text-xs text-emerald-600">● Calm, here to coach you</div>
          </div>
        </div>
        <div className="flex items-center gap-2 text-xs text-slate-500">
          <Activity className="h-4 w-4" />
          HRV: —
          <Gauge className="h-4 w-4 ml-3" />
          Load: —
        </div>
      </div>

      <div className="mt-4 flex flex-wrap gap-2">
        {chips.map((c) => (
          <button
            key={c.label}
            onClick={() => onQuickState(c.label)}
            className={`rounded-xl bg-gradient-to-r ${c.color} px-3 py-1.5 text-xs text-white shadow-sm hover:opacity-90`}
          >
            {c.label}
          </button>
        ))}
      </div>
    </Card>
  );
}

function Card({ children, className = "" }) {
  return (
    <div className={`rounded-2xl border border-slate-200/80 bg-white/80 p-4 shadow-sm backdrop-blur ${className}`}>
      {children}
    </div>
  );
}

function Pill({ icon, text }) {
  return (
    <div className="inline-flex items-center gap-2 rounded-full border border-slate-200 bg-white/80 px-3 py-1 text-xs text-slate-600 shadow-sm">
      {icon}
      <span>{text}</span>
    </div>
  );
}

function Button({ children, onClick, intent = "light", loading = false, iconLeft }) {
  const styles = {
    light: "bg-white text-slate-800 border border-slate-200 hover:bg-slate-50",
    primary: "bg-indigo-600 text-white hover:bg-indigo-500",
    dark: "bg-slate-900 text-white hover:bg-slate-800",
    ghost: "border border-slate-200 text-slate-700 hover:bg-slate-50",
  };
  return (
    <button
      onClick={onClick}
      disabled={loading}
      className={`inline-flex items-center gap-2 rounded-xl px-4 py-2 text-sm shadow-sm transition ${styles[intent]} ${
        loading ? "opacity-60" : ""
      }`}
    >
      {iconLeft}
      {loading ? "Please wait…" : children}
    </button>
  );
}

function LabeledInput({ label, className = "", type = "text", value, onChange }) {
  return (
    <label className={`flex flex-col gap-1 ${className}`}>
      <span className="text-xs font-medium text-slate-600">{label}</span>
      <input
        type={type}
        value={value}
        onChange={(e) => onChange(e.target.value)}
        className="rounded-xl border border-slate-200 bg-white/80 px-3 py-2 text-sm shadow-sm backdrop-blur focus:outline-none focus:ring focus:ring-indigo-200"
      />
    </label>
  );
}

function Bubble({ role, text }) {
  const isMe = role === "you";
  return (
    <motion.div
      initial={{ opacity: 0, y: 4 }}
      animate={{ opacity: 1, y: 0 }}
      className={`max-w-[85%] rounded-2xl px-4 py-2 text-sm shadow-sm ${
        isMe ? "ml-auto bg-indigo-600 text-white" : "mr-auto bg-white/90 text-slate-800 ring-1 ring-slate-100"
      }`}
    >
      {!isMe && (
        <div className="mb-0.5 text-[10px] uppercase tracking-wide text-slate-500">Coach</div>
      )}
      {isMe && (
        <div className="mb-0.5 text-[10px] uppercase tracking-wide text-white/70">You</div>
      )}
      <div className="whitespace-pre-wrap">{text}</div>
    </motion.div>
  );
}

function TypingBubble() {
  return (
    <motion.div
      initial={{ opacity: 0 }}
      animate={{ opacity: 1 }}
      exit={{ opacity: 0 }}
      className="mr-auto max-w-[85%] rounded-2xl bg-white/90 px-4 py-2 text-sm shadow-sm ring-1 ring-slate-100"
    >
      <div className="mb-0.5 text-[10px] uppercase tracking-wide text-slate-500">Coach</div>
      <div className="flex items-center gap-1">
        <span className="h-1.5 w-1.5 animate-bounce rounded-full bg-slate-400 [animation-delay:-0.2s]" />
        <span className="h-1.5 w-1.5 animate-bounce rounded-full bg-slate-400" />
        <span className="h-1.5 w-1.5 animate-bounce rounded-full bg-slate-400 [animation-delay:0.2s]" />
      </div>
    </motion.div>
  );
}

// ---------- Recorder (inline) ----------
function InlineRecorder({ onTranscript }) {
  const [recording, setRecording] = useState(false);
  const mediaRecorderRef = useRef(null);
  const chunksRef = useRef([]);

  const start = async () => {
    if (recording) return;
    const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
    const mr = new MediaRecorder(stream, { mimeType: "audio/webm" });
    chunksRef.current = [];
    mr.ondataavailable = (e) => e.data.size && chunksRef.current.push(e.data);
    mr.onstop = async () => {
      const blob = new Blob(chunksRef.current, { type: "audio/webm" });
      chunksRef.current = [];
      onTranscript && onTranscript(await sttUpload(blob));
      stream.getTracks().forEach((t) => t.stop());
    };
    mr.start();
    mediaRecorderRef.current = mr;
    setRecording(true);
  };

  const stop = () => {
    if (!recording || !mediaRecorderRef.current) return;
    mediaRecorderRef.current.stop();
    setRecording(false);
  };

  const sttUpload = async (blob) => {
    try {
      const fd = new FormData();
      fd.append("audio", blob, "clip.webm");
      const { data } = await api.post("/voice/utterance", fd, {
        headers: { "Content-Type": "multipart/form-data" },
      });
      return data?.text || "";
    } catch (e) {
      console.error(e);
      return "";
    }
  };

  return (
    <div className="flex items-center gap-2">
      {!recording ? (
        <button className="inline-flex items-center gap-2 rounded-xl border border-slate-200 bg-white/80 px-3 py-2 text-sm shadow-sm hover:bg-slate-50" onClick={start}>
          <Mic className="h-4 w-4" /> Record
        </button>
      ) : (
        <button className="inline-flex items-center gap-2 rounded-xl bg-rose-600 px-3 py-2 text-sm text-white shadow-sm hover:bg-rose-500" onClick={stop}>
          <Square className="h-4 w-4" /> Stop
        </button>
      )}
    </div>
  );
}

function BottomBar({ onTranscript, onAsk, onSummary }) {
  const [recording, setRecording] = useState(false);
  const mediaRecorderRef = useRef(null);
  const chunksRef = useRef([]);

  const start = async () => {
    if (recording) return;
    const stream = await navigator.mediaDevices.getUserMedia({ audio: true });
    const mr = new MediaRecorder(stream, { mimeType: "audio/webm" });
    chunksRef.current = [];
    mr.ondataavailable = (e) => e.data.size && chunksRef.current.push(e.data);
    mr.onstop = async () => {
      const blob = new Blob(chunksRef.current, { type: "audio/webm" });
      chunksRef.current = [];
      onTranscript && onTranscript(await sttUpload(blob));
      stream.getTracks().forEach((t) => t.stop());
    };
    mr.start();
    mediaRecorderRef.current = mr;
    setRecording(true);
  };

  const stop = () => {
    if (!recording || !mediaRecorderRef.current) return;
    mediaRecorderRef.current.stop();
    setRecording(false);
  };

  const sttUpload = async (blob) => {
    try {
      const fd = new FormData();
      fd.append("audio", blob, "clip.webm");
      const { data } = await api.post("/voice/utterance", fd, {
        headers: { "Content-Type": "multipart/form-data" },
      });
      return data?.text || "";
    } catch (e) {
      console.error(e);
      return "";
    }
  };

  const downProps = {
    onMouseDown: start,
    onMouseUp: stop,
    onMouseLeave: stop,
    onTouchStart: (e) => {
      e.preventDefault();
      start();
    },
    onTouchEnd: (e) => {
      e.preventDefault();
      stop();
    },
  };

  return (
    <div className="fixed inset-x-0 bottom-0 z-20 border-t border-slate-200/80 bg-white/80 backdrop-blur">
      <div className="mx-auto flex max-w-3xl items-center justify-between gap-4 px-4 py-3">
        <Button onClick={onAsk} intent="ghost" iconLeft={<MessageCircle className="h-4 w-4" />}>Ask</Button>
        <div className="relative">
          {recording && <span className="absolute -inset-3 animate-ping rounded-full bg-rose-400/60" />}
          <button
            {...downProps}
            className={`grid h-14 w-14 place-items-center rounded-full shadow-lg transition-colors ${
              recording ? "bg-rose-600 text-white" : "bg-slate-900 text-white hover:bg-slate-800"
            }`}
            title={recording ? "Release to stop" : "Press & hold to record"}
          >
            {recording ? <Square className="h-5 w-5" /> : <Mic className="h-5 w-5" />}
          </button>
        </div>
        <Button onClick={onSummary} intent="ghost">Summary</Button>
      </div>
    </div>
  );
}

// ---------- Assessment Modal ----------
function AssessmentModal({ open, onClose, step, setStep, questions, answers, setAnswers, onSubmit, loading, result }) {
  if (!open) return null;
  const total = questions.length;
  const progress = Math.round(((step) / total) * 100);

  const setValue = (key, value) => setAnswers((a) => ({ ...a, [key]: value }));

  return (
    <div className="fixed inset-0 z-30 grid place-items-center bg-slate-900/30 p-4 backdrop-blur-sm">
      <div className="w-full max-w-md rounded-3xl border border-slate-200/60 bg-white/90 p-5 shadow-xl backdrop-blur">
        <div className="flex items-center justify-between">
          <div className="text-base font-semibold">Self‑Assessment</div>
          <button className="text-slate-500 hover:text-slate-700" onClick={onClose}>Close</button>
        </div>

        {!result ? (
          <>
            <div className="mt-2 h-1.5 w-full overflow-hidden rounded-full bg-slate-100">
              <div className="h-full bg-gradient-to-r from-fuchsia-500 to-indigo-500" style={{ width: `${progress}%` }} />
            </div>

            <div className="mt-4">
              {questions.slice(step, step + 1).map((q) => (
                <div key={q.key}>
                  <div className="text-sm font-medium text-slate-700">{q.title}</div>
                  <div className="mt-3 space-y-2">
                    {q.options.map((op) => (
                      <label
                        key={op}
                        className={`flex cursor-pointer items-center justify-between rounded-2xl border px-3 py-2 text-sm shadow-sm transition ${
                          answers[q.key] === op
                            ? "border-indigo-300 bg-indigo-50"
                            : "border-slate-200 bg-white/80 hover:bg-slate-50"
                        }`}
                        onClick={() => setValue(q.key, op)}
                      >
                        <span>{op}</span>
                        {answers[q.key] === op && (
                          <span className="text-xs text-indigo-600">Selected</span>
                        )}
                      </label>
                    ))}
                  </div>
                </div>
              ))}
            </div>

            <div className="mt-5 flex items-center justify-between">
              <button
                className="rounded-xl border border-slate-200 px-4 py-2 text-sm hover:bg-slate-50"
                onClick={() => setStep((s) => Math.max(0, s - 1))}
                disabled={step === 0}
              >
                Back
              </button>
              {step < total - 1 ? (
                <button
                  className="rounded-xl bg-indigo-600 px-4 py-2 text-sm text-white hover:bg-indigo-500"
                  onClick={() => setStep((s) => s + 1)}
                >
                  Next
                </button>
              ) : (
                <button
                  className="rounded-xl bg-gradient-to-r from-fuchsia-600 to-indigo-600 px-4 py-2 text-sm text-white shadow-sm hover:brightness-110 disabled:opacity-60"
                  onClick={onSubmit}
                  disabled={loading}
                >
                  {loading ? "Submitting…" : "Finish & Diagnose"}
                </button>
              )}
            </div>
          </>
        ) : (
          <div className="mt-3">
            <div className="text-sm font-semibold text-slate-800">Suggested Plan</div>
            <div className="mt-2 rounded-2xl bg-gradient-to-r from-indigo-50 to-fuchsia-50 p-4 text-sm text-slate-700 ring-1 ring-slate-100">
              <div className="mb-2 font-medium">Readiness Score: {Math.round(result.score)}</div>
              <div className="mb-3">{result.summary}</div>
              <ul className="list-disc pl-5">
                {result.plan?.map((p, i) => (
                  <li key={i}>{p}</li>
                ))}
              </ul>
            </div>
            <div className="mt-4 text-right">
              <button className="rounded-xl border border-slate-200 px-4 py-2 text-sm hover:bg-slate-50" onClick={onClose}>Close</button>
            </div>
          </div>
        )}
      </div>
    </div>
  );
}

// ---------- Utils ----------
function splitComma(v) {
  return (v || "").split(",").map((s) => s.trim()).filter(Boolean);
}

function msgOf(e) {
  if (e?.response?.data?.error) return e.response.data.error;
  if (typeof e?.message === "string") return e.message;
  try {
    return JSON.stringify(e?.response?.data || {});
  } catch {
    return "Unknown error";
  }
}

function pseudoScore(answers) {
  // quick mock: map chosen index to score, then average
  const weights = { execution: 0.4, mood: 0.3, fatigue: 0.3 };
  const scale = (arr, v) => (arr.indexOf(v) + 1) * (100 / arr.length);
  const ex = scale(["Never", "Rarely", "Sometimes", "Often", "Very Often"], answers.execution || "Sometimes");
  const md = scale(["Very Low", "Low", "Neutral", "Good", "Great"], answers.mood || "Neutral");
  const ft = scale(["None", "Mild", "Moderate", "High", "Extreme"], answers.fatigue || "Moderate");
  return ex * weights.execution + md * weights.mood + (100 - ft) * weights.fatigue;
}
```


---

### Start the frontend:

```bash
npm run dev
```

Open:
[http://localhost:5173](http://localhost:5173)

---

## ✅ Key points for success

* **Must** start with `uvicorn api:app` — don’t run `streamlit run voice.py`
* `.env` must have the correct `VITE_API_URL`
* CORS is currently wide open for development. Later, you can restrict to:

  ```python
  allow_origins=["http://localhost:5173"]
  ```
* Ollama / ElevenLabs are optional — without them, TTS falls back to `pyttsx3`
* With `/voice/utterance` and `/voice/tts`, the frontend can:
  record audio → upload for STT → coach generates reply → reply converted to audio for playback

---

# Ella Tso | Portfolio

:::info
**AI/ML · Full-Stack Developer · Student Entrepreneur**

🎓 National Yang Ming Chiao Tung University | Information Management & Finance  
📍 Hsinchu, Taiwan  
📧 ella.tso.cc@gmail.com  
🔗 [GitHub](https://github.com/ellatso) | [LinkedIn](#)

**Specializations**: AI × FinTech × Sustainability  
**Languages**: Python, C++, JavaScript/React.js, Java
:::

---

## 🏆 Featured Achievements

| Competition | Achievement | Date |
|------------|-------------|------|
| **Mei-Chu Hackathon 2025** | 🥈 2nd Place (Maker Track) | Sep 2025 |
| **Hult Prize 2025** | 🌏 Global Top 5% / Taiwan Top 19 | May 2025 |
| **IDEA FinTech 2025** | 🏁 Quarter-Finalist (Top 8) | June 2025 |
| **Global AI Hackathon**( MIT Sloan AI Club Co-host) | participant | Aug 2025 |
| **Raise Ur Hack**( Palais du Louvre, Paris) | participant | July 2025 |

---

## 🚀 Featured Projects

### 1. GLIDE - AI Traffic Coordination System
**Mei-Chu Hackathon 2025 | 2nd Place, Maker Track**


![GLIDE Dashboard](https://g0v.hackmd.io/_uploads/H1gtPqznxbe.png)
![](https://g0v.hackmd.io/_uploads/HyEtcMngZx.png)


**The Challenge**  
Urban traffic congestion in Taipei costs the city an estimated $2.3 billion annually in lost productivity and increased emissions. Traditional traffic light systems operate on fixed timing schedules, unable to adapt to:

Peak hour congestion with 60%+ longer commute times
Bus bunching causing irregular service and passenger frustration
Emergency vehicle delays - average 3-5 minutes lost at intersections
Pedestrian safety concerns - especially for elderly crossing major arterials

The core problem: Static traffic control cannot handle dynamic, real-world complexity. We needed an intelligent system that could coordinate multi-intersection traffic in real-time while prioritizing safety and efficiency.

**Our Solution**  
GLIDE (Green Light Intelligent Dynamic Engine) is an AI-powered traffic coordination system that uses multi-agent deep reinforcement learning to optimize urban traffic flow across multiple intersections simultaneously.
Core Innovation: Four Integrated Algorithms

🌊 Green Wave Optimization

DQN-based adaptive signal timing
Coordinates 5+ consecutive intersections
Reduces stops by up to 40% during rush hour


👥 Pedestrian-Adaptive Crossing

Computer vision for real-time crowd detection
Dynamic crossing time allocation (elderly support)
Safety-first priority with smart pre-emptive signals


🚌 Bus Coordination & Anti-Bunching

Real-time headway monitoring
Predictive hold/release strategies
Maintains 180s target headway (±30s accuracy)


🚑 Emergency Vehicle Priority

500m advance detection system
Automatic green corridor creation
30s average time saved per intersection




**Tech Stack**
```
AI/ML Core

PyTorch - Deep learning framework
Stable-Baselines3 - Multi-agent DQN implementation
OpenAI Gym - Custom traffic environment

Traffic Simulation

SUMO (Simulation of Urban MObility) - Microscopic traffic simulator
TraCI API - Real-time control interface
SUMO-RL - Reinforcement learning integration

Backend

Python 3.9+ - Core logic
FastAPI - REST API services
WebSocket - Real-time data streaming

Frontend

React 18 - UI framework
TypeScript - Type-safe development
Chart.js - Real-time data visualization
Tailwind CSS - Responsive design

DevOps

Docker - Containerization
GitHub Actions - CI/CD pipeline
pytest - Automated testing
```

**Key Results**
- ✅ **30% improvement** in simulated corridor flow
- ✅ **28% throughput** during peak hours
- ✅ **62% reduction** in vehicle stops
- ✅ Prioritized pedestrian safety in algorithm design
- 🏆 **Recognition from Hsinchu County Transportation Bureau**

**My Role**: Captain, Full-Stack Developer & Tech Lead
- Led cross-functional team through 48-hour hackathon
- Designed and implemented RL algorithm for multi-intersection coordination
- Built React dashboard with real-time traffic visualization
- Pitched solution to government officials and judges

**Impact & Recognition**  
> Received recognition from the Hsinchu County Transportation Bureau and Youth Department Director for its potential public value.
![](https://g0v.hackmd.io/_uploads/Byyj5f3gZl.png)

**Technical Deep Dive**
- **State Space**: Queue length, waiting time, pedestrian requests, real-time density
- **Action Space**: Phase switching decisions
- **Reward Function**: Safety-first + corridor efficiency optimization

[GitHub Repo](https://github.com/ellatso/meichuhackathonteam8/blob/main/README.md)

---

### 2. DevNewsCopilot - AI Tech News Assistant
**Raise Ur Hack @ Palais du Louvre | July 2025**

![](https://g0v.hackmd.io/_uploads/SkxphTzhgbx.png)
![](https://g0v.hackmd.io/_uploads/rJVa6z2x-x.png)
![](https://g0v.hackmd.io/_uploads/BJ_aTz3e-l.png)


**The Problem**  
Developers are overwhelmed with tech news but lack time to filter relevant, actionable information. They need concise updates with ready-to-use code snippets.

**The Solution**  
An AI-driven news assistant that delivers personalized, actionable tech updates with relevant code examples.

**Tech Stack**
```
Frontend:  React.js + TailwindCSS + Framer Motion
Backend:   FastAPI + LLM Integration
AI:        Multi-agent workflow (search/summarize/generate)
```

**Key Features**
- 🔍 **Smart Search**: AI-powered news filtering by relevance
- 📝 **Concise Summaries**: Key takeaways in < 2 minutes
- 💻 **Code Snippets**: Ready-to-use examples from articles
- 🎨 **Clean UX**: Single-page design with smooth animations

**My Role**: Team Captain, Frontend Developer & Product Designer
- Designed entire UI/UX with focus on low cognitive load
- Implemented smooth animations using Framer Motion
- Integrated FastAPI backend with LLM-powered multi-agent system
- Optimized information hierarchy for developer workflows

**Design Philosophy**
> "Information should be effortless to consume. We eliminated every unnecessary click, every extra scroll, every moment of confusion."

[GitHub Repo](https://github.com/nosheen/DevNews-Copilot-Blackbox.ai)

---

### 3. PsyMuse - Voice-Interactive 3D AI Coach
**Global AI Hackathon (MIT Sloan AI Club) | August 2025**

![](https://g0v.hackmd.io/_uploads/HkxINAz3xbg.png)
![](https://g0v.hackmd.io/_uploads/B1TECG2x-e.png)


**The Vision**  
Health and sports coaching requires high engagement and personal connection. Traditional apps lack the immersive, conversational experience users need.

**The Innovation**  
A voice-interactive 3D AI coach that provides real-time feedback through natural conversation with realistic avatar animation.

**Tech Stack**
```
Voice:     Speech-to-Text (STT) + Text-to-Speech (TTS)
AI:        LLM for conversational responses
Avatar:    ReadyPlayerMe + Wawa Lipsync
Frontend:  React.js + Three.js
```

**Key Features**
- 🎤 **Real-time Voice Interaction**: Natural conversation flow
- 👤 **3D Avatar with Lipsync**: Realistic visual feedback
- 🧠 **Contextual Responses**: LLM-powered personalized guidance
- 🔒 **Safety Filters**: Automatic detection and appropriate referrals

**My Role**: Frontend Developer & API Integration Specialist
- Integrated STT → LLM → Avatar pipeline
- Implemented real-time lipsync synchronization
- Coordinated with international team across time zones
- Balanced technical implementation with UX goals

**International Collaboration**  
Worked with teammates across 3 continents, mastering asynchronous communication and technical documentation.

**Taiwan Application Potential**  
> "This technology can be adapted for mental health support, educational tutoring, and elderly care - critical needs in Taiwan's aging society."

 [Technical Blog](https://github.com/tawab2001/activemind)

---

### 4. Carbon Wallet - ESG Behavioral Reward Platform
**Hult Prize 2025 | Global Top 5%, Taiwan Top 19**

![](https://g0v.hackmd.io/_uploads/SJf0Az3eWx.png)
![](https://g0v.hackmd.io/_uploads/B1wRRGhlWe.png)
![](https://g0v.hackmd.io/_uploads/H1xpACMhlbx.png)
![](https://g0v.hackmd.io/_uploads/rJ3yJ73gbx.png)


**The Problem**  
People know about carbon reduction but lack continuous motivation and credible feedback mechanisms. Businesses struggle with ESG data collection and reporting.

**The Solution**  
A dual-sided platform that:
- **B2C**: Rewards users for low-carbon behaviors with carbon points
- **B2B**: Provides ESG insights and verified reports to businesses

**Business Model**
```
User Side:
- Connect with transit cards, e-commerce, retail partners
- AI verifies carbon-reducing behaviors
- Earn carbon points redeemable for discounts

Business Side:
- Purchase aggregated ESG data insights
- Blockchain-verified carbon credits
- Automated ESG reporting tools
```

**Key Features**
- 🔗 **API Integration**: Transit, e-commerce, retail partners
- ⛓️ **Blockchain**: Immutable verification of key credentials
- 📊 **ESG Analytics**: B2B insights dashboard
- 💰 **Incentive Economics**: Behavioral economics-driven rewards

**My Role**: Team Lead, Product & UI/UX Designer
- Conducted user research and market validation
- Designed complete UI/UX in Figma
- Defined incentive mechanisms and revenue model
- Led pitch presentations to judges and investors

**Pitch Results**  
Advanced through Taiwan regional to global top 5% among 10,000+ teams worldwide.

**Taiwan Impact Potential**
> "Partnering with campuses, shopping districts, and local governments to create 'carbon reduction = rewards' demonstration zones across Taiwan."


---

### 5. SME Credit Scoring Platform
**IDEA FinTech 2025 | Quarter-Finalist (Top 8)**

![](https://g0v.hackmd.io/_uploads/H1ZYjJm3g-x.png)
![](https://g0v.hackmd.io/_uploads/S1Who172gWl.png)
![](https://g0v.hackmd.io/_uploads/SydkgXhlZg.png)
![](https://g0v.hackmd.io/_uploads/Sk5elXhl-l.png)


**The Problem**  
Small and medium enterprises (SMEs) face financing inequality due to insufficient traditional credit data. Banks lack tools for transparent, explainable risk assessment.

**The Solution**  
An alternative-data-driven credit evaluation platform using non-traditional data sources.

**Tech Stack**
```
Data Sources:  E-commerce transactions, invoices, behavioral data
ML Model:      LightGBM (gradient boosting)
Explainability: SHAP (SHapley Additive exPlanations)
Verification:  Blockchain for key metrics
```

**Key Innovations**
- 📊 **Alternative Data**: E-commerce, invoice history, online behavior
- 🔍 **Explainable AI**: SHAP values show decision factors
- 🏦 **Regulatory Alignment**: Compliant with financial regulations
- ⛓️ **Blockchain**: Immutable records of key indicators

**My Role**: Team Lead, Proposal Lead & Model Designer
- Designed LightGBM + SHAP explainability framework
- Authored complete business proposal
- Developed compliance and business model roadmap
- Presented solution to fintech judges and industry experts

**Taiwan Financial Inclusion Impact**
> "Addressing information asymmetry in SME financing, compatible with policy lending and local bank micro-credit programs."

**Technical Highlight**: Explainable AI
```python
# SHAP values show why the model made its decision
import shap
explainer = shap.TreeExplainer(model)
shap_values = explainer.shap_values(X_test)

# Visualize feature importance for each prediction
shap.force_plot(explainer.expected_value, shap_values[0], X_test.iloc[0])
```


---

## 💻 Technical Skills

### Programming & Web Development
```javascript
const skills = {
  languages: ["Python", "C++", "Java", "JavaScript/TypeScript"],
  frontend: ["React.js", "TailwindCSS", "Framer Motion", "Three.js"],
  backend: ["FastAPI", "Node.js", "REST APIs"],
  tools: ["Git/GitHub", "Figma", "Vercel", "Railway"]
};
```

### AI & Machine Learning
```python
expertise = {
    "classical_ml": ["Regression", "Tree-based models (LightGBM)", "Clustering"],
    "deep_learning": ["NLP basics", "Speech processing"],
    "reinforcement_learning": ["SUMO-RL", "Multi-agent systems"],
    "explainability": ["SHAP", "Model interpretation"],
    "frameworks": ["scikit-learn", "NumPy", "pandas"]
}
```

### Product & Business
- 📊 **Data Analysis**: Excel, data visualization, statistical modeling
- 🎨 **UI/UX Design**: Figma, wireframing, user research
- 💼 **Business Strategy**: MVP validation, unit economics, pitch deck creation
- 🗣️ **Communication**: Bilingual pitching (Mandarin & English), cross-cultural collaboration

### Soft Skills
- 👥 **Team Leadership**: Led 5+ hackathon teams to success
- 🚀 **Agile Collaboration**: 48-hour sprints, rapid prototyping
- 🎤 **Public Speaking**: Presentations to government officials, investors, judges
- 🌏 **International Teamwork**: Collaborated across 3 continents and time zones

---

## 📚 Education & Coursework

**National Yang Ming Chiao Tung University (NYCU)**  
*Bachelor of Science in Information Management and Finance*  
Information Management Track | Sep 2024 - Present

### Computer Science & AI
- Programming (C/C++, Python)
- Data Structures & Algorithms
- Introduction to Machine Learning *(in progress)*
- JavaScript Web Development
- Introduction to Computer Science

### Business & Finance
- Financial Management *(in progress)*
- Engineering Economy *(in progress)*
- Economics, Accounting
- Patent Law *(in progress)*

### Mathematics & Statistics
- Calculus, Linear Algebra
- Probability *(in progress)*
- Statistics *(in progress)*

### Cross-Disciplinary
- Psychology (human behavior & decision-making)

---

## 🎯 Current Focus & Interests

### Active Projects
- 🏆 **MABe Kaggle Competition**: Mouse behavior detection (Top 5% leaderboard)
- 🌐 **Portfolio Website**: Advanced React site with 3D graphics and particle systems
- 🔐 **Cryptography Challenges**: Multi-layer encryption implementations

### Research Interests
- **AI for Public Good**: Smart cities, transportation optimization, sustainability
- **FinTech Innovation**: Alternative data, explainable AI, financial inclusion
- **Developer Tools**: AI-powered productivity tools for engineers

### Career Goals
- International opportunities in AI/ML engineering
- Building impactful products at the intersection of technology and social good
- Contributing to open-source and startup ecosystems

---

## 🌍 Languages

| Language | Proficiency | Certifications |
|----------|-------------|----------------|
| **Mandarin** | Native | — |
| **English** | Fluent | IELTS 6.5, TOEIC 925/990 |

**International Experience**
- Multiple international hackathons with cross-cultural teams
- Model United Nations participant (Honorable Mention)
- Technical presentations and pitches in English

---

## 🤝 Leadership & Community

### Active Involvement
- **Google Developer Student Club (GDSC-NYCU)**: Member | Sep 2025 - Present
- **NTHU Data Science Club**: Member | Aug 2025 - Present
- **NYCU English Resume & Interview Competition 2025**: Event Host & Planner

### Past Leadership
- **RS Model United Nations**: Organizer | June 2022

### Community Goals
- Build mentorship networks connecting students with industry professionals
- Share resources about international opportunities and startup ecosystems
- Promote entrepreneurship and innovation culture in Taiwan universities

---

## 📫 Let's Connect

I'm actively seeking **international opportunities** in:
- 🎓 Bachelor internships in AI/ML or full-stack development
- 🚀 Startup accelerator programs
- 🌏 Cross-border collaboration projects
- 🤝 Research opportunities in AI for social good

**Get in Touch**
- 📧 Email: ella.tso.cc@gmail.com
- 💼 GitHub: [github.com/ellatso](https://github.com/ellatso)
- 📱 Phone: +886 972-845-330

---

<div style="text-align: center; padding: 40px 0; border-top: 2px solid #e0e0e0; margin-top: 60px;">

### "Building technology that matters, one project at a time."

*Last Updated: November 2025*

</div>

---

## 📎 Appendix: Quick Links

### Project Repositories
- [GLIDE Traffic System](#) - Full-stack AI traffic optimization
- [DevNewsCopilot](#) - AI news assistant for developers
- [PsyMuse](#) - Voice-interactive 3D AI coach
- [Carbon Wallet](#) - ESG behavioral reward platform
- [SME Credit Platform](#) - Alternative data credit scoring

### Competition Results
- [Mei-Chu Hackathon Certificate](#)
- [Hult Prize Advancement](#)
- [IDEA FinTech Finals](#)

### Additional Materials
- [Full Resume (PDF)](#)
- [Recommendation Letters](#)
- [Academic Transcript](#)

---

:::success
**Open to Opportunities**

I'm currently exploring:
- Summer 2025 internships in AI/ML engineering
- International accelerator programs
- Research collaboration in smart cities & sustainability

**Available**: June - August 2025

📩 Feel free to reach out: ella.tso.cc@gmail.com
:::

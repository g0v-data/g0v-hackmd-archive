# 🎭 3D Avatar + Lipsync Integration Setup Guide

## 📋 Quick Setup Checklist

### 1. **Install Required Dependencies**
```bash
npm install three @react-three/fiber @react-three/drei wawa-lipsync
```

### 2. **Replace File**
- Replace `src/Food.jsx` with the new version I provided

### 3. **Add New Files**
Create these new files exactly as shown:

```
src/
├── avatar/
│   ├── AvatarStage.jsx     # 3D Avatar component
│   └── wawa-adapter.ts     # Lipsync adapter
└── Food.jsx                # Updated main component
```

### 4. **Add Assets to Public Folder**
```
public/
├── models/
│   └── avatar.glb         # Your 3D avatar model
└── img/
    └── bg.jpg            # Background image
```

---

---

## 🚀 Testing Instructions

1. **Start the dev server:**
   ```bash
   npm start
   ```

2. **Test the avatar:**
   - Click "Test Voice" button
   - Avatar should load and animate mouth movements
   - Check browser console for debug logs

3. **Debug checklist:**
   - ✅ No console errors
   - ✅ Avatar model loads
   - ✅ Mouth moves during speech
   - ✅ Audio plays correctly

---

## 🔧 Troubleshooting

### Common Issues:

1. **"Module not found: wawa-lipsync"**
   - Run: `npm install wawa-lipsync`

2. **Avatar doesn't load**
   - Check if `/public/models/avatar.glb` exists
   - Verify model has proper viseme morph targets

3. **No mouth movement**
   - Check browser console for viseme debug logs
   - Verify VISEME_MAP matches your model's morph targets

4. **Audio doesn't play**
   - Check audio file permissions
   - Try clicking on page first (browser autoplay policy)

---

## 📝 What This Gives You

- ✅ **3D Avatar with lipsync** - Mouth moves with speech
- ✅ **Wawa Lipsync integration** - Real-time viseme analysis  
- ✅ **Fallback system** - Works even without Wawa Lipsync
- ✅ **Debug tools** - Console logs for troubleshooting
- ✅ **Smooth animations** - 12fps viseme updates
- ✅ **Error handling** - Graceful fallbacks

Ready to test! 🎉
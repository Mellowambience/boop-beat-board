# 🥁 Boop Beat Board

> Hybrid iOS beat pad + step sequencer. Built fast. Scaled by feedback.

**Live alpha:** https://boopbeatboar-bbx6jdbk.manus.space  
**Stack:** Expo 51 + React Native WebView + expo-haptics  
**Part of:** [Aetherhaven Multiverse](https://github.com/Mellowambience/aetherhaven-multiverse)

---

## Sprint Roadmap

| Sprint | Goal | Status |
|--------|------|--------|
| 1 | Expo WebView hybrid + haptics + feedback loop | ✅ This |
| 2 | MIST (clawd) voice control — BPM/pattern commands | 🔲 |
| 3 | Lumina-Core Swift AVAudioEngine native rewrite | 🔲 |

## Quick Start

```bash
npm install
npx expo start
# Press `i` for iOS simulator
```

## Feedback

The app includes a built-in feedback button. Every tap on the floating `?` sends structured feedback (platform, version, note) to the collection endpoint. We ship, you react, we iterate.

## Architecture

```
iOS Native Shell (Expo)
├── WebView → boopbeatboar-bbx6jdbk.manus.space
│   └── JS Bridge (postMessage ↔ onMessage)
│       ├── pad_hit → expo-haptics impactAsync(Heavy)
│       └── beat_state → native state sync
├── useFeedback hook → feedback endpoint
└── (Sprint 2) MIST voice layer via tRPC
```

## Environment

Create `.env.local`:
```
EXPO_PUBLIC_BBB_URL=https://boopbeatboar-bbx6jdbk.manus.space
EXPO_PUBLIC_FEEDBACK_URL=https://your-feedback-endpoint.com/api/feedback
```

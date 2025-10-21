<div align="center">

# 🏝️ Felika Island — GeoTour

### *Educational Virtual Tour Experience in Unity*

[![Unity](https://img.shields.io/badge/Unity-2022_LTS-black.svg?style=flat&logo=unity)](https://unity.com/)
[![Platform](https://img.shields.io/badge/Platform-iOS-blue.svg?style=flat&logo=apple)](https://www.apple.com/ios/)
[![License](https://img.shields.io/badge/License-Internal-red.svg?style=flat)](LICENSE)

*An immersive 3D mobile app showcasing the geological wonders of Felika Island through interactive exploration and educational content.*

[Features](#-features) • [Quick Start](#-quick-start) • [Roadmap](#-development-roadmap)

</div>

---

## 📖 Overview

**Felika Island GeoTour** is a lightweight, educational virtual tour application that brings geology to life through interactive 3D experiences. Users explore an island map with four distinct locations, each offering immersive geological points of interest (POIs) with educational content.

### 🎯 Key Highlights

- **Tourism-First Experience**: Beautiful, engaging entry point for users
- **Educational Content**: 12+ geological POIs with informative descriptions
- **iOS Optimized**: Smooth performance on iPhone and iPad devices
- **Rapid Development**: Prototype-quality build achievable in 1 week

---

## ✨ Features

### 🗺️ Four Explorable Locations
1. **Geological Heritage Museum** — Indoor exhibit with rock samples and stratigraphy
2. **Groundwater Wells** — Outdoor site exploring aquifers and water systems
3. **Nature Walk Trail** — Linear path showcasing erosion and sediments
4. **Seating Area Viewpoint** — Scenic overlook with coastal geology

### 📍 Interactive Learning
- 12+ geological points of interest across all locations
- Tap-to-reveal info cards with educational content
- Progress tracking and collectible badges
- Optional audio narration

### 🎮 Simple Controls
- Touch-based movement and camera controls
- Intuitive tap-to-interact system
- Adjustable sensitivity settings

### 💾 Progress Tracking
- Saves visited POIs automatically
- Badge collection for completing locations
- Settings persistence

---

## 🚀 Quick Start

### Prerequisites

- Unity 2022 LTS with iOS Build Support
- Xcode (latest version)
- macOS for building iOS apps
- iPhone or iPad for testing

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/felika-geotour.git
cd felika-geotour
```

### Building for iOS

1. **Open Project in Unity**
   - Open Unity Hub → Add Project → Select project folder

2. **Switch to iOS Platform**
   - File → Build Settings → iOS → Switch Platform

3. **Configure Settings**
   - Edit → Project Settings → Player
   - Set Bundle Identifier: `com.yourcompany.felikageotour`
   - Set Target iOS Version: iOS 13.0 or higher

4. **Build Xcode Project**
   - File → Build Settings → Build
   - Open generated Xcode project
   - Connect device and build from Xcode

---

## 🛠️ Tech Stack

- **Unity 2022 LTS** — Game engine
- **Universal Render Pipeline (URP)** — Mobile-optimized graphics
- **TextMeshPro** — Text rendering
- **Unity Input System** — Touch controls
- **Git** — Version control

### Performance Targets
- **FPS**: 30+ on iPhone/iPad
- **App Size**: ≤ 300 MB
- **Scene Loading**: ≤ 5s cold start
- **Memory**: < 600 MB peak

---

## 🗓️ Development Roadmap

### Week 1 Sprint

**Days 1-2: Foundation**
- Unity project setup with URP
- Island map and navigation system
- Scene loading infrastructure

**Days 3-5: Content**
- Four location scenes with POIs
- Info card system and interactions
- Ambient audio implementation

**Days 6-7: Polish & Release**
- Settings and controls refinement
- iOS build and device testing
- Screenshots and documentation

### Success Criteria
- ✅ All 4 scenes with 12+ POIs
- ✅ Progress tracking and badges
- ✅ 30+ FPS on iPhone/iPad
- ✅ Clean iOS build

---

## 🧪 Testing

### QA Checklist

**Navigation**
- [ ] All 4 location pins load correctly
- [ ] Back to map navigation works
- [ ] Scene transitions are smooth

**POI System**
- [ ] POI markers are tappable
- [ ] Info cards display properly
- [ ] Progress saves and persists

**Performance**
- [ ] 30+ FPS maintained
- [ ] Scene loads within 5 seconds
- [ ] No crashes or memory issues

**Audio & Settings**
- [ ] Ambient audio plays in all scenes
- [ ] Volume controls function
- [ ] Settings persist across sessions

---

## ⚠️ Risks & Mitigations

| Risk | Mitigation |
|------|------------|
| **Performance Issues** | Bake lighting, optimize textures, use LODs |
| **Scope Creep** | Lock to 4 scenes and 12+ POIs |
| **Device Compatibility** | Test on multiple iPhone/iPad models |
| **Content Delays** | Use placeholder assets early |

---

## 🚀 Future Enhancements

- **Arabic Localization** — Full RTL UI support
- **Photo Mode** — Screenshot capture and sharing
- **Educational Quizzes** — Interactive assessments
- **Educator Dashboard** — Progress tracking for classrooms
- **Additional Content** — More locations and scenes
- **AR Mode** — Augmented reality features

---

## 📄 License

Internal educational prototype. Contact project owner for licensing information.

---

## 👥 Contributing

This is an internal prototype project. For contributions:
1. Keep commits clear and descriptive
2. Open issues for any blockers
3. Maintain playable builds in main branch

---

<div align="center">

**Built for geological education**

*Explore • Learn • Discover*

</div>

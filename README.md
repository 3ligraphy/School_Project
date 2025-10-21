<div align="center">

# 🏝️ Felika Island — GeoTour

### *Educational Virtual Tour Experience in Unity*

[![Unity](https://img.shields.io/badge/Unity-2022_LTS-black.svg?style=flat&logo=unity)](https://unity.com/)
[![Platform](https://img.shields.io/badge/Platform-Android-green.svg?style=flat&logo=android)](https://www.android.com/)
[![VR Support](https://img.shields.io/badge/VR-Cardboard_Compatible-blue.svg?style=flat)](https://arvr.google.com/cardboard/)
[![License](https://img.shields.io/badge/License-Internal-red.svg?style=flat)](LICENSE)

*An immersive 3D/VR mobile app showcasing the geological wonders of Felika Island through interactive exploration and educational content.*

[Features](#-features) • [Demo](#-demo) • [Quick Start](#-quick-start) • [Documentation](#-documentation)

</div>

---

## 📖 Overview

**Felika Island GeoTour** is a lightweight, educational virtual tour application that brings geology to life through interactive 3D experiences. Users explore an island map with four distinct locations, each offering immersive geological points of interest (POIs) with educational content.

### 🎯 Project Goals

- **Tourism-First Experience**: Beautiful, engaging entry point for users
- **Educational Content**: 12+ geological POIs with informative descriptions
- **Mobile Optimized**: Smooth performance on mid-range Android devices (30+ FPS)
- **VR Ready**: Optional Google Cardboard/gyro mode for immersive viewing
- **Rapid Development**: Prototype-quality build achievable in 1 week

### 🎮 Platform Support

- **Primary**: Android (API 26+, Android 8.0 Oreo or higher)
- **Optional**: iOS (time permitting)
- **VR Mode**: Google Cardboard compatible with gyro controls

---

## ✨ Features

### 🗺️ Interactive Island Map
- Four distinct tappable locations with detailed previews
- Progress tracking showing completion percentage for each location
- Intuitive navigation between scenes

### 🏛️ Four Unique Locations
1. **Geological Heritage Museum** — Indoor exhibit with rock samples and stratigraphy displays
2. **Groundwater Wells** — Outdoor site exploring aquifers and water systems
3. **Nature Walk Trail** — Linear path showcasing erosion, sediments, and fossils
4. **Seating Area Viewpoint** — Scenic overlook with coastal geology insights

### 📍 Interactive Points of Interest (POIs)
- 12+ geological learning points across all locations
- Tap-to-reveal info cards with concise educational content
- Progress tracking and collectible badges for completing locations
- Optional audio narration support

### 🎮 Flexible Controls
- **Standard Mode**: Touch joystick controls (move + look)
- **VR Mode**: Google Cardboard compatible with gyro/head tracking
- Adjustable sensitivity settings
- Intuitive tap-to-interact system

### 🌍 Localization Ready
- English UI (default)
- Infrastructure prepared for Arabic localization
- RTL (right-to-left) support framework

### 💾 Progress Persistence
- Local save system for visited POIs
- Settings persistence across sessions
- Badge collection and achievement tracking

---

## 🎬 Demo

> **Note**: Screenshots and demo video coming soon in `/Docs/`

### User Journey
1. **Hero Screen** → Tap "Enter" to begin
2. **Island Map** → View four location pins with descriptions
3. **Select Location** → Tap any pin to load the 3D scene
4. **Explore** → Move around and tap POI markers for information
5. **Learn** → Read geology facts and collect badges
6. **Return** → Navigate back to map to explore other locations

---

## 🚀 Quick Start

### Prerequisites

- Unity 2022 LTS with Android Build Support
- Android SDK (API Level 26+)
- Git with Git LFS installed
- Mid-range Android device for testing (Snapdragon 7-series or equivalent)

### Installation

```bash
# Clone the repository
git clone https://github.com/yourusername/felika-geotour.git
cd felika-geotour

# Ensure Git LFS is tracking large files
git lfs pull
```

### Building for Android

1. **Open Project**
   ```
   Open Unity Hub → Add Project → Select FelikaGeoTour folder
   ```

2. **Switch Platform**
   - File → Build Settings
   - Select Android
   - Click "Switch Platform"

3. **Configure Player Settings**
   - Edit → Project Settings → Player
   - Set Package Name: `com.yourcompany.felikageotour`
   - Set Minimum API Level: Android 8.0 (API 26)
   - Scripting Backend: IL2CPP (recommended)
   - Target Architectures: ARM64

4. **Build**
   - File → Build Settings → Build
   - Choose output location for APK/AAB
   - Test on target device

### Running the App

1. Install the APK on your Android device
2. Grant necessary permissions (storage, if applicable)
3. Launch and enjoy exploring Felika Island!

---

## 🛠️ Tech Stack

### Core Technologies

| Technology | Purpose |
|------------|---------|
| **Unity 2022 LTS** | Game engine and development platform |
| **Universal Render Pipeline (URP)** | Optimized graphics rendering for mobile |
| **TextMeshPro** | High-quality text rendering |
| **Unity Input System** | Modern input handling |
| **Unity Addressables** | Asset management and streaming |
| **Unity Localization** | Multi-language support |
| **Unity Analytics** | Event tracking and metrics |

### Development Tools
- **Version Control**: Git + Git LFS
- **IDE**: Visual Studio / Visual Studio Code / Rider
- **Build Target**: Android (API 26+)

### Performance Profile
- **Target FPS**: 30+ on mid-range devices
- **App Size**: ≤ 300 MB (APK/AAB)
- **Memory Usage**: < 600 MB peak during scene loads
- **Draw Calls**: < 120 per frame
- **Scene Load Time**: ≤ 5s cold start, ≤ 3s warm

---

## 📁 Project Structure

```
FelikaGeoTour/
├── Assets/
│   ├── Art/                    # 3D models, textures, materials
│   ├── Audio/                  # SFX, ambient sounds, voice-overs
│   ├── Data/                   # JSON data files (pins, POIs, localization)
│   ├── Prefabs/                # Reusable game objects (POIs, pins, UI)
│   ├── Scenes/                 # Unity scene files
│   │   ├── Splash_Landing.unity
│   │   ├── Island_Map.unity
│   │   ├── Museum_Scene.unity
│   │   ├── Wells_Scene.unity
│   │   ├── Trail_Scene.unity
│   │   └── Seating_Scene.unity
│   ├── Scripts/
│   │   ├── Core/              # SceneLoader, SaveSystem, Settings
│   │   ├── Map/               # Map navigation and pin interaction
│   │   ├── POI/               # POI system and info cards
│   │   ├── Player/            # Movement and camera controls
│   │   └── UI/                # Menu systems and HUD
│   └── UI/                     # UI sprites and assets
├── ProjectSettings/            # Unity project configuration
├── Packages/                   # Unity package dependencies
├── Docs/                       # Screenshots and demo videos
└── README.md
```

### Scene Overview

| Scene | Description | POI Count |
|-------|-------------|-----------|
| `Splash_Landing` | Hero screen with branding and settings | N/A |
| `Island_Map` | Interactive map with 4 location pins | N/A |
| `Museum_Scene` | Indoor geological exhibit | 3-5 POIs |
| `Wells_Scene` | Outdoor groundwater exploration | 3-5 POIs |
| `Trail_Scene` | Nature walk with waypoints | 3-5 POIs |
| `Seating_Scene` | Scenic viewpoint | 3-5 POIs |

---

## 📊 Data Architecture

The application uses JSON-based data files for flexible content management.

### Location Pins Data Structure

**File**: `Assets/Data/pins.json`

```json
[
  {
    "id": "museum",
    "displayName": "Geological Heritage Museum",
    "scene": "Museum_Scene",
    "description": "Indoor exhibits on Felika Island geology.",
    "thumbnail": "Art/UI/Icons/museum_icon.png",
    "estimatedMinutes": 5
  }
]
```

### POI Data Structure

**File**: `Assets/Data/pois_{scene}.json`

```json
[
  {
    "id": "rock_samples",
    "title": "Rock Samples & Stratigraphy",
    "body": "Discover sediment layers that record sea level changes.",
    "icon": "Art/UI/Icons/rock.png",
    "position": { "x": 3.1, "y": 1.2, "z": -2.4 }
  }
]
```

---

## 📖 Documentation

### Development Guidelines

#### Art & Audio Standards
- **Visual Style**: Clean, stylized low-poly to optimized mid-poly
- **Lighting**: Baked Global Illumination preferred; minimal real-time lights
- **Textures**: ≤ 1K resolution for mobile; use texture atlases; ASTC/ETC2 compression
- **Audio**: Looping ambient tracks per scene (≤ 128 kbps), balanced volumes

#### Performance Benchmarks
- **Frame Rate**: Maintain ≥ 30 FPS on mid-range Android
- **App Size**: Target ≤ 300 MB (APK/AAB)
- **Scene Loading**: ≤ 5s cold start, ≤ 3s warm load
- **Memory Usage**: < 600 MB peak during transitions
- **Rendering**: < 120 draw calls per frame

---

## 🗓️ Development Roadmap

### Sprint Timeline (7 Days)

<details>
<summary><b>Day 1: Project Foundation</b></summary>

- [x] Initialize Unity 2022 LTS project with URP
- [x] Set up Git repository with LFS
- [x] Configure project structure and folders
- [x] Implement Splash/Landing screen
- [x] Create Settings framework
- [x] Define performance budget

</details>

<details>
<summary><b>Day 2: Core Navigation</b></summary>

- [x] Build Island Map scene
- [x] Implement pin system with JSON loading
- [x] Create scene loading pipeline
- [x] Develop pause and back menu systems

</details>

<details>
<summary><b>Day 3: Museum Scene</b></summary>

- [x] Design and blockout museum interior
- [x] Add 3-5 POIs with info card system
- [x] Implement ambient audio
- [x] Set up POI progress tracking
- [x] Bake lighting

</details>

<details>
<summary><b>Day 4: Wells Scene</b></summary>

- [x] Create outdoor terrain and well structures
- [x] Implement 3-5 groundwater POIs
- [x] Optimize assets with LODs
- [x] Apply texture compression

</details>

<details>
<summary><b>Day 5: Trail & Seating Scenes</b></summary>

- [x] Build nature trail with waypoint system
- [x] Create seating area viewpoint
- [x] Add 3-5 POIs to each scene
- [x] Implement badge/achievement system

</details>

<details>
<summary><b>Day 6: Polish & Features</b></summary>

- [x] Implement VR/Cardboard mode with gyro controls
- [x] Add sensitivity settings
- [x] Set up localization infrastructure
- [x] Integrate analytics events

</details>

<details>
<summary><b>Day 7: QA & Release</b></summary>

- [x] Comprehensive device testing
- [x] Performance optimization pass
- [x] Capture screenshots and demo video
- [x] Build release APK/AAB
- [x] Final documentation update

</details>

### Success Criteria

#### ✅ Product Goals
- All 4 scenes accessible from map with ≥ 3 POIs each
- Complete POI tracking and badge system
- Functional settings (audio, sensitivity, VR mode, language)
- Local save persistence

#### ✅ Engineering Goals
- Maintain ≥ 30 FPS on target devices
- Scene load times ≤ 5s (cold start)
- Zero crashes in 10-minute soak tests
- Clean release build with no critical errors

#### ✅ Content Goals
- Minimum 12 POIs with accurate geological information
- Map pins with thumbnails and descriptions
- Seamless ambient audio in all scenes

#### ✅ Delivery Goals
- Signed APK/AAB ready for distribution
- Complete documentation and build instructions
- 5-10 high-quality screenshots
- 90-second demo video

---

## 🧪 Testing

### QA Checklist

#### Navigation Testing
- [ ] Splash screen → Island Map transition works smoothly
- [ ] All 4 location pins are tappable and load correctly
- [ ] Back to Map button functions in all scenes
- [ ] Scene loader displays progress appropriately
- [ ] Android back button handled correctly on all screens

#### POI Functionality
- [ ] POI markers are visible and tappable in all scenes
- [ ] Info cards open/close properly
- [ ] Visited state persists after app restart
- [ ] Badge awarded when all POIs in a scene are viewed
- [ ] Progress percentage displays correctly on map

#### Performance Validation
- [ ] FPS maintains ≥ 30 in all scenes
- [ ] No memory spikes during scene transitions
- [ ] Scene load times within target (≤5s cold, ≤3s warm)
- [ ] No frame drops during camera movement

#### Audio System
- [ ] Ambient audio present in all scenes
- [ ] Audio loops seamlessly without gaps
- [ ] Volume controls work in Settings
- [ ] Audio persists correctly across scene changes

#### Settings & Controls
- [ ] VR toggle switches between touch and gyro controls
- [ ] Sensitivity sliders affect camera movement speed
- [ ] Language switch updates UI text (where implemented)
- [ ] Settings persist across sessions

#### Stability Testing
- [ ] 10-minute soak test per scene without crashes
- [ ] No critical errors in device logs
- [ ] Graceful handling of interruptions (calls, notifications)
- [ ] Proper cleanup when app is backgrounded

---

## ⚠️ Risks & Mitigations

| Risk | Impact | Mitigation Strategy |
|------|--------|---------------------|
| **Art Pipeline Overload** | High | Use low-poly stylized asset kits; prioritize functional layouts over visual fidelity |
| **Performance Degradation** | High | Bake lighting, limit post-processing, use texture atlases, implement LODs, enable occlusion culling |
| **Scope Creep** | Medium | Lock to 4 scenes and ≥12 POIs; defer additional features to post-launch |
| **VR Motion Sickness** | Medium | Default to touch controls; in VR mode use teleport or slow movement, minimize acceleration |
| **Device Fragmentation** | Medium | Test on range of devices; use dynamic resolution scaling for lower-end hardware |
| **Content Creation Delays** | Low | Prepare placeholder content early; use procedural generation where appropriate |

---

## 🚀 Future Enhancements

### Planned Features
- **Arabic Localization**: Full RTL (right-to-left) UI support
- **Photo Mode**: In-app screenshot capture and social sharing
- **Educational Quizzes**: Interactive assessments at POI locations
- **Educator Dashboard**: Progress tracking for classroom use
- **Cloud Content**: Remote configuration for content updates without app updates

### Platform Expansion
- **iOS Build**: Apple App Store distribution
- **Headset VR**: Meta Quest native port
- **WebGL Version**: Browser-based experience

### Content Extensions
- Additional island locations and scenes
- Seasonal content and events
- Multiplayer guided tours
- AR (Augmented Reality) mode for real-world exploration

---

## 📄 License

**Internal Educational Prototype**

This project is an educational prototype. Distribution is restricted to the project owner.

For licensing inquiries or to use this project, please contact the project maintainer.

---

## 👥 Contributing

This is currently an internal prototype project. Contributions, bug reports, and feature suggestions are welcome from the development team.

### Development Workflow
1. Keep commit messages clear and descriptive
2. Push buildable code daily
3. Open issues for blockers immediately
4. Maintain playable end-to-end experience in main branch
5. Follow Unity coding standards and style guide

---

## 📞 Contact & Support

For questions, issues, or collaboration inquiries:

- **Project Lead**: [Your Name]
- **Repository**: [GitHub Repository URL]
- **Issues**: [GitHub Issues URL]

---

<div align="center">

**Built with ❤️ for geological education**

*Explore • Learn • Discover*

</div>

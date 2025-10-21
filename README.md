Sure! Here’s the content you provided, properly formatted as a `README.md` file for your GitHub repository:

---

```markdown
# Felika Island — GeoTour (Unity Mobile VR/3D)

A lightweight, educational **virtual tour app** for **Felika Island**.  
Users start on a tourism-style **hero screen**, then see a **simple island map with four pins**.  
Tapping a pin loads a **3D/VR experience** for that location, with **geology points** and **info pop-ups** to learn as they explore.

> **Scope:** 1-week implementation (prototype-quality, shippable build).  
> **Target:** Mobile (Android primary, iOS optional). Non-headset 3D with **optional Cardboard/gyro mode** toggle.

---

## Table of Contents

- [Core Goals](#core-goals)
- [Player Flow](#player-flow)
- [Scenes & Content](#scenes--content)
- [Geology Points (POIs)](#geology-points-pois)
- [UX & Controls](#ux--controls)
- [Tech Stack & Project Setup](#tech-stack--project-setup)
- [Repo Structure](#repo-structure)
- [Data Model](#data-model)
- [Art & Audio Guidelines](#art--audio-guidelines)
- [Performance Targets](#performance-targets)
- [KPIs (for the 1-Week Sprint)](#kpis-for-the-1week-sprint)
- [Milestones & Timeline (7 Days)](#milestones--timeline-7-days)
- [Deliverables & Definition of Done](#deliverables--definition-of-done)
- [Testing Checklist](#testing-checklist)
- [Risks & Mitigations](#risks--mitigations)
- [Future Extensions](#future-extensions)
- [License](#license)

---

## Core Goals

1. **Tourism-first entry**: Beautiful landing screen showcasing Felika Island.
2. **Island map** with **four tappable pins** (locations).
3. Each pin opens a **self-contained 3D/VR scene**:
   - **Geological Heritage Museum** (indoor exhibit)
   - **Groundwater Wells Visit** (outdoor site with well shafts)
   - **Nature Walk (Trail)** (linear path with waypoints)
   - **Tourist Seating Area** (viewpoint at trail end)
4. Each scene includes **POIs (“points”) with concise geology information** (panels + voice-over optional).
5. **English UI** (default). Structure ready for Arabic localization (strings file).
6. **Mobile-friendly performance** and app size constraints.

---

## Player Flow

1. **Splash/Hero Screen** → tap **Enter**
2. **Island Map** (top-down stylized). Four pins visible with labels.
3. Tap a **pin** → **Scene Loader** → corresponding **3D/VR scene**
4. Explore: move/look, tap **POIs** to open **info cards**
   - Optional **collectible “badges”** when all POIs in a scene are viewed.
5. **Back to Map** via UI button. Progress (seen POIs) saved locally.

---

## Scenes & Content

### 0. `Splash_Landing`
- Static hero image (Felika Island tourism style), title, **Enter** button, **Settings** (Audio, Sensitivity, Language, VR mode toggle).

### 1. `Island_Map`
- Simplified island silhouette or stylized map.
- **4 Pins**:
  - **Museum** (Geological Heritage)
  - **Groundwater Wells**
  - **Nature Walk (Trail)**
  - **Seating Area (Viewpoint)**
- Tap pin → load scene. UI shows completion % (POIs viewed).

### 2. `Museum_Scene`
- Small interior with exhibit stands. 3–5 POIs.
- Ambient indoor audio.

### 3. `Wells_Scene`
- Outdoor sandy terrain with wells.
- 3–5 POIs (aquifers, groundwater recharge, salinity notes).
- Soft wind ambience.

### 4. `Trail_Scene`
- Linear path with waypoints.
- POIs: erosion, sediments, outcrops, fossils.
- Final waypoint links to Seating Area.

### 5. `Seating_Scene`
- Vista point with benches/pergola.
- POIs: landforms, coastal processes, geologic timeline.

---

## Geology Points (POIs)

- **Marker** in world → **tap** to open **Info Card** (title, 2–4 lines, icon).
- Optional **“Listen”** button for voice-over.
- **Visited** state stored locally. Scene badge awarded at 100%.

---

## UX & Controls

- **Default**: Touch joystick (left = move, right = look)
- **Optional VR**: Cardboard/gyro mode toggle (look by head/gyro, tap to interact)
- **Pause/Menu**: Resume, Map, Settings, Exit
- **Info Card**: swipe/close; supports basic rich text & image

---

## Tech Stack & Project Setup

- **Engine**: Unity **2022 LTS** (URP)
- **Platforms**: Android (API 26+), iOS optional
- **Packages**:
  - URP
  - TextMeshPro
  - Input System
  - Addressables
  - Unity Localization
  - Unity Analytics
- **Source Control**: Git (Git LFS for large assets)

**Project Settings**

- Target: 30+ FPS on mid-range Android
- Fixed DPI, dynamic resolution allowed
- Quality: Mobile URP profile (≤ 2x MSAA, baked lighting preferred)

---

## Repo Structure

```

FelikaGeoTour/
├─ Assets/
│  ├─ Art/
│  ├─ Audio/
│  ├─ Data/
│  ├─ Prefabs/
│  ├─ Scenes/
│  ├─ Scripts/
│  └─ UI/
├─ ProjectSettings/
├─ Packages/
└─ README.md

````

---

## Data Model

### Pins (Island Map)

`Assets/Data/pins.json`:

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
````

### POIs (per Scene)

`Assets/Data/pois_museum.json`:

```json
[
  {
    "id": "rock_samples",
    "title": "Rock Samples & Stratigraphy",
    "body": "Discover sediment layers that record sea level changes and island formation.",
    "icon": "Art/UI/Icons/rock.png",
    "position": { "x": 3.1, "y": 1.2, "z": -2.4 }
  }
]
```

---

## Art & Audio Guidelines

* **Style:** Stylized low-poly or optimized mid-poly
* **Lighting:** Baked GI preferred
* **Textures:** ≤ 1K, atlases, ASTC/ETC2
* **Audio:** ≤ 128 kbps looping ambient per scene

---

## Performance Targets

* **FPS:** ≥ 30 FPS
* **App size:** ≤ 300 MB
* **Scene load:** ≤ 5 s cold / ≤ 3 s warm
* **Memory spikes:** < 600 MB
* **Draw calls:** < 120 per frame

---

## KPIs (for the 1-Week Sprint)

* ✅ All 4 scenes reachable, each with ≥ 3 POIs
* ✅ POI tracking & badges
* ✅ Settings functional
* ✅ Local save works
* ✅ 30+ FPS average
* ✅ No crashes
* ✅ 12+ POIs total
* ✅ Ambient audio present
* ✅ Release build produced

---

## Milestones & Timeline (7 Days)

**Day 1:** Project setup
**Day 2:** Map & Navigation
**Day 3:** Museum Scene
**Day 4:** Wells Scene
**Day 5:** Trail & Seating Scenes
**Day 6:** Polish & Settings
**Day 7:** QA & Delivery

---

## Deliverables & Definition of Done

* ✅ Unity project
* ✅ Android AAB/APK
* ✅ README
* ✅ JSON data files
* ✅ Screenshots & demo video
* ✅ No critical errors

---

## Testing Checklist

* Navigation works
* POIs tap → info card opens
* Performance within targets
* Audio correct
* Settings functional
* Stability maintained

---

## Risks & Mitigations

* **Art overload** → Use stylized kits
* **Performance drops** → Bake lights, use LODs
* **Scope creep** → Lock to MVP
* **VR sickness** → Use slow movement or teleport

---

## Future Extensions

* Arabic localization
* Photo mode
* POI quizzes
* Cloud content updates
* iOS & headset VR support

---

## License

Internal educational prototype. Distribution by project owner only.

---

### Quick Build Notes (Android)

1. Install Unity 2022 LTS with Android modules
2. Open project → **File > Build Settings > Android** → Switch Platform
3. Configure Player Settings
4. Build **AAB/APK** (Release) and test on device

---

**Contact & Handover:**
Push daily buildable commits. Report blockers early. Keep scenes playable end-to-end.

```

---

```

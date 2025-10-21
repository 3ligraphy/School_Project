# Felika Island — GeoTour (Unity Mobile VR/3D)

A lightweight, educational **virtual tour app** for **Felika Island**.
Users start on a tourism-style **hero screen**, then see a **simple island map with four pins**. Tapping a pin loads a **3D/VR experience** for that location, with **geology points** and **info pop-ups** to learn as they explore.

> **Scope:** 1-week implementation (prototype-quality, shippable build).
> **Target:** Mobile (Android primary, iOS optional). Non-headset 3D with **optional Cardboard/gyro mode** toggle.

---

## Table of Contents

* [Core Goals](#core-goals)
* [Player Flow](#player-flow)
* [Scenes & Content](#scenes--content)
* [Geology Points (POIs)](#geology-points-pois)
* [UX & Controls](#ux--controls)
* [Tech Stack & Project Setup](#tech-stack--project-setup)
* [Repo Structure](#repo-structure)
* [Data Model](#data-model)
* [Art & Audio Guidelines](#art--audio-guidelines)
* [Performance Targets](#performance-targets)
* [KPIs (for the 1-Week Sprint)](#kpis-for-the-1week-sprint)
* [Milestones & Timeline (7 Days)](#milestones--timeline-7-days)
* [Deliverables & Definition of Done](#deliverables--definition-of-done)
* [Testing Checklist](#testing-checklist)
* [Risks & Mitigations](#risks--mitigations)
* [Future Extensions](#future-extensions)
* [License](#license)

---

## Core Goals

1. **Tourism-first entry**: Beautiful landing screen showcasing Felika Island.
2. **Island map** with **four tappable pins** (locations).
3. Each pin opens a **self-contained 3D/VR scene**:

   * **Geological Heritage Museum** (indoor exhibit).
   * **Groundwater Wells Visit** (outdoor site with well shafts).
   * **Nature Walk (Trail)** (linear path with waypoints).
   * **Tourist Seating Area** (viewpoint at trail end).
4. Each scene includes **POIs (“points”) with concise geology information** (panels + voice-over optional).
5. **English UI** (default). Structure ready for Arabic localization (strings file).
6. **Mobile-friendly performance** and app size constraints.

---

## Player Flow

1. **Splash/Hero Screen** → tap **Enter**.
2. **Island Map** (top-down stylized). Four pins visible with labels.
3. Tap a **pin** → **Scene Loader** → corresponding **3D/VR scene**.
4. Explore: move/look, tap **POIs** to open **info cards**.

   * Optional **collectible “badges”** when all POIs in a scene are viewed.
5. **Back to Map** via UI button. Progress (seen POIs) saved locally.

---

## Scenes & Content

### 0. `Splash_Landing`

* Static hero image (Felika Island tourism style), title, **Enter** button, **Settings** (Audio, Sensitivity, Language, VR mode toggle).

### 1. `Island_Map`

* Simplified island silhouette or stylized map.
* **4 Pins**:

  * **Museum** (Geological Heritage)
  * **Groundwater Wells**
  * **Nature Walk (Trail)**
  * **Seating Area (Viewpoint)**
* Tap pin → load scene. UI shows completion % (POIs viewed).

### 2. `Museum_Scene`

* Small interior with exhibit stands. 3–5 POIs (e.g., rock samples, stratigraphy boards).
* Ambient indoor audio.

### 3. `Wells_Scene`

* Outdoor sandy terrain with 1–2 wells, rope/bucket props.
* 3–5 POIs (aquifers, groundwater recharge, salinity notes).
* Soft wind ambience.

### 4. `Trail_Scene`

* Linear path with **waypoints** (min 5).
* POIs explain **erosion**, **sediments**, **outcrops**, **fossils (if applicable)**.
* Final waypoint links to Seating Area.

### 5. `Seating_Scene`

* Vista point with benches/pergola.
* POIs on **landforms**, **coastal processes**, **geologic timeline** of the island.

---

## Geology Points (POIs)

* **Marker** in world → **tap** to open **Info Card** (title, 2–4 lines, icon).
* Optional **“Listen”** button for short voice-over (TTS or simple audio file).
* **Visited** state stored locally. Scene badge awarded at 100%.

---

## UX & Controls

* **Default**: Touch joystick (left = move, right = look).
* **Optional VR**: Cardboard/gyro mode toggle in **Settings** (look by head/gyro, tap to interact).
* **Pause/Menu**: Resume, Map, Settings, Exit.
* **Info Card**: swipe/close; supports basic rich text & image.

---

## Tech Stack & Project Setup

* **Engine**: Unity **2022 LTS** (URP).
* **Platforms**: Android (API 26+). iOS optional if time allows.
* **Packages**:

  * URP
  * TextMeshPro
  * Input System
  * Addressables (for scene/content streaming if needed)
  * Unity Localization (strings ready for EN/AR)
  * Unity Analytics (basic events)
* **Source Control**: Git (Git LFS for large art/audio).

**Project Settings**

* Target 30+ FPS on mid-range Android (e.g., Snapdragon 7-series).
* Fixed DPI, allow dynamic resolution if needed.
* Quality: Mobile URP profile (no MSAA > 2x, simple shadows, baked lighting preferred).

---

## Repo Structure

```
FelikaGeoTour/
├─ Assets/
│  ├─ Art/           # models, textures, materials
│  ├─ Audio/         # sfx, ambience, (optional VO)
│  ├─ Data/          # JSON for pins, POIs, localization tables
│  ├─ Prefabs/       # POI, Pins, UI widgets
│  ├─ Scenes/
│  │  ├─ Splash_Landing.unity
│  │  ├─ Island_Map.unity
│  │  ├─ Museum_Scene.unity
│  │  ├─ Wells_Scene.unity
│  │  ├─ Trail_Scene.unity
│  │  └─ Seating_Scene.unity
│  ├─ Scripts/
│  │  ├─ Core/       # SceneLoader, SaveSystem, Settings, Analytics
│  │  ├─ Map/        # PinController, MapUI
│  │  ├─ POI/        # POIController, InfoCard, Collectibles
│  │  ├─ Player/     # MobileController, GyroLook
│  │  └─ UI/         # Menus, HUD
│  └─ UI/
├─ ProjectSettings/
├─ Packages/
└─ README.md
```

---

## Data Model

### Pins (Island Map)

`Assets/Data/pins.json`

```json
[
  {
    "id": "museum",
    "displayName": "Geological Heritage Museum",
    "scene": "Museum_Scene",
    "description": "Indoor exhibits on Felika Island geology.",
    "thumbnail": "Art/UI/Icons/museum_icon.png",
    "estimatedMinutes": 5
  },
  {
    "id": "wells",
    "displayName": "Groundwater Wells",
    "scene": "Wells_Scene",
    "description": "Outdoor visit to historic wells and aquifers.",
    "thumbnail": "Art/UI/Icons/wells_icon.png",
    "estimatedMinutes": 5
  },
  {
    "id": "trail",
    "displayName": "Nature Walk (Trail)",
    "scene": "Trail_Scene",
    "description": "Explore sediments and erosion along a path.",
    "thumbnail": "Art/UI/Icons/trail_icon.png",
    "estimatedMinutes": 6
  },
  {
    "id": "seating",
    "displayName": "Seating Area (Viewpoint)",
    "scene": "Seating_Scene",
    "description": "Scenic spot with coastal geology insights.",
    "thumbnail": "Art/UI/Icons/seating_icon.png",
    "estimatedMinutes": 4
  }
]
```

### POIs (per Scene)

`Assets/Data/pois_museum.json` (similar naming for each scene)

```json
[
  {
    "id": "rock_samples",
    "title": "Rock Samples & Stratigraphy",
    "body": "Discover sediment layers that record sea level changes and island formation.",
    "icon": "Art/UI/Icons/rock.png",
    "position": { "x": 3.1, "y": 1.2, "z": -2.4 }
  },
  {
    "id": "tectonics_panel",
    "title": "Regional Tectonics",
    "body": "How plate movements shaped regional basins and uplift.",
    "icon": "Art/UI/Icons/plate.png",
    "position": { "x": -1.2, "y": 1.1, "z": 2.0 }
  }
]
```

---

## Art & Audio Guidelines

* **Style:** Clean, stylized low-poly or optimized mid-poly.
* **Lighting:** Prefer **baked** GI; minimal real-time lights.
* **Textures:** ≤ 1K for mobile; use atlases; compress ASTC/ETC2.
* **Audio:** Looping ambient per scene (≤ 128 kbps). Volume balanced.

---

## Performance Targets

* **FPS:** ≥ **30 FPS** on a mid-range Android device.
* **App size:** **≤ 300 MB** (APK/AAB, excluding OBB).
* **Scene load time:** **≤ 5 s** cold; **≤ 3 s** warm.
* **Memory spikes:** < 600 MB during scene load on test device.
* **Draw calls:** Aim **< 120** per frame per scene (mobile URP).

---

## KPIs (for the 1-Week Sprint)

**Product KPIs**

* ✅ All **4 scenes** reachable from the map; each includes **≥ 3 POIs** with working info cards.
* ✅ **100% POI tracking** per scene and **badge** when all viewed.
* ✅ **Settings** functional: audio, sensitivity, **VR toggle**, language switch (strings ready).
* ✅ **Local save** of POI progress and settings.

**Engineering KPIs**

* ✅ Average FPS ≥ 30 on test device.
* ✅ Average **scene load** ≤ 5 s (cold).
* ✅ **No crash** in 10-minute soak test per scene.
* ✅ **Lint/style** pass; zero critical console errors in release build.
* ✅ **CI build** (local or GitHub Actions) produces signed Android AAB.

**Content KPIs**

* ✅ Minimum **12 POIs total** (≥3 per scene) with accurate geology copy (2–4 lines each).
* ✅ Map pins have **thumbnails + tooltips**.
* ✅ **Ambient audio** per scene present and looped seamlessly.

**Delivery KPIs**

* ✅ **Playable AAB/APK**, **README**, and **5–10 screenshots** from device.
* ✅ Short **demo video** (≤ 90 s) showing map → each scene → POI interaction.

---

## Milestones & Timeline (7 Days)

**Day 1 — Project Bootstrapping**

* Create Unity project (URP), folders, Git/LFS, base packages, Input System.
* Implement `Splash_Landing` with hero image + Settings stub.
* Performance budget doc; target device chosen.

**Day 2 — Map & Navigation**

* Build `Island_Map` scene (dummy geometry or stylized 2D/3D).
* Implement **Pin prefab**, load pins from JSON, scene loading pipeline.
* Back & pause menus framework.

**Day 3 — Museum Scene**

* Blockout Museum; add **3 POIs** with working info cards.
* Bake lighting; add ambient audio. Save visited states.

**Day 4 — Wells Scene**

* Outdoor terrain blockout; wells props; **3 POIs** + info cards.
* Optimize LODs; texture compression.

**Day 5 — Trail & Seating Scenes**

* Build Trail with waypoints; **3 POIs**.
* Build Seating vista; **3 POIs**; simple skybox, baked light.
* Implement **Badges** when all POIs visited per scene.

**Day 6 — Polish & Settings**

* Implement **VR/Cardboard toggle** (gyro look) + sensitivity.
* Localization table (EN ready, AR keys stubbed).
* Analytics events: `PinOpened`, `POIViewed`, `SceneCompleted`.

**Day 7 — QA & Delivery**

* Device tests, performance passes, fix crashes.
* Capture screenshots & short demo video.
* Produce **release AAB/APK** and update README.

---

## Deliverables & Definition of Done

* ✅ **Unity project** in repo with clean structure and Addressables (if used).
* ✅ **Android AAB/APK** (Release, IL2CPP or Mono if time-constrained).
* ✅ **README** (this file) + quickstart build steps.
* ✅ **Data JSONs** for pins and POIs.
* ✅ **Screenshots + short demo video** in `/Docs/`.
* ✅ **No critical errors** in player log; passes testing checklist.

---

## Testing Checklist

* **Navigation**

  * Enter → Map → each pin → back to Map works.
  * Scene Loader shows progress; cancel/back is safe.
* **POIs**

  * Tapping registers; info card opens/closes.
  * Visited state persists across app relaunch.
* **Performance**

  * FPS ≥ 30 in all scenes; no memory spikes on scene swaps.
* **Audio**

  * Ambience present; volumes adjustable in Settings.
* **Settings**

  * VR toggle switches control scheme (gyro vs touch).
  * Sensitivity sliders affect look speed.
  * Language switch updates UI text (where implemented).
* **Stability**

  * 10-minute soak per scene without crash.
  * Back button (Android) behavior correct in all screens.

---

## Risks & Mitigations

* **Art pipeline overload** → Use **low-poly stylized** kits; prioritize readable layouts.
* **Performance drops** → Bake lighting, limit post-FX, atlas textures, LODs, occlusion culling.
* **Scope creep** → Lock to **4 scenes**, **≥12 POIs**; future features deferred.
* **VR motion sickness** → Default to touch/joystick; in VR mode, prefer **teleport** or slow walk, reduce acceleration.

---

## Future Extensions

* Arabic full localization (RTL UI).
* Photo mode & postcard share.
* Quizzes at POIs; educator dashboard.
* Cloud content updates via remote config.
* iOS build & headset VR (Quest) port.

---

## License

Internal educational prototype. Distribution by project owner only. Add your preferred license if needed.

---

### Quick Build Notes (Android)

1. Install Unity 2022 LTS with Android modules.
2. Open project → **File > Build Settings > Android** → Switch Platform.
3. Player Settings: set package name, IL2CPP (if time allows), ARM64, Min SDK 26.
4. Build **AAB/APK** (Release). Test on target device.

---

**Contact & Handover**
Please keep commit messages clear and push a buildable project daily.
Open issues for blockers immediately; aim to keep scenes playable end-to-end each day.
#   S c h o o l _ P r o j e c t  
 
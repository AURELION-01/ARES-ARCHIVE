# ARES-ARCHIVE
Explore Mars through interactive maps, mission planning, rover weather data, and EVA simulations. A little step towards understanding the Red Planet and imagining life beyond Earth. 🔴


# 🔴 ARES Archive
### Martian Map · Astronaut Marswalk · Mission Planner

**Explore Mars. Study its terrain. Plan the traverse.**

ARES Archive is an interactive Mars exploration and mission-planning workspace built around NASA planetary datasets and rover observations. It combines orbital imagery, Martian terrain exploration, rover weather telemetry, astronomical timekeeping, and an experimental Extravehicular Activity (EVA) planner into one immersive interface.

The goal is to make planetary exploration more than a collection of images and numbers: a place where you can explore the surface, investigate landmarks, create routes, and experiment with the challenges of human exploration on Mars.

---

## 🚀 Features

### 🗺️ Interactive Martian Map
- Interactive planetary map powered by **Leaflet 1.9.4**.
- NASA Mars Trek WMTS imagery using the `EPSG:4326` coordinate reference system.
- Pan, zoom, inspect coordinates, and navigate across the Martian surface.
- Custom planetary scale bar designed around Mars rather than Earth's default map scale.
- Click-to-inspect mode and click-to-add-waypoint mode.
- Smooth map navigation and route-focused zoom controls.
- NASA imagery loading with a simulated terrain fallback when tiles are unavailable.

### 🛰️ NASA Mars Trek Map Layers

Switch between different orbital and scientific map products:

| Layer | Dataset / Resolution |
| Viking Color Mosaic | Viking MDIM 2.1, 232 m |
| MGS MOLA Color Elevation | 463 m |
| MOLA + HRSC Hillshade Blend | 200 m |
| MGS TES Plagioclase Mineralogy | Spectral overlay |

Additional capabilities:
- Toggle the TES mineralogy overlay.
- Adjust overlay opacity.
- Add custom layers using NASA Mars Trek catalog layer IDs.
- Display tile-loading status and distinguish imagery from fallback rendering.

### 📍 Scientific Landmarks

Explore important Martian locations, including:

- Jezero Crater
- Gale Crater
- Olympus Mons
- Valles Marineris

Each location includes coordinates, scientific context, and a sample exploration route where available.

### 🪨 AI4Mars-Inspired Terrain Classification

The planner uses the four terrain categories associated with NASA/JPL's AI4Mars dataset:

| Terrain | Interpretation |

| Soil | Firm regolith |
| Bedrock | Exposed rock and outcrops |
| Sand | Potential slip and sink hazard |
| Big Rock | Boulder and obstacle hazard |

The interface includes terrain previews, illustrative class distributions, waypoint terrain editing, and terrain-dependent effort multipliers.

**Important:** The current coordinate-based terrain assignment is a heuristic demonstration, not an actual AI4Mars neural-network prediction or image segmentation result. The displayed class distributions are illustrative samples.

### 🌡️ Mars Weather Dashboard

Weather monitoring is centred around two NASA rover missions:

**Perseverance**
- Location: Jezero Crater
- Weather instrument: MEDA
- Temperature and atmospheric pressure information

**Curiosity**
- Location: Gale Crater
- Weather instrument: REMS
- Temperature and atmospheric pressure information

The dashboard includes:
- Rover switching.
- Weather synchronization controls.
- Temperature readings and pressure displays.
- Seven-Sol temperature trend visualisations.
- Data-status indicators for live and sample values.

Weather retrieval attempts to use:
- NASA Mars 2020 weather feed (MEDA).
- NASA Mars Science Laboratory weather feed (REMS).
- A Vercel-hosted weather endpoint as an additional source.

If live retrieval is unavailable, built-in sample values are displayed instead.

### 🕒 Mars Astronomical Clock

A dedicated Martian timekeeping system featuring:

- Coordinated Mars Time (MTC).
- Mars Sol Date (MSD).
- Local solar time at Perseverance's Jezero location.
- Local solar time at Curiosity's Gale location.
- Rover mission Sol counters.

### 👨‍🚀 EVA Mission Planner

Plan experimental astronaut traverses across the Martian surface.

**Route planning**
- Place a habitat starting point and multiple EVA waypoints.
- Create, undo, and clear routes.
- Automatically calculate great-circle distances.
- View individual route legs and total traverse distance.
- Inspect waypoint coordinates, terrain, elevation provenance, and science objectives.
- Generate an elevation cross-section from planned waypoints.
- Export and copy mission telemetry briefs.

**Science objectives**
- Core Sample Drill
- Subsurface Ice Radar
- Biosignature UV Scan
- APXS Rock Chemistry
- Seismic / Meteorological Station
- Depot / Habitat Waypoint

### 🧪 Life Support and Hazard Estimation

The EVA planner estimates:

- Traverse distance.
- Terrain-adjusted walking time.
- Oxygen consumption.
- Suit battery and thermal-resource usage.
- Habitat walkback distance.
- Return-resource reserve.
- Potential point-of-no-return conditions.
- Terrain-related route warnings.

Several assumptions are editable, including nominal walking speed, PLSS duration, walkback radius, return reserve, and terrain effort multipliers.

The model uses:
- Great-circle route calculations.
- Tobler's hiking function for slope-adjusted walking speed.
- A Pandolf-style metabolic effort model.
- Terrain-dependent effort multipliers.

These are experimental planning estimates, not validated astronaut-performance predictions. The walking and metabolic models are Earth-derived and do not fully model Mars gravity, spacesuit mechanics, or actual PLSS engineering.

---

## 🧬 Data Sources and Scientific References

ARES Archive draws inspiration and data from publicly accessible planetary science resources.

| Source | Used for |
|---|---|
| [NASA Mars Trek](https://trek.nasa.gov/mars/) | Martian orbital imagery and map layers |
| [NASA Mars Trek API Documentation](https://trek.nasa.gov/tiles/apidoc/trekAPI.html?body=mars) | WMTS tile-service structure and layer access |
| [NASA AI4Mars Dataset](https://data.nasa.gov/dataset/ai4mars-a-dataset-for-terrain-aware-autonomous-driving-on-mars) | Four-class terrain taxonomy and rover terrain-label reference |
| [NASA Mars 2020 Weather Feed](https://mars.nasa.gov/rss/api/?feed=weather&category=mars2020&feedtype=json) | Perseverance MEDA weather observations |
| [NASA MSL Weather Feed](https://mars.nasa.gov/rss/api/?feed=weather&category=msl&feedtype=json) | Curiosity REMS weather observations |
| [NASA Planetary Science](https://science.nasa.gov/mars/) | Mars science and mission-landmark references |
| [NASA PDS Geosciences Node](https://pds-geosciences.wustl.edu/) | MOLA and planetary topography dataset reference |

The project also uses a Vercel-hosted weather endpoint as an additional weather retrieval source.

### Data Provenance

Not every displayed value represents a direct NASA measurement.

- **NASA imagery:** Retrieved through Mars Trek WMTS where available.
- **Weather:** Live retrieval is attempted through the listed rover feeds and proxy endpoint. Built-in samples remain available as fallback.
- **Elevation:** The application contains a synthetic terrain-elevation model. It also attempts a point-elevation request through a NASA Trek endpoint, but that endpoint is not verified as a supported public service.
- **Terrain classification:** Uses coordinate-based heuristics and AI4Mars-inspired labels, not live AI4Mars image inference.
- **Mars time:** Calculated using astronomical timekeeping logic.
- **EVA estimates:** Generated from editable assumptions and Earth-derived mathematical models.

---

## 🎨 Interface and Experience

ARES Archive includes more than the mission planner itself:

- Animated starfield and cosmic backgrounds.
- Aurora-style visual effects.
- Interactive Mars hero display.
- Scrolling planetary data-source ticker.
- Scroll-triggered reveal animations.
- Pointer-responsive card highlights.
- Dedicated mission-team page.
- Animated team profile modal.
- Dark, space-inspired mission-control interface.
- Responsive layouts and interactive navigation.

---

## ⚠️ Disclaimer

ARES Archive is an independent educational and experimental project. It is not an official NASA product, and its EVA calculations, simulated terrain, illustrative classifications, and fallback environmental values should not be used for actual mission operations or safety-critical decisions.

The project aims to explore how planetary datasets, geospatial interfaces, and simplified mission models can come together in an interactive Mars exploration environment.

---

## 🔴 The Mission

To make Mars exploration more accessible, more interactive, and more understandable.

Because before humanity can walk on another planet, it has to learn how to explore it.

**Welcome to ARES Archive.**

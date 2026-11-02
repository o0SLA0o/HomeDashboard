# Ma Maison — Home Assistant dashboard

🇫🇷 [Version française](README.fr.md)

A **single-file** web dashboard (`maison.html`), with no dependencies and no build step, that controls Home Assistant in real time through its WebSocket API. Drop it into Home Assistant and open it in any browser: desktop, wall-mounted tablet or phone.

![Interactive floor plan, night mode](docs/plan-nuit.jpg)

> The interface follows the browser language: **English, French or Polish** (English for any other language). The screenshots on this page show the French interface with a demo house (simulated data), so button labels are given in English followed by the French label visible in the screenshots.

## Contents

- [Languages](#languages)
- [Interactive floor plan](#interactive-floor-plan)
- [Multiple levels](#multiple-levels)
- [Side panels](#side-panels)
- [Room controls](#room-controls)
- [Day / night mode](#day--night-mode)
- [Edit mode](#edit-mode)
- [Rooms and Types views](#rooms-and-types-views)
- [Cameras](#cameras)
- [Secure sign-in](#secure-sign-in)
- [On phones and tablets](#on-phones-and-tablets)
- [Installation](#installation)
- [Data and privacy](#data-and-privacy)

## Languages

The dashboard automatically follows the browser's preferred language:

- 🇬🇧 **English** (also used for any unsupported language)
- 🇫🇷 **French**
- 🇵🇱 **Polish**

Everything is translated: texts, device states (open, locked, detected…), error messages, plural forms (including Polish rules for 1, 2–4 and 5+), and number, date and time formats. Room and scene icons are recognised from their names in all three languages (e.g. *Kitchen*, *Cuisine*, *Kuchnia* → 🍳). Entity, room and device names come from Home Assistant and are shown as they are.

## Interactive floor plan

The **Plan** view shows the house from above. Rooms are generated automatically from the areas defined in Home Assistant, and can then be fully adjusted.

The floor plan reacts to the state of the house in real time:

- **Lights**: the room is lit by a glow in the **actual colour of the bulb** (RGB, or warm → cool white), whose intensity follows the brightness; the glow stops at the walls.
- **Temperature**: the floor is tinted blue when it is cool and orange when it is warm.
- **Openings**: an open door or window makes the room's walls flash red.
- **Presence**: a ripple spreads out from an active motion sensor.
- **Media**: a player that is currently playing shows the **cover art** of what is playing, with the title and artist scrolling under its name.
- **Sensors**: the value is shown under the icon's name.

Tapping an icon toggles the device (opens or closes a cover, starts a camera). Tapping a room opens a panel with all its controls.

## Multiple levels

![Upper floor](docs/etage.jpg)

**Floors** defined in Home Assistant (*Settings → Areas, labels & zones*) are picked up automatically. You can also create your own levels, for example an **outbuilding**, and assign rooms to them.

The level tabs sit in the top bar, with **activity badges**: number of lights on, a yellow dot when presence is detected, a flashing red dot when an opening is reported. On a tablet, you can also **swipe** left or right on the plan to change level.

## Side panels

![Side panels open](docs/panneaux.jpg)

Two floating panels complement the plan without taking space from it: they are **collapsed by default**, slide **over the plan** from a tab on each edge, and **collapse on their own after 30 seconds** without interaction.

**Left**

- **Occupancy**: house occupied or empty, with the Home Assistant people and their status (home, away, zone).
- **Quick scenes**: all scenes and scripts, run with one click.
- **House status**: alarm, gate, garage, doors and windows, locks, with a green tick or a red alert.

**Right**

- Average indoor **temperature**, with its 24-hour curve.
- **Energy**: current consumption (power sensor such as a smart meter) and a 12-hour histogram.
- **Shortcuts**: all lights, all covers and heating (with its mode: Comfort, Eco…).

Even when collapsed, the tabs show the essentials: number of people at home, alert badge and average temperature.

## Room controls

![Room panel](docs/piece.jpg)

Tapping a room opens a panel with all its controls, **grouped by device**: a smart bulb brings together its light and its power consumption, a smart plug its switch and its energy meter. It includes switches, brightness, covers, thermostat setpoint, media, locks, scenes and sensors.

## Day / night mode

![Plan in day mode](docs/plan-jour.jpg)

The ☀️ / 🌙 button in the top bar switches between:

- a midnight-blue **night theme**, with glowing effects;
- a light **day theme**, styled like an architect's model: off-white floors, slate walls, light glows that tint the floor.

Each mode can have **its own background photo** for each level, for example a 3D render of the house by day and by night.

## Edit mode

![Edit mode](docs/edition.jpg)

The ✎ button in the top bar turns on edit mode:

- **Rooms**: drag to move, corner ◢ to resize. Room names only appear in edit mode, to keep the plan uncluttered.
- **Devices**: every room starts empty. The **＋** in the top-right corner of a room opens a checklist of its Home Assistant entities, grouped by device; **×** removes a device from the plan.
- **Icon size**: **＋ / −** buttons under each room's **＋** (50 % to 250 %).
- **Alignment grid**: icons snap to a grid aligned with the walls; **Align** (« Aligner ») moves every icon on the level onto the grid at once.
- **Levels**: create, rename and delete levels, and assign rooms to them.
- **Background photo**: import one image per level and per mode, resize it with the **handles at the 4 corners** (aspect ratio kept, Shift for free resizing) and move it with the centre handle. **Overlay** (« Superposer ») shows the other mode's photo semi-transparently, and **Match** (« Caler ») copies its exact position, to align the day and night photos.
- **People**: remove a person from the occupancy strip.

![Choosing a room's devices](docs/choix-appareils.jpg)

## Rooms and Types views

![Rooms view](docs/vue-pieces.jpg)

The **Maison ▾** menu in the top-left corner gives access to two other views:

- **Rooms** (« Pièces »): every control, room by room, grouped by device;
- **Types**: every device by category (lights, plugs, covers, heating, media, sensors…).

Sections can be collapsed (the choice is remembered), search covers entities, devices and rooms, and a filter limits the display to one device type. In edit mode, you can **hide** an entity or a whole device; technical entities (diagnostic, configuration) are hidden by default.

![View menu](docs/menu-vues.jpg)

## Cameras

Cameras show a preview refreshed every 5 seconds. A click opens the full-screen **live stream** (MJPEG), automatically falling back to rapid snapshots if the camera does not provide a stream. Images go through the temporary token that Home Assistant provides for each camera.

## Secure sign-in

![Sign-in screen](docs/connexion.jpg)

**Sign in with Home Assistant** (« Se connecter avec Home Assistant ») uses Home Assistant's built-in OAuth authentication: you log in on HA's usual login page (username, password, two-factor authentication if enabled), then return to the dashboard.

- The access token lasts 30 minutes and is **renewed automatically**.
- Each device appears in the Home Assistant profile (*Security → Refresh tokens*) and can be **revoked** individually there.
- Signing out revokes the session on the Home Assistant side.
- For a kiosk-mode screen, a **long-lived access token** can still be used.

## On phones and tablets

<img src="docs/mobile.jpg" alt="Phone layout" width="320">

The layout adapts to small screens: two-row top bar, full-width plan, panels that slide over it. On a wall-mounted tablet, automatic session renewal means you never have to sign in again.

## Installation

1. Copy `maison.html` into Home Assistant's `/config/www/` folder, for example with the *File editor* or *Samba* add-on. Restart HA if the `www` folder has just been created.
2. Open `http://<ha-address>:8123/local/maison.html`.
3. Click **Sign in with Home Assistant** (« Se connecter avec Home Assistant »).
   - Alternative for a kiosk-mode screen: « Utiliser plutôt un jeton d'accès longue durée » (use a long-lived access token instead), created in your HA profile → Security → Long-lived access tokens.
   - If the page is not served by Home Assistant, allow its origin in `configuration.yaml` (`http: cors_allowed_origins:`).
4. Switch to edit mode (✎) and add the devices of each room with **＋**.

After updating the file, reload the page with **Ctrl+F5** to avoid the old cached version.

### Requirements

- Home Assistant with **areas** defined, and ideally **floors** (2024.4 or later).
- Optional: `person` and `weather` entities, temperature and power sensors, scenes and scripts to enrich the side panels.

## Data and privacy

### Where are the settings stored?

| Data | Location |
|---|---|
| Floor plan (rooms, chosen devices and their position, icon size, grid), levels and room assignment, hidden entities and people, photo framing | **Home Assistant**, in the frontend user-data store (`frontend/set_user_data`, key `maison_dashboard`) |
| Background photos (one per level and per mode) | **Home Assistant**, in the image store (`/api/image/upload`, like profile pictures) |
| Last view, last level, day/night mode, collapsed sections, sign-in session | The device's browser |

What this means:

- **Same settings on every device** signed in with the same Home Assistant account: a plan set up on the computer shows up on the tablet. Changes made elsewhere are picked up when signing in and when returning to the tab.
- **Included in Home Assistant backups** (the `.storage` folder and the image folder).
- Settings are **per account**: a tablet signed in with another HA user has its own plan.
- Uploading photos requires an **administrator account**. Without it, the photo stays on the device (a message says so in the edit banner); the rest of the settings are still saved in HA.
- The first time this version runs, the settings and photos already in the browser are **uploaded automatically** to Home Assistant.
- The edit-mode banner shows the status: « ☁️ Enregistré dans Home Assistant » (saved in Home Assistant), « Enregistrement… » (saving…) or a warning.

### Privacy

- The `maison.html` file contains **no secrets**: signing in happens in the browser. Since files in `/config/www/` are accessible without authentication, nothing sensitive is written there.
- House data is only exchanged with your Home Assistant instance. Only the font (Inter) is loaded from Google Fonts; without Internet access, the system font is used instead.

# smart-alarm-ha

Phone‑free **Smart Alarm** for Home Assistant: calendar‑aware, Nest output, NFC/button snooze with safe dismiss, Android fallback when traveling. No phone at the bedside.

- **Calendar aware**: respects Workday + your Vacation calendar.
- **Programs**: Work / Gym / Weekend (customizable).
- **Snooze with task**: NFC or button for snooze, bathroom tag for dismiss.
- **Outputs**: Nest speakers (MP3/TTS), lights, optional shutters; volume ramp + escalation.
- **Travel fallback**: sets an Android alarm via the HA companion app (`SET_ALARM`).
- **UI**: Daily Control dashboard + Admin/Settings dashboard. Full config via **Blueprint UI**.

## Install

### Option A – HACS (recommended)
1. In HACS → *Integrate* (three dots) → **Custom repositories** →
   - **Repository**: `https://github.com/YOUR_GITHUB/smart-alarm-ha`
   - **Category**: `Blueprints`
2. Add → Then open **HACS → Blueprints** → find **Phone‑free Smart Alarm** → **Import**.
3. Create an automation from the blueprint and select your entities.
4. (Optional) Dashboards: After HACS clones the repo, import the YAML in `dashboards/` into your Lovelace dashboards (Raw config editor → *Manage dashboards* → *New* → *Show in sidebar* → paste YAML).

> If HACS asks for minimum HA version: this project targets **Home Assistant 2024.12+**.

### Option B – Manual install
- Copy `blueprints/automation/phone_free_alarm.yaml` to `/config/blueprints/automation/smart-alarm-ha/`.
- Copy the **optional** files:
  - `packages/intelligent_alarm.yaml` → `/config/packages/` (if you use package mode)
  - `dashboards/*.yaml` → import into Lovelace
  - `media/alarms/` → `/config/www/alarms/` or `/media/alarms/` (adjust paths if needed)

## Setup
1. **Integrations**: Workday + Google Calendar (choose your *Urlaub* calendar).
2. **Companion App**: Install on Android and enable **Notification Commands**.
3. **Write NFC tags** with the HA app (one for snooze, one for dismiss) and paste IDs in the blueprint inputs.
4. **Create an automation** from the blueprint:
   - Select Workday/Vacation entities
   - Choose your schedules and program selector
   - Map Nest speaker, bedroom light, optional shutter, and your notify device
5. **Dashboards** (optional): import `dashboards/alarm_daily.yaml` and `dashboards/alarm_admin.yaml`.

## Files
- `blueprints/automation/phone_free_alarm.yaml` – Main blueprint (UI‑configurable)
- `dashboards/alarm_daily.yaml` – Daily controls
- `dashboards/alarm_admin.yaml` – Admin/settings view
- `packages/intelligent_alarm.yaml` – Alternative package (advanced users)
- `media/alarms/wakeup_chime.mp3` – Example tone placeholder (add your own)

## Travel mode
If you create a boolean like `input_boolean.travel_mode` and set the program to **Travel**, the system sets your next alarm on Android as fallback using the companion app intent.

## License
[MIT](LICENSE)

## Contributing
PRs and issues welcome! Please keep blueprints UI‑first, and add examples/screens in `/docs`.

## Roadmap
- Multi‑profile support (per person)
- Optional siren and multi‑room alarm cascade
- iOS Shortcuts fallback

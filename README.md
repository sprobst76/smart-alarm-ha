# Smart Alarm for Home Assistant (Blueprint)

Sleep-as-Android-like alarm as a **Home Assistant Blueprint**.

**Features**
- Weekly schedule (pick weekdays), even/odd weeks, day-of-month, one-shot
- Skip next (one-shot) via `input_boolean`
- Smart window (gentle pre-alarm before main alarm)
- Snooze with limit + failsafe (force loud alarm after X minutes)
- Holiday/Vacation calendar skip
- Optional task: **scan a specific NFC/Tag** to dismiss
- Mobile fallback: Companion App push with **SNOOZE/DISMISS** actions

## Quick start
1. Put this repo on GitHub (e.g. `https://github.com/sprobst76/smart-alarm-ha`).
2. In Home Assistant go to **Settings → Automations & Scenes → Blueprints → Import** and paste this URL:  
   `https://github.com/sprobst76/smart-alarm-ha/blob/main/blueprints/automation/smart_alarm/blueprint.yaml`
3. Create an automation from the imported blueprint and fill the inputs.

## Helpers (recommended)
Create an `input_boolean` for "skip next":
```yaml
input_boolean:
  smart_alarm_skip_next:
    name: Smart Alarm – Skip Next
    icon: mdi:alarm-snooze
```
Then select that boolean in the blueprint input.

## Media
Place sound files in **/media** and reference them in the inputs, e.g. `/media/alarm.mp3` and `/media/alarm_soft.mp3`.

## Notes
- HACS currently doesn't install Blueprints directly. Use the **Import by URL** flow.
- Add a Tag in **Settings → Tags** if you want the "NFC/Tag required" task.

---

MIT © 2025

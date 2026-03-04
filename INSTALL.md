# Installation

This guide sets up ViewAssist Room Panels in Home Assistant.

## 1. Prerequisites

Install and verify:

- ViewAssist integration
- `custom:button-card`
- Mushroom cards
- `card-mod`

Also ensure each ViewAssist satellite/audio device is assigned to a Home Assistant Area.

## 2. Install the Blueprint

1. Copy `blueprints/va-room-light-blueprint.yml` into your HA config:
   - `/config/blueprints/automation/<your_namespace>/va-room-light-blueprint.yml`
2. In Home Assistant, go to **Settings -> Automations & Scenes -> Blueprints**.
3. Import/select the blueprint and create an automation from it.

## 3. Create Your Areas Mapping

1. Open `examples/areas-example.json`.
2. Replace example entries with your own `area_id -> entity_ids[]` mapping.
3. Paste the final JSON into the blueprint input field: **Areas mapping (JSON)**.

Recommended:

- Keep your personal mapping in `areas-mysetup.json` (already gitignored).

## 4. Create Dashboard Panels

In your ViewAssist dashboard, create panel views and paste these files into each view YAML:

- Lights panel: `views/lights.yml`
- Room panel: `views/room.yml`
- Areas panel: `views/areas.yml`

Use paths that match the blueprint defaults:

- `/view-assist/lights`
- `/view-assist/room`
- `/view-assist/areas`

If your paths differ, update the blueprint inputs accordingly.

## 5. Optional Menu Buttons

To add menu shortcuts, copy content from `templates/custom_icon_templates.yml` into your dashboard raw YAML under:

- `button_card_templates:`

## 6. Activate and Test

1. Save automation.
2. Run the automation once manually.
3. Test voice commands:
   - `show lights`
   - `show bedroom lights`
   - `show room`
   - `show areas`

## Troubleshooting

- If no entities appear in panels:
  - Re-run the automation manually.
  - Check `areas_json` is valid JSON.
  - Confirm `area_id` names match what your setup expects.
- If area voice commands do not route correctly:
  - Verify spoken area normalizes to your key format (`living_room`, `guest_room`, etc.).

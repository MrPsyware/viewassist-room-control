# ViewAssist Room Panels

Reusable Home Assistant assets for ViewAssist dashboards with per-area navigation and dynamic room/light panels.

## What This Repo Includes

- `blueprints/va-room-light-blueprint.yml`: Automation blueprint that:
  - Loads an area-to-entities map
  - Pushes `area_entity_list` and `areas_entity_map` into ViewAssist entities
  - Handles voice navigation for Lights, Room, and Areas panels
- `views/lights.yml`: Dynamic per-area lights/scenes panel
- `views/room.yml`: Dynamic per-area room status/control panel
- `views/areas.yml`: Area launcher panel with high-level room chips
- `templates/custom_icon_templates.yml`: Optional button-card templates for menu shortcuts
- `examples/areas-example.json`: Generic example area/entity mapping
- `areas-mysetup.json`: Personal/local mapping (gitignored)

## Requirements

- Home Assistant with:
  - ViewAssist
  - `button-card`
  - Mushroom cards
  - `card-mod`
- A ViewAssist dashboard already created
- ViewAssist satellite/audio entities assigned to Home Assistant Areas

## Quick Start

1. Copy `blueprints/va-room-light-blueprint.yml` to:
   - `/config/blueprints/automation/<your_namespace>/`
2. Import the blueprint in Home Assistant Automation UI.
3. Use `examples/areas-example.json` as your template and create your own local mapping JSON.
4. Create 3 panel views in your ViewAssist dashboard:
   - Lights (`views/lights.yml`)
   - Room (`views/room.yml`)
   - Areas (`views/areas.yml`)
5. Add optional menu templates from `templates/custom_icon_templates.yml` under `button_card_templates` in your raw dashboard YAML.
6. Run the automation once manually, then test voice commands.

## Voice Commands

Default commands included in blueprint inputs:

- `show lights`
- `show <area> lights`
- `show room`
- `show <area> room`
- `show areas`

## Configuration Notes

- Area names from voice are normalized to lowercase snake_case (`Living Room` -> `living_room`).
- `areas_json` keys should match normalized area IDs used by your setup.
- `areas-mysetup.json` is intended for local/private data and excluded from git.

## Installation Guide

See [INSTALL.md](INSTALL.md) for full setup instructions.

## Notes

This is a personal project and support is best-effort.
Pull requests are welcome, but review/merge timing is not guaranteed.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE).

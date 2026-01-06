# Plant Soil Moisture Notification Blueprint

A Home Assistant blueprint that automatically sends notifications when your plants need water and confirms when they've been watered.

## Features

- 🌱 **Smart notifications** when soil moisture drops below threshold
- ✅ **Confirmation alerts** when plant has been watered
- 📱 **Multi-device support** - notify multiple phones
- 💧 **Customizable thresholds** for different plant types
- 🔔 **Persistent notifications** in Home Assistant UI
- 🎯 **Status tracking** using input boolean helpers

## Installation

### Option 1: Direct Import

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2Fspiddeer%2Fha-plant-notifications%2Fblob%2Fmain%2Fplant_soil_moisture_notification.yaml)

### Option 2: Manual Installation

1. Copy the blueprint URL: `https://github.com/spiddeer/ha-plant-notifications/blob/main/plant_soil_moisture_notification.yaml`
2. In Home Assistant, go to **Settings** → **Automations & Scenes** → **Blueprints**
3. Click the **Import Blueprint** button
4. Paste the URL and click **Preview**
5. Click **Import Blueprint**

## Prerequisites

Before using this blueprint, you need:

1. **Soil moisture sensor** (e.g., Xiaomi Mi Flora, ESPHome-based sensor)
2. **Input boolean helper** to track watering status:
   - Go to **Settings** → **Devices & Services** → **Helpers**
   - Click **Create Helper** → **Toggle**
   - Name it something like `Plant Name Needs Water`

## Configuration

After importing the blueprint, create a new automation and configure:

| Parameter | Description | Example |
|-----------|-------------|---------|
| **Plant Name** | Display name of your plant | `Fredskallan` |
| **Soil Moisture Sensor** | Entity ID of the sensor | `sensor.plant_2_soil_moisture` |
| **Thirsty Threshold** | Moisture % to trigger "needs water" | `20` |
| **Watered Threshold** | Moisture % to trigger "watered" confirmation | `40` |
| **Watering Status Boolean** | Helper to track status | `input_boolean.fredskallan_behover_vatten` |
| **Notification Devices** | Mobile app services to notify | Select from list |

## Example Usage

This blueprint will:

1. **When moisture drops below threshold:**
   - Turn on the status boolean
   - Send push notification to selected devices
   - Create persistent notification in HA

2. **When moisture rises above threshold (and boolean is on):**
   - Send "watered" confirmation to devices
   - Update persistent notification
   - Turn off the status boolean

## Notification Examples

**Thirsty Alert:**
```
💧 Växtvarning - Fredskallan
Fredskallan behöver vatten! Nuvarande fukt: 18%
```

**Watered Confirmation:**
```
✅ Fredskallan vattnad
Fukt är nu OK igen: 42%
```

## Tips

- Set **Thirsty Threshold** based on your plant's needs (succulents ~15%, tropical ~25%)
- Set **Watered Threshold** higher than thirsty threshold to avoid notification spam
- Use different thresholds for different plant species
- Create one automation per plant using this blueprint

## Contributing

Found a bug or have a suggestion? [Open an issue](https://github.com/spiddeer/ha-plant-notifications/issues) or submit a pull request!

## License

MIT License - feel free to use and modify as needed.

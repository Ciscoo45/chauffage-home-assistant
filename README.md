## Ciscoo45 - Chauffage Home Assistant

This README file is available in: [English](README.md) | [Français](README-fr.md)

Complete implementation of a heating management system for Home Assistant
    
## Notes

- Currently supports electric radiators only.
- A "simple" integration in terms of technologies used (YAML files organized into subfolders + blueprints for specific features): requires manual installation but makes the code easy to understand, maintain, and extend.

## Implemented Features

- **Time-based scheduling** for Home and Away modes (via Scheduler).
- **Separate weekday and weekend schedules**, with the option to use weekend schedules during holidays and public holidays (also suitable for working from home).
- **Manual mode** with a fixed target temperature, overriding Home / Away schedules.
- **Frost Protection mode**, with an optional maximum humidity threshold to control heating.
- **Temporary override (Boost)** with the option to return to the previous state or switch to another mode. Supports physical switches and mobile notifications sent to people currently at home, allowing them to extend or stop the Boost period.
- **Automatic absence detection**, supporting both whole-home absence and a primary occupant assigned to a specific room. When that person is away, only the relevant rooms have their temperature reduced, while shared rooms remain unaffected. Presence can also be manually forced (e.g., when guests are staying).
- **EDF Tempo tariff management**, with configurable automatic temperature reductions on White and/or Red days. Day colors and electricity rates are retrieved via api-couleur-tempo.fr (avoiding any reliability issues with the RTE API).
- **Door and window opening detection**, with automatic heating suspension after a configurable delay, optional heating restart when the opening is closed, and support for multiple doors/windows per room.
- **Multiple radiators per room**, controlled together.
- **Pilot wire control**, with an optional inverted mode (e.g., Sonoff ZBMINI relay + diode).
- **RF control** for radiators equipped with Delta Dore X2D modules.
- **Electricity consumption tracking** for radiators (kWh), integrated with the Home Assistant Energy Dashboard, based on the radiator's operating time and rated power.
- **Control switches** for heating, absence detection, and Tempo management, with both centralized master switches and individual radiator controls.
- **Lovelace dashboard cards**:
  - **Basic**: essential features.
  - **Advanced**: all features, including the currently active schedule, time remaining until the next scheduled temperature change, and daily energy consumption for the room.
  - **Heating diagnostics**: regulation graphs and direct access to schedules via Scheduler.
- **One-time event scheduling** via Scheduler (e.g., activate Home mode for a specific room in X hours).
- **Battery level monitoring** for temperature and humidity sensors.
- **Simple tuning guidance** for the two main room-specific parameters: heating power and room heat loss. Default values are provided, and users can fine-tune these settings to achieve faster heating and reduce temperature oscillations simply by analyzing the regulation graphs.
- **Consolidated outdoor temperature sensor**, with a fallback priority order: apparent temperature (OWM) > Météo-France temperature > local outdoor temperature sensor. A standalone local outdoor temperature sensor can also be used, provided it is properly positioned.

## Planned Features

- **Grid demand response (load reduction)**: use signals such as RTE EcoWatt (similar to services offered by Voltalis) to temporarily reduce electricity demand during grid stress events, within configurable time and temperature limits (e.g., a maximum temperature reduction of 1°C for up to 1 hour).
- **Vacation mode**, with progressive preheating before returning home.
- **Staggered heating control for rooms with multiple radiators** (`over_switch` mode), allowing radiator activation times to be offset to smooth electricity consumption.
- **Local load shedding**, automatically reducing electricity consumption when measured power approaches or exceeds a configured limit, prioritizing radiators closest to their target temperature.
- **Safety monitoring**: detection of heating failures, overheating due to unavailable or faulty sensors/relays, etc., with automatic safety measures and/or alerts.
- **Global open-window/door alert badge** on the main dashboard, displaying the number of doors or windows left open.

## Installation

    2 ways :
    - [prefered] config files and directories to merge to your HA config dir, then edit to change entities names
    - step by step from full documentation XLSX (needs update)

Doc structure:

https://github.com/Ciscoo45/chauffage-home-assistant/blob/Week-Vs-WE/Structure%20de%20la%20documentation%20-%20xlsx.png

<br>
<br>

## Original Work

**Home Assistant – Gestion de bout en bout du chauffage**

**Author:** Argonaute

**Source:** [Forum HACF – Gestion de bout en bout du chauffage](https://forum.hacf.fr/t/gestion-de-bout-en-bout-du-chauffage/4897)

<br>

## Related Project – Versatile Thermostat

A very comprehensive project for controlling electric radiators, thermostatic radiator valves, and air conditioning systems:

Integration and Lovelace card available on HA Marketplace.

**Versatile Thermostat pour Home Assistant**

**Auteur :** jmcollin78

**Source :** [Versatile Thermostat](https://www.versatile-thermostat.org/fr/)


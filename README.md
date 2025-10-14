Home Assistant - Electric heater management :

Complete implementation of a heating management system for Home Assistant:

    Proportional thermostat
    Window opening management
    Heating modes (Présence, Absence...)
    Time zones for heating shedule
    
Available forks here:

[Based on] Presence-Absence: [ProdOk]

    Based on Argonaute work (thanks for this work!), plus:
    - different mode names (Presence-Absence, instead of AutoConfort-AutoEco)
    - single Absence mode
    - 'radiateur' switch name instead of 'chauffage'

[Actual branch] Week-Vs-WE: [ProdOk]

    Based on Presence-Absence branch, plus:
    - multiple schedules for Presence (or Absence) modes if needed (ex. different Week & Weekend temp targets)
    - fixed: heater do not cut in Stop mode
    - better explanations for coef c and coef t to easy set each room
    - adjustable temperature for frost protection mode (blueprint selector)
    - multi-heaters for a same room, thermostat and temperature sensor
    - optional Climate mode, to drive Climate entities in HA instead of relays
        (ex. thru GCE RFplayer 1000 to drive heaters with Delta Dore X2D receiver)
    - optional inverted mode (ex. for SonOff ZBmini relay + diode)
    - note: still need to create a group of sensors in case of multi open-windows sensors per room

[Later] To do

    - add support for a limited time boost period
    - add support for target temperature auto-change option in case of EDF Tempo Red day
    - delay so every Thermostat doesn't start at the same moment (load optimization)
    - auto-absence mode thru location sharing in case nobody's home, with last status remembered for return
    - maybe: humidity threshold not to be exceeded (auto sanity boost)
    - maybe: option to accept optional load shedding during peak demand, as a civic act (Voltalis like)


###################################### ORIGINAL WORK ##############################

Home Assistant - Gestion de bout en bout du chauffage

by Argonaute

Please see https://forum.hacf.fr/t/gestion-de-bout-en-bout-du-chauffage/4897


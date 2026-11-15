
## Ciscoo45 - Chauffage Home Assistant

Ce fichier README est disponible en : [English](README.md) | [Français](README-fr.md)

Solution complète de gestion du chauffage pour Home Assistant.

## Notes

- Permet actuellement de piloter uniquement des radiateurs électriques.
- Intégration « simple » en termes de technologies utilisées (fichiers YAML organisés en sous-dossiers + blueprints selon les fonctions) : installation manuelle, mais permettant de comprendre, maintenir et faire évoluer facilement le code.

## Fonctionnalités intégrées

- **Programmation horaire** pour les modes Présence et Absence (via Scheduler).
- **Programmations différentes pour la semaine et le week-end**, avec possibilité d'appliquer la programmation du week-end pendant les vacances et les jours fériés (également compatible avec le télétravail).
- **Mode Manuel** avec une température de consigne fixe, permettant de contourner les programmations Présence / Absence.
- **Mode Hors-gel**, avec option de pilotage du chauffage selon un seuil maximal d'humidité à ne pas dépasser.
- **Dérogation temporaire (Boost)** avec retour, au choix, à l'état précédent ou à un autre mode. Prise en charge d'un interrupteur physique et notifications sur les mobiles des personnes présentes dans le logement, avec possibilité de prolonger la durée du Boost ou de l'arrêter.
- **Gestion automatique des absences**, prenant en charge aussi bien l'absence générale du logement que celle d'un utilisateur principal associé à une pièce. Lorsque cette personne est absente, seules les pièces concernées voient leur température réduite, sans affecter les pièces communes. Possibilité également de forcer la présence (par exemple, lorsque des invités sont présents).
- **Gestion du tarif EDF Tempo**, avec choix de réductions automatiques de température les jours blancs et/ou rouges. Les couleurs des jours et les tarifs de l'électricité sont récupérés via api-couleur-tempo.fr (afin d'éviter les problèmes de fiabilité de l'API RTE).
- **Détection des ouvertures de portes et fenêtres**, avec suspension automatique du chauffage après un délai configurable, possibilité de relancer la chauffe une fois l'ouvrant refermé et prise en charge de plusieurs portes/fenêtres par pièce.
- **Gestion de plusieurs radiateurs dans une même pièce**, pilotés ensemble.
- **Pilotage par fil pilote**, avec option de mode inversé (ex. : relais Sonoff ZBMINI + diode).
- **Pilotage RF** des radiateurs équipés de modules Delta Dore X2D.
- **Suivi de la consommation électrique** des radiateurs (kWh), intégré au tableau de bord Énergie de Home Assistant.
- **Interrupteurs de contrôle** pour la gestion du chauffage, des absences et de Tempo, avec des interrupteurs généraux centralisés ainsi que des commandes individuelles par radiateur.
- **Cartes Lovelace pour les tableaux de bord** :
  - **Simple** : fonctionnalités essentielles.
  - **Évoluée** : toutes les fonctionnalités, avec affichage de la programmation actuellement active, du temps restant avant le prochain changement de température programmé et de la consommation électrique du jour pour la pièce.
  - **Diagnostic de la chauffe** : courbes de régulation et accès direct aux programmations via Scheduler.
- **Programmation d'événements ponctuels à venir** via Scheduler (ex. : activer le mode Présence d'une pièce donnée dans X heures).
- **Suivi du niveau des piles** des capteurs de température et d'humidité.
- **Aide au réglage des paramètres de chauffe**, avec des explications simples sur les deux principaux paramètres à configurer par pièce : la puissance de chauffe et les déperditions thermiques. Des valeurs par défaut sont proposées, puis l'utilisateur peut affiner les réglages pour obtenir une chauffe plus rapide et limiter les oscillations de température, simplement en analysant les courbes de régulation.
- **Capteur de température extérieure consolidé**, avec un ordre de priorité en cas d'indisponibilité des données : température ressentie (OWM) > température Météo-France > sonde de température extérieure locale. Il est également possible d'utiliser uniquement une sonde de température extérieure locale, à condition de bien la positionner.

## Fonctionnalités prévues

- **Effacement réseau (réduction de charge)** : utilisation de signaux comme EcoWatt de RTE (sur le principe des services proposés par Voltalis) afin de réduire temporairement la consommation électrique lors des périodes de tension sur le réseau, dans des limites configurables de durée et de baisse de température (ex. : réduction maximale de 1 °C pendant 1 h).
- **Mode Vacances**, avec remise en chauffe progressive avant le retour au logement.
- **Pilotage décalé des radiateurs dans une même pièce** (mode `over_switch`), permettant de décaler les activations des différents radiateurs afin de lisser la consommation électrique.
- **Délestage local**, réduisant automatiquement la consommation électrique lorsque la puissance mesurée approche ou dépasse une limite configurée, en priorisant les radiateurs les plus proches de leur température de consigne.
- **Surveillance de sécurité** : détection des anomalies de chauffage (absence de chauffe, surchauffe due à un capteur ou à un relais indisponible ou défectueux, etc.), avec mise en sécurité automatique et/ou envoi d'alertes.
- **Indicateur global d'alerte pour les ouvrants** sur le tableau de bord principal, affichant le nombre de portes ou fenêtres restées ouvertes.

## Installation

Deux méthodes possibles :

- **Installation à partir des fichiers de configuration (conseillé)** : copier ou fusionner les fichiers et dossiers fournis avec le répertoire de configuration de Home Assistant, puis adapter les noms des entités à votre installation.
- **Installation pas à pas** : suivre la documentation complète au format XLSX (documentation nécessitant une mise à jour).

Structure de la documentation (release 1.22):

[![Structure de la documentation](Structure%20de%20la%20documentation%20-%20xlsx.png)](Structure%20de%20la%20documentation%20-%20xlsx.png)

<br>
<br>

## Travail original

**Home Assistant – Gestion de bout en bout du chauffage**

**Auteur :** Argonaute

**Source :** [Forum HACF – Gestion de bout en bout du chauffage](https://forum.hacf.fr/t/gestion-de-bout-en-bout-du-chauffage/4897)

<br>

## Projet connexe – Versatile Thermostat

Projet très complet permettant de piloter des radiateurs électriques, des radiateurs équipés de vannes thermostatiques ainsi que des systèmes de climatisation.

Intégration et carte Lovelace disponibles sur HA Marketplace :

**Versatile Thermostat pour Home Assistant**

**Auteur :** jmcollin78

**Source :** [Versatile Thermostat](https://www.versatile-thermostat.org/fr/)

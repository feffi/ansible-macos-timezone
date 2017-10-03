# ansible-macos-timezone
Ansible role to manage timezone settings in macOS.

[![Build Status](https://img.shields.io/travis/feffi/ansible-macos-timezone.svg)](https://travis-ci.org/feffi/ansible-macos-timezone) [![Github All Releases](https://img.shields.io/github/downloads/feffi/ansible-macos-timezone/total.svg)](https://github.com/feffi/ansible-macos-timezone) [![GitHub forks](https://img.shields.io/github/forks/feffi/ansible-macos-timezone.svg?style=social&label=Fork)](https://github.com/feffi/ansible-macos-timezone) [![GitHub stars](https://img.shields.io/github/stars/feffi/ansible-macos-timezone.svg?style=social&label=Star)](https://github.com/feffi/ansible-macos-timezone) [![GitHub watchers](https://img.shields.io/github/watchers/feffi/ansible-macos-timezone.svg?style=social&label=Watch)](https://github.com/feffi/ansible-macos-timezone) [![Twitter Follow](https://img.shields.io/twitter/follow/feffi1.svg?style=social&label=Follow)](https://twitter.com/feffi1) [![License](http://img.shields.io/:license-mit-blue.svg)](https://github.com/feffi/ansible-macos-timezone/blob/master/LICENSE)

## Requirements
- Ansible 2.3

### ansible.cfg
```
hash_behaviour = merge
```

## Install
Just add the role to your ``requirements.yml`` file:
```yaml
- src: https://github.com/feffi/ansible-macos-timezone.git
  name: feffi.macos-timezone
```

## Role Variables
All role based variables are listed below, along with default values:

```yaml
---
macos_timezone:
  # Set the timezone; see `systemsetup -listtimezones` for other values
  timezone: "Europe/Berlin"

  # Set 24-Hour time scale
  twentyfour: true

  # Set the current locale
  locale: "de_DE"

  # Set the current currency
  currency: "EUR"

  # Set available default languages
  languages: [ "de", "en" ]

  # Set locale to metric units scale
  use_metric_units: true

  # Set the current measurement units
  measurement_units: "Centimeters"

  # Set the current temperature unit
  temperature_units: "Celsius"
```

## Dependencies
None.

## Example Playbook

```yaml
    - hosts: all
      vars:
        macos_timezone:
          timezone: "Europe/Berlin"
          twentyfour: true
          locale: "de_DE"
          currency: "EUR"
          languages: [ "de", "en" ]
          use_metric_units: true
          measurement_units: "Centimeters"
          temperature_units: "Celsius"
      roles:
        - { role: feffi.macos-timezone }
```
Or with local parameters:

```yaml
    - hosts: all
      roles:
        - { role: feffi.macos-timezone,
            macos_timezone: {
              timezone: "Europe/Berlin",
              twentyfour: true,
              locale: "de_DE",
              currency: "EUR",
              languages: [ "de", "en" ],
              use_metric_units: true,
              measurement_units: "Centimeters",
              temperature_units: "Celsius"
            }
          }
```

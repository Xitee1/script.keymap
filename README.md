# script.keymap
A keymap editor for Kodi

## Extra features:
- New actions to send button presses to Home Assistant

### Home Assistant example
```yaml
triggers:
  - trigger: event
    event_type: kodi_keypress
    event_data:
      entity_id: fernseher_kodi
conditions: []
actions:
  - choose:
      - conditions:
          - condition: template
            value_template: "{{ trigger.event.data.data.key == 'notify1' }}"
        sequence:
          - action: switch.toggle
            target:
              entity_id: switch.some_switch
      - conditions:
          - condition: template
            value_template: "{{ trigger.event.data.data.key == 'notify2' }}"
        sequence:
          - action: light.toggle
            metadata: {}
            data: {}
            target:
              entity_id: light.some_light
mode: single
```

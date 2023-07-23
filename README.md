# ha-dashboard

This is designed to integrate Home Assistant and FoxESS hybrid inverters into one dashboard customised for a medium-sized tablet.

You may need to alter the names entities referenced as they're designed to work with Nathan's FoxESS-modbus integration.

Required add-ons:

1. FoxESS (modbus or web).
2. mini-graph-card
3. mushroom cards (or delete buttons if not wanted)
4. custom-bar-card
5. power-flow-card-plus

The battery percentage is adapted to reflect the true charge level (0 - 100%, instead of the Fox reported 10 - 100%). Add this code to your configuration.yaml to implement this on your own setup:

'''battery_soc_corrected:
           friendly_name: "Corrected State of Charge"
           unit_of_measurement: '%'
           device_class: battery
           value_template: >
               {{ ((states('sensor.battery_soc')|float - 10) | multiply(1.11)) | round(0) }}'''

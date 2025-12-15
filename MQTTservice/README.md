### MQTT Service

This section describes the configuration of the Tasmota smart socket and its integration with the MQTT service.

## Plug Configuration

Once the smart socket is configured using the setup instructions provided by the manufacturer, two rules are defined in the **Tasmota Console**.

# Rule 1: Binary Power State Publishing

This rule enables continuous publishing of a **binary power state**:
- `1` if power consumption is **> 5 W**
- `0` if power consumption is **< 1 W**

This allows the **CPEE process engine** to subscribe to the MQTT topic and detect whether the kettle is actively heating.

```text
Rule1
ON ENERGY#Power>5 DO Publish2 /lab-power/socket-4/Power 1 ENDON
ON ENERGY#Power<1 DO Publish2 /lab-power/socket-4/Power 0 ENDON
Rule1 1

Purpose:
  - Detect when the kettle is switched on
  - Detect when the kettle switches off after reaching the target temperature

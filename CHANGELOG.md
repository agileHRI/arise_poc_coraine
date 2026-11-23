# Changelog

## 0.2.0 - 2026-11-23

The OPC UA part of the PoC, through the FIWARE IoT Agent for OPC UA (interim: it will be replaced by
coraine's own OPC UA bridge once the coraine image includes it).

- OPC UA test server: Microsoft OPC PLC simulator 2.15.10.
- FIWARE IoT Agent for OPC UA 2.3.2 (registry in memory, no MongoDB), provisioned by the `iot-provision`
  service: `urn:ngsi-ld:Machine:press-1` with `cycleCount`, `running`, `temperature`, `vibration`, `inCell`.
- The press lives in coraine's tenant `arise` (the IoT Agent always writes to a named tenant; the DDS bridge
  writes to the default one). The seed also creates the robot cell in that tenant.
- Grafana: data sources for the tenant `arise`, dashboard "ARISE PoC - Press (OPC UA)", alert rule
  "Press temperature high" (above 103).
- c³ named demo `arise-opcua` (tenant `arise`) with the alarm "Press temperature high".

## 0.1.0 - 2026-11-23

First version: the ROS 2 part of the ARISE PoC, on coraine 0.7.0.

- turtlesim (Vulcanexus Jazzy) → coraine DDS bridge, with DataChannels: one `Turtle` entity per turtle,
  linked to an `Arena` and a `RobotCell`.
- History in TimescaleDB (`--troe timescale`).
- Grafana 13: a live dashboard (SQL) and a history dashboard (NGSI-LD temporal API, Infinity plugin).
- Grafana alert rule "Turtle near a wall", with an optional Telegram contact point.
- c³ named demo `arise`: graph view and four wall alarms.

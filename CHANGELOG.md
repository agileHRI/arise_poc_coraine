# Changelog

## 0.1.0 - 2026-11-23

First version: the ROS 2 part of the ARISE PoC, on coraine 0.7.0.

- turtlesim (Vulcanexus Jazzy) → coraine DDS bridge, with DataChannels: one `Turtle` entity per turtle,
  linked to an `Arena` and a `RobotCell`.
- History in TimescaleDB (`--troe timescale`).
- Grafana 13: a live dashboard (SQL) and a history dashboard (NGSI-LD temporal API, Infinity plugin).
- Grafana alert rule "Turtle near a wall", with an optional Telegram contact point.
- c³ named demo `arise`: graph view and four wall alarms.

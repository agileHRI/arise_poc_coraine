# ARISE PoC with coraine

The ARISE Proof of Concept on [coraine](https://github.com/SEAMWARE/coraine), the ARISE context broker:
three ROS 2 turtles become NGSI-LD entities, their history goes to TimescaleDB, Grafana shows it live
and over time, and the coraine Control Center (c³) shows the turtles as a live graph with alarms.

```text
turtlesim (ROS 2) ──DDS──►  coraine  ──►  TimescaleDB  ──SQL──────────────►  Grafana
                               ├──── NGSI-LD temporal API ────────────────────┘
                               └──── NGSI-LD API + live notifications ──────►  c³
```

**The step-by-step guide is in the ARISE documentation:**
[Run the ARISE PoC with coraine](https://arise-framework-documentation.readthedocs.io/en/latest/rst/how_to/arise_poc_coraine/arise_poc_coraine.html).
This README is the short version.

## Requirements

- Linux on `amd64`, Docker and Docker Compose v2, about 10 GB of free disk.
- Optional: an X11 desktop to see the turtles; [c³](https://github.com/SEAMWARE/c3) for the live graph.

## Quick start

```bash
git clone https://github.com/agileHRI/arise_poc_coraine.git
cd arise_poc_coraine
docker compose up -d --build

# the turtles (add QT_QPA_PLATFORM=offscreen without a desktop; with one, run `xhost +local:docker` first)
docker compose exec ros2 bash -ic "ros2 run docs_turtlesim turtlesim_node_keys"

# in a second terminal: 1/2/3 choose a turtle, the arrows move it, q quits
docker compose exec ros2 bash -ic "ros2 run docs_turtlesim turtlesim_multi_control"
```

Then:

- **coraine** - `curl -s "localhost:1026/ngsi-ld/v1/entities?type=Turtle"`
- **Grafana** - http://localhost:3000 (`admin` / `admin`), folder **ARISE PoC**: two dashboards and the
  alert rule *Turtle near a wall*. Telegram: see
  [`telegram.yaml.example`](grafana/provisioning/alerting/telegram.yaml.example).
- **c³** - add `"demos": { "arise": { "url": "http://127.0.0.1:7996/c3.json" } }` to `~/.config/c3/c3.json`,
  start `c3`, type `arise` in Explore and press **Connect**.

Stop with `docker compose down` (`-v` also deletes the data).

⚠ A local demo: coraine runs without authentication and the passwords are the defaults. Do not expose
these ports to a network you do not trust.

## What is in it

| Path | What |
|---|---|
| `docker-compose.yaml` | timescale, coraine, seed, c3-descriptor, ros2, grafana |
| `dds.json` | the DDS bridge mapping: ROS 2 topics → `Turtle` entities (DataChannels) |
| `seed/arena.json` | the static model: the robot cell and the arena |
| `c3/c3.json` | the c³ demo descriptor: graph view, types, alarms |
| `ros2/Dockerfile` | Vulcanexus Jazzy with eProsima's keyed turtlesim |
| `grafana/` | data sources, dashboards and alert rules (provisioned) |

## Status

The ROS 2 part of the PoC. Next: OPC UA (through coraine's OPC UA bridge) - see [CHANGELOG.md](CHANGELOG.md)
and the issues.

## License

Licensed under the [Apache License 2.0](LICENSE) - Copyright 2026 Seamware. Every file that can hold a
comment carries an `SPDX-License-Identifier`. Contributions: see [CONTRIBUTING.md](CONTRIBUTING.md).

This repository shares no files with the original ARISE PoC
([Engineering-Research-and-Development/arise-poc](https://github.com/Engineering-Research-and-Development/arise-poc),
AGPL-3.0): everything here was written for coraine.

## Maintainers

- Ken Zangelin ([@kzangeli](https://github.com/kzangeli))
- Francisco Meléndez ([@FcoMelendez](https://github.com/FcoMelendez))

The ARISE project has received funding from the European Union's Horizon Europe research and innovation
programme.

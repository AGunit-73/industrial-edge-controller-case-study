

# Industrial Edge Controller — Text-Only Case Study (Redacted)

> Local-network **industrial controller** enabling device calibration, safe automated runs, real-time telemetry, and exportable reports. Operable from a desktop tablet UI and a web/mobile UI.  
> **Note:** Public, text-only summary. No client names, screenshots, videos, or code.

---

## Summary
- Built a **local-first** control system used in low-connectivity environments.
- Operators can **calibrate channels**, run sessions with **total limits** and **per-channel targets**, and export **searchable history** for audits.
- Emphasis on **safety**, **observability**, and **latency-predictable UX**.

## My Role
End-to-end engineering across:
- Architecture & device-service design (commands + realtime telemetry)
- Tablet kiosk flows and web/mobile UI behavior
- Calibration, run orchestration, and reporting pipeline
- Packaging & on-device deployment (system services, logging, env config)

## Problem & Constraints (generalized)
- Must function **offline on LAN**; internet may be unavailable.
- **Safety-critical** actions (E-stop, low-volume, level sensor).
- **Simple operator workflows** in harsh field conditions.
- **Auditable** actions and results for compliance.

## Approach (high level)
- **Local Python service** interfaces with pumps/sensors.
- **REST for commands** (idempotent, retryable).
- **Event stream** for telemetry to UIs (low-latency updates).
- **Authoritative device state**; UIs mirror state and remain stateless.
- **Lightweight local store** for calibration, sessions, and reports.

## Capabilities (abstracted)
- Channel **calibration & priming** (direction, speed/RPM caps)
- **Run sessions** with total-mix limit & per-channel targets
- **Live telemetry** (flow, RPM, totals) and operator alerts
- **Emergency Stop** path independent of UI state
- **Searchable history** and **CSV export**

## Key Engineering Decisions
- Split **commands vs telemetry** to simplify reliability and UX.
- Keep **safety paths hardware-first**; UI is never the single point of failure.
- Provide **mock sensors** for rapid UI/dev testing without hardware.
- Add **structured logs + rotation**, and surface health via simple status endpoints.

## Reliability, Safety, and Observability
- Watchdog restart of device service; defensive command handling.
- Debounced/validated inputs; clear state transitions.
- Traces/logs for: channel actions, session lifecycle, alerts, exports.

## Security & Privacy (local-first)
- LAN-scoped control; optional admin token for write endpoints.
- No cloud dependencies required for normal operation.

## Outcomes (generalized)
- Faster setup, fewer operator mistakes, predictable latency.
- Auditable sessions with consistent exports.

> **Interview-only note:** I can walk through a redacted demo privately (no production assets) to illustrate flows and decisions.

## What I’d Improve Next
- Formal typed command/telemetry schema & contract tests
- OTA update mechanism for device service
- Role-based access & per-operator analytics

## Contact
Abhishek Gurudwar • abhishekgurudwar1997@gmail.com • linkedin.com/in/abhishek-gurudwar

---

### Repo Scope
This repository is a **text-only portfolio summary**. It intentionally contains no source code, media, or identifiers from the original engagement.

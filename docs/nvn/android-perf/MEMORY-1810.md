# Android memory reduction, 2026-10-18 (Galaxy S23)

Status: **no phone measurements were possible** in this session: `adb devices` listed no device (USB not connected
or not authorised, adb server restarted twice). Nothing below is measured on a phone.

## Done
| Change | Status |
|---|---|
| MEMORY.md item 11: every 30 s the memory guard also logs `memory: anon/file/swapped (VmSwap) | MemAvailable, SwapFree` from `/proc/self/status` and `/proc/meminfo` (counters only, no page-table walk, so no repeat of the smaps hitch). Pss/SwapPss deliberately not logged: they need `smaps_rollup`, which causes the 45-60 ms hitch (PHASE4 H0). | implemented, built, not run |

## Not done (needs the phone to be kept honest)
Upload ring 256 -> 64 MB (`NX_UPLOAD_RING_MB`, item 12), staging spikes, image retention, `NX_AFFINITY` 0/1/2 A/B,
render_scale 0.67 vs 1. Each must be an ABBA run with cool-down (tools/phone_thermal_wait.py) before becoming a default.
`NX_UPLOAD_RING_MB=64` can already be tried through config.txt without a rebuild.

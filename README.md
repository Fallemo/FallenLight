# FallenLight — Ambilight for Robobloq monitor LED strips (Windows)

**FallenLight** is a lightweight Windows 10/11 tray app that turns a **Robobloq USB monitor light strip** into a smooth, low-latency **Ambilight / screen sync** — without the official **DX Light / Robobloq SyncLight** app, without OpenRGB or SignalRGB plugins, and **without making Windows stutter** on high refresh rate monitors (tested at 3440×1440 @ 165 Hz, HDR on).

If the official app makes your desktop feel choppy, or your strip shows up in SignalRGB as *"ROBOBLOQ USBHID – Plugin: None"*, this is for you.

## Download

➡️ **[Latest release](../../releases/latest)** → download `FallenLight-vX.Y.zip`, unzip anywhere you can write to (e.g. Documents), run `FallenLight.exe`.

- Nothing to install — the .NET runtime is bundled.
- First launch: Windows SmartScreen may say *"Windows protected your PC"* (the app isn't code-signed). Click **More info → Run anyway**.
- Close DX Light / SyncLight, OpenRGB and SignalRGB first, otherwise they fight over the strip.

## Supported hardware

| | |
|---|---|
| Controller | **ROBOBLOQ "USBHID"**, USB VID:PID **`1a86:fe07`** (HID, vendor page 0xFF00, 64-byte reports) |
| Strips | Robobloq / DX Light / SyncLight USB-powered monitor backlight strips. Tested: **34" kit** — 75 LEDs = 17 left + 41 top + 17 right; **32" kit** — 78 LEDs = 21 + 36 + 21 (firmware 1.9.4) |
| Other sizes | Should work — set LEDs per side in Settings and use the **Test** button |
| OS | Windows 10 / 11, 64-bit |

The controller is detected automatically; size, LED count and firmware version are read from the device.

## Features

- **Efficient capture** — DXGI Desktop Duplication with GPU downscaling (mipmaps). Only a ~215×90 image reaches the CPU: ~0.3–0.6 ms per frame, ~1–3 % of one CPU core at 30 fps.
- **HDR aware** — captures the real 16-bit (FP16 scRGB) desktop and normalizes it to your Windows *SDR content brightness*, so HDR games don't wash out to white.
- **Color controls** — gamma (default 2.2), black threshold, saturation, smoothing, brightness, edge sampling depth, capture FPS.
- **Strip layout** — LEDs per side + start corner (bottom-left clockwise or bottom-right counter-clockwise), with a 5-second **Test** pattern (left red, top green, right blue, first LEDs white).
- **Turns the strip off** on shutdown/restart, sleep/hibernate and when the monitor goes to standby (the controller is powered by the monitor's USB and would otherwise keep its last color).
- **Auto-updates** — *Check for updates* downloads, verifies (SHA-256) and installs new versions, then restarts.
- **Multiple strips / multiple monitors** — each strip is detected automatically and has its own mode, monitor, LED layout and colors; *Identify* makes a strip blink.
- **Flexible layout** — LEDs on any of the 4 sides (incl. bottom), any start corner and direction; rotated / portrait monitors supported.
- **Per-app modes** — e.g. a game → Ambilight, everything else → static color.
- **Light effects** besides Ambilight — static color, breathing, rainbow wave, rainbow cycle, aurora (3 custom colors); adjustable speed, strips stay in sync.
- **English / Romanian** interface.
- Tray app, start with Windows, multi-monitor selection, live stats.

## Protocol notes

The strip uses a proprietary HID protocol: `RB` frames (`52 42 len id cmd … sum`) for simple commands and `SC` frames (`53 43 lenHi lenLo id cmd … sum`) split into 64-byte reports for per-LED data. Screen sync is command `0x80` with `[start, R, G, B, end]` tuples (1-based LED indices); `0x82` returns device info. Checksums are a byte sum. Credit to the [OpenRGB](https://gitlab.com/CalcProgrammer1/OpenRGB) project for the original reverse engineering — FallenLight is an independent implementation (no OpenRGB code is used); the protocol details were also verified on real hardware.

## Third-party components

- [Vortice.Windows](https://github.com/amerkoleci/Vortice.Windows) (Direct3D11, DXGI bindings) — MIT License
- .NET Runtime / Windows Forms — MIT License

## Keywords

Robobloq, SyncLight, DX Light, monitor light strip, monitor backlight, screen sync, ambilight, ambient light, bias lighting, USB LED strip, 1a86:fe07, USBHID, Prismatik alternative, OpenRGB alternative, SignalRGB unsupported device, Alienware AW3423DWF, ultrawide, HDR, Windows 11.

## License

**Freeware** — free to use and to share the unmodified official release. Selling it and distributing modified versions are not allowed. No warranty. Full text: [LICENSE](LICENSE).

FallenLight is an independent project, **not affiliated with Robobloq**, DX Light or SyncLight. All trademarks belong to their owners.

---

© 2026 Fallen

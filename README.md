# E-skate ESC Configurator

This is an early, non-writing interface prototype for a portable ESC configurator. It is not ESP32 firmware and does not communicate with an ESC.

## Preview

Open `prototype/index.html` in a browser. The screen is sized to resemble a 240x320 portrait display and can also be previewed on a phone.

## Safety and hardware status

- The prototype cannot read or write ESC settings.
- Any future write workflow must require the board to be stopped, secured, and motor output disabled. It must not support configuration while riding.
- The exact touchscreen board and ESC USB protocol have not been confirmed. Flipsky's desktop application cannot simply be copied onto an ESP32; a compatible USB-host implementation and documented ESC protocol are needed.
- Battery details provided: 12S1P, 44.4 V nominal, 50.4 V fully charged, 45.6 V storage, about 39.6 V minimum recommended, and 36 V absolute lowest (avoid). Two 22.2 V, 8.2 Ah packs in series produce a 12S, 8.2 Ah pack; capacity does not double in series.
- The owner reports a manufacturer-stated continuous discharge rating of 1,230 A. This unusually high figure has not been independently verified; confirm it against the exact battery datasheet. It does not establish a safe ESC setting: the ESC, motor, BMS (if present), wiring, and connectors may have much lower limits.
- The owner reports there is no BMS, the LiPo packs are balance-charged individually, and the ESC configuration includes separate battery cutoff start/end and maximum battery current start/end parameters. The reported 3.50 V/cell low-voltage setting is 42.0 V pack-equivalent for 12S only if the setting is per-cell; verify the units shown by the ESC tool. Cutoff start/end are separate thresholds (typically the start of voltage-based current reduction and the end/strongest cutoff), not one interchangeable cutoff value. The ESC generally measures total pack voltage, not each cell, so it cannot guarantee that every cell stays above its limit if the pack is imbalanced. Do not change or infer current limits without the ESC, motor, and battery documentation.

## Next hardware details needed

Confirm the full board model printed on the PCB/product page (the reported ESP32-S3 and "ESP32-32e" descriptions may identify different hardware), and provide the ESC firmware/protocol documentation plus the battery manufacturer's continuous-discharge rating.

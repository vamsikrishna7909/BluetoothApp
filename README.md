# BluetoothApp

BluetoothApp is a SwiftUI iOS app for discovering nearby Bluetooth Low Energy (BLE) devices. It uses CoreBluetooth to scan as a central device, display discovered peripherals, and start a connection flow when the user selects a device.

## What This Project Does

- Scans for nearby BLE peripherals using `CBCentralManager`.
- Displays discovered devices in a SwiftUI list.
- Shows each device name, identifier, and RSSI signal strength.
- Deduplicates scan results by `CBPeripheral.identifier`.
- Sorts devices by strongest RSSI first.
- Connects to a selected peripheral and begins service discovery.
- Enables Bluetooth central and peripheral background modes in `Info.plist`.

## What We Built

The project currently includes a simple BLE browsing flow:

- `BLECentralManager` manages CoreBluetooth scanning, discovered devices, connection requests, and delegate callbacks.
- `DiscoveredDevice` models each scanned peripheral with its identifier, CoreBluetooth peripheral reference, display name, and RSSI.
- `DeviceListView` presents the scanned devices and provides a `Scan` button to restart discovery.
- `ContentView` loads the device list as the main app screen.
- `BluetoothAppApp` defines the SwiftUI app entry point.

## Project Structure

```text
BluetoothApp/
├── BluetoothApp/
│   ├── Assets.xcassets
│   ├── BLECentralManager.swift
│   ├── BluetoothAppApp.swift
│   ├── ContentView.swift
│   ├── DeviceListView.swift
│   ├── DiscoveredDevice.swift
│   └── Info.plist
├── BluetoothAppTests/
└── BluetoothAppUITests/
```

## Requirements

- Xcode
- iOS device with Bluetooth support
- Bluetooth permission enabled for the app

BLE scanning and connection behavior should be tested on a physical iOS device because the simulator does not provide full Bluetooth hardware behavior.

## Running The App

1. Open the project in Xcode.
2. Select a physical iOS device as the run destination.
3. Build and run the app.
4. Grant Bluetooth permission if prompted.
5. Tap `Scan` to refresh nearby devices.
6. Tap a discovered device to connect and start service discovery.

## Current Status

This is an early BLE central manager prototype. It discovers and lists nearby devices, supports basic connection requests, and has a placeholder for handling discovered services. Future work can add service and characteristic browsing, read/write operations, notifications, connection status UI, and test coverage around the device list behavior.

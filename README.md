# Logitech MX Master 3S and MX Master Keys Configuration for Linux

This repository contains configuration settings for Logitech's MX Master 3S mouse tailored for Linux operating systems. 

Using Logiops, a versatile Linux daemon for configuring Logitech devices, these configurations allow you to customize the functionality and behavior of your Logitech peripherals to enhance your productivity and user experience.

## Features

### MX Master 3S Mouse

- **SmartShift**: Automatically adjusts the scroll wheel mode based on the speed of scrolling, providing a seamless transition between ratchet and free-spin modes.
  - **On**: `true`
  - **Threshold**: `30`
  - **Torque**: `50`

- **High-Resolution Scroll (HiResScroll)**: Configures the behavior of the scroll wheel.
  - **Hires**: `false`
  - **Invert**: `false`
  - **Target**: `true`
  - **Up Scroll**: Maps to `REL_WHEEL` with a multiplier of `2.0`
  - **Down Scroll**: Maps to `REL_WHEEL` with a multiplier of `-2.0`

- **Thumbwheel**: Inverts the scroll direction for the thumbwheel and assigns actions for left and right scrolls.
  - **Divert**: `false`
  - **Invert**: `true`
  - **Left Scroll**: No action (`NoPress`)
  - **Right Scroll**: No action (`NoPress`)

- **DPI**: Sets the default DPI to `1800` (maximum `4000`).

- **Buttons Configuration**: Customizes button actions, including gestures and keypresses.
  - **Button CID 0xc3**: Configured for directional gestures with different actions such as cycling DPI, toggling SmartShift, and sending keypresses for `KEY_UP` and `KEY_DOWN`.
  - **Button CID 0xc4**: Configured to send a `KEY_A` keypress.

### MX Master Keys Keyboard

- **Keys Configuration**: Customize keys to send specific keypresses, launch applications, or perform complex macros.

## Installation

1. **Install Logiops**:
   ```sh
   git clone https://github.com/PixlOne/logiops
   cd logiops
   mkdir build
   cd build
   cmake ..
   make
   sudo make install

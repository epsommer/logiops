# Logitech MX Master 3S Configuration for Linux

This repository contains configuration settings for Logitech's MX Master 3S mouse tailored for Linux operating systems. 

Using Logiops, a versatile Linux daemon for configuring Logitech devices, these configurations allow you to customize the functionality and behavior of your Logitech peripherals to enhance your productivity and user experience.

## Dependencies and Acknowledgments

This project relies on [PixlOne/logiops](https://github.com/PixlOne/logiops) for configuring Logitech devices on Linux. Please refer to their repository for more details and advanced configurations.

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

2. **Clone This Repository**:
    ```sh
    git clone https://github.com/epsommer/logiops.git ~/.config/logiops
    ```

3. **Set Up Configuration File**:
    Ensure the `logid.cfg` file is in the `~/.config/logiops` directory.

4. **Override Systemd Service**:
    Create a drop-in file to specify the configuration directory:
    ```sh
    sudo mkdir -p /etc/systemd/system/logid.service.d
    echo -e "[Service]\nExecStart=\nExecStart=/usr/bin/logid -c /home/epsommer/.config/logiops/logid.cfg" | sudo tee /etc/systemd/system/logid.service.d/override.conf
    ```

5. **Reload Systemd and Start the Service**:
    ```sh
    sudo systemctl daemon-reload
    sudo systemctl enable --now logid
    ```

## Customization

- **Modify Configuration**: Edit `~/.config/logiops/logid.cfg` to customize settings according to your preferences.
- **Apply Changes**: Restart the Logiops service to apply changes.
    ```sh
    sudo systemctl restart logid
    ```

## Troubleshooting

- **Check Service Status**:
    ```sh
    sudo systemctl status logid
    ```

- **View Logs**:
    ```sh
    journalctl -u logid
    ```
    
## To Do
- [ ] Implement button remapping for `MX Keys S` right alt / opt key

## Contribution

Contributions are welcome! Feel free to fork the repository, make modifications, and submit pull requests.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

## Contact

For any questions or support, please open an issue on the GitHub repository.

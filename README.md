# IoT-Based Smart Beehouse Network

This repository contains the code for an IoT-based smart beehouse network built on the ESP32 platform. The system allows for monitoring various metrics within a beehive and communicates these metrics over a custom ESP32-based access point. The beehouses form a star network mesh, allowing multiple beehouses to connect and transmit data to a central hub.

## Features

- **Wireless Access Point (AP):** Creates a local access point using ESP32 for connecting multiple beehouses in a star network.
- **Data Transmission:** Sends and receives data between beehouses over TCP.
- **Hive Monitoring:** Collects hive-specific data, such as humidity, temperature, and hive identification.
- **HTTP Server:** Hosts a local web server for displaying data.
- **Custom IP Configuration:** Each beehouse has its own unique IP address within the network.

## Components

- **ESP32 microcontroller**: Serves as the main processor and wireless communication module.
- **Wi-Fi module**: Used to create an access point and handle TCP connections.
- **WebServer Library**: Implements a basic HTTP server for viewing and managing hive data.

## Setup and Configuration

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/your-username/smart-beehouse.git
   ```

2. **Hardware Requirements:**

   - ESP32 boards for each beehouse.
   - Sensors for humidity, temperature, and other hive-specific data collection.
   - Power source for each ESP32 module.

3. **Network Configuration:**

   The ESP32 board will create an access point with the following credentials:

   ```plaintext
   SSID: Esp_Server
   Password: 12345678
   IP: 192.168.1.128
   ```

   The default server IP is set to `192.168.1.120` on port `8088`. Each ESP32 board communicates with this IP as the central hub.

4. **Upload the Code:**

   - Modify the SSID and password in the code if needed.
   - Upload the code to your ESP32 boards using the Arduino IDE or PlatformIO.

5. **Monitor Hive Metrics:**

   Once the beehouses are connected to the access point, they will start sending data such as temperature, humidity, and hive-specific information, which can be accessed through the web server hosted on the ESP32.

## Usage

1. **Start the Network:**
   After uploading the code, the ESP32 board will automatically create an access point and attempt to communicate with other beehouses.

2. **Accessing Data:**
   The local web server hosted on the ESP32 can be accessed via the assigned IP. The server listens on port 80 and provides basic HTML output showing the status of the hive metrics.

3. **Real-Time Monitoring:**
   The beehouse sends and receives data in real-time through the network, providing up-to-date information about the hive conditions.

## Code Overview

- **`setup()`**: Initializes the ESP32 as an access point and starts the HTTP server.
- **`loop()`**: Handles incoming client connections and processes data transmission between the beehouses.
- **`OnConnect()`**: Responds to successful client connections.
- **`NotFound()`**: Handles 404 errors for unknown routes.
- **`getPage()`**: Generates the HTML content for the HTTP server.

## Future Improvements

- Implement a user interface to display hive metrics more interactively.
- Add security measures like encrypted communication between beehouses.
- Expand support for additional sensors (weight, CO2 levels, etc.).
- Optimize network traffic for larger-scale operations.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributions

Contributions are welcome! Feel free to open an issue or submit a pull request if you have any improvements or suggestions.

---


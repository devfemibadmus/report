
# Project Report: Vehicle Tracking System

## Goal:
-   Track vehicles/cars in the company with features like stop counts, movement tracking, etc.
-   Focus on cost-efficiency due to the large number of vehicles.
# Comparison: GF-07 vs GF-09 vs TK103B

| **Feature**                        | **GF-07**                             | **GF-09**                             | **TK103B**                                  |
|------------------------------------|---------------------------------------|---------------------------------------|---------------------------------------------|
| **Tracking Method**                | Real-time tracking via SMS           | Real-time tracking via SMS and GPRS  | Real-time tracking via GPRS                |
| **Battery Life**                   | 4 hours (short)                       | 48 hours (longer than GF-07)          | 2-3 days (depends on usage and settings)   |
| **Power Source**                   | Internal rechargeable battery         | Internal rechargeable battery         | Internal rechargeable battery or vehicle's power |
| **Communication**                  | SMS only                              | SMS, GPRS                            | SMS, GPRS                                  |
| **Geofencing**                     | No                                    | Yes                                   | Yes (with notifications)                   |
| **SOS Functionality**              | No                                    | Yes (SOS button)                      | Yes (SOS alerts to designated contacts)    |
| **Voice Monitoring**               | No                                    | Yes (remote listening)                | No                                         |
| **Accident Detection**             | No                                    | Yes (crash detection)                 | No                                         |
| **Real-Time Updates**              | Limited by SMS                        | Real-time (GPRS)                      | Real-time updates via GPRS                 |
| **Mobile App**                     | No (we build)                                    | No (we build)                                    | No (we build)   |
| **Installation Type**              | Plug and play, self-installed         | Plug and play, self-installed         | Plug and play, self-installed              |
| **Tracking Frequency**             | Typically slower due to SMS delays   | Faster updates (GPRS-based)          | Frequent real-time updates (depending on settings) |
| **Cost**                           | $4-$8                                  | $8-13                                 | $25-$35                                     |
| **Waterproof**                     | No                                    | No                                    | Yes (IP65-rated)                           |

## Key Differences:
- **Communication:**  
  - **GF-07** relies solely on **SMS** for tracking, which can be slower and less reliable for real-time updates.  
  - **GF-09** uses both **SMS** and **GPRS**, providing better real-time tracking.  
  - **TK103B** uses **GPRS** for real-time data transfer, allowing faster and more frequent updates compared to SMS-based trackers.

- **Battery Life:**  
  - **GF-07** has the shortest battery life (about 4 hours).  
  - **GF-09** has a much longer battery life (48 hours).  
  - **TK103B** typically lasts for **2-3 days**, depending on settings and usage.

- **Additional Features:**  
  - **GF-09** has additional features like **geofencing**, **SOS button**, **voice monitoring**, and **accident detection**.  
  - **TK103B** supports **geofencing** and **SOS alerts** but lacks **voice monitoring** and **accident detection**.

- **App Integration:**  
  - **GF-07** and **GF-09** do not offer a mobile app for tracking.  
  - **TK103B** can be tracked via third-party apps that support GPRS tracking.

## Conclusion:
- **GF-07**: Best for budget-conscious users who need basic tracking with SMS but are okay with limited features and battery life.
- **GF-09**: A step up from the GF-07, offering better battery life, more features (like accident detection and remote listening), and real-time tracking via SMS/GPRS.
- **TK103B**: Ideal for users who need reliable GPRS-based real-time tracking, with basic features like geofencing and SOS, at a more affordable price point.

## GPS Options:

| **Device**                      | **Good**                                                                                  | **Bad**                                                                                                                                           |
|----------------------------------|-------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| **GF-07/GF-09 GPS Device**             | - Real-time tracking. <br> - Low cost. <br> - Multiple command features. | - Relies on SMS for communication. <br> - Short battery life. |
| **Driver's Application (Mobile-Based)** | - Real-time data via the internet (socket communication). <br> - Zero cost. <br> - Includes features of GF-07. | - Drivers can control the app (e.g., turning off mobile, battery, or internet).                                                                |


## Suggestions:

| **Suggestion**                   | **Details**                                                                                                                                     |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
| **Mixed System for Vehicles**    | - Use the driver's application for regular vehicles. <br> - Use GF-07 for long-distance/night vehicles and cars to ensure tracking during off-hours.     |
| **Custom Battery for GF-07/GF-09**     | - Design a custom battery to extend usage.                |
| **Ensure Sufficient Airtime**    | - Ensure that GF-07/GF-09 has enough SMS airtime to maintain communication.                                                                           |
| **Development Approach**         | - Start by developing and testing the driver's application. <br> - Once successful, proceed with implementing the GF-07/GF-09 for other vehicles.     |



# Development Using GF-07/GF-09/TK103B

## Overview

This system involves three types of GPS tracking devices: **GF-07**, **GF-09**, and **TK103B**. Each device will transmit location data to a server, where the data will be stored and processed. The system also includes a **frontend dashboard** for real-time tracking of the devices.

### Key Components
1. **Mobile Device** - Sends location data via SMS (GF-07) or GPRS (GF-09/TK103B).
2. **Server (Database)** - Receives and stores the location data.
3. **Frontend Dashboard** - Displays location data in real-time.

---

## GF-07 Device

GF-07 is a GPS tracker that communicates using **SMS**. The mobile device sends location data at regular intervals (every 1 minute) via SMS to a server, which then processes and stores the received data.

### Development Breakdown

1. **Mobile Device**  
   - The mobile device sends an SMS every 1 minute, containing the GPS location of the device.
   - The system is responsible for sending the SMS and ensuring it is delivered.

2. **Server (Database)**  
   - The server receives the SMS data from the mobile device.
   - Upon receiving the SMS, the server will parse the data (e.g., latitude, longitude) and store it in the database.

3. **Frontend Dashboard**  
   - The dashboard will display the real-time GPS location of the devices on a map.

### Cost Analysis

The **GF-07** device uses SMS for communication, which incurs the following costs:

- **Cost per SMS**: (Amount per SMS, depends on your carrier)
- **SMS Interval**: 1 minute
- **Total SMS per Day**: 1440 (1 SMS per minute x 24 hours)
- **Total Daily Cost per Device**: `(Cost per SMS x 1440) x 2 (for both sending and receiving SMS)`

**Example Cost Breakdown:**

- If the cost per SMS is $0.05:
  - `(4 x 1440) x 2 = NGN11,520 per device per day`
  
The main cost here is the **SMS and airtime** for both sending location updates and receiving tracking data.

---

## GF-09 Device

GF-09 is a more advanced GPS tracker that supports **GPRS** communication, reducing the need for SMS. This device can send data over a network, using the internet for communication instead of relying on SMS.

### Development Breakdown

1. **Mobile Device**  
   - The device will use **GPRS** for communication and connect to the company’s Wi-Fi or internet service.
   - Data can be sent using more efficient protocols like **WebSockets**, enabling real-time updates.

2. **Server (Database)**  
   - The server will receive location data via GPRS or WebSocket and store it in the database.
   - This connection will be more reliable and cost-effective compared to SMS, reducing operational costs.

3. **Frontend Dashboard**  
   - The dashboard will receive real-time location data from the device through the GPRS or WebSocket connection, displaying updates instantly.

### Cost Analysis

The **GF-09** device uses **GPRS** communication, which incurs the following costs:

- **Internet Access**: The cost of the internet connection for sending data to the server.
- **Tracking Device Connection**: The device will connect to the company’s Wi-Fi, reducing the need for a mobile network.

Since the device uses internet-based communication, the primary cost here is the **internet access** for the device and the server, significantly reducing the cost of SMS (compared to GF-07).

---

## TK103B Device

The **TK103B** is another GPS tracker with **GPRS** functionality, similar to the **GF-09**, but with some added features like **SOS panic button**, **voice monitoring**, and **geofence capabilities**. It can also communicate over **SMS** for backup in case GPRS is unavailable.

### Development Breakdown

1. **Mobile Device**  
   - The device can operate over **GPRS**, but can also fall back to SMS if the internet connection is unstable or unavailable.
   - Features like **SOS button** and **voice monitoring** add extra functionalities that the system should be prepared to handle.

2. **Server (Database)**  
   - The server will receive location data via GPRS or SMS, depending on network availability.
   - The system should also handle special messages from the device like **SOS alerts** and **geofence breach notifications**.

3. **Frontend Dashboard**  
   - The dashboard will handle real-time updates from GPRS communication but also be able to display emergency notifications like **SOS alerts** and **geofence breaches**.

### Cost Analysis

The **TK103B** device offers a similar cost structure to **GF-09**, as it uses **GPRS** for communication. However, if it falls back to **SMS** (e.g., in areas without internet access), the costs will be similar to the **GF-07**.

- **Cost per SMS**: (if used for fallback communication)
- **Internet Access**: (for GPRS communication)
- **Special Feature Costs**: Monitoring services like **voice calls** or **SOS alerts** may have additional costs associated with them.

---

## Summary

| Feature             | GF-07 (SMS)                               | GF-09 (GPRS/Internet)                       | TK103B (GPRS + SMS Fallback)                |
|---------------------|-------------------------------------------|---------------------------------------------|---------------------------------------------|
| **Communication**    | SMS (every 1 minute)                     | GPRS (internet access)                     | GPRS (internet) + SMS (fallback)           |
| **Cost**             | Airtime cost                              | Internet access for both device and server | Internet access + SMS costs (if fallback)  |
| **Real-Time**        | Delayed (based on SMS delivery)          | Real-time updates (via WebSocket/GPRS)      | Real-time updates (via GPRS, SMS as fallback)|
| **Setup**            | Requires SMS-enabled SIM cards           | Requires Internet access SIM cards         | Requires Internet access or fallback to SMS|
| **Special Features** | Basic tracking                           | Advanced GPRS communication                | SOS button, voice monitoring, geofence     |

- **GF-07** incurs higher costs due to SMS usage, but works on a basic mobile network.
- **GF-09** and **TK103B** are more efficient and cost-effective for long-term use, utilizing GPRS and internet access. **TK103B** has the added benefit of **SMS fallback** and extra features like **SOS alerts** and **geofencing**.

---

## Next Steps

- **GF-07**: Focus on SMS handling, ensuring proper delivery and parsing of location data.
- **GF-09**: Implement GPRS communication with WebSocket support for real-time data transmission.
- **TK103B**: Implement GPRS communication with fallback to SMS and integrate special features like **SOS alerts** and **geofencing**.
- **Frontend Dashboard**: Implement a real-time map interface to visualize the location data from all devices and integrate notifications for SOS and geofence breaches.

---

## Conclusion

The **GF-07** is ideal for basic tracking with SMS communication, the **GF-09** is more advanced and cost-efficient using GPRS for real-time updates, and the **TK103B** combines GPRS with SMS fallback and added features like **SOS alerts** and **geofencing**, making it versatile for various use cases.


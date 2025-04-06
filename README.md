# Diotp Humidity
http://135.236.209.197/
  
  
  

## Overview

  

This project demonstrates an IoT pipeline where an embedded device (Rasberry Pi Pico W) collects data and transmit it to a cloud platform.

  

The pipeline is built using the following technologies:

  

- Embedded device: Rasberry Pi Pico W

- Cloud: Azure Virtual Machine running Ubuntu 24.04 LTS

- Backend: Node.js 23

- Database: InfluxDB v2.7.10

- Web Server: Nginx v1.24.0

- Frontend: Custom HTML dashboard displaying real-time data

  

This program can handle these messages:

  

-  `/` which responds with a chart representing the current data stored in the system

-  `/api/v1/embed?value=x` which takes the value and stores it into the system memory

-  `/api/v1/get-data` which shows the value to be stored

  

The end user can access the frontend through a web browser. The frontend is hosted on a web server, which serves the necessary files to the browser, enabling it to render the user interface.

![Humidity chart](https://i.imgur.com/IwohHyL.png)

  
  

## System Architecture

  

### IoT device

Collects sensor data and send it to the backend using HTTP GET request.

1. Intializes the DHT11 sensor and reads its data at regular intervals (every 5 seconds by default).

2. Connects to a WiFi network using a preconfigured SSID and password.

3. Sends the measured humidity as a query parameter to the backend server via an HTTP GET request.

### Backend Data Handling

The backend is a Node.js application that handles incoming data from the IoT device and saves data in a time-series database (InfluxDB)

1. It extracts the humidity value from the `value` query parameter when receives a request at `/api/v1/embed?value=x`.
`/api/v1/embed?value=30`

2. The value is then converted to a numeric format and validated to ensure it is a proper number.

3. The backend creates a point object in InfluxDB. Each point represents a single humidity reading at a specific time.
  
4. Retrieving data for visualization using `/api/v1/get-data`.

    The backend sends a query to InfluxDB to fetch the last 10 days of data.
    The query filters data with the measurement name `qparams` with the field `value` which stores humidity readings.

### Frontend

A custom HTML dashboard fetches data from the backend's `api/v1/get-data` endpoint.

The real-time chart displays the humidity data that get updated every 5 seconds providing a live view of the current humidity level.

### Nginx

- Acts as a reverse proxy between the user’s browser and the backend server.

- Improves security by hiding the backend’s implementation details.

- Provides high-speed file serving for the frontend HTML and JavaScript files.

## Resources and Benefits

  

### Operating Costs

  

- Azure Virtual Machine: $11.17 average per month

- Hardware: JOY-iT Explorer board for Rasberry Pi Pico ~27€

- Nginx, Node.js: Free

  

### Benefits

  

Scalable and cost-effective IoT solution.

  

Open-source technologies ensure flexibility and community support.

  

VPS provides 24/7 reliability

  

## Video Demonstration

  

https://youtu.be/4S8vpAUcOuk

  

## Source Code

  

https://gitlab.com/nhingnguyen/diotp_humidity

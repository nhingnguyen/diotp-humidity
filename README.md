#   Diotp Humidity



## Overview

This project demonstrates an IoT pipeline where an embedded device (Rasberry Pi Pico W) collects data and transmit it to a cloud platform. 

The pipeline is built using the following technologies:

- Embedded device: Rasberry Pi Pico W
- Cloud: Azure Virtual Machine running Ubuntu 24.04 LTS
    - Backend: Node.js 23
    - Database: InfluxDB v2.7.10
    - Web Server: Nginx v1.24.0
- Frontend: Custom HTML dashboard displaying real-time data

This program can handle two types of message:

- `/` which responds with a chart representing the current data stored in the system
- `/api/v1/embed?value=x` which takes the value and stores it into the system memory
- `/api/v1/get-data` which shows the value to be stored

The end user can access the frontend through a web browser. The frontend is hosted on a web server, which serves the necessary files to the browser, enabling it to render the user interface.

## System Architecture 

### IoT device

Collects sensor data and send it to the backend using HTTP GET request.

### Node.js Backend

Receives, sanitizes, and logs the data; stores it in InfluxDB.

### InfluxDB

Stores time-series data for efficient querying and visualization.

### Frontend

Displays real-time data fetched from the database.

### Nginx

Serves as a reverse proxy for HTTP traffic.


## Resources and Benefits

### Operating Costs

- Azure Virtual Machine: $11.17 average per month
- Hardware: JOY-iT Explorer board for Rasberry Pi Pico ~27€
- Nginx, Node.js: Free

### Benefits

Scalable and cost-effective IoT solution.

Open-source technologies ensure flexibility and community support.

VPS provides 24/7 reliability

### Demo 
[![Demo Video](https://img.youtube.com/vi/YOUR_VIDEO_ID/0.jpg)](https://www.youtube.com/watch?v=4S8vpAUcOuk&ab_channel=IrisNguyen)
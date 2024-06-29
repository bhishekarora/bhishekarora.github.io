---
layout: post
published: false
title: Vision Based Real Time Parking System for Airport
---
---
layout: post
published: false
title: Vision Based Real Time Parking System for Airport
---
Real-Time Tail Number Extraction Tool with AMS Interface 
========================================================

Real-time tail number extraction using OCR, integrated with a simulated AMS (Aircraft Management System) interface. This project leverages powerful tools like OpenCV, EasyOCR, and Flask to create a seamless end-to-end solution for capturing, processing, and posting tail numbers from video streams.

![](https://github.com/bhishekarora/parkingsystem/blob/main/main.png)
Overview
--------

For a small airport, hangar spaces are limited and there are ways to monetize the space by introducing a vision based parking system. This project aims to automate the extraction of tail numbers from video streams of cameras and post them to ams/billing system. The solution consists of three main components:

1.  **RTSP Server**: An RTSP server that announces multiple camera streams.
2.  **Tail Number Extractor Tool**: A Python tool that captures frames from an RTSP stream, performs OCR to detect tail numbers, and sends the detected numbers to an AMS interface.
3.  **AMS Interface**: A Flask-based API that simulates an external system receiving the tail numbers.

![logical.png]({{site.baseurl}}/img/logical.png)


Key Technologies
----------------

-   **OpenCV**: An open-source computer vision library used to capture and process video frames.
-   **EasyOCR**: A Python library for optical character recognition, enabling text extraction from images.
-   **Flask**: A lightweight WSGI web application framework used to create the AMS interface.
-   **Torch**: An optional deep learning library for GPU support, enhancing OCR performance.

Project Structure
-----------------

The project is organized into three main scripts:

1.  **`rtsp_server.py`**: This script sets up the RTSP server to announce multiple camera streams.
2.  **`tail_number_extractor.py`**: This tool captures video frames, performs OCR, and posts detected tail numbers to the AMS interface.
3.  **`ams_server.py`**: This script sets up a Flask API that receives and logs the posted tail numbers.

How It Works
------------

### RTSP Server

1.  **Setup**: The RTSP server is configured to announce multiple camera streams, making them accessible for processing.

### Tail Number Extractor Tool

1.  **Connecting to RTSP Stream**: The tool connects to an RTSP stream using OpenCV.
2.  **Frame Capture and Processing**: It captures frames from the video stream and converts them to grayscale for OCR processing.
3.  **Text Detection with EasyOCR**: The EasyOCR library is used to detect text within the frames. A regular expression is applied to filter out valid tail numbers.
4.  **Posting to AMS Interface**: Detected tail numbers are posted to the AMS interface using HTTP POST requests.

### AMS Interface

1.  **Flask API Setup**: The Flask API listens for POST requests on the `/ams` endpoint.
2.  **Receiving and Logging Tail Numbers**: The API receives tail numbers in JSON format and update the system for sending it to further downstream systems for billing.


New Features
----------

This project demonstrates how to integrate computer vision and web technologies to automate the extraction and management of aircraft tail numbers. With the use of OpenCV, EasyOCR, and Flask, we can efficiently process video streams and interact with external systems in real-time.

For more information and to access the source code, visit my [GitHub repository](https://github.com/bhishekarora/parkingsystem).
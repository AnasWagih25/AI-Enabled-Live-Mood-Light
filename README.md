# AI-Enabled-Live-Mood-Light

This project is a **real-time mood-detecting LED light** using a **Raspberry Pi 4**, **12-LED NeoPixel ring**, and a **Boya USB microphone**. The LEDs change color and effects based on the sentiment of your speech. Features include detection of positive, negative, and neutral moods, keyword and sentiment analysis, and live LED effects: **Happy** (yellow, pulsing), **Angry** (red, shooting), **Neutral** (purple, breathing), **Silence** (blue, static).  

## Hardware Requirements
- Raspberry Pi 4 B (4GB)  
- Boya USB Microphone  
- 12-LED NeoPixel ring  
- Jumper wires / breadboard (optional)  

## Connections
NeoPixel ring to Raspberry Pi GPIO: Data In → GPIO18 (Pin 12), 5V → 5V (Pin 2/4), GND → GND (Pin 6). USB mic connects via USB port. GPIO18 must have PWM enabled.  

## Software Dependencies
Python libraries: numpy, sounddevice, neopixel, board, vosk, textblob, queue, json, threading, time.  

## Vosk Speech Recognition
This project uses **Vosk**, an offline speech recognition toolkit, to convert live microphone input into text. It uses a **small English model** (`vosk-model-small-en-us-0.15`) for efficient, real-time processing on Raspberry Pi. The text output is analyzed for **keywords** and **sentiment** using TextBlob to determine the mood. Vosk works offline, so no internet connection is required, and it supports streaming input through `sounddevice`.  

## Setup Instructions
Update system: `sudo apt update && sudo apt upgrade -y`. Install Python dependencies: `sudo apt install python3-pip python3-venv -y && pip3 install numpy sounddevice adafruit-circuitpython-neopixel vosk textblob`. Install NeoPixel support: `sudo pip3 install rpi_ws281x adafruit-circuitpython-neopixel`. Download Vosk model: `cd ~ && mkdir vosk-model && cd vosk-model && wget https://alphacephei.com/vosk/models/vosk-model-small-en-us-0.15.zip && unzip vosk-model-small-en-us-0.15.zip`. Enable PWM on GPIO18: `sudo raspi-config` → Interface Options → PWM → Enable. Copy Python script to Raspberry Pi (e.g., `live_mood_light.py`).  

## Running the Project
Run: `python3 ~/live_mood_light.py`. Console shows detected text and mood; NeoPixel ring displays corresponding effect.  

## Video Demo
A demo video of **AI-Enabled-Live-Mood-Light** is included in this repository. You can view it with the following Markdown:  

## Demo

A demo of **AI-Enabled-Live-Mood-Light** is included in this repository.

### Inline Preview
![Demo](./demo_video.gif)

### Full-Length Video
[Watch Full Demo](./demo_video.mp4)


## Troubleshooting
- No LEDs: Check GPIO18, PWM, and power connections.  
- No mic input: Verify with `arecord -l`.  
- Slow performance: Close heavy apps; ensure Python 3.9+.  

## License
MIT License

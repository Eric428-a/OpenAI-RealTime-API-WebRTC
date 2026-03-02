# OpenAI Real-Time WebRTC Demo

## Overview

This project demonstrates how to establish a real-time WebRTC connection between a browser and OpenAI’s Realtime API. It enables live audio streaming and bidirectional data communication, allowing AI-powered interaction directly within the browser.

The system uses a backend signaling server (Java or Python) to negotiate the WebRTC connection between the browser and OpenAI’s real-time endpoint.

---

## Key Capabilities

### 1. Real-Time Audio Streaming

The browser captures microphone input and streams audio to OpenAI using WebRTC. Once the connection is established:

* Live microphone audio is transmitted to OpenAI
* OpenAI processes the audio input
* Audio responses are streamed back to the browser in real time

This enables low-latency voice-based AI interaction.

---

### 2. WebRTC Data Channel Communication

In addition to audio streaming, a WebRTC Data Channel is established to exchange structured JSON messages between the browser and the AI endpoint.

The Data Channel allows:

* Sending structured commands
* Receiving AI-generated responses
* Executing browser-side functions
* Returning execution results

The communication is reliable, low-latency, and fully bidirectional.

---

## Demo Features Implemented

The demo includes browser interaction capabilities to demonstrate AI-driven control via the Data Channel:

* Retrieve current HTML element content
* Change webpage background color
* Change font color
* Modify button size
* Modify button color

Commands are sent through the Data Channel and executed dynamically in the browser.

---

## Connection Flow

### 1. Browser Initiates Connection

The frontend sends a request to the backend endpoint (e.g., `/api/rtc-connect`) including the local SDP offer and connection metadata.

### 2. Backend Requests OpenAI Realtime Session

The backend forwards the browser’s SDP offer to OpenAI and receives an SDP answer in return.

The backend acts as a signaling intermediary and does not process media directly.

### 3. Backend Returns SDP Answer

The SDP answer is returned to the browser.

### 4. WebRTC Negotiation

The browser:

* Applies the remote SDP answer
* Establishes ICE connectivity
* Negotiates audio streams and the Data Channel

### 5. Real-Time Session Established

Once connected:

* Audio streams to OpenAI
* Audio responses stream back to the browser
* Structured messages are exchanged over the Data Channel
* AI-driven browser interactions occur in real time

---

## Project Structure

```
front/              → Frontend (HTML, JS, CSS)
java_backend/       → Spring Boot signaling backend
python_backend/     → Python signaling backend
```

Either backend implementation can be used for signaling.

---

## Configuration

### Backend Configuration

Configure the following:

* Server port
* OpenAI API key (via environment variable)
* Realtime endpoint settings

Example environment variable:

```
OPENAI_API_KEY=your_api_key_here
```

### Frontend Configuration

Update the frontend base URL to match the backend server address.

Example:

```
const baseUrl = "http://localhost:PORT";
```

---

## Security Notes

* Do not commit API keys
* Use environment variables for secrets
* Add a `.gitignore` file to exclude IDE files, build artifacts, and system files

Recommended exclusions:

```
.idea/
target/
__pycache__/
*.iml
desktop.ini
```

---

## Use Cases

This architecture can be extended for:

* Real-time AI voice assistants
* AI-powered browser copilots
* Interactive AI dashboards
* Live transcription systems
* Voice-controlled applications

---

## Conclusion

This project demonstrates how WebRTC can be used to create direct, low-latency communication between a browser and an AI system. It provides a foundation for building real-time, voice-enabled AI applications powered by OpenAI’s Realtime API.

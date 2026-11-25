# MAX Robot – Setup and Software

**Installation, system configuration, software architecture, and development environment for the MAX open-source robotics platform.**

This guide explains how to prepare a computing environment, configure the operating system, install software dependencies, and set up the development environment required to work with MAX.

MAX is designed as an extensible platform, allowing developers, students, and researchers to explore its software, customise existing functionalities, integrate new technologies, and develop additional capabilities.

---

## Table of Contents

- [Overview](#overview)
- [System Requirements](#system-requirements)
- [Raspberry Pi Setup](#raspberry-pi-setup)
- [Jetson Orin Nano Setup](#jetson-orin-nano-setup)
- [Software Architecture](#software-architecture)
- [Technology Stack](#technology-stack)
- [Software Installation](#software-installation)
- [Software Configuration](#software-configuration)
- [Running the Application](#running-the-application)
- [Development Environment](#development-environment)
- [Customisation and Further Development](#customisation-and-further-development)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)
- [About MAX](#about-max)

## Overview

The MAX software environment brings together AI technologies, voice processing, web-based interaction, real-time communication, and hardware integration.

The software architecture combines a Python-based backend with a web-based frontend to support interaction between users and the robot.

This repository provides guidance for:

- Computing platform preparation and operating system installation.
- Software architecture and technologies.
- Required software packages and dependencies.
- Backend and frontend configuration.
- Development environment preparation.
- Software customisation and extension.

## System Requirements

MAX can be developed and configured using supported computing platforms.

| Component | Requirement |
|---|---|
| Standard computing option | Compatible Raspberry Pi |
| Advanced computing option | NVIDIA Jetson Orin Nano |
| Microcontroller | Arduino Mega 2560 |
| Network | Wi-Fi or Ethernet |
| Storage | Compatible SD card or SSD |
| Development tools | Git, Python, and code editor |

**Note:** The required computing resources depend on the software features and applications being used. Check the compatibility of the selected operating system and software dependencies with your computing platform.

## Raspberry Pi Setup

This section covers the preparation and initial configuration of the Raspberry Pi computing environment.

### 1. Required Items

- Raspberry Pi board.
- Compatible microSD card.
- Card reader.
- Power supply suitable for the Raspberry Pi model.
- Computer for preparing the operating system.
- Network connection.

### 2. Install Raspberry Pi Imager

1. Visit the official [Raspberry Pi Software page](https://www.raspberrypi.com/software/).
2. Download Raspberry Pi Imager for your computer's operating system.
3. Install and open Raspberry Pi Imager.
4. Insert the microSD card into your computer.

### 3. Flash the Operating System

1. Open Raspberry Pi Imager.
2. Select **Choose Device** and select your Raspberry Pi model.
3. Select **Choose OS** and select a compatible 64-bit operating system.
4. Select **Choose Storage** and choose your microSD card.
5. Open the OS customisation settings, if available.
6. Configure:
   - Hostname.
   - Username and password.
   - Wi-Fi credentials.
   - Wireless LAN country.
   - SSH access.
7. Review the settings and write the operating system to the microSD card.

<text color="secondary" size="xs">Use an operating system version confirmed to be compatible with the selected Raspberry Pi model and MAX software dependencies.</text>

### 4. First Boot and System Configuration

1. Insert the prepared microSD card into the Raspberry Pi.
2. Connect the power supply.
3. Allow the operating system to complete its first boot.
4. Connect to the configured network.
5. Access the device locally or through SSH.

To connect through SSH:

```bash
ssh username@hostname.local
```

Replace `username` and `hostname` with the values configured during installation.

### 5. Update the System

Open the terminal and execute:

```bash
sudo apt update
sudo apt upgrade -y
```

Install essential development utilities:

```bash
sudo apt install -y git python3 python3-pip python3-venv
```

The Raspberry Pi environment is now prepared for the software setup.

## Jetson Orin Nano Setup

**Advanced Computing Option**

For applications requiring greater computing performance, GPU acceleration, and advanced AI processing capabilities, developers can also use the **NVIDIA Jetson Orin Nano** as an alternative computing platform.

The setup process includes:

1. Preparing the Jetson Orin Nano development kit.
2. Installing a compatible NVIDIA JetPack software environment.
3. Configuring network connectivity and remote access.
4. Updating system packages.
5. Installing the required development tools and software dependencies.
6. Configuring the MAX software environment.

Refer to the official [NVIDIA Jetson documentation](https://developer.nvidia.com/embedded/learn/get-started-jetson-orin-nano-devkit) for the appropriate installation procedure.

The software configuration may vary depending on the selected computing platform.

## Software Architecture

MAX uses a modular software architecture that integrates AI processing, voice interaction, web-based interfaces, and robot hardware control.

The architecture consists of:

- **Frontend:** Provides the web-based interface for user interaction.
- **Backend:** Handles application logic, request processing, and coordination between software components.
- **AI Integration:** Processes user queries and generates intelligent responses.
- **Voice Processing:** Supports speech recognition and audio response generation.
- **Real-Time Communication:** Enables data exchange between the frontend and backend.
- **Hardware Integration:** Connects software operations with the robot's control hardware.

## Technology Stack

The following technologies form part of the MAX software environment.

| Category | Technology |
|---|---|
| Programming Language | Python |
| Backend Framework | FastAPI |
| Frontend | HTML, CSS, JavaScript |
| AI Framework | LangChain |
| AI Model Integration | OpenAI |
| Speech Recognition | Google Cloud Speech-to-Text |
| Speech Generation | Google Cloud Text-to-Speech |
| Real-Time Communication | WebSockets |
| Voice Activity Detection | Silero VAD |
| Wake-Word Detection | Picovoice Porcupine |
| Audio Processing | FFmpeg |
| Document Retrieval | FAISS and RAG |
| Hardware Communication | PySerial and Arduino |
| Containerisation | Docker |

## Software Installation

This section describes the general process for preparing the Python development environment.

### 1. Install Required Packages

Make sure Python and Git are installed:

```bash
python3 --version
git --version
```

If Python is not installed, refer to the installation instructions for your selected operating system.

### 2. Obtain the MAX Software Source Code

Obtain the MAX application source repository from the project maintainers.

The central MAX ecosystem repository provides project information and links to supporting repositories. It does not itself contain the complete application source code.

### 3. Create a Python Virtual Environment

Navigate to the application source directory:

```bash
cd path/to/max-software
```

Create a virtual environment:

```bash
python3 -m venv venv
```

Activate it:

**Linux / Raspberry Pi / Jetson:**

```bash
source venv/bin/activate
```

### 4. Install Software Dependencies

If the application source repository provides a `requirements.txt` file, install its dependencies:

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

If dependencies are maintained through another package manager or installation file, follow the instructions provided by that repository.

### 5. Install Additional System Dependencies

Some software components may require system-level packages, audio libraries, or hardware communication utilities.

Install these according to the application requirements and the selected operating system.

## Software Configuration

After installing the dependencies, configure the software components.

The configuration process may include:

- Backend application settings.
- Frontend configuration.
- AI service credentials and API keys.
- Speech recognition and speech generation settings.
- WebSocket communication settings.
- Serial communication settings for Arduino.
- Hardware and device configuration.

### Environment Variables

If the application provides an example environment file, create a working copy:

```bash
cp .env.example .env
```

Update the required configuration values in `.env` according to the application's documentation.

**Important:** Keep API keys, passwords, and other credentials private. Do not commit `.env` files or secret credentials to GitHub.

## Running the Application

Once the dependencies and configuration are ready:

1. Activate the Python virtual environment.
2. Verify that the required services and hardware connections are available.
3. Follow the application repository's instructions to start the backend.
4. Start the frontend using its documented procedure, if it runs separately.
5. Open the configured web interface.
6. Verify communication between the application and the robot hardware.

The exact startup commands depend on the MAX application source repository and its configuration.

## Development Environment

The development environment provides the tools and configuration needed to explore, modify, and extend the MAX software.

It covers:

- Development tool installation.
- Source code management using Git.
- Repository cloning and project setup.
- Python environment and dependency management.
- Backend and frontend development.
- Application execution and testing.
- Configuration and debugging.

## Customisation and Further Development

MAX is designed as an extensible robotics platform that encourages developers, students, and researchers to explore, customise, improve, and expand its software capabilities.

The software architecture provides opportunities to:

- Modify and extend existing software components.
- Integrate additional AI models and services.
- Develop new voice interaction capabilities.
- Add support for additional languages.
- Customise the web interface and user experience.
- Integrate new libraries, tools, and software frameworks.
- Develop additional robot functionalities.
- Extend communication and hardware integration.
- Experiment with new software features and applications.

Developers are encouraged to experiment with the existing implementation, introduce improvements, and contribute new capabilities to the MAX ecosystem.

The goal is to provide a flexible software foundation for learning, experimentation, customisation, and further robotics development.

## Troubleshooting

| Issue | Suggested Check |
|---|---|
| Raspberry Pi does not boot | Check the OS image, microSD card, and power supply |
| SSH connection fails | Verify network connectivity, hostname, and SSH configuration |
| Python package installation fails | Check Python version, virtual environment, and package compatibility |
| Application does not start | Check dependencies, configuration files, and application logs |
| Arduino is not detected | Check USB connection, serial device permissions, and port configuration |
| API connection fails | Verify network connectivity and API credentials |

For unresolved issues, provide the operating system, computing platform, error message, and relevant logs when reporting a problem.

## Contributing

Contributions from the robotics and open-source community are welcome.

You can contribute by:

- Improving installation and configuration guides.
- Developing new software functionalities.
- Extending existing software components.
- Integrating additional tools and technologies.
- Improving documentation and examples.
- Reporting bugs and suggesting enhancements.

### Contribution Guidelines

1. Explore the existing repository and documentation.
2. Identify an area for improvement or development.
3. Create a separate branch for your changes.
4. Make your modifications and test them.
5. Document your changes clearly.
6. Submit a pull request for review.

All contributions should include clear descriptions and relevant technical information.

## License

Licensing information will be announced once the project license has been finalised and approved by Mensch Robotics.

## About MAX

MAX is an open-source educational robotics platform developed by **Mensch Robotics Private Limited**.

It is designed to encourage practical learning, experimentation, and innovation in robotics by bringing together hardware, electronics, software, AI, and computing technologies.

**Developed by:** Mensch Robotics Private Limited

**Website:** https://menschrobotics.com

**Main Ecosystem Repository:** https://github.com/menschrobotics/maxrobot

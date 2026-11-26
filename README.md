# MAX Robot – Setup and Software

**Installation, system configuration, software architecture, and development environment for the MAX open-source robotics platform.**

This repository provides documentation for preparing the computing environment, configuring the operating system, understanding the software architecture, and setting up the development environment for MAX.

MAX is designed as an extensible robotics platform that allows developers, students, and researchers to explore its software, customise existing functionalities, integrate new technologies, and develop additional capabilities.

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

---

## Overview

The MAX software environment integrates artificial intelligence, voice processing, web-based interaction, real-time communication, and hardware control.

Its architecture combines a Python-based backend with a web-based frontend to support communication between users and the robot.

This repository covers:

- Computing platform preparation.
- Operating system installation and configuration.
- Software architecture and technology stack.
- Development environment preparation.
- General software installation and configuration.
- Application execution and development.
- Software customisation and extension.

## System Requirements

MAX supports different computing platforms depending on application requirements and available computing resources.

| Component | Requirement |
|---|---|
| Standard computing option | Compatible Raspberry Pi |
| Advanced computing option | NVIDIA Jetson Orin Nano |
| Microcontroller | Arduino Mega 2560 |
| Network | Wi-Fi or Ethernet |
| Storage | Compatible microSD card or SSD |
| Development tools | Git, Python, and code editor |

### Computing Platform Options

- **Raspberry Pi:** A standard computing option for running supported MAX software functionalities.
- **NVIDIA Jetson Orin Nano:** An advanced computing option for applications requiring higher processing performance and GPU-accelerated AI capabilities.

These platforms are alternative computing options. Developers can select a suitable platform based on their project requirements and adapt the software to other compatible computing hardware.

**Note:** Computing requirements may vary depending on the software features, applications, and hardware configuration. Verify operating system and dependency compatibility before installation.

## Raspberry Pi Setup

This section explains how to prepare and configure a Raspberry Pi for the MAX software environment.

### 1. Required Items

- Raspberry Pi board.
- Compatible microSD card.
- Card reader.
- Suitable power supply.
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
3. Select **Choose OS** and choose a compatible 64-bit operating system.
4. Select **Choose Storage** and select your microSD card.
5. Open the OS customisation settings, if available.
6. Configure the following:
   - Hostname.
   - Username and password.
   - Wi-Fi credentials.
   - Wireless LAN country.
   - SSH access.
7. Review the configuration and write the operating system to the microSD card.

Use an operating system version compatible with the selected Raspberry Pi model and MAX software dependencies.

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

The Raspberry Pi environment is now prepared for software development and configuration.

## Jetson Orin Nano Setup

**Advanced Computing Option**

The NVIDIA Jetson Orin Nano can be used as an alternative computing platform for MAX applications requiring greater processing performance, GPU acceleration, and advanced AI capabilities.

The setup process generally includes:

1. Preparing the Jetson Orin Nano development kit.
2. Installing a compatible NVIDIA JetPack environment.
3. Configuring network connectivity and remote access.
4. Updating system packages.
5. Installing required development tools.
6. Preparing the MAX software environment.

Refer to the official [NVIDIA Jetson documentation](https://developer.nvidia.com/embedded/learn/get-started-jetson-orin-nano-devkit) for installation instructions.

Software configuration may vary depending on the selected JetPack version and application requirements.

## Software Architecture

MAX follows a modular software architecture that connects AI processing, voice interaction, user interfaces, and robot hardware.

The major software components include:

- **Frontend:** Provides the web-based interface for user interaction.
- **Backend:** Manages application logic, request processing, and communication between software components.
- **AI Integration:** Handles AI model integration, query processing, and response generation.
- **Voice Processing:** Supports speech recognition and audio response generation.
- **Real-Time Communication:** Enables data exchange between the frontend and backend.
- **Hardware Integration:** Connects software operations with the robot's control hardware.

The modular structure allows individual components to be developed, maintained, and extended independently.

## Technology Stack

The MAX software environment uses a combination of programming languages, frameworks, and development tools.

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

Technology requirements may vary depending on the application configuration and enabled functionalities.

## Software Installation

This section outlines the general process for preparing the Python development environment.

### 1. Install Required Packages

Verify that Python and Git are installed:

```bash
python3 --version
git --version
```

If Python is not installed, refer to the installation instructions for your selected operating system.

### 2. Create a Python Virtual Environment

Navigate to the application source directory:

```bash
cd path/to/application
```

Create a virtual environment:

```bash
python3 -m venv venv
```

Activate the environment:

**Linux / Raspberry Pi / Jetson:**

```bash
source venv/bin/activate
```

### 3. Install Software Dependencies

If the application source repository provides a `requirements.txt` file, install the dependencies:

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

If the project uses another dependency management method, follow the instructions provided by its source repository.

### 4. Install Additional System Dependencies

Some software components may require additional system packages, audio libraries, or hardware communication utilities.

Install the required packages according to the application documentation and selected operating system.

## Software Configuration

After preparing the development environment, configure the software components according to the application requirements.

Configuration may include:

- Backend application settings.
- Frontend settings.
- AI service credentials and API keys.
- Speech recognition and speech generation settings.
- WebSocket communication settings.
- Serial communication settings.
- Hardware and device configuration.

### Environment Variables

If the application provides an example environment file, create a working copy:

```bash
cp .env.example .env
```

Update the required values in `.env` according to the application's documentation.

**Important:** Keep API keys, passwords, and other credentials private. Never commit `.env` files or secret credentials to GitHub.

## Running the Application

After completing the installation and configuration:

1. Activate the Python virtual environment.
2. Verify that the required services and hardware connections are available.
3. Start the backend using the documented application procedure.
4. Start the frontend if it runs separately.
5. Open the configured web interface.
6. Verify communication between the application and robot hardware.

Application-specific startup commands depend on the source code and configuration being used.

## Development Environment

The development environment provides the tools and configuration required to explore and modify the MAX software.

It covers:

- Development tool installation.
- Source code management using Git.
- Repository management.
- Python environment and dependency management.
- Backend and frontend development.
- Application testing and debugging.
- Software configuration.

Developers can use these tools to understand the existing implementation, troubleshoot issues, and contribute improvements.

## Customisation and Further Development

MAX is designed as an extensible robotics platform that encourages developers, students, and researchers to explore and expand its software capabilities.

The platform provides opportunities to:

- Modify and extend existing software components.
- Integrate additional AI models and services.
- Develop new voice interaction capabilities.
- Add support for additional languages.
- Customise the user interface and interaction experience.
- Integrate additional libraries and frameworks.
- Develop new robot functionalities.
- Extend communication and hardware integration.
- Experiment with new software features and applications.

Developers are encouraged to explore the existing implementation, introduce improvements, and contribute new capabilities to the MAX ecosystem.

### MAX Intelligence – Application Source Code

The MAX Intelligence repository contains the application software for the MAX Robot ecosystem.

**Repository:** [MAX Intelligence – GitHub](https://github.com/menschrobotics/maxrobot_intelligence)

Explore the repository to access the source code and learn more about the software implementation and its development.

## Troubleshooting

The following table provides general checks for common setup and configuration issues.

| Issue | Suggested Check |
|---|---|
| Raspberry Pi does not boot | Check the operating system image, microSD card, and power supply. |
| SSH connection fails | Verify network connectivity, hostname, and SSH configuration. |
| Python package installation fails | Check Python version, virtual environment, and package compatibility. |
| Application does not start | Check dependencies, configuration files, and application logs. |
| Arduino is not detected | Check the USB connection, serial port, and device permissions. |
| API connection fails | Verify network connectivity and API credentials. |

When reporting an issue, include the computing platform, operating system, error message, and relevant logs to help identify the problem.

## Contributing

Contributions from the robotics and open-source community are welcome.

You can contribute by:

- Improving installation and configuration documentation.
- Developing new software functionalities.
- Extending existing software components.
- Integrating additional tools and technologies.
- Improving examples and documentation.
- Reporting bugs and suggesting enhancements.

### Contribution Guidelines

1. Explore the repository and existing documentation.
2. Identify an area for improvement or development.
3. Create a separate branch for your changes.
4. Implement and test your modifications.
5. Document your changes clearly.
6. Submit a pull request for review.

All contributions should include clear descriptions and relevant technical information.

## License

Licensing information will be announced once the project license has been finalised and approved by Mensch Robotics.

## About MAX

MAX is an open-source educational robotics platform developed by **Mensch Robotics Private Limited**.

It is designed to encourage practical learning, experimentation, and innovation in robotics by bringing together hardware, electronics, software, AI, and computing technologies.

**Developed by:** Mensch Robotics Private Limited

**Website:** [https://menschrobotics.com](https://menschrobotics.com/)

**Main Ecosystem Repository:** [MAX Robot – GitHub](https://github.com/menschrobotics/maxrobot)

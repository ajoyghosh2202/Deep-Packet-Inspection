# DPI Engine - Deep Packet Inspection System

A high-performance Deep Packet Inspection (DPI) Engine developed in C++17 for analyzing, classifying, and filtering network traffic from PCAP files. The project uses flow-based packet processing, TLS SNI extraction, and a multi-threaded architecture for efficient packet inspection.

---

## Features

- Deep Packet Inspection (DPI)
- PCAP File Parsing
- TLS SNI Extraction
- Application Detection (YouTube, Facebook, Google, GitHub, etc.)
- Ethernet, IPv4, TCP, and UDP Packet Parsing
- Five-Tuple Based Flow Tracking
- IP Blocking
- Domain Blocking
- Application Blocking
- Multi-threaded Packet Processing
- Thread-safe Queues
- Traffic Statistics and Reporting
- Filtered PCAP Output Generation

---

## Technologies Used

- C++17
- Multi-threading
- Networking Protocols
- TLS/HTTPS Analysis
- PCAP File Processing
- Producer-Consumer Architecture
- Flow-Based Packet Classification

---

## Project Structure

```
packet_analyzer/
│
├── include/
│   ├── pcap_reader.h
│   ├── packet_parser.h
│   ├── sni_extractor.h
│   ├── types.h
│   ├── rule_manager.h
│   ├── connection_tracker.h
│   ├── load_balancer.h
│   ├── fast_path.h
│   ├── thread_safe_queue.h
│   └── dpi_engine.h
│
├── src/
│   ├── pcap_reader.cpp
│   ├── packet_parser.cpp
│   ├── sni_extractor.cpp
│   ├── types.cpp
│   ├── main_working.cpp
│   └── dpi_mt.cpp
│
├── generate_test_pcap.py
├── test_dpi.pcap
└── README.md
```

---

## How It Works

1. Reads packets from a PCAP file.
2. Parses Ethernet, IP, TCP, and UDP headers.
3. Creates a Five-Tuple for flow identification.
4. Performs Deep Packet Inspection.
5. Extracts TLS SNI from HTTPS traffic.
6. Classifies applications based on domain names.
7. Applies blocking rules.
8. Writes forwarded packets to an output PCAP file.
9. Generates traffic statistics and reports.

---

## Supported Blocking Rules

- Application Blocking
- Domain Blocking
- Source IP Blocking

Examples:

```
YouTube
TikTok
Facebook
192.168.1.50
```

---

## Requirements

### Windows

- MinGW-w64
- g++
- VS Code (Recommended)

### Linux/macOS

- GCC or Clang
- C++17 Compiler

---

## Build Instructions

### Simple Version

```bash
g++ -std=c++17 -O2 -I include -o dpi_simple src/main_working.cpp src/pcap_reader.cpp src/packet_parser.cpp src/sni_extractor.cpp src/types.cpp
```

### Multi-threaded Version

```bash
g++ -std=c++17 -pthread -O2 -I include -o dpi_engine src/dpi_mt.cpp src/pcap_reader.cpp src/packet_parser.cpp src/sni_extractor.cpp src/types.cpp
```

For Windows:

```bash
g++ -std=c++17 -O2 -I include -o dpi_engine.exe src/dpi_mt.cpp src/pcap_reader.cpp src/packet_parser.cpp src/sni_extractor.cpp src/types.cpp
```

---

## Running the Project

### Basic Usage

Linux/macOS

```bash
./dpi_engine test_dpi.pcap output.pcap
```

Windows PowerShell

```powershell
.\dpi_engine.exe test_dpi.pcap output.pcap
```

---

## Running with Blocking Rules

```bash
./dpi_engine test_dpi.pcap output.pcap \
--block-app YouTube \
--block-app TikTok \
--block-ip 192.168.1.50 \
--block-domain facebook
```

Windows:

```powershell
.\dpi_engine.exe test_dpi.pcap output.pcap --block-app YouTube --block-app TikTok --block-ip 192.168.1.50 --block-domain facebook
```

---

## Multi-threaded Execution

```bash
./dpi_engine input.pcap output.pcap --lbs 4 --fps 4
```

Example:

- 4 Load Balancer Threads
- 4 Fast Path Threads
- Total Processing Threads = 16

---

## Output

The program generates:

- Filtered PCAP File
- Application Statistics
- Packet Statistics
- Thread Statistics
- Detected Domains
- Traffic Classification Report

Sample Output:

```
Total Packets
Forwarded Packets
Dropped Packets
TCP Packets
UDP Packets
Detected Applications
Detected Domains
```

---

## Future Improvements

- QUIC / HTTP3 Support
- Bandwidth Throttling
- Persistent Blocking Rules
- Live Statistics Dashboard
- Additional Application Signatures
- Real-Time Packet Capture Support

---

## Learning Outcomes

This project demonstrates:

- Deep Packet Inspection
- Network Packet Analysis
- TLS SNI Extraction
- Multi-threaded Programming
- Flow Tracking
- Traffic Classification
- Packet Filtering
- Producer-Consumer Pattern
- PCAP Processing
- Thread-safe Data Structures

---

## Author

**Ajoy Ghosh**

B.Tech CSE Student | AI/ML Enthusiast | Software Developer

---

## License

This project is developed for educational and learning purposes.

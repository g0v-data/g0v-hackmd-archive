---
tags: digital-resilience, resilience, internet-shutdown, digiresi, civil-defense, 民防, 數位韌性松, DigiResiTh0n, hackathon, civil defense,
image:
title: g0mesh - quickstart
---

# g0mesh - quickstart

# prerequisite
- having a compatible Meshtastic hardware (such as TTGO T-Beam, RAKwireless nodes, or other ESP32 LoRa devices)
- standardize on similar antenna types when possible to ensure consistent signal propagation
- 

# quickstart
## core config
- Region Setting: All devices must use the same region setting based on your location's regulatory requirements
- Modem Preset: Standardize on "Long Range - Fast" preset for all backbone nodes to ensure compatibility
- Max Hops: Set to 3-5 depending on network size (higher values increase range but can impact network efficiency)
LoRa Frequency Slot: Must be identical across all nodes (dependent on your region)




# for critical relay points
- consider using solar-powered nodes with backup batteries
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
## Basic config
- Region Setting: All devices must use the same region setting based on your location's regulatory requirements
- Modem Preset: Standardize on "Long Range - Fast" preset for all backbone nodes to ensure compatibility
- Max Hops: Set to 3-5 depending on network size (higher values increase range but can impact network efficiency)
- LoRa Frequency Slot: Must be identical across all nodes (dependent on your region)

# Channel and Encryption Configuration
## secure channel setup
- Use AES-256 encryption with a custom pre-shared key (PSK)
- Never use the default channel name "LongFast" or default PSK "AQ==" for your backbone
- Document the PSK securely and share only with trusted community members

## for Channels setups
- Create a public channel for community users to connect to the backbone
- Consider a separate admin channel with restricted access for network management

## Security Measures
- (optional) Rotate the PSK periodically (every 3-6 months) to maintain network security
- For critical relay points, enable "Managed Mode" to prevent unauthorized configuration changes
- Configure position precision settings appropriately for privacy (reduce precision if needed)

# Node Verification and Authentication
## Node Identity Management
- Maintain a central registry of all authorized nodes including:
    - Node ID
    - Geographic location
    - Hardware specifications
    - Public key for direct message authentication
    - Owner/operator contact information
## Node Verification Process
- Implement a node verification procedure before adding new nodes:
    - Physical verification of hardware when possible
    - Test message exchange to confirm proper configuration
    - Document the public key of each node for future verification
    - Issue a unique identifier in the node name (e.g., "CB-Node01-[Location]")
## Authentication
- Use Public Key Cryptography (PKC) for direct messages between administrators
- For critical commands, require acknowledgment from multiple trusted nodes
# Relay Point Placement and Monitoring
## Strategic Placement
- Map your community area and identify optimal relay point locations
- Ensure each node has line-of-sight to at least two other nodes when possible
- Document expected signal strength between adjacent nodes for baseline comparison
## Signal Quality Monitoring
- Establish regular network health checks with traceroute tests between key nodes
- Monitor signal-to-noise ratios between adjacent nodes
- Create a schedule for checking battery levels on solar-powered nodes

## Network Reliability Testing
- Conduct periodic network tests by temporarily disabling random nodes to verify mesh resilience
- Document alternative routing paths for critical communications
- Test full network restarts to ensure automatic recovery

# Data Routing and Traffic Management
## Traffic Prioritization
- Establish message priority categories:
    - Emergency messages (highest priority)
    - Network management messages
    - Regular user messages
    - Telemetry data (lowest priority)
## Bandwidth Conservation
- Limit position broadcasts to essential nodes
- Configure appropriate telemetry intervals (not too frequent)
- Consider disabling unnecessary broadcasts during high traffic periods
## Gateway Management
- If using MQTT gateways to connect to the internet:
    - Implement strict uplink/downlink controls
    - Configure encryption for internet-bound messages
    - Monitor gateway bandwidth usage
# Community Guidelines and Governance
## Access Control
- Define clear criteria for who can operate backbone nodes
- Establish a process for approving new community members
- Document procedures for revoking access when necessary
## Maintenance Responsibilities
- Assign specific maintenance roles to community members
- Create a schedule for regular firmware updates
- Establish a communication procedure for notifying users of planned maintenance
## Network Expansion
- Document the process for proposing and approving new relay points
- Establish criteria for evaluating new node locations
- Define a testing period for new nodes before full integration

# Documentation and Implementation
## Setup Documentation
- Create step-by-step configuration guides for new nodes
- Use QR codes to share channel configurations securely
- Document troubleshooting procedures for common issues
## Network Map
- Maintain an up-to-date visual map of all relay points
- Document expected coverage areas
- Note any known dead zones or weak signal areas
## Implementation Plan
- Start with a small core network (3-5 nodes)
- Test thoroughly before expanding
- Gradually add community access points
- Conduct regular reviews of network performance
# Resilience and Emergency Protocols
## Node Failure Procedures
- Document step-by-step procedures for identifying failed nodes
- Establish backup nodes that can be quickly deployed
- Create a contact list for node operators

# Emergency Operation Mode
- Define protocol for switching to emergency operation (reduced features, maximized reliability)
- Create pre-configured emergency channels
- Establish clear procedures for emergency message handling






















# for critical relay points
- consider using solar-powered nodes with backup batteries
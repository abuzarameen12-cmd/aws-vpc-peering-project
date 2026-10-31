# AWS VPC Peering Implementation

## Overview
This project demonstrates the setup and configuration of a bidirectional VPC Peering Connection between two Amazon VPCs (`VPC-A` and `VPC-B`) within the same AWS region (`eu-north-1`), allowing secure private communication.

## Architecture & Configuration Details
- **VPC-A CIDR:** `10.1.0.0/16`
- **VPC-B CIDR:** `10.2.0.0/16`
- **Internet Gateway:** `My-IGW` (Attached to `VPC-A`)
- **VPC Peering Connection ID:** `pcx-0b8e82a41755f3e56` (Status: Active)

## Route Table Configurations
1. **VPC-A Route Table:**
   - Destination: `0.0.0.0/0` -> Target: `My-IGW` (Internet Access)
   - Destination: `10.2.0.0/16` -> Target: `pcx-0b8e82a41755f3e56` (VPC Peering)

2. **VPC-B Route Table:**
   - Destination: `10.1.0.0/16` -> Target: `pcx-0b8e82a41755f3e56` (VPC Peering)

## Implementation Steps
1. Created `VPC-A` and `VPC-B` with non-overlapping IPv4 CIDR blocks.
2. Created and attached `My-IGW` to `VPC-A`.
3. Initiated a VPC Peering Connection request from `VPC-A` to `VPC-B`.
4. Accepted the peering request to change the status to **Active**.
5. Updated route tables for both VPCs to route traffic through the active peering connection.
6. 

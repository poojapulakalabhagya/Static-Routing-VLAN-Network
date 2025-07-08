# Static Routing and VLAN-Based Network Configuration

## Overview
This project configures static routing between three routers and multiple VLANs. VLANs are used to segregate network traffic by department, and routing is handled using static routes. The configuration also includes secure access to network devices with encrypted passwords and SSH.

## Topology
- **VLANs**: HR, IT, Native (Loopback), Management (SVI)
- **Routers**: R1, R2, R3 (Handling static routing between VLANs and networks)
- **Switches**: S1, S2 (VLAN segmentation and trunking)
- **Devices**: PCs in each VLAN with static IP assignment and routing between departments.

## Objectives:
- Configure static routes between routers for inter-VLAN communication.
- Implement VLANs on switches to segment network traffic.
- Secure routers and switches with password encryption and SSH access.
- Use loopback addresses for testing and management.

## Network Details:
### VLAN Configuration:
- **VLAN 10 (HR)** - `192.168.10.0/24`
- **VLAN 20 (IT)** - `192.168.20.0/24`
- **Management VLAN (SVI)** - `192.168.100.0/29`
- **Point-to-Point links between routers**:
  - `192.168.12.0/30` (R1-R2)
  - `192.168.23.0/30` (R2-R3)

### Addressing Table:
Refer to the [Addressing Table.pdf](Addressing%20Table.pdf) for complete IP address assignments, or have a look here:

| **Device** | **Interface**       | **IP Address**         | **Subnet Mask**        | **Description**        |
|------------|---------------------|------------------------|------------------------|------------------------|
| **Router 1 (R1)** | `G0/0/0.10`          | `192.168.10.1`         | `255.255.255.0`         | HR Department           |
|            | `G0/0/0.20`          | `192.168.20.1`         | `255.255.255.0`         | IT Department           |
|            | `G0/0/0.100`         | `192.168.100.1`        | `255.255.255.248`       | Management VLAN         |
|            | `S0/1/0`             | `192.168.12.1`         | `255.255.255.252`       | Link to R2              |
| **Router 2 (R2)** | `S0/1/1`             | `192.168.12.2`         | `255.255.255.252`       | Link to R1              |
|            | `S0/2/0`             | `192.168.23.2`         | `255.255.255.252`       | Link to R3              |
|            | `Loopback0`          | `200.0.0.1`            | `255.255.255.0`         | Loopback Interface      |
| **Router 3 (R3)** | `S0/2/0`             | `192.168.23.1`         | `255.255.255.252`       | Link to R2              |
|            | `G0/0/0`             | `192.168.30.1`         | `255.255.255.0`         | Department Network      |
| **Switch 1 (S1)** | `VLAN 100 (Management)` | `192.168.100.2`        | `255.255.255.248`       | Management VLAN         |
| **Switch 2 (S2)** | `VLAN 100 (Management)` | `192.168.100.3`        | `255.255.255.248`       | Management VLAN         |

### VLAN Table:

| **VLAN**    | **VLAN ID** | **Subnet**              | **Description**        |
|-------------|-------------|-------------------------|------------------------|
| **HR**      | 10          | `192.168.10.0/24`       | HR Department           |
| **IT**      | 20          | `192.168.20.0/24`       | IT Department           |
| **Native**  | 40          | N/A                     | Native VLAN (Trunking)  |
| **SVI**     | 100         | `192.168.100.0/29`      | Management VLAN         |

### Network Topology:
Refer to the [Lab-2_Mohamed_Khaled.pkt](Lab-2_Mohamed_Khaled.pkt).
- User: admin
- Pass:123
- Privilege: 12345

## Configuration Files:
- **Switch 1 (S1)**, **Switch 2 (S2)**, **Router 1 (R1)**, **Router 2 (R2)**, and **Router 3 (R3)** configurations are available in the [Static Route.txt](Static%20Route.txt) file.

## Steps to Implement:
1. Set up VLANs on switches.
2. Configure static routing between routers.
3. Secure the devices using SSH, password encryption, and MOTD banners.
4. Assign IP addresses to interfaces as per the configuration.
5. Apply management VLAN settings for device management.
6. Test connectivity between routers and VLANs.

## **Contact**
For any questions or feedback, please contact:
- **Name**: Mohamed Khaled Mahmoud Sayed
- **Email**: Mo7ammad244@gmail.com

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

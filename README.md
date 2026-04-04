*This project has been created as part of the 42 curriculum by vabatist.*

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Description](#description)
- [Instructions](#instructions)
  - [1) Running the training and evaluation interface](#1-running-the-training-and-evaluation-interface)
  - [1.1) Manual launch (fallback if run.sh fails)](#11-manual-launch-fallback-if-runsh-fails)
  - [2) Exporting configurations](#2-exporting-configurations)
  - [3) Submission requirements](#3-submission-requirements)
  - [4) Evaluation interface](#4-evaluation-interface)
- [Resources](#resources)
  - [Networking concepts studied](#networking-concepts-studied)
    - [- TCP (Transmission Control Protocol)](#--tcp-transmission-control-protocol)
    - [- IP address](#--ip-address)
    - [- Public vs. Private IP addresses](#--public-vs-private-ip-addresses)
    - [- Subnet mask](#--subnet-mask)
    - [- CIDR notation](#--cidr-notation)
    - [- Subnetting table / reference](#--subnetting-table--reference)
    - [- Default gateways](#--default-gateways)
    - [- Switch](#--switch)
    - [- Router](#--router)
    - [- Routing table](#--routing-table)
    - [- OSI model (7 layers)](#--osi-model-7-layers)
  - [Classic reference](#classic-reference)
  - [Useful links](#useful-links)
  - [AI usage (what and where)](#ai-usage-what-and-where)

## Description
**NetPractice** is a project that involves solving networking problems to make a network function properly.

**Goal:** The goal of the project is to configure the provided network (IP addresses, subnet masks, routes/gateways, etc.) so that the required hosts can communicate according to the level’s objectives. This repository includes the **10 exported configuration files** (one per level) at the repository root: `level1.json` through `level10.json`. The project focuses on understanding *why* a configuration works rather than memorizing values.

## Instructions

### 1) Running the training and evaluation interface
1. Download the file attached to the project’s page.
2. Extract the files into any folder of your choice.
3. From that directory, run:
   ```bash
   ./run.sh
   ```
This shell script will launch a local web server and automatically open your preferred web browser to the dedicated NetPractice page.

### 1.1) Manual launch (fallback if run.sh fails)
Due to technical design and security constraints on various web browsers, it is required to use a local web server to deliver NetPractice’s web pages.
**If the “run.sh” script does not function properly, you can access the project manually:**
- first run *(you may change the port number)*:
   ```bash
   python3 -m http.server 49242
   ```
- then in your web browser navigate to the URL *(or any other port you may have chosen)*:
   ```bash
   http://localhost:49242
   ```

### 2) Exporting configurations
- In the **training interface**, enter your **42 intranet login** so the tool generates/export files tied to your user.
- For each level, a non-functioning network diagram is displayed.
- At the top of your window, you will see one or more objectives that you must achieve by
adjusting the available configuration so that the network functions properly.
- To succeed, modify the unshaded fields until your network configuration is correct.
- At the bottom of the page, you will see logs. They can help you understand why your
configuration is incorrect, for example, if a **gateway** is missing or an **IP address** is invalid.
- Click the **Check again button** to verify whether your configuration is correct
- After completing a level and meeting all goals, you can click the **Get my config button** to export the configuration for that level and move to **Next level**.
- Repeat for all required levels until you have exported **10 configuration files**.

### 3) Submission requirements
For the final submission, **exactly 10 exported configuration files (one per level) must be placed at the root of this Git repository** (same level as this `README.md`).
Only files inside your repository are evaluated.

### 4) Evaluation interface
- In the **evaluation interface**, you will have to successfully complete three random levels, as mentioned on the training platform. You will have a limited amount of time to do so.
- You are not allowed to use external tools during your evaluation.
The use of a simple calculator such as bc is tolerated, but it will be the limit.

## Resources

To complete this assignment, you have to understand how addressing works in a network that includes devices such as routers and switches. Read about TCP/IP addressing to strengthen your understanding of these concepts.

### Networking concepts studied
This project practices fundamental concepts, including:
#### - TCP (Transmission Control Protocol)
A reliable, connection-oriented transport protocol. TCP establishes a connection, breaks data into smaller packets and uses acknowledgements to provide end‑to‑end delivery without loss.
#### - IP address
Your device's logical address on a network. It is split into two parts: one part identifies the network you belong to, and the other part identifies your specific host device
#### - Public vs. Private IP addresses
  - Public IP: A globally routable address assigned by your internet service provider that lets you connect directly to the Internet
  - Private IP: An internal address assigned by your router strictly for devices on the same local network to talk to each other. It is not routable on the public Internet, keeping your internal devices hidden
#### - Subnet mask
A 32-bit value (4 bytes) that indicates which bits of your IP address represent the network and which represent the host. It defines the size of the subnet and which addresses are considered “local”.
#### - CIDR notation
A compact way to write a subnet mask using a prefix length (e.g., `/24`, `/30`). The number after / is how many bits are in the network prefix. So instead of writing out `255.255.255.0`, you just use a slash followed by the number of bits that serve as the network address, like `/24`.
#### - Subnetting table / reference
It gives you a quick lookup to map prefix lengths to:
    - Subnet mask (e.g., /27 → 255.255.255.224)
    - Number of usable hosts per subnet
    - Block size / address increment
#### - Default gateways
The ultimate "way out" of your network. It is the next-hop router IP your device blindly tosses traffic to when the destination is outside the local subnet and it doesn't have a more specific route (`0.0.0.0/0`).
#### - Switch
A Layer 2 device that connects multiple hosts together within a single local network. It only distributes packets locally and cannot talk directly to an outside network.
#### - Router
A Layer 3 device that connects multiple different networks together. It has an interface for every network it touches, and the IP ranges on those interfaces absolutely must not overlap.
#### - Routing table
A data table stored in a router that lists the directions to particular network destinations. Each entry pairs a destination network with a "next hop" IP address, telling the packet exactly where to go next.
#### - OSI model (7 layers)
- OSI stands for **Open Systems Interconnect** Reference Model. It is an architectural model developed by the International Standards Organization (ISO) to describe the structure and functions of data communications protocols. By dividing network communications into seven distinct layers, it isolates functions so that new network applications or hardware can be added without having to rewrite the entire system. The layers are:
    1. **Physical**: Defines the physical characteristics of the network media and hardware. *Examples: voltage levels, interface pins, RS232C and V.35 connectors, and IEEE 802.3 wiring standards*.
    2. **Data Link**: Handles the reliable delivery of data across the underlying physical network link. *Examples: existing data link protocols over which IP transmits, such as Ethernet frames*.
    3. **Network**: Manages connections across the network and handles the addressing, routing, and delivery of data. *Example: the Internet Protocol (IP)*.
    4. **Transport**: Provides end-to-end error detection and correction, guaranteeing that the receiver gets the data exactly as it was sent. *Examples: Transmission Control Protocol (TCP) and User Datagram Protocol (UDP)*.
    5. **Session**: Manages the sessions (connections) between cooperating applications. *Examples: In TCP/IP, this is handled using "sockets" and "ports" to describe the communication path*.
    6. **Presentation**: Standardizes how data is represented and presented to the applications. *Examples: XDR and MIME protocols*.
    7. **Application**: The top level where user-accessed network processes and application programs reside. *Examples: File Transfer Protocol (FTP), Hypertext Transfer Protocol (HTTP), Simple Mail Transfer Protocol (SMTP), and Telnet*.

### Classic reference
- [TCP/IP Network Administration, Craig Hunt (3rd Edition)](https://www.oreilly.com/library/view/tcp-ip-network-administration/0596002971/) — *Used as a reliable reference to review core TCP/IP fundamentals (addressing, routing principles, and a troubleshooting mindset).*

### Useful links
- [You Suck at Subnetting (YouTube series)](https://youtube.com/playlist?list=PLIhvC56v63IKrRHh3gvZZBAGvsvOhwrRF&si=mVq2UlD8b8q1WdmL) — *This is where I started to learn about subnetting*
- [Guide to NetPractice (github)](https://github.com/lpaube/NetPractice) — *Helped a lot to fill the gaps that the videos didn’t cover: clearer explanations of common NetPractice patterns, typical mistakes, and how to reason about gateways/routes in the exercises. It helped me build the intuition for subnetting (CIDR, network/broadcast, usable host ranges) and get faster at doing calculations under time pressure.*
- [Subnet Masks Reference Table](https://www.cloudaccess.net/cloud-control-panel-ccp/157-dns-management/322-subnet-masks-reference-table.html) — *Useful to quickly map a CIDR prefix (e.g., `/30`, `/29`, `/27`) to its subnet mask, block size, and number of usable hosts. Knowing these common values (especially `/30` and `/29`) is important in NetPractice because many levels require choosing the smallest correct subnet and verifying that hosts are in the same network (or not) without spending too much time recalculating everything from scratch.*

### AI usage (what and where)
AI tools were used **only for documentation support**, specifically to:
- Rewrite and structure this `README.md` in clear English.
- Reduce repetitive editing (formatting, section organization, wording).

AI tools were **not** used to generate the exported configuration files; the network solutions were produced by completing the NetPractice levels and exporting the results from the training interface.

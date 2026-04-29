*This project has been created as part of the 42 curriculum by vabatist.*

<div id="top"></div>

```text
███╗   ██╗███████╗████████╗██████╗ ██████╗  █████╗  ██████╗████████╗██╗ ██████╗███████╗
████╗  ██║██╔════╝╚══██╔══╝██╔══██╗██╔══██╗██╔══██╗██╔════╝╚══██╔══╝██║██╔════╝██╔════╝
██╔██╗ ██║█████╗     ██║   ██████╔╝██████╔╝███████║██║        ██║   ██║██║     █████╗  
██║╚██╗██║██╔══╝     ██║   ██╔═══╝ ██╔══██╗██╔══██║██║        ██║   ██║██║     ██╔══╝  
██║ ╚████║███████╗   ██║   ██║     ██║  ██║██║  ██║╚██████╗   ██║   ██║╚██████╗███████╗
╚═╝  ╚═══╝╚══════╝   ╚═╝   ╚═╝     ╚═╝  ╚═╝╚═╝  ╚═╝ ╚═════╝   ╚═╝   ╚═╝ ╚═════╝╚══════╝
```

## Table of Contents

- [Description](#description)
- [Instructions](#instructions)
  - [1) Running the training and evaluation interface](#1-running-the-training-and-evaluation-interface)
  - [1.1) Manual launch (fallback if run.sh fails)](#11-manual-launch-fallback-if-runsh-fails)
  - [2) Exporting configurations](#2-exporting-configurations)
  - [3) Submission requirements](#3-submission-requirements)
  - [4) Evaluation interface](#4-evaluation-interface)
- [Resources](#resources)
  - [Networking concepts](#networking-concepts)
  - [Classic reference](#classic-reference)
  - [Useful links](#useful-links)
  - [AI usage (what and where)](#ai-usage-what-and-where)

## Description
**NetPractice** is a project that involves solving networking problems to make a network function properly.

**Goal:** The goal of the project is to configure the provided network (IP addresses, subnet masks, routes/gateways, etc.) so that the required hosts can communicate according to the level’s objectives. This repository includes the **10 exported configuration files** (one per level) at the repository root: `level1.json` through `level10.json`. The project focuses on understanding *why* a configuration works rather than memorizing values.

## Instructions

### 1) Running the training and evaluation interface
1. Download the file `net_practice.1.9.tgz` attached to the project’s page.
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

### Networking concepts
This project practices fundamental concepts, including:

<details>
  <summary><b>TCP (Transmission Control Protocol)</b></summary>

  A reliable, connection-oriented transport protocol. TCP establishes a connection, breaks data into smaller packets, uses acknowledgements/retransmissions, and delivers bytes in order to provide end‑to‑end delivery without loss.

</details>

<details>
  <summary><b>IP (Internet Protocol) address</b></summary>

  Your device’s logical address on a network, kind of like a phone number for computers and routers. It is composed of 4 sets of numbers (octets) separated by dots. Most private IPs use ranges like `192.168.1.x`. It is split into two parts: one part identifies the network you belong to, and the other part identifies your specific host device. Without IP addresses, devices would not be able to communicate with each other or connect to the Internet.

</details>

<details>
  <summary><b>Public vs. Private IP addresses</b></summary>

  - **Public IP**: A globally routable address assigned by your Internet Service Provider (ISP) that lets you connect directly to the Internet.
  - **Private IP**: An internal address used only inside your local network. It is not routable on the public Internet (often used together with NAT).

</details>

<details>
  <summary><b>Subnet mask</b></summary>

  A 32-bit value (4 bytes) that indicates which bits of your IP address represent the network and which represent the host. For example, `255.255.255.0` is the same as `/24`: the `255` octets mean those IP bits stay the same inside the subnet, and the `0` octet means that part can vary for the hosts.

  In a `/24` network, the last octet usually goes from `1` to `254` for devices. `0` is reserved for the network address, which identifies the subnet itself, and `255` is reserved for the broadcast address, which sends a message to every device in that subnet.

</details>

<details>
  <summary><b>CIDR (Classless Inter-Domain Routing) notation</b></summary>

  A compact way to write a subnet mask using a prefix length (e.g., `/24`, `/30`). The number after `/` is how many bits are in the network prefix.  
  Example: instead of writing `255.255.255.0`, you can write `/24`.

</details>

<details>
  <summary><b>Subnetting table / reference</b></summary>

  A quick lookup to map prefix lengths to:
  - subnet mask (e.g., `/27` → `255.255.255.224`)
  - number of usable hosts per subnet
  - block size / address increment

</details>

<details>
  <summary><b>IPv4 address classes and reserved ranges</b></summary>

  IPv4 classful addressing is a historical reference, but it is still useful for understanding common ranges:
  - **Class A**: `1.0.0.0` to `126.255.255.255` — Designed for very large networks with millions of hosts (host-heavy networks). Many Class A addresses were assigned to large corporations early on; for example:
    - General Electric: `3.0.0.0` to `3.255.255.255`
    - IBM: `9.0.0.0` to `9.255.255.255`
    - Xerox: `13.0.0.0` to `13.255.255.255`
    - Hewlett-Packard: `15.0.0.0` to `15.255.255.255`
  - **Class B**: `128.0.0.0` to `191.255.255.255`
  - **Class C**: `192.0.0.0` to `223.255.255.255`
  - **Class D**: `224.0.0.0` to `239.255.255.255` (multicast)
  - **Class E**: `240.0.0.0` to `255.255.255.255` (experimental/reserved)

  Reserved address ranges for private use:
  - `10.0.0.0` to `10.255.255.255`
  - `172.16.0.0` to `172.31.255.255`
  - `192.168.0.0` to `192.168.255.255`

  Other reserved ranges:
  - `127.0.0.0` to `127.255.255.255` is reserved for loopback and local host communication. Loopback addresses are virtual IPs that allow a computer to send traffic to itself, useful for testing whether the local network stack is working. You can use `ping 127.0.0.1` (also called "localhost") to verify that your own machine's networking is functioning correctly.
  - `224.0.0.0` to `239.255.255.255` is reserved for multicast addresses.

</details>

<details>
  <summary><b>Default gateway</b></summary>

  The “way out” of your network. It is the next-hop router IP your device sends traffic to when the destination is outside the local subnet (when no more specific route matches, i.e., the default route).

</details>

<details>
  <summary><b>Switch</b></summary>

  A Layer 2 device that connects multiple hosts together within a single local network. It forwards traffic locally (based on MAC addresses) and does not route between IP networks.

</details>

<details>
  <summary><b>Router</b></summary>

  A Layer 3 device that connects multiple different networks together. On a local network, the router is often the default gateway for the devices connected to that subnet. It has an interface for every network it touches, and the IP ranges on those interfaces must not overlap.

</details>

<details>
  <summary><b>Routing table</b></summary>

  A data table stored in a router that lists the directions to particular network destinations. Each entry pairs a destination network/prefix with a “next hop” IP address (or an outgoing interface), telling packets where to go next.

</details>

<details>
  <summary><b>OSI model (7 layers)</b></summary>

  OSI stands for **Open Systems Interconnect** Reference Model. It describes networking as 7 layers:
  1. **Physical**
  2. **Data Link**
  3. **Network**
  4. **Transport**
  5. **Session**
  6. **Presentation**
  7. **Application**

</details>

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
<div align="right">
  <b><a href="#top">↥ back to top</a></b>
</div>
</br>

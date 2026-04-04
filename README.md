*This project has been created as part of the 42 curriculum by vabatist.*

## Description
**NetPractice** is a project that involves solving networking problems to make a network function properly.

**Goal:** The goal of the project is to configure the provided network (IP addresses, subnet masks, routes/gateways, etc.) so that the required hosts can communicate according to the level’s objectives. This repository includes the **10 exported configuration files** (one per level) at the repository root: `level1.json` through `level10.json`. The project focuses on understanding *why* a configuration works rather than memorizing values.

## Instructions

### 1) Running the training/evaluation interface
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

### 4) Evaluation
- In the **evaluation interface**, you will have to successfully complete three random levels, as mentioned on the training platform. You will have a limited amount of time to do so.
- You are not allowed to use external tools during your evaluation.
The use of a simple calculator such as bc is tolerated, but it will
be the limit.

## Resources

To complete this assignment, you have to understand how addressing works in a network that includes devices such as routers and switches. Read about TCP/IP addressing to strengthen your understanding of these concepts.

### Networking concepts studied
This project practices fundamental concepts, including:
- **TCP (Transmission Control Protocol)** A reliable, connection-oriented transport protocol. TCP establishes a connection, segments data, uses acknowledgements/retransmissions, and delivers bytes in order to provide end‑to‑end reliability.
- **IP address** A logical address used to identify a device and the network it belongs to. In IPv4, an address is split into a network part (which subnet) and a host part (which device inside that subnet).
- **Public vs. Private IP addresses**
  - Public IP: globally routable on the Internet (typically assigned by an ISP).
  - Private IP: used inside local networks (RFC1918 ranges) and not routable on the public Internet; usually translated to a public IP through NAT.
- **Subnet mask** A 32-bit value that indicates which bits of an IPv4 address represent the network and which represent the host. It defines the size of the subnet and which addresses are considered “local”.
- **CIDR notation** A compact way to write a subnet mask using a prefix length (e.g., `/24`, `/30`). The number after / is how many bits are in the network prefix.
- **Subnetting table / reference** A quick lookup to map prefix lengths to:
    - Subnet mask (e.g., /27 → 255.255.255.224)
    - Number of usable hosts per subnet
    - Block size / address increment
- **Default gateways**  The router IP a host sends traffic to when the destination is outside its local subnet (i.e., no more specific route matches).
- **Switch** A Layer 2 device that connects hosts within the same LAN and forwards frames based on MAC addresses. It does not route between IP networks.
- **Router** A Layer 3 device that connects different IP networks and forwards packets based on IP routes. Each router interface belongs to a specific subnet, and subnets must not overlap.
- **Routing table** A list of routes used to decide where to forward packets. Each entry typically includes a destination network/prefix and a next hop (or outgoing interface). NetPractice often simplifies this to “destination network + next hop”.
- **OSI model (7 layers)** A conceptual model that helps locate where protocols operate:
1. Physical
2. Data Link
3. Network
4. Transport
5. Session
6. Presentation
7. Application

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

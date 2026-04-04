*This project has been created as part of the 42 curriculum by vabatist.*

## Description
**NetPractice** is a project that involves solving networking problems to make a network function properly.

**Goal:** The goal of the project is to configure the provided network (IP addresses, subnet masks, routes/gateways, etc.) so that the required hosts can communicate according to the level’s objectives. This repository includes the **10 exported configuration files** (one per level) at the repository root: `level1.json` through `level10.json`. The project focuses on understanding *why* a configuration works rather than memorizing values.


## Instructions

### 1) Running the training interface
1. Download the file attached to the project’s page.
2. Extract the files into any folder of your choice.
3. From that directory, run:
   ```bash
   ./run.sh
   ```
This shell script will launch a local web server and automatically open your preferred web browser to the dedicated NetPractice page.

Due to technical design and security constraints on various web browsers, it is required to use a local web server to deliver NetPractice’s web pages.
**If the “run.sh” script does not function properly, you can access the project manually:**
- first run:
   ```bash
   python3 -m http.server 49242
   ```
(you may change the port number)
- then in your web browser navigate to the URL:
   ```bash
   http://localhost:49242
   ```
 (or any other port you may have chosen).

### 2) Exporting configurations
- In the training interface, enter your **42 intranet login** so the tool generates/export files tied to your user.
- After completing a level and meeting all goals, **export** the configuration for that level.
- Repeat for all required levels until you have exported **10 configuration files**.

### 3) Submission requirements
For the final submission, **exactly 10 exported configuration files (one per level) must be placed at the root of this Git repository** (same level as this `README.md`).
Only files inside your repository are evaluated.

## Resources

### Networking concepts studied
This project practices fundamental concepts, including:
- TCP/IP addressing
- Subnet masks (CIDR)
- Default gateways
- Routers and switches
- OSI layers

### Classic references & links
- Craig Hunt, *TCP/IP Network Administration* (3rd Edition)
- [You Suck at Subnetting (YouTube series)](https://youtube.com/playlist?list=PLIhvC56v63IKrRHh3gvZZBAGvsvOhwrRF&si=mVq2UlD8b8q1WdmL)
- [Guide to NetPractice (github)](https://github.com/lpaube/NetPractice)

### AI usage (what and where)
AI tools were used **only for documentation support**, specifically to:
- Rewrite and structure this `README.md` in clear English.
- Reduce repetitive editing (formatting, section organization, wording).

AI tools were **not** used to generate the exported configuration files; the network solutions were produced by completing the NetPractice levels and exporting the results from the training interface.

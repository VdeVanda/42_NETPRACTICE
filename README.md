*This project has been created as part of the 42 curriculum by vabatist.*

## Description
**NetPractice** is a practical introduction to core computer networking concepts through a set of small, visual network scenarios.

**Goal:** for each level, configure the provided network (IP addresses, subnet masks, routes/gateways, etc.) so that the required hosts can communicate according to the level’s objectives. The project focuses on understanding *why* a configuration works rather than memorizing values.

## Instructions

### 1) Running the training interface
1. Download the NetPractice training files from the 42 intranet.
2. Extract them into a directory of your choice.
3. From that directory, run:
   ```bash
   ./run.sh
   ```
This starts a local web server and opens the training interface in your browser.

### 2) Exporting configurations
- In the training interface, enter your **42 intranet login** so the tool generates/export files tied to your user.
- After completing a level and meeting all goals, **export** the configuration for that level.
- Repeat for all required levels until you have exported **10 configuration files** (one per level).

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
- “You Suck at Subnetting” (YouTube series): https://youtube.com/playlist?list=PLIhvC56v63IKrRHh3gvZZBAGvsvOhwrRF&si=mVq2UlD8b8q1WdmL
- Community training/mirror: https://github.com/lpaube/NetPractice

### AI usage (what and where)
AI tools were used **only for documentation support**, specifically to:
- Rewrite and structure this `README.md` in clear English.
- Reduce repetitive editing (formatting, section organization, wording).

AI tools were **not** used to generate the exported configuration files; the network solutions were produced by completing the NetPractice levels and exporting the results from the training interface.
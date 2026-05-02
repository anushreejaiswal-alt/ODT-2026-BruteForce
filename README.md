# SKILL LAB PRATICAL HACKATHON

## Final Project README

> **Project Weight:** 100%  
> **Team Size:** 4/3 students  
> **Project Duration:** 16 hours  
> **Total Time Available:** 32 effort-hours per team  
> **Project Type:** Playful, interactive, technology-based experience

---

# Before you begin

## Fork and rename this repository

After forking this repository, rename it using the format:

`SKILLLAB_PROR-2026-TeamName`

### Example

`SKILLLAB_PROR-2026-AuroWizards`

Do not keep the default repository name.

---

# How to use this README

This file is your team’s **working project document**.

You must keep updating it throughout the build period.  
By the final review, this README should clearly show:

- your idea,
- your planning,
- your design decisions,
- your technical process,
- your build progress,
- your testing,
- your failures and changes,
- your final outcome.

## Rules

- Fill every section.
- Do not delete headings.
- If something does not apply, write `Not applicable` and explain why.
- Add images, screenshots, sketches, links, and videos wherever useful.
- Update task status and weekly logs regularly.
- Use this file as evidence of process, not only as a final report.

---

# 1. Team Identity

## 1.1 Studio / Group Name

`Project^2`

## 1.2 Team Members

| Name                  | Primary Role                    | Secondary Role   | Strengths Brought to the Project |
| --------------        | ------------------------------- | --------------   | -------------------------------- |
| `Mrugendra Vasmatkar` | `[Electronics / Coding / App ]` | `Documentation`  | `Documentation, Gift of Gab `|
| `Jyoti Bagate`        | `[Electronics / Fabrication]`   | `[Coding]`       | `Material Handling, Hardware`    |

## 1.3 Project Title

`"Project Project"`

`(because Project-or)`

<img width="1600" height="1131" alt="image" src="https://github.com/user-attachments/assets/c64bfbd4-b3b7-43d9-83ad-c203a5aa11bc" />

## 1.4 One-Line Pitch

`A projected, fully customizable time portal where engineering education is done through PUBG battlefield in the comfort of our home`

## 1.5 Expanded Project Idea

In 1–2 paragraphs, explain:

- what your project is,
- what kind of experience it creates,
- what technologies are involved.

**Response:**  
`A projected and fully customizable time portal can transform engineering education into an immersive PUBG-style battlefield experience from the comfort of home. In this environment, students can learn engineering concepts by entering a virtual battlefield where challenges, obstacles, and missions are designed around real technical problems. Instead of passively studying theory, learners actively apply concepts such as electronics, coding, sensors, robotics, mechanics, and system design to complete missions, solve problems, and progress through different levels. This approach makes engineering education more interactive, engaging, and practical by combining gaming, simulation, and hands-on problem-solving in a familiar and exciting format.`

---

# 2. Inspiration

## 2.1 References

List what inspired the project.

| Source Type | Title / Link                                                        | What Inspired You                                                                         |
| ----------- | ------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| `[Video]`   | `https://www.instagram.com/reel/DW4CT7WCDry/?igsh=cXg3dzAxYmdncDBo` | `How projection mapping can be used to create interactive digital + physical experiences` |
|             |                                                                     |                                                                                           |
|             |                                                                     |                                                                                           |

## 2.2 Original Twist

What makes your project original?

**Response:**  


---

# 3. Project Intent

## 3.1 User Journey 

Describe exactly how a user will use the project.Make it a story
**Response:**  

                                                  |



---

# 4. Definition of Success

## 4.1 Definition of “Usable”



## 4.2 Minimum Usable Version

What is the smallest version of this project that still delivers the core experience?

**Response:**  


## 4.3 Stretch Features

What features are nice to have but not essential?


---

# 5. System Overview

## 5.1 Project Type

Check all that apply.

- [x] Electronics-based

- [ ] Mechanical

- [ ] Sensor-based

- [ ] App-connected

- [ ] Motorized

- [ ] Sound-based

- [x] Light-based

- [ ] Screen/UI-based

- [ ] Fabricated structure

- [ ] Game logic based

- [ ] Installation

- [ ] Other:

## 5.2 High-Level System Description
## Features and Inputs

The system processes real-time environmental data via physical switches on the FPGA board to determine signal timing:

* **Traffic Density (D_A, D_B):** Represents the number of vehicles on each road.
* **Waiting Time (T_A, T_B):** Monitors how long vehicles have been stationary.
* **Priority Signals (P_A, P_B):** Emergency overrides for ambulances, fire trucks, or high-priority lanes.
* **Special Conditions (S_A, S_B):** Conditions such as pedestrian crossings or road restrictions.
* **Clock and Reset:** Global signals for synchronization and system initialization.

---

## Processing Logic

The controller logic is divided into two primary stages:

### 1. Priority Calculation
A dynamic score is calculated for each road to determine switching priority:
* **Score Increases:** Higher traffic density, extended waiting time, or active priority signals.
* **Score Decreases:** Higher saturation levels to maintain throughput and prevent bottlenecks.

### 2. FSM Decision Logic
A Finite State Machine (FSM) controls the signal transitions using the following constraints:
* **Minimum Green Time:** Ensures no rapid, flickering signal changes.
* **Early Switching:** Allows the signal to change early if traffic reduces significantly.
* **Maximum Time Limit:** Enforces fairness by preventing one road from holding the green light indefinitely.
* **Priority Comparison:** Dynamically selects the next road based on the highest calculated score.

---

## System Outputs

The controller drives standard traffic light signals for Road A and Road B. Safety logic ensures only one road is granted a green signal at any time.

* **Road A:** Red (R_A), Yellow (Y_A), Green (G_A).
* **Road B:** Red (R_B), Yellow (Y_B), Green (G_B).

---

## Physical Structure and Implementation

The design is optimized for the Spartan-7 FPGA using Verilog HDL:

* **Inputs:** Mapped to physical onboard switches representing traffic conditions.
* **Outputs:** Mapped to onboard LEDs (including RGB support) representing traffic signals.
* **Clock Divider:** Converts the high-frequency FPGA clock into a slower signal for real-time operation.
* **Controller Logic:** Implemented using Verilog and synthesized on hardware.

---

## Design Documentation

The following architectural diagrams serve as the blueprint for this implementation:

1. **State-diagram.jpeg:** Illustrates the behavioral flow and transition triggers between states S0-S3.
2. **FSM transition table.jpeg:** Maps the Current State (CS) and inputs to the Next State (NS).
3. **FSM output table.jpeg:** Defines the Moore Machine output logic for signal color encodings.

---

> **Note:** This design operates as a standalone hardware controller; there is currently no external app or software interaction required.
**Response:**  

## 5.3 Input / Output Map

| System Part | Type | What It Does |
| :--- | :--- | :--- |
| Input Signals | Input | Provides traffic data such as density, waiting time, priority, and special conditions for both roads. |
| Priority Calculator | Processing | Computes priority values using a weighted formula to decide which road should get preference. |
| Finite State Machine (FSM) | Control Logic | Controls traffic light states (Green, Yellow, Red) and manages switching between roads. |
| Timer | Processing | Ensures minimum, maximum, and yellow signal durations are maintained. |
| Clock Divider | Processing | Slows down the FPGA clock to a human-observable speed for traffic signal timing. |
| Output Logic | Output | Generates control signals for traffic lights based on current FSM state. |
| Traffic Lights (LEDs) | Output Hardware | Displays Red, Yellow, Green signals for both roads. |

---

# 6. System Design, Sketches and Visual Planning 

## 6.1 Concept Architecture/sketch/schematic

Add an early sketch of the full idea.

**Insert image below:**  
`[Upload image and link here]`

Example:

```md

```



## 6.2 Labeled Build Sketch/architecture/flow diagram/algorithm

Add a sketch with labels showing:

- structure,
- electronics placement,
- user touch points,
- moving parts,
- output elements.

**Insert image below:**  
`[Upload image and link here]`
<img width="1600" height="1200" alt="image" src="https://github.com/user-attachments/assets/95637f31-b4e7-4427-a9e1-4b63fbeb0ac5" />

## 6.3 Approximate Dimensions

| Dimension        | Value   |
| ---------------- | ------- |
| Length           | `16 cm` |
| Width            | `16 cm` |
| Height           | `8 cm`  |
| Estimated weight | `400 g` |

---

# 7. Electronics Planning

## 7.1 Electronics Used

| Component                 | Quantity | Purpose                               |
| ------------------------- | --------:| ------------------------------------- |
| `[FPGA Board (Spartan 7]` | `1`      | `[Main controller that implements the traffic logic and FSM]`                   |
---

## 7.2 Wiring Plan

The implementation utilizes separate dedicated LEDs for every signal to ensure clear visual feedback.

### Input Mapping
| Signal | Port Type | Hardware Component |
| :--- | :--- | :--- |
| clk | Input | Onboard 100 MHz Oscillator |
| reset | Input | Master Reset Push Button |
| emg_override | Input | Emergency Slide Switch |
| ped_button | Input | Pedestrian Request Push Button |
| D_A [3:0] | Input | 4 Slide Switches (Road A Density) |
| D_B [3:0] | Input | 4 Slide Switches (Road B Density) |
| T_A [3:0] | Input | 4 Slide Switches (Road A Wait Time) |
| T_B [3:0] | Input | 4 Slide Switches (Road B Wait Time) |

### Output Mapping (Dedicated LEDs)
| Signal | Color | Function |
| :--- | :--- | :--- |
| G_A | Green | Road A Go |
| Y_A | Yellow | Road A Transition |
| R_A | Red | Road A Stop |
| G_B | Green | Road B Go |
| Y_B | Yellow | Road B Transition |
| R_B | Red | Road B Stop |
| PED_WALK | Blue/White | Dedicated Pedestrian Walking Signal |

---

## Processing Logic

### 1. Priority Calculation
The controller calculates a score for each road using a weighted formula:
$$priority\_A = (w1 \cdot D\_A + w2 \cdot T\_A + w3 \cdot P\_A - w4 \cdot S\_A)$$
* **Weight Parameters:** w1=2, w2=1, w3=1, w4=1.
* **Logic:** Higher density and wait times increase the priority, while special restrictions reduce it.

**sample Response:**  
`The RASPI is connected to the motor driver (L298N) using four GPIO pins (18,19; 22,23) to control motor direction (IN1, IN2, IN3, IN4). Two PWM-capable pins (ENA and ENB; 25 and 26) are connected to control the speed of each motor.

The motors are connected to the output terminals of the motor driver. The motor driver is powered directly by the battery pack (higher voltage), while the ESP32 receives regulated 5V from the buck converter.

All components share a common ground to ensure stable operation. The projector and camera are connected to the laptop, which handles tracking and game logic separately.`

## 7.3 Circuit Diagram/architecture diagram

Insert a hand-drawn or software-made circuit diagram.

**Insert image below:**  
`[Upload image and link here]`
<img width="867" height="1156" alt="" src="" />


# 7.4. Power Plan

| Question         | Response                                                                                                                                          |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| Power source     | `Battery (Li-ion pack)`                                                                                                                           |
| Voltage required | `~6–8.4V for motors (via driver), stepped down to 5V for ESP32 (buck converter)`                                                                  |
| Current concerns | `Motors can draw high current under load, which may cause voltage drops affecting ESP32 and WiFi stability`                                       |
| Safety concerns  | `Avoid over-discharging Li-ion batteries, ensure proper voltage regulation, prevent short circuits, and secure wiring to avoid loose connections` |

---

# 8. Software Planning/

## 8.1 Software Tools

| Tool / Platform                | Purpose                                        |
| ------------------------------ | ---------------------------------------------- |
| `[MicroPython]`                | `Control ESP32`                                |
| `[Python/PyGame/OpenCV]`       | `Track markers, game logic, create projection` |
| `[Fusion/Blender/Illustrator]` | `[Prototyping structure]`                      |
|                                |                                                |

## 8.2 Software Logic/Algorithm

Describe what the code must do.

Include:

- startup behavior,
- input handling,
- sensor reading,
- decision logic,
- output behavior,
- communication logic,
- reset behavior.

**Response:**  
`

- **Sample Startup behavior:**  
  The Raspi/FPGA initializes motor pins, PWM control, and starts a WiFi access point with a web server. The laptop initializes camera input, tracking system, and projection mapping.
- **Input handling:**  
  Movement commands are received from the laptop (pygame sends http requests)
- **Sensor reading:**  
  The camera continuously captures frames, and OpenCV detects ArUco markers to determine the car’s position and orientation.
- **Decision logic:**  
  The system maps the car’s position into a virtual coordinate system and checks for nearby obstacles or collisions. If movement is valid, the command is allowed; if not, it is blocked or replaced with a feedback action (like a slight shake).
- **Output behavior:**  
  The ESP32 drives the motors using PWM signals to control speed and direction. The projector displays the updated game environment, including obstacles, targets, and feedback visuals.
- **Communication logic:**  
  The laptop sends HTTP requests (e.g., `/forward`, `/left`) to the ESP32 over WiFi. The ESP32 parses these commands and executes motor actions.
- **Reset behavior:**  
  If no command is received within a short timeout, the ESP32 stops the motors. The game resets when a level is completed or restarted.`

## 8.3 Code Flowchart

Insert a flowchart showing your code logic.

Suggested sequence:

- start,
- initialize,
- wait for input,
- read input,
- decision,
- trigger output,
- repeat or reset,
- error handling.

**Insert image below:**  
<img width="1600" height="1200" alt="image" src="" />
<img width="1600" height="1200" alt="image" src="" />




# 9. Bill of Materials

## 9.1 Full BOM

## Project Component List

| Item | Qty | In Kit? | Need to Buy? | Est. Cost | Material / Spec | Why This Choice? |
| :--- | :---: | :---: | :---: | :---: | :--- | :--- |
| **Spartan-7 FPGA Board** | 1 | Yes | No | $0 | Xilinx Spartan-7 (XC7S50), 100MHz clock | Required to compute priority score ($w_1D + w_2T + w_3P - w_4S$) in parallel for 4 lanes. |
| **USB Programming Cable** | 1 | Yes | No | $0 | USB Type-A to Micro-USB | To flash the bitstream via Vivado and power the board. |
| **On-board Slide Switches** | 2 | Yes | No | $0 | Built-in to Boolean Board | Used to simulate varying levels of Density (D) and trigger Emergency Override. |
| **On-board Push Button** | 1 | Yes | No | $0 | Built-in to Boolean Board | Used to trigger the Pedestrian Demand (P) variable. |
| **On-board RGB LEDs** | 5 | Yes | No | $0 | Built-in to Boolean Board | To visually represent the winning lane and the pedestrian signal. |## 9.2 Material Justification

Explain why you selected your main materials and components.

**Response:**  
## Hardware Design Rationale

> **Core Logic:** The **Real Digital Boolean Board (Spartan-7 FPGA)** was selected as the central processing unit because the new adaptive scheduling algorithm requires calculating multiple arithmetic equations ($w_1D + w_2T + w_3P - w_4S$) and comparing their results at the exact same time. 

### Why FPGA?
An FPGA's **parallel processing capabilities** handle this mathematical arbitration instantly and deterministically, providing a level of timing precision that sequential microcontrollers cannot match.

### Simulation & Interface
To keep the project strictly focused on digital logic design and to ensure a fail-safe testing environment, external environmental detectors were omitted. Instead, the algorithm's required variables are simulated via:

*   **Density ($D$), Pedestrian Demand ($P$), and Emergency Overrides:** Fed directly into the FPGA using the board's built-in **debounced push buttons** and **slide switches**.
*   **Visual Feedback:** The onboard **RGB LEDs** are utilized to display dynamic light transitions.

This integrated approach eliminates the need for external breadboarding and complex power routing, keeping the hardware footprint clean and reliable.


## 9.3 Items You chose

| Item                 | Why Needed               | Purchase Link | Latest Safe Date to Procure | Status       |
| -------------------- | ------------------------ | ------------- | --------------------------- | ------------ |
| `BO Motors + Wheels` | `Drive system for car`   | `robu.in`     | `15th April`                | `[Received]` |
| `Buck Converter`     | `Stable power for ESP32` | `local store` | `before testing`            | `[Received]` |
| `Li-ion Batteries`   | `Portable power`         | `local store` | `before testing`            | `Recieved`   |

## 9.4 Budget Summary

## Procurement & Availability

| Item | Why Needed | Purchase Link | Latest Safe Date | Status |
| :--- | :--- | :--- | :---: | :---: |
| **Spartan-7 Boolean Board** | Parallel computation of priority scores and physical I/O | Provided by Campus Lab | N/A | ✅ Available |
| **Micro-USB Cable** | Flashing bitstream from PC | Existing | N/A | ✅ Available |
| **PC with Vivado Suite** | Verilog synthesis and simulation | Existing | N/A | ✅ Available |

## 9.5 Budget Reflection
## Project Budget Overview

| Budget Item | Estimated Cost (₹) |
| :--- | :---: |
| Electronics | 0 |
| Mechanical parts | 0 |
| Fabrication materials | 0 |
| Purchased extras | 0 |
| Contingency | 0 |
| **Total** | **₹0** |

> **Note:** Since all primary components (FPGA board, cables, and software) are provided by the Campus Lab or are already owned, the current projected out-of-pocket expenditure for this project is zero.


If your cost is too high, what can be simplified, removed, substituted, or shared?

## Budget Summary & Hardware Efficiency

The project budget is successfully maintained at **zero**. By strategically mapping the advanced algorithm parameters—**Density**, **Wait Time**, and **Pedestrian Demand**—to the existing switches and internal timers of the Boolean Board, we eliminated the need to purchase any external detection modules or microcontrollers. 

### Key Efficiency Outcomes:
*   **Cost Minimization:** Total expenditure is ₹0 by leveraging campus resources.
*   **Resource Optimization:** Maximizes the utility of the Spartan-7's onboard resources (switches, buttons, and timers).
*   **Hardware Realization:** Achieves complex, adaptive traffic routing through mathematical arbitration rather than expensive external sensors.

This approach demonstrates that high-level adaptive systems can be effectively modeled and validated using foundational digital logic components.

# 10. Planning the Work

## 10.1 Team Working Agreement

## Team Organization & Workflow

*   **Task Division:** Tasks are divided based on technical strengths with intentional overlap for support.
    *   **Devyani:** Leads the system architecture, algorithm optimization, `.xdc` hardware constraints, and handles physical hardware connections. Actively co-codes and assists with integrating the logic blocks.
    *   **Anushree & Disha:** Lead the main Verilog implementation and Vivado synthesis.
    *   **Nidhi:** Drives the ideation phase, manages version control, and owns all project documentation.

*   **Decision Making:** 
    Architectural and algorithmic decisions are proposed by Devyani and finalized during ideation syncs guided by Nidhi. Code-level implementation decisions are managed jointly by Anushree, Disha, and Devyani.

*   **Progress Checks:** 
    The team uses the shared Git repository (managed by Nidhi) as the single source of truth. Progress is tracked via successful module commits and Vivado simulation passes.

*   **Handling Delays:** 
    *   *Technical Roadblocks:* If Vivado synthesis or timing constraints fail, Devyani, Anushree, and Disha will swarm the issue to debug the Verilog logic and connections. 
    *   *Administrative Roadblocks:* If documentation or presentation deliverables lag, team members will support Nidhi after their primary technical modules are complete.

*   **Documentation:** 
    Nidhi maintains the live project documentation and presentation (PPT), pulling technical details from the Git repository and Vivado reports generated by the coding team.

    
## 10.2 Task Breakdown

| Task ID | Task | Owner | Est. Hours | Deadline | Dependency | Status |
| :---: | :--- | :--- | :---: | :---: | :---: | :--- |
| **T1** | Ideation & Algorithm Finalization | Everyone | 2 | April 30 | None | Done |
| **T2** | Define System Architecture & Math Logic | Devyani | 3 | April 30 | T1 | Done |
| **T3** | Git Repository Setup | Nidhi | 1 | April 30 | None | Ongoing |
| **T4** | Main Verilog Coding (FSM & Submodules) | Anushree & Disha (assist: Devyani) | 6 | May 2 | T2 |  Ongoing |
| **T5** | Map .xdc Constraints & Hardware Connections | Devyani | 2 | May 2 | T2 | Ongoing |
| **T6** | Vivado Synthesis, Implementation & Testing | Anushree, Disha, & Devyani | 4 | May 2 | T4, T5 | Half-way |
| **T7** | Final Project Documentation & PPT | Nidhi | 4 | May 2 | T6 | Pending |


## 10.3 Responsibility Split

| Area | Main Owner | Support Owner |
| :--- | :--- | :--- |
| **Concept & Ideation** | All members | All Members |
| **Architecture & Algorithm sketching** | Devyani | Nidhi |
| **Coding (Verilog in Vivado)** | Anushree & Disha | Devyani |
| **Electronics (Hardware connections / .xdc)** | Devyani | Anushree |
| **Version Control (Git Repo)** | Nidhi | Disha |
| **Testing (Simulation & On-Board)** | Anushree & Disha | Devyani |
| **Documentation & PPT** | Nidhi | All Members |

# 11 hour Milestones

## 11.1 8-hour Plan(tentetively you may set)

### Bi Hour 1 — Plan and De-risk

Expected outcomes:

- [x] Idea finalized
- [x] Core interaction decided
- [x] Sketches made
- [x] BOM completed
- [x] Purchase needs identified
- [ ] Key uncertainty identified
- [x] Basic feasibility tested

### Bi Hour 2 — Build Subsystems

Expected outcomes:

- [x] Electronics tests completed
- [ ] CAD / structure planning completed
- [ ] App UI started if needed
- [x] Mechanical concept tested
- [x] Main subsystems partially working

### Bi Hour 3 — Integrate

Expected outcomes:

- [x] Physical body built
- [x] Electronics integrated
- [ ] Code connected to hardware
- [ ] App connected if required
- [x] First playable version exists

### Bi Hour 4 — Refine and Finish

Expected outcomes:

- [ ] Technical bugs reduced
- [ ] Playtesting completed
- [ ] Improvements made
- [ ] Documentation completed
- [ ] Final build ready

## 12.2  Update Log

| Days | Planned Goal | What Actually Happened | What Changed | Next Steps |
| :---: | :--- | :--- | :--- | :--- |
| **Day 1** | Setup environment, map hardware, and build a baseline traffic controller prototype. | Shreenidhi initialized the Git repo. Devyani mapped the basic `.xdc` file. Anushree and Disha successfully coded, synthesized, and flashed a normal round-robin FSM that included basic switch-based density logic. Displayed outputs on same-color LEDs. | Decided to build a simpler MVP first to guarantee a working project before tackling the complex mathematical arbiter. | **Tomorrow (Day 2):** Upgrade the FSM to the Weighted Priority Algorithm, add debounced pedestrian/emergency interrupts, and remap to RGB LEDs. |
| **Day 2** | Upgrade to Weighted Priority algorithm, add interrupts, and test. | *(To be filled tomorrow)* | *(To be filled tomorrow)* | *(To be filled tomorrow - Final Project Submission)* |

---

# 13. Risks and Unknowns

## 13.1 Risk Register

| Risk                                                            | Type         | Likelihood | Impact   | Mitigation Plan                                                                       | Owner                |
| --------------------------------------------------------------- | ------------ | ---------- | -------- | ------------------------------------------------------------------------------------- | -------------------- |
| WiFi connection between laptop and ESP32 becomes unstable       | `Technical`  | `Medium`   | `High`   | Keep ESP32 close, ensure stable power supply, reduce network load, add fail-safe stop | `[Gopal]`           |


## 13.2 Biggest Unknown Right Now

What is the single biggest uncertainty in your project at this stage?

**Response:**  


---

# 14. Testing 

## 14.1 Technical Testing Plan

| What Needs Testing     | How You Will Test It                                                                 | Success Condition                                                                                    |
| ---------------------- | ------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------- |
| `[Wifi connection]`    | `[Check if motor spins via app button]`                                              | `[Both motors accurately respond to wifi signals]`                                                   |
                       |
## 14.2 Testing and Debugging Log

| Date          | Problem Found                         | Type         | What You Tried                                | Result               | Next Action                                    |
| ------------- | ------------------------------------- | ------------ | --------------------------------------------- | -------------------- | ---------------------------------------------- |
| `18th April`  | `Car not balancing properly`          | `Mechanical` | `Add low-friction caster support to one side` | `Worked`             | `improve caster structure`                     |


## 14.3 Playtesting Notes

| Tester      | What They Did                        | What Confused Them                    | What They Enjoyed                         | What You Will Change                          |
| ----------- | ------------------------------------ | ------------------------------------- | ----------------------------------------- | --------------------------------------------- |
| `Gopal` | `Tried navigating through obstacles` | `Some obstacles ewren't clear enough` | `Liked projection + real car interaction` | `Add a slight red highlight around obstacles` |


---

# 15. Build Documentation

## 15.1 Fabrication Process(if any)

Describe how the project was physically made.

Include:

- cutting,
- 3D printing,
- assembly,
- fastening,
- wiring,
- finishing,
- revisions.

**Response:**  
`The fabrication process involved designing, manufacturing, assembling, and refining both the physical structure and electronic integration of the system.`

`Design (CAD Modeling):
The initial model was created using CAD software, where components were designed based on the actual dimensions of the electronic parts. This ensured accurate fitting and minimized errors during assembly.
Cutting (Laser Cutting):
The designed parts were fabricated using laser cutting techniques. Sheets were cut precisely according to the CAD model to create the structural base and mounts for components.`

`Components were fixed using adhesives and mechanical supports. Certain parts were intentionally kept modular (not permanently fixed) to allow easy replacement and modification of electronics.
Surface Finishing:
Some parts were sanded to smooth rough edges after cutting. Sawdust mixed with adhesive was used to fill gaps and uneven edges, improving structural finish. The final structure was then painted for better aesthetics and durability.`

`Environment Setup (Dark Room Fabrication):
To enhance projection visibility, a controlled dark environment was created using Z-boards, paper sheets, and bedsheets. This minimized external light interference and improved projection clarity.
Revisions and Iterations:
Multiple adjustments were made throughout the process, including refining alignment, improving structural stability, repositioning components, and optimizing the interaction between the physical car and projected environment.`

## 16 Build Photos

Add photos throughout the project.

Suggested images:

- early sketch,
- prototype,
- electronics testing,
- mechanism test,
- app screenshot,
- final build.
- <img width="960" height="1280" alt="WhatsApp Image 2026-04-24 at 9 46 02 AM (1)" src="https://github.com/user-attachments/assets/74baa570-5770-483e-be6d-d2f03386e37c" />





# 17. Final Outcome

## 17.1 Final Description

Describe the final version of your project.

**Response:**  


## 17.2 What Works Well



## 17.3 What Still Needs Improvement


## 17.4 What Changed From the Original Plan

How did the project change from the initial idea?

**Response:**  


---

# 18. Reflection

## 18.1 Team Reflection

What did your team do well?  
What slowed you down?  
How well did you manage time, tasks, and responsibilities?

**Response:**  


## 18.2 Technical Reflection

What did you learn about:

- electronics,
- coding,
- mechanisms,
- fabrication,
- integration?

**Response:**  


## 18.3 Design Reflection

What did you learn about:

- designing ,
- delight,
- clarity,
- physical interaction,
- understanding,
- iteration?

**Response:**  


## 18.4 If You Had One More hour

What would you improve next?

**Response:**  

` `

---

# 19. Final Submission Checklist

Before submission, confirm that:

- [x] Team details are complete
- [x] Project description is complete
- [x] Inspiration sources are included
- [x] Sketches are added
- [x] BOM is complete
- [x] Purchase list is complete
- [x] Budget summary is complete
- [x] Mechanical planning is documented if applicable
- [ ] App planning is documented if applicable
- [x] Code flowchart is added
- [x] Task breakdown is complete
- [x] Weekly logs are updated
- [x] Risk register is complete
- [x] Testing log is updated
- [x] Playtesting notes are included
- [x] Build photos are included
- [x] Final reflection is written
<img width="1131" height="1600" alt="image" src="" />

---


---



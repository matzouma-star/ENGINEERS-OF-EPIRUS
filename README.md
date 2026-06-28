# ENGINEERS-OF-EPIRUS
We are students from the 2nd Intercultural Junior High School of Ioannina, Greece,  competing in the Future Engineers competition. Through this project,  we develop our STEM skills, team spirit, and creativity, proudly representing our school and the historic region of Epirus
we are angelomenos theodoros and aggelina kontogiani we are two people who like to innovate to participate in many competions robotics.                                 
# Future Engineers - Engineers of Epirus 🤖🚗

> This repository contains the source code and design files of our autonomous vehicle for the **WRO Future Engineers** competition. Our robot is built using the **LEGO Spike Prime** platform and utilizes the **DFRobot HuskyLens** AI camera for navigation and obstacle avoidance.

---

## Criterion 1: Mobility & Chassis

### 1.1 Chassis Architecture & Design
Our robot is constructed using the **LEGO Education Spike Prime** core set. A four-wheel configuration based on automotive principles (**Ackermann steering**) was selected, providing high stability when navigating the track's corners.

* **Dimensions:** The chassis dimensions are **20 cm x 10 cm**, remaining strictly within the competition's regulation limits ($30 \times 20 \times 30$ cm).
* **Weight Distribution:** The *Spike Prime Hub* is positioned at the **rear** of the chassis, ensuring a low center of gravity to prevent any tipping over during sharp turns.

---

### 1.2 Drive Mechanism
The robot's propulsion is transmitted to the **rear wheels** via a **Spike Prime Medium Motor**.

* **Power Transmission:** Power is delivered **directly** from the motor to the wheels without intermediate gearing, effectively minimizing mechanical backlash.
* **Wheel Selection:** * At the **rear**, large *LEGO Technic* wheels (62.4 x 20 mm diameter) are utilized to provide the necessary traction (grip), preventing wheel spin and ensuring precise distance tracking via the built-in motor encoders.
  * At the **front**, medium *Spike Prime* wheels (56 × 14 mm dimensions) are implemented to achieve optimal agility and steering precision.

---

### 1.3 Steering Mechanism
For steering and navigation, a front-wheel steering mechanism was designed, controlled by a second **Spike Prime Medium Motor**.

> **Engineering Decision:** We chose *Ackermann steering* over a differential drive setup because it delivers a smoother and much more predictable trajectory through turns, drastically reducing wheel slippage.

* **Steering Mechanics:** The motor converts rotational movement into linear/lateral motion, moving a steering **linkage** that turns both front wheels simultaneously.
* **Steering Angle:** The maximum steering angle of the wheels is mechanically limited to **25°** to prevent motor stalling and loss of vehicle control.
* **Alignment:** A hardware **calibration** routine is executed upon startup, forcing the motor to find its exact "center" (absolute straight line) before the competitive round begins.
* 
## Criterion 2: Sensors & Electronics

### 2.1 Sensor Selection & Mission Profile
For autonomous navigation and precise obstacle avoidance on the track, the vehicle is equipped with the following sensors:

* **HuskyLens Vision Sensor (AI Camera):** This serves as the primary sensor for obstacle avoidance. The HuskyLens is mounted at the **front** of the robot at an optimal height to ensure a clear line of sight to both red and green obstacles.
  * **AI Mode:** We utilize the **"Object Classification"** mode. The camera is pre-trained to recognize:
    * Red obstacles
    * Green obstacles
  * **Purpose:** The HuskyLens transmits real-time data to the Spike Prime Hub regarding the type (red/green) and position (X/Y coordinates) of the nearest obstacle. The algorithm processes this telemetry to decide whether to steer right (to avoid a green obstacle) or left (to avoid a red obstacle), according to the competition rules.

> **Engineering Decision: Object Classification vs. Color Recognition**
> We chose *Object Classification* over simple color recognition to guarantee the robot's robustness. Standard color recognition is highly vulnerable to changes in ambient light, which can cause false positives due to shadows or external optical interference. By training the HuskyLens with Object Classification, the AI model combines shape, volume, and color features. This makes our autonomous driving resilient and dependable under any lighting conditions on the track.

* **Spike Prime Ultrasonic Sensor:** Mounted **laterally on the right side** of the robot. It is used to measure the exact distance from the track walls, helping the vehicle maintain a stable trajectory and avoid collisions.
* **Spike Prime Color Sensor:** Positioned **low at the front, facing the ground**. It is used to detect the blue and orange lines on the track surface.
* **Inertial Measurement Unit (Internal IMU / Gyro):** We utilize the built-in 6-axis gyroscopic sensor of the Spike Prime Hub. It is responsible for tracking the robot’s heading angle with degree-level precision, ensuring the vehicle executes exact $90^{\circ}$ or $180^{\circ}$ turns and maintains a straight course.

---

### 2.2 Electronic Connectivity & Custom Wiring
The integration between the HuskyLens and the Spike Prime Hub was accomplished via a **custom wire harness** designed and fabricated by our team, eliminating the need for any external electronic converters.

* **Technical Implementation:** The HuskyLens is configured to communicate via the **UART (Serial)** protocol. We manufactured a 4-wire cable, mapping the HuskyLens pins directly to the Spike Prime connector as follows:
  * **VCC (Power):** Draws power directly from the Hub to the camera.
  * **GND (Ground):** Establishes a common ground for the circuit.
  * **RX / TX (Data):** Crosses the Receive (RX) and Transmit (TX) data lines, allowing the Spike Prime Hub to seamlessly ingest obstacle coordinates from the HuskyLens.
* **Advantage:** This direct-wiring solution reduced overall vehicle weight, eliminated the dependency on a secondary battery pack, and guaranteed near-zero data latency for the AI vision feedback loop.

#### Port Mapping (Updated)

| Component | Port | Function |
| :--- | :---: | :--- |
| **Rear Motor (Large)** | **D** | Vehicle Propulsion (Drive) |
| **Front Motor (Medium)** | **C** | Steering Control (Ackermann) |
| **HuskyLens Vision Sensor** | **A** | Red/Green Obstacle Recognition |
| **Ultrasonic Sensor** | **B** | Wall Distance Measurement |
| **Color Sensor** | **E** | Track Floor Line Detection |

#### Cable Management
All wiring, including the custom HuskyLens serial cable, is neatly routed along the **top section of the chassis** and secured using zip-ties. This prevent cables from tangling with the wheels or mechanical linkages, while reducing electronic noise and accidental disconnections during the race.

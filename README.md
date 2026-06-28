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

# ENGINEERS-OF-EPIRUS
We are students from the 2nd Intercultural Junior High School of Ioannina, Greece,  competing in the Future Engineers competition. Through this project,  we develop our STEM skills, team spirit, and creativity, proudly representing our school and the historic region of Epirus
we are angelomenos theodoros and aggelina kontogiani we are two people who like to innovate to participate in many competions robotics.                                 
# Future Engineers - Engineers of Epirus 🤖🚗

> This repository contains the source code and design files of our autonomous vehicle for the **WRO Future Engineers** competition. Our robot is built using the **LEGO Spike Prime** platform and utilizes the **DFRobot HuskyLens** AI camera for navigation and obstacle avoidance.

---

## 📌 Features

* **Autonomous Navigation:** Precise movement and steering control using Spike Prime motors.
* **AI Vision (HuskyLens):** Real-time color recognition, lane tracking, and pre-trained object detection.
* **Dual-Phase Architecture:** 
  * **Phase 1 (Open Challenge):** Implemented using visual programming (Word Blocks) for consistent lane tracking.
  * **Phase 2 (Obstacle Challenge):** Implemented using advanced Python for dynamic decision-making and obstacle avoidance.

---

## ⚙️ Installation

### Prerequisites
To open and run this project, you will need:
* **LEGO Education SPIKE App** (Version 3.x or newer).
* **HuskyLens Camera** configured to the correct communication protocol (I2C or Serial at 115200 baud).
* Any required custom Python libraries for Spike-HuskyLens communication.

### Steps
1. Clone this repository:
   ```bash
   git clone https://github.com[your-username]/[your-repo-name].git
   ```
2. **For Blocks:** Open the SPIKE App, select `Import File`, and load the `.llsp` file from the blocks folder.
3. **For Python:** Create a new Python Project in the SPIKE App and paste the code from the `.py` file in the python folder.

---

## 🚀 Usage

### 🧩 Part 1: Open Challenge (Word Blocks)
In the first part, the vehicle completes the 3 required laps on the open track. The block-based program guides the robot by keeping it within the traffic lanes using the camera.
* **Main Focus:** Line tracking and turn counting.

### 🐍 Part 2: Obstacle Challenge (Python)
In the second part, the robot must safely avoid red and green obstacle pillars. The Python script continuously requests block data (X, Y coordinates, Width, Height) from the HuskyLens via the Spike hub's port.

```python
# Sample code structure for Spike Prime & HuskyLens communication
import hub
import time

def check_obstacles():
    # Code to read data packets from HuskyLens
    # If Red Obstacle detected -> Turn Left
    # If Green Obstacle detected -> Turn Right
    pass
```

### 📸 Gallery & Robot Design
![Our Robot Design]([image_url_or_path])
*Add a picture of your robot or a flowchart of your strategy here.*

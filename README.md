# IMU Simulation With OpenSim

This repository provides a full workflow for processing IMU (Inertial Measurement Unit) data, calibrating sensor orientations, and running OpenSim scripts to estimate joint kinematics. The pipeline is implemented in Python and uses OpenSim’s scripting interface for model-based motion analysis.

---

## 📦 Project Overview

The goal of this project is to read raw IMU data recorded from multiple sensors, perform proper calibration, assign each sensor to a specific body segment, configure the simulation, and finally run joint-angle estimation using OpenSim.

The project includes:

- Scripts for reading and formatting IMU measurements  
- A configurable calibration system  
- Automated mapping between sensors and model segments  
- A Python-based OpenSim pipeline  
- A main execution script (`main.py`) to run the full workflow

---

## 📁 Folder Structure

IMU_Simulation_OpenSim/

│

├── src/

| ├── Data/ # Place IMU recordings & calibration files here

│ ├── main.py # Main execution file

│ ├── config.py # Central configuration file

│ ├── data.py # Creates a suitable dataframe from IMU data

│ └── orientation/ # Creates orientation.sto + orientation_calib.sto files 

│

└── README.md
---

## 🧭 Workflow Summary

Below is a clear overview based on the provided project and attached instructions.

---

### 1. Perform Sensor Calibration

Place all IMU sensors flat on a table, aligned in a single direction, and record **several seconds** of data. These samples will be used to compute calibration offsets for each sensor.

> Sensors with six degrees of freedom perform better during this step.

Store the calibration recordings in the `Data` directory.

---

### 2. Collect Motion Data

Attach each sensor to the corresponding body segment.

Important notes:

- Record the identification number of each sensor  
- Record the body segment each sensor is attached to  
- Ensure all sensors are oriented consistently when mounted(sensor alignment on the body should be the same as you did in the calibration section)  

When recording is complete, place the raw data inside the `Data` directory.

---

### 3. Configure the Project

Open the project in an IDE such as VS Code or PyCharm.

Navigate to:

│ ├── src/config.py

Modify this file to match your setup.  
This file controls:

- Calibration file paths  
- Raw IMU data paths  
- Sensor-to-segment mapping  
- The joint angles you want to outputs

---

### 4. Define Sensor–Segment Mapping

Inside `config.py`, specify:

- Sensor IDs  
- Corresponding body segments  
- Any necessary orientation corrections  

This mapping ensures OpenSim interprets the IMU data correctly.

---

### 5. Select Desired Joint Angles

Some joint-angle computations may be commented out.  
Uncomment only the ones you want to process to improve efficiency.

---

### 6. Run the Full Pipeline

To run the entire workflow:

python src/main.py

Before running, make sure to activate the virtual environment that contains _requirements.txt_ libraries.

---

## 🛠 Requirements

- Python 3.x  
- OpenSim software
- Opensim python library
- Standard scientific Python libraries (NumPy, Pandas and scipy)  
- Several seconds of calibrated IMU dataset
- Raw IMU data

## 📬 Contact

For questions or suggestions, please open an issue or contact me via my email: reza.firouzii.2000@gmail.com

# Internship-task-1

The system uses an ESP32 with FreeRTOS to concurrently monitor multiple health and environmental parameters. Each sensor is implemented as an independent task to ensure real-time performance and system stability. Sensor data is processed, validated, and transmitted to a dashboard that provides real-time visualization, alerts, and role-based views for patients and facility operators. Simulation is performed using Wokwi with virtual sliders and software-generated sensor values.

**Step 1: System Setup :**- An ESP32 microcontroller is used as the central controller. FreeRTOS is enabled to allow multiple health parameters to be monitored simultaneously using independent tasks.

**Step 2: Sensor Simulation & Data Acquisition:-** Health and environmental parameters are either:
Simulated in Wokwi (using random() and slider inputs), or Read from real sensors in hardware implementation.

Monitored parameters:Heart Rate (BPM), SpO₂(%) ,Blood Pressure (Systolic / Diastolic) ,ECG Signal ,Gas / Air Quality level

**Step 3: FreeRTOS Task Execution :-** Each parameter runs in a separate FreeRTOS task, ensuring:
🔹Concurrent execution
🔹No blocking or delay conflicts
🔹Stable system performance
🔹Mutex/queues are used to safely share data between tasks.

**Step 4: Data Processing & Validation**
Sensor values are: Filtered or range-checked,Compared against safe thresholds,Marked as normal or abnormal
This logic ensures only meaningful data is sent to the dashboard.

**Step 5: Data Transmission**
Processed data is: Displayed on Serial Monitor (Wokwi)
Sent to the dashboard (IoT platform / web UI)
Updated in real time without affecting sensor tasks

🔹 Role of Each Component (Quick Table)
Component	Function
ESP32	Main controller, runs FreeRTOS
Heart Rate Task	Monitors BPM
SpO₂ Task	Measures oxygen saturation
BP Task	Simulates blood pressure
ECG Task	Generates ECG signal values
Gas Sensor	Monitors air quality
Slider (Wokwi)	Manually simulates sensor variation
Mutex / Queue	Prevents data collision
Dashboard	Visualizes and alerts health data

🔹 How the Dashboard Works (Simple Explanation)
Receives data from ESP32 tasks (via serial / IoT protocol)

Separates views based on user role:
Patient Dashboard: Live vitals
Facility Dashboard: Alerts & trends
Updates values in real time
Triggers alerts when thresholds are crossed
Displays status (Normal / Warning / Critical)

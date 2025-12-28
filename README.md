# Inverted-pendulum-on-a-cart-control-system-project
📖 Overview
The Inverted Pendulum on a Cart is a classic control systems problem that demonstrates the stabilization of an inherently unstable nonlinear system using feedback control.
In this project, a pendulum mounted on a moving cart is actively balanced in the upright position by controlling the cart’s motion using sensor feedback and a closed-loop control algorithm.
This project combines control theory, embedded systems, and real-time hardware implementation.

🎯 Objectives
1. To model and understand the dynamics of an inverted pendulum system
2. To design and implement a real-time feedback controller
3. To stabilize the pendulum in the upright position
4. To validate the controller using both simulation and physical hardware

🧠 Principle of Operation
The inverted pendulum is open-loop unstable—any small disturbance causes it to fall.
A feedback controller continuously measures the pendulum angle and applies corrective motion to the cart so that the pendulum remains balanced.

The system follows this loop:

1.Measure pendulum angle using an IMU sensor
2.Compute error from the desired upright position
3.Apply control law to calculate motor command
4.Drive motors to move the cart and correct the error
5.This closed-loop process runs continuously in real time.
   
⚙️ System Components

Hardware:
1. Arduino Uno
2. MPU6050 (6-DOF IMU)
3. L298 Motor Driver
4. DC BO Motors (~200 RPM)
5. Wheels + Cart chassis
6. Pendulum rod (16 cm, 85 g)
7. 11.1 V Li-ion/LiPo Battery
   
Software:
1. Arduino IDE
2. MPU6050 library
3. Embedded C/C++
   
🧠 Control System Explanation

The inverted pendulum is an open-loop unstable system.
A feedback controller is used to stabilize it.

States considered:

Pendulum angle (θ)

Angular velocity (θ̇)

Control law (PD / simplified LQR):

𝑢 = 𝐾𝑝 𝜃 + 𝐾𝑑 𝜃˙

Where:

θ = pendulum angle error

θ˙ = angular velocity

𝑢 = motor PWM command

🧩 Control System Block Diagram
Pendulum → MPU6050 → Angle Estimation → Controller → Motor Driver → Cart → Pendulum
        ↑———————————————————— Feedback ————————————————————↑


(See /docs/block_diagram.png)

🔧 MPU6050 Mounting & Calibration

MPU mounted on pendulum rod

Axis alignment:

Rotation axis: Z-axis

Forward direction: Y-axis

Upright position calibrated as 0° reference

Accelerometer + Gyroscope fused using complementary filtering

🔌 Wiring Connections

MPU6050:

MPU6050	- Arduino

VCC	- 5V

GND	- GND

SDA	- A4

SCL	- A5

Motor Driver (L298):

Signal - Arduino

ENA	- 9

IN1	- 6

IN2	- 7

ENB	- 10

IN3	- 4

IN4	- 5

📈 Results & Observations
1. System can recover from small disturbances
2. High friction improves stability
3. Motor lag limits fast response
4. L298 driver causes voltage drop
5. Reaction speed is the primary bottleneck
   
⚠️ Limitations
1. L298 driver inefficiency
2. DC motor torque limitations
3. No wheel encoders used
4. Sensor noise at high frequencies
   
🚀 Future Improvements
1. Replace L298 with TB6612FNG / BTS7960
2. Use higher torque motors
3. Add wheel encoders
4. Full-state LQR implementation
5. Kalman filtering
   
🧪 Learning Outcomes
1. Practical control system implementation
2. Sensor fusion challenges
3. Real-world limitations vs theory
4. Embedded real-time control

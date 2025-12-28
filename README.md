# Inverted-pendulum-on-a-cart-control-system-project
📖 Overview
This project implements an inverted pendulum on a cart system, a classic unstable control problem, using an Arduino Uno, MPU6050 IMU, and DC motors driven by L298.
The objective is to stabilize the pendulum in the upright position using feedback control (PD / LQR-inspired control).

🎯 Objectives
1. Measure pendulum angle using MPU6050
2. Stabilize the pendulum at the upright position
3. Implement real-time closed-loop control
4. Study limitations of low-cost hardware in fast control systems
   
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

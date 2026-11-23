# Makara AUV — ROS 2 Autonomy & Control Stack (SAUVC 2026)

![ROS 2 Humble](https://img.shields.io/badge/ROS_2-Humble-22314E?style=for-the-badge&logo=ros&logoColor=white)
![C++](https://img.shields.io/badge/C++-17-00599C?style=for-the-badge&logo=cplusplus&logoColor=white)
![Python](https://img.shields.io/badge/Python-3.10-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Stonefish](https://img.shields.io/badge/Sim-Stonefish_%26_Gazebo-3fb950?style=for-the-badge)

Official ROS 2 workspace for **Makara**, Team Tiburon's competition Autonomous Underwater Vehicle (NIT Rourkela) built for **SAUVC 2026**.

<p align="center">
  <img src="assets/makara_demo.gif" alt="Makara AUV Simulation & Thruster Allocation Demo" width="820"/>
</p>

## System Architecture

```
Sensors (IMU + Depth + Camera + DVL)
        │
        ▼
┌───────────────────────────────┐
│  State Estimation & EKF       │  Unified 6-DOF pose & velocity estimate
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│  Mission Planner & Vision     │  Gate detection, flare tracking, buoy alignment
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│  PID / 6-DOF -> 8-Thruster    │  Thruster allocation matrix -> STM32 / Pico PWM
└───────────────────────────────┘
```

## Key Capabilities
- **6-DOF Navigation & Control:** Surge, sway, heave, roll, pitch, and yaw PID control mapped to an 8-thruster vectored configuration.
- **Sensor Fusion:** Combines IMU orientation, pressure-sensor depth, and vision estimates for stable underwater tracking.
- **Underwater Computer Vision:** Real-time gate, flare, and target detection integrated directly into the ROS 2 control loop.
- **Sim-to-Real Validation:** Validated end-to-end in Stonefish/Gazebo underwater physics simulations and real pool trials.

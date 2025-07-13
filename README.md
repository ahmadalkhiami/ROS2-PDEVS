# ROS2-PDEVS

This repository contains a PythonPDEVS model of a ROS 2 system. The simulation is structured in layers (Application → `rclcpp` → `rcl` → `rmw`) so you can test ROS‑style publishers, subscribers, timers and services without deploying a full ROS 2 environment.

## Requirements
- Python 3.8+
- [PyPDEVS](https://github.com/INTO-CPS-Association/PyPDEVS) installed in your Python environment.

Install dependencies with:
```bash
pip install PyPDEVS
```
If `PyPDEVS` is not available via `pip`, install it from the official repository.

## Running the simulation
Execute the main model:
```bash
python ros2_pdevs_model.py
```
The simulation runs for a few seconds, saves traces in `ros2_traces.csv` and prints a brief analysis of the generated events.

## Customising the model
Edit `ros2_pdevs_model.py` to add or remove publishers, subscribers, timers, and services. QoS policies are defined via the `QoSProfile` dataclass. You can modify the profiles or add new ones to match your application.

## Analysis output
After simulation the `analyze_results` function counts events such as `rmw_publish` and `rmw_take` to give insight into end‑to‑end latencies and callback behaviour. These metrics can be used to spot bottlenecks or timing issues before porting code to a real ROS 2 system.

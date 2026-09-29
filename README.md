# ImpactIQ

> Model-car impact telemetry with an Arduino Uno, MPU-6500, a live dashboard, and a SOLIDWORKS prototype.

**Live dashboard:** [impact-f1tech.vercel.app/dashboard](https://impact-f1tech.vercel.app/dashboard/)

ImpactIQ is a model-car telemetry prototype. A sensor mounted on the car detects a tap or sudden movement, then the dashboard shows the acceleration reading, calibrated direction, recent impact history, and a 3D model of the car.

## What it demonstrates

- Arduino Uno + MPU-6500 impact detection
- Accelerometer sampling at about 1,000 readings per second through the MPU FIFO
- Serial event output: `IMPACT,DIRECTION,Ax,Ay,Az,TotalG`
- Live dashboard with acceleration, peak readings, direction, and interactive 3D view
- A SOLIDWORKS upper-right upright prototype and exported node-level stress data

## Run the project yourself

The complete project source is in [**ImpactIQ-source.zip**](./ImpactIQ-source.zip).

1. Download and unzip the file.
2. Open a terminal in the extracted `FormulaTech-main` folder.
3. Create an environment and install the dependencies:

   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   pip install -r requirements.txt
   ```

4. Start the backend:

   ```bash
   python -m uvicorn backend.app:app --host 0.0.0.0 --port 8000
   ```

5. Open `dashboard/index.html` in Chrome or Edge. To use a real Arduino, upload `arduino/impact_imu.ino`, close Arduino IDE Serial Monitor, then choose **Connect sensor** in the dashboard.

## Hardware

| Part | Purpose |
| --- | --- |
| Arduino Uno | Reads and sends sensor data |
| MPU-6500 | Measures acceleration on three axes |
| Model car + breadboard | Physical demo platform |

The calibrated demo orientation is: **Y− = front, Y+ = back, X+ = left, X− = right.**

## Current limits

This is a prototype, not a vehicle safety system. The sensor measures acceleration at its own mounting point. A value in g does not automatically equal force in Newtons, and the current SolidWorks work covers only the upper-right component. The project cannot yet identify the exact component struck or confirm damage.

## Next steps

- Secure the sensor to a moving model car and collect repeatable impact tests.
- Build validated simulation cases for more components and impact directions.
- Match live sensor events to the closest validated simulation case.
- Expand the 3D model and explore separate telemetry inputs such as track position and weather.

## Team project

Built for a Formula Tech team project. The public dashboard is hosted at the link above.

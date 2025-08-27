# Predictive Maintenance: Synthetic Data Generation for Motor Failure Analysis

## Project Overview

This project demonstrates an advanced data science workflow for predictive maintenance, focusing on the generation of high-quality, synthetic time-series data to simulate motor failure. The goal was to create a realistic dataset that could be used to train a machine learning model to forecast mechanical failures based on vibration data.

This project was completed for a private client and, as such, the source code and data are not publicly available. The following sections describe the methodology and showcase the final visual deliverables.

---
## The Challenge: No Failure Data

The primary challenge was that the client's original dataset, containing over 250,000 rows of real-world sensor readings, captured only normal motor operations. Without any examples of a motor failing, it's impossible to train a model to predict such an event. The core of this project was to solve this "no-fault data" problem by fabricating a realistic failure scenario based on detailed client feedback.

---
## Methodology

The project was executed in a multi-step process to ensure the final synthetic data was both realistic and met the client's specific engineering requirements.

1.  **Baseline Analysis:** The original dataset was analyzed to establish the statistical properties of a "healthy" motor.
2.  **Advanced Synthetic Data Generation:** A new, 120,000-row dataset was programmatically generated. This involved creating a full **"Normal -> Failure -> Recovery"** cycle, injecting **early-stage micro-faults**, and using a **non-linear, erratic failure ramp**.
3.  **Visualization:** A series of professional graphs were created to visualize the final dataset, adhering to specific client requirements for titles, axis labels, and annotations.

---
## Final Deliverables & Visual Results

The final delivery included the synthetic vibration dataset and a series of detailed graphs that addressed all client feedback.

#### 1. Acceleration Analysis
This graph provides a high-level overview of the entire simulated event, showing the motor's vibration as it moves from a healthy state, through a failure, and back to a normal state.

**Full Cycle Acceleration Graph**
![Full Cycle Acceleration Graph](full_cycle_acceleration.png)

#### 2. Vibration Velocity (RMS) Analysis
This graph shows the intensity (RMS) of the vibration. The red dotted line represents the "Alarm Threshold," clearly showing the point where the motor's condition becomes critical.

**RMS Velocity with Alarm Threshold**
![RMS Velocity with Alarm Threshold](rms_velocity_alarm_threshold.png)

#### 3. FFT Spectrum Analysis
This graph provides a deeper analysis by showing the specific frequencies of the vibration. The plot clearly shows the emergence of new "fault frequencies" during the failure event.

**FFT Spectrum Analysis**
![FFT Spectrum Analysis](fft_spectrum_analysis.png)

#### 4. Separate Phase Analysis
This final graph was created to address a specific client request to view the failure phase separately for a more granular analysis.

**Failure Phase Acceleration**
![Failure phase acceleration](failure_phase_acceleration.png)

---
## Technologies Used

-   **Language:** Python
-   **Libraries:**
    -   Pandas & NumPy (for data manipulation and generation)
    -   Matplotlib & Seaborn (for visualization)
    -   SciPy (for FFT and signal processing)
-   **Techniques:** Synthetic Data Generation, Time-Series Analysis, Signal Processing, Anomaly Detection.
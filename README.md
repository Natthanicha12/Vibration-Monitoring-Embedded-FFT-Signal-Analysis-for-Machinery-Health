# Condition-Based Maintenance (CBM)  
**🎯 Objective**

The objective of this project is to develop a **Condition-Based Maintenance (CBM) sensor node** for machine health monitoring.

This system focuses on vibration analysis to detect abnormalities and assess machine condition in real time.

**📤 Expected Outputs**
The system provides two main outputs:

1.  **Dominant Frequency (Hz)**
    -   Used to identify the source of machine abnormalities.
    -   By analyzing the vibration frequency spectrum (FFT), specific fault types (e.g., imbalance, misalignment, looseness, bearing defects) can be detected based on their characteristic frequencies.
        
2.  **Velocity RMS (mm/s)**
    -   Used to evaluate overall machine condition.
    -   The RMS velocity value is compared with the vibration severity limits defined in **ISO 10816-3**.
    -   This allows classification of machine health into acceptable or critical operating zones.

# Technical Knowledge and Methods

### 🔍 Dominant Frequency (Hz)

The following signal processing techniques are used to extract the dominant frequency:
-   **Fast Fourier Transform (FFT)**  
    Used to transform the vibration signal from the time domain into the frequency domain for spectral analysis.
-   **Hanning Window**  
    Applied before performing FFT to reduce spectral leakage and improve frequency resolution accuracy.
-   **Low-Pass Filter (LPF)**  
    Implemented to reduce the impact of aliasing effects and suppress high-frequency noise beyond the Nyquist frequency.
-   **Stochastic Spectrum Estimator**  
    Used to reduce random noise and improve the stability and reliability of the frequency spectrum estimation.
    
### 📊 Velocity RMS (VRMS)

The following techniques are used to accurately estimate vibration velocity RMS:
-   **Quadratic Interpolation of Spectral Peaks**  
    Applied to refine the peak frequency estimation from the FFT spectrum.  
    This improves frequency accuracy and allows more precise VRMS calculation at the dominant frequency.
-   **Second-Order Polynomial Regression (Calibration)**  
    Used for sensor calibration to improve measurement accuracy and compensate for system nonlinearities.

## 🔋 Low Power Mode

To optimize power consumption for edge or IoT applications:

-   The user can define a vibration threshold to control the operating state:
    
    -   **Active Mode** – When vibration exceeds the defined threshold
    -   **Inactive Mode (Low Power Mode)** – When vibration remains below the threshold
        
-   **Interrupt-based Wake-Up**  
    An interrupt is triggered automatically when vibration exceeds the threshold, allowing the system to switch from low power mode to active processing.
    

## ⚙️ Additional Functional Features

**1️⃣ Offset Mode**
Allows the user to compensate for static acceleration (e.g., gravity) at a specific installation orientation.  
This improves measurement accuracy by removing gravitational bias from the vibration signal.

**2️⃣ Wake-Up Mode**
Forces the sensor node to operate immediately, even if the vibration level is below the predefined threshold.  
Useful for diagnostics or manual inspection.

**3️⃣ Train Function**
Temporarily increases measurement precision and resolution during a selected time interval.  
This mode enhances data quality for calibration, testing, or detailed signal analysis.

## As I co-developed this project with my team member, the section I worked on can be reviewed 
-> Vibration_LoRa/Vibration_LoRa/STM32CubeIDE/Application/Primus/Interface/Inc/Sensor.h
-> Vibration_LoRa/Vibration_LoRa/STM32CubeIDE/Application/Primus/Interface/Src/Sensor.c
-> Vibration_LoRa/Vibration_LoRa/STM32CubeIDE/Application/Primus/Application.c

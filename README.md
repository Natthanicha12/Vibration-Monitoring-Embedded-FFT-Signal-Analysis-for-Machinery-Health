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

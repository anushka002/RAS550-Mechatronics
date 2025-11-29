# EGR 550: Mechatronic Systems (Fall 2025 C)
## Lab 08 – Temperature Signal Filtering Using MATLAB and Simulink

### Description
This lab focuses on developing and implementing a **digital filter** in Simulink to smooth the temperature data collected from previous experiments. A higher-order **low-pass filter** is designed in MATLAB with a sampling time of **0.5 seconds** to attenuate measurement noise and improve signal quality. The filtered data allows for clearer observation of system behavior and more reliable control performance in future applications.

---

### Objectives
1. Utilize temperature data recorded from previous labs as the input signal for filtering.  
2. Design a higher-order low-pass filter in MATLAB with a specified sampling time of **0.5 s**.  
3. Implement the designed filter in Simulink to process and smooth the temperature data.  
4. Generate and analyze the **Bode plot** of the designed filter to evaluate its frequency response and filtering characteristics.  

---

### Expected Outcome
By the end of this lab, students will gain hands-on experience in digital filter design and implementation using MATLAB and Simulink. The resulting filtered temperature signal should exhibit reduced noise, smoother trends, and improved suitability for closed-loop control or further data analysis.

---

### Description
This supplementary task focuses on using **digital filtering** techniques to smooth the noisy temperature data collected from the thermal system (Heater 1) during the step response experiment (Lab 05). The raw temperature data contains high-frequency noise that can negatively affect system identification and controller performance. A **Lowpass Finite Impulse Response (FIR) filter** was designed in MATLAB to effectively attenuate this noise while preserving the system's underlying thermal dynamics.

---

### Objectives
1. Load and analyze the raw temperature data collected from the previous lab.
2. Design a **high-order digital Lowpass Filter** using MATLAB's `filterBuilder` tool.
3. Apply the designed filter to the raw temperature data to generate a **smoothed signal**.
4. Visualize and compare the **original** and **filtered** temperature data.
5. Provide the **Bode Diagram (frequency response)** of the designed filter.

---

### Filter Design and Implementation

#### Step 1: Data Preparation and Sampling Rate
* **Data Source:** `heater_data_plot3-2.xlsx` (containing time and temperature columns).
* **Sampling Interval ($\Delta t$):** 0.5 seconds.
* **Input Sample Rate ($F_s$):** $1 / \Delta t = 1 / 0.5 = 2.0 \text{ Hz}$.

#### Step 2: Lowpass Filter Specifications
The filter was designed using the **`filterBuilder`** tool with the following specifications:

| Specification | Value | Type |
|:--------------|:------|:-----|
| Impulse Response | FIR | Finite Impulse Response |
| Filter Type | Single-rate | |
| Design Method | Equiripple | Ensures uniform ripple in pass/stop bands |
| **Passband Frequency** | $\mathbf{0.01 \text{ Hz}}$ | Frequency below which signals pass with minimal attenuation |
| **Stopband Frequency** | $\mathbf{0.05 \text{ Hz}}$ | Frequency above which signals are heavily attenuated |
| Passband Ripple | $0.1 \text{ dB}$ | Maximum allowed ripple in the passband |
| Stopband Attenuation | $20 \text{ dB}$ | Minimum required attenuation in the stopband |
<img width="565" height="661" alt="image" src="https://github.com/user-attachments/assets/ba312f26-b741-467e-840b-5fc593bfd61c" />

#### Step 3: Filtering Command
The filtering was performed in MATLAB using the `filter` command. To filter the temperature data correctly, the DC offset (initial temperature/ambient temperature) was removed before filtering and re-added afterward.

```matlab
% Read data
[data] = xlsread('heater_data_plot3-2.xlsx');
time=data(:,1);
temp=data(:,2);

% Filter the data, accounting for DC offset (e.g., assuming DC offset is 24)
y2=filter(Hlp,temp-24);

% Plot Original vs. Filtered Data
plot(time,temp,time,y2+24); 
title("Temperature Data Analysis"); 
legend("Original Data (Blue)", "Filtered Data (Red)");
```

### Results and Analysis

#### Filter Performance
The designed Lowpass FIR filter successfully smoothed the temperature data. The comparison plot clearly illustrates the effectiveness of the filtering .

* **Original Data (Blue):** Shows noticeable high-frequency noise, especially in the steady-state regions and during the transient cooling phase.
* **Filtered Data (Red):** The red line closely follows the general trend of the blue line but is significantly smoother. This indicates that the high-frequency noise has been effectively removed without distorting the underlying thermal dynamics of the system. This smoothed data is much better suited for accurate system identification and subsequent controller design.
<img width="452" height="339" alt="image" src="https://github.com/user-attachments/assets/e615f695-9a8c-4403-a1fd-6c332468d52d" />


#### Filter Frequency Response (Bode Diagram)
The Bode Diagram (frequency response) of the designed filter confirms its lowpass characteristics:

* Frequencies below $0.01 \text{ Hz}$ are passed (Passband).
* Frequencies above $0.05 \text{ Hz}$ are attenuated by at least $20 \text{ dB}$ (Stopband).

<img width="1202" height="832" alt="image" src="https://github.com/user-attachments/assets/1f58c34f-7469-4b96-a1f0-4d21da0aa29d" />


---

### Key Learning Outcomes
* Understood the necessity of **data filtering** to reduce high-frequency measurement noise.
* Designed a **Lowpass FIR filter** using specified frequency and magnitude parameters.
* Successfully applied the digital filter to time-series data using the **MATLAB `filter` function**.
* Observed the significant improvement in signal quality, making the temperature data more reliable for modeling.

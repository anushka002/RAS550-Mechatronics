# EGR 550: Mechatronic Systems (Fall 2025 C)  
## Lab 02 – Open Loop Velocity Control of a Motor  

### Description  
This lab focuses on **open-loop velocity control** of a DC motor using **PWM (Pulse Width Modulation)** in **MATLAB Simulink** with an Arduino Uno and an L298N motor driver. The goal is to increase and decrease motor speed by adjusting the PWM duty cycle and to visualize motor performance through RPM measurements.  

---

### Hardware Diagrams  

| Arduino Uno | L298N Motor Driver | GA12-N20 Motor with Encoder |
|-------------|--------------------|-----------------------------|
| <img width="250" alt="Arduino Uno" src="https://github.com/user-attachments/assets/2203837f-746f-4b6e-8214-7adb68a8c7d0" /> | <img width="250" alt="L298N Motor Driver" src="https://github.com/user-attachments/assets/048af7fa-cc8a-4546-8d2d-b68c417c9854" /> | <img width="250" alt="GA12-N20 Motor with Encoder" src="https://github.com/user-attachments/assets/df88ccd8-d7fd-4a69-9c8e-56ec57d347f2" /> |  
|[Arduino Uno Datasheet (PDF)](https://docs.arduino.cc/resources/datasheets/A000066-datasheet.pdf) | [L298N Motor Driver Datasheet (PDF)](https://www.handsontec.com/dataspecs/L298N%20Motor%20Driver.pdf) |[GA12-N20 Motor Datasheet (PDF)](https://www.handsontec.com/dataspecs/GA12-N20.pdf)  

---

### Tasks Completed  
1. **Simulink Model**  
   - Built an open-loop velocity control model in Simulink using a PWM block.  
   - Configured to run on Arduino Uno hardware with Embedded Real-Time.  

2. **Motor Speed Control**  
   - Verified speed increase and decrease using PWM duty cycle adjustments.  
   - Motor connected through L298N H-bridge driver.  

3. **RPM Measurement & Plot**  
   - Collected motor RPM data from encoder feedback.  
   - Generated plots to illustrate motor speed variation under PWM control.  

4. **Demonstration Video**  
   - A short video is included to showcase the motor moving under Simulink control.  

---

### Submissions  
- **Video:** Demonstrating motor speed variation with PWM (Simulink-based control).

https://github.com/user-attachments/assets/3fd2b712-d372-4cfd-86b9-9588efc9e067

- **Simulink Model Screenshot:** Full model diagram used for motor control.  

<img width="1804" height="777" alt="image" src="https://github.com/user-attachments/assets/18016ff7-4289-41af-b515-152d22c5b4b9" />

- **RPM Plot:** Showing motor speed behavior over time.

<img width="1076" height="863" alt="lab2 plot 1" src="https://github.com/user-attachments/assets/f829bd72-059f-4303-ac69-e7d175bb37d0" />
<img width="1076" height="863" alt="lab2 plot 1 zoomed" src="https://github.com/user-attachments/assets/238130e4-a3df-4483-a8a1-a20c986bcba6" />

---

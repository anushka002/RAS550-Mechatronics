# RAS 550: Mechatronics Final Project  
## Controller Fine-Tuning and Response Comparison: PI and PID Controllers for Motor Speed Regulation  

**Name:** Anushka Gangadhar Satav  
**ASU ID:** 1233530170  
**Course:** RAS 550 Mechatronics  

---

## **Abstract**
The goal of this project is to design and implement a closed-loop motor velocity control system using PI and PID controllers on an Arduino Uno through MATLAB/Simulink. The objective is to analyze and compare the performance of both controllers in achieving stable and accurate speed regulation.  

The developed Simulink model processes real-time encoder feedback to compute motor velocity, applies tuned control algorithms, and generates PWM signals for motor actuation. Experimental tuning showed that while the PID controller slightly reduced overshoot, the PI controller provided smoother response, faster settling, and easier implementation with minimal parameter adjustment.  

The results demonstrate that PI control is sufficient and more practical for real-time motor velocity regulation, balancing simplicity, stability, and performance for embedded applications.

---

## **1. Overview of the Simulink Model**
A new Simulink model was developed to design and analyze the performance of PI and PID controllers for velocity control of a DC motor. The model simulates the motor’s response to a step input and compares the behavior of both controllers in achieving stable and accurate speed regulation.  
It consists of modular subsystems that represent the controllers, feedback loop, and data acquisition elements. The simulation was fine-tuned to evaluate overshoot, settling time, and steady-state error under different gain settings.

---

## **2. Explanation of Model Subsections**

### **a. Encoder and RPM Measurement Subsystem**
This section uses a digital clock and Arduino input block to read pulses from the motor’s rotary encoder. The encoder data is passed through a discrete derivative block to calculate speed and then filtered using a moving average block to obtain smooth and accurate RPM readings. The processed velocity data serves as feedback for the controller.

### **b. Controller Subsystem (PI / PID)**
Two alternate subsystems are implemented: one for the PI controller and another for the PID controller.  
- In the **PI controller**, the error between desired (step input) and measured RPM is processed through proportional and integral terms. The controller output corrects the input voltage to minimize steady-state error.  
- The **PID controller** follows the same structure but includes a derivative gain to anticipate rapid changes, helping to reduce overshoot. Both subsystems can be tuned and tested using the same hardware setup for performance comparison.

### **c. Duty Cycle Generation and PWM Output Subsystem**
The control signal from the PI or PID block is scaled to produce a duty cycle value between 0 and 255. This signal drives a PWM block configured on Arduino Pin 9. The PWM duty cycle determines the effective voltage applied to the motor, allowing precise speed control. Direction control signals are also managed using Arduino pins 4 and 5.

---

## **3. Simulink Model**

### **PI Controller Model**

<img width="929" height="397" alt="image" src="https://github.com/user-attachments/assets/ec4dc4cc-513a-4776-bcbe-b0c602d7c796" />


### **PID Controller Model**

<img width="936" height="411" alt="image" src="https://github.com/user-attachments/assets/6dd1616e-5c50-461f-bf75-65bb6edf8a3b" />


---

## **4. Plots**

### **PI Controller Response**

<img width="887" height="529" alt="image" src="https://github.com/user-attachments/assets/96ac5c3a-12ce-46c6-84e7-a9cf524a7265" />


### **PID Controller Response**

<img width="890" height="530" alt="image" src="https://github.com/user-attachments/assets/4108bb88-e739-490a-b4d2-9afafcbfb364" />


---

## **5. Results and Discussion**

The model was compiled and successfully deployed on the Arduino Uno. Both controllers were tuned through trial and fine adjustment to achieve optimal performance.

**Final Tuned Gains:**  
- **PI Controller:** Kp = 0.01, Ki = 0.75  
- **PID Controller:** Kp = 0.03, Ki = 0.07, Kd = 0.0009  

The step response plots showed that the PID controller achieved a slightly lower overshoot and faster transient response. However, the tuning process was more sensitive, and small gain changes caused instability. In contrast, the PI controller produced a stable, smooth response with minimal steady-state error and required much less tuning effort.  

Therefore, based on experimental observation and simulation, the PI controller proved to be more practical and efficient for motor velocity control. Its simpler structure, reduced computational demand, and adequate response make it preferable for embedded systems and real-time control applications where implementation simplicity is critical.



# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board 

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/ecdfbc9e-23f8-4a38-bafd-bc325172d3da" />

2. Click **File → New STM32 Project**.
<img width="845" height="934" alt="Screenshot 2025-11-03 192156" src="https://github.com/user-attachments/assets/a6bfb740-aecc-42ce-8777-f673d0ff1709" />

<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/0165b1f4-25c3-4b5f-97ad-05d1c8502026" />

3. Select the **target microcontroller** or board and click **Next**.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/be420275-30ea-45c9-ac83-a7ac55769a89" />

4. Name the project.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/c07df32b-9d84-4018-8eba-10c7e6590600" />

5. The corresponding `.ioc` file will be generated automatically.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/20cc0401-fc49-4f5a-900f-268700415d42" />

6. Configure the pins as **GPIO (Input/Output)**, **USART**, etc. as needed.
 <img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/c0e49cfd-cfc3-4003-8ec4-94382bb245de" />
 <img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/fe8a2873-6aa9-4c2e-bcee-f8b053d699d6" />

7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
 <img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/fe8a2873-6aa9-4c2e-bcee-f8b053d699d6" />
 
8. Edit the generated main program as required.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/5fa18c54-d1dc-40f3-9944-480e638955e9" />
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/3ceac528-0625-4a97-8c39-5a82333d993f" />

9. Click **Project → Build All**.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/e24eeb76-c340-41dd-9924-8ceed89d3614" />

10. Link the **HEX file** using the post-build process.
<img width="940" height="213" alt="image" src="https://github.com/user-attachments/assets/bb10ad9f-c8b7-4f6a-ba2e-3579af7efc5e" />

11. Click **Debug** and connect the **STM Nucleo Board**.
<img width="840" height="929" alt="image" src="https://github.com/user-attachments/assets/e24eeb76-c340-41dd-9924-8ceed89d3614" />

12. Click **Run** to execute the program.
 <img width="840" height="920" alt="image" src="https://github.com/user-attachments/assets/28d3bac5-d7b2-4faa-9ac8-5822f0f1b82a" />
   
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 

<img width="840" height="973" alt="image" src="https://github.com/user-attachments/assets/228557ea-c08f-46e4-bfce-5a1a3a54300e" />

CASE 2: LED OFF

<img width="831" height="950" alt="image" src="https://github.com/user-attachments/assets/096de591-73c0-4d51-b9ae-f98898fd5816" />

---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.

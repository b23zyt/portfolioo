# Benjamin (Yuetian) Zeng

Computer Engineering @ University of Waterloo (4.0 CGPA / 94.86%, Term First in Class) · Exchange student @ TU Delft, Fall 2026 · Seeking Winter 2027 co-op

I work mostly at the boundary between hardware and software, such as kernel-level firmware, FPGA datapaths, and the embedded Linux/RTOS layer in between. Most of what's below came out of coursework, research, or internships, not online tutorials.

`b23zeng@uwaterloo.ca` · [LinkedIn](https://www.linkedin.com/in/benjaminzeng2110/) · [GitHub](https://github.com/b23zyt) · [LeetCode](https://leetcode.com/zeng23/) · [ePortfolio](https://benjaminzeng.vercel.app/portfolio)

---

## Projects

### RTOS Kernel for ARM Cortex-M4
`C` `ARM Assembly` · May – Aug 2026 · [Github](https://github.com/b23zyt/arm-kernel)

A preemptive, work-conserving RTOS kernel written from scratch for Cortex-M4, supporting up to 16 concurrent tasks under Earliest Deadline First scheduling.

- Context switches happen through `SVC` and `PendSV` exception handlers, with register save/restore done by hand in ARM assembly
- Dynamic per-task stack memory is handled by a first-fit allocator with fragmentation tracking, since a fixed static allocation scheme wastes SRAM fast on a chip this small (avoid internal fragmentation).
- Spent a fair amount of time chasing scheduler bugs that only showed up under specific task-count and priority combinations.

### FPGA Matrix-Vector Multiplication Accelerator
`SystemVerilog` `Xilinx Kria` · Jul – Aug 2026 · [Github](https://github.com/b23zyt/mvm)

A parameterized MVM accelerator targeting high throughput on a Kria SoM: 128 parallel output lanes, each driven by an 8-lane dot-product engine.

- Hit 633 MHz operating frequency and 615 GOPS peak throughput after several passes at retiming and balancing the adder trees feeding the DSP-mapped multipliers.
- The FSM controller was the trickiest part, coordinating BRAM read/write timing, accumulation boundaries, and multi-stage output write-back without stalling the pipeline.
- Parameterization means lane count and precision aren't hardcoded, so the design can trade throughput for area depending on the target part.

### Tanh Activation Accelerator
`SystemVerilog` `Xilinx Kria` · May – Jun 2026 · [Github](https://github.com/b23zyt/tanh)

A pipelined hardware tanh unit for use in an ML inference datapath, hitting 588 MHz by splitting the polynomial evaluation into short combinational stages instead of one long critical path.

- Interface is latency-insensitive (ready/valid), so the pipeline depth can change later — e.g. adding more stages for shorter clock periods without affecting whatever's downstream.

### Concurrent Web Crawler & Image Assembler 
`C` `POSIX IPC` `libcurl` · Sep – Dec 2025 · [Github](https://github.com/b23zyt/web-crawler)

Two pieces built together as a systems-programming project: a multi-threaded crawler and a multi-process image assembler.

- Crawler: hash-table-based URL deduplication, XPath parsing for link extraction, and both a blocking multi-threaded version and a non-blocking version built on libcurl's multi interface.
- Image assembler: multiple processes coordinate over shared memory using a producer-consumer model with semaphores

### STM32 Smart Vehicle (obstacle avoidance / line tracing / object following / remote control)
`STM32` `C` `PWM` `I2C` `WiFi` `Bluetooth` · Jun – Aug 2025 · [Github](https://github.com/b23zyt/self-driving-car)

A 4-mode robot car on STM32 — closed-loop motor control via PWM and timer interrupts, ultrasonic sensors on SG90 servos for obstacle avoidance, line sensors for tracing, and mode switching over a voice module plus Bluetooth/WiFi. Speed and mode state are shown live on an I2C OLED.

### Smart Home System
`STM32` `C` `ADC` `DMA` `Flash` `MQTT` · May – Jun 2025 · [Github](https://github.com/b23zyt/Smart-Home)

A multi-threaded home automation system on a single STM32: door access control with password storage in on-chip Flash (with modification and alarm-on-failure logic), smoke detection tied to fan control, and temperature/humidity data pushed out over MQTT to an IoT backend.

### Country Data Management System
`C++` · Jan – May 2025 · [Github](https://github.com/b23zyt/CSV-data-manager)

Parses country statistics from CSV into a linked list, then re-indexes the same data into a binary tree keyed on the mean of a chosen attribute, so relationships between countries (by time-series similarity) can be found and rendered as a graph. Mostly a data-structures exercise, but the linked-list → tree → graph pipeline ended up being a decent lesson in picking the right structure for the query you actually need.

### Traffic Light Control FSM
`VHDL` `Altera Cyclone` · Jun – Jul 2024 · [Github](https://github.com/b23zyt/124_vhdl_Traffic_Light_System)

An FSM in VHDL controlling a real intersection's light sequencing, deployed on an Altera Cyclone FPGA, with a pedestrian push-button interrupt that shortens the current red-light phase on activation.

---

## Experience

**Software Engineer Intern — KA Imaging** (Jan – Apr 2026)
Wrote Python modules for concurrent X-ray and motor control on a medical CT machine (inCiTe 2.0), with hardware interlocks and priority scheduling across threads — cut calibration time by 35%. Led the control platform's migration from Windows to a custom-tuned Raspberry Pi OS, re-adapting the REST API and system services for the target hardware and cutting boot time by 80%.

**Undergraduate Research Assistant, AquaSensing — University of Waterloo** (Sep – Dec 2025)
Maintained a cellular IoT gateway on the nRF9160 DK (C, Zephyr OS) for real-time environmental sensing, supporting graduate researchers' data collection.

**Firmware Developer Intern — Fallyx** (May – Aug 2025)
Optimized BLE gateway firmware to manage 10+ peripheral devices concurrently with zero packet loss, and built an MQTT pipeline into AWS IoT holding under 50ms latency at 100+ msg/sec. Wrote 5 reusable Python HAL modules for Orange Pi to speed up future hardware bring-up.

**Embedded Engineer Intern — Chamlion Laser Technology Inc.** (Sep – Dec 2024, Nanjing)
Built a Verilog HDMI display pipeline with SRAM frame buffering and pixel-timing control, and implemented fault detection/interlock logic for 3D printing systems in ladder logic, reaching 99.9% accuracy.

---

## Skills

**Languages:** SystemVerilog, Verilog, VHDL, C++, C, C#, Python, x86/RISC-V Assembly, JavaScript, Bash

**Platforms:** FPGA (Xilinx/Altera), STM32, Embedded Linux, nRF SDK, Raspberry Pi OS, Zephyr OS, RISC-V, x86

**Digital Design:** RTL design, FSMs, pipelining, retiming, FIFO, LUT/BRAM/SRAM, DSP, AXI, timing analysis

**Tools:** Git, Vivado/Vitis, Quartus, ModelSim, STM32CubeIDE, PlatformIO, AWS IoT, JIRA, Confluence, Bitbucket, VS Code


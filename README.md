
# Automatic Washing Machine Control System Using Verilog HDL

This project simulates the control system of an automatic washing machine using a Finite State Machine (FSM) implemented in Verilog HDL. The system models the operation of a washing machine by managing states such as filling water, adding detergent, washing, draining, and spinning.

## Table of Contents

1. [Introduction](#introduction)
2. [Project Structure](#project-structure)
3. [Finite State Machine (FSM) Design](#finite-state-machine-fsm-design)
4. [Signals and Ports](#signals-and-ports)
5. [State Descriptions](#state-descriptions)
6. [Testbench Simulation](#testbench-simulation)
7. [How to Run](#how-to-run)
8. [Results](#results)
9. [Future Enhancements](#future-enhancements)
10. [Contributing](#contributing)
11. [License](#license)

## Introduction

The objective of this project is to design and implement a control system for an automatic washing machine using Verilog HDL. The control logic is modeled as an FSM that transitions through various states, representing different stages of the washing process.

## Project Structure

```
├── automatic_washing_machine.v   # Main Verilog module for the washing machine FSM
├── new_test.v                    # Testbench for simulating the washing machine FSM
└── README.md                     # Project documentation
```

## Finite State Machine (FSM) Design

The washing machine control system is designed as a finite state machine (FSM) with the following states:

- **Check Door**: Verifies if the door is closed before starting.
- **Fill Water**: Fills the drum with water.
- **Add Detergent**: Adds detergent to the water.
- **Cycle**: Performs the washing cycle.
- **Drain Water**: Drains the water from the drum.
- **Spin**: Spins the drum to remove excess water.
- **End**: Signals the end of the washing process.

The FSM transitions between these states based on inputs such as door closure, water level, detergent addition, and cycle completion.

## Signals and Ports

### Inputs

- **clk**: Clock signal to synchronize the FSM.
- **reset**: Resets the FSM to the initial state.
- **door_close**: Indicates if the washing machine door is closed.
- **start**: Starts the washing process.
- **filled**: Indicates that the drum is filled with water.
- **detergent_added**: Indicates that detergent has been added.
- **cycle_timeout**: Signals that the wash cycle is complete.
- **drained**: Indicates that the water has been drained.
- **spin_timeout**: Signals that the spin cycle is complete.

### Outputs

- **door_lock**: Controls the door lock mechanism.
- **motor_on**: Controls the washing machine's motor.
- **fill_value_on**: Controls the water filling valve.
- **drain_value_on**: Controls the water draining valve.
- **done**: Indicates the completion of the washing process.
- **soap_wash**: Indicates whether soap washing is in progress.
- **water_wash**: Indicates whether water washing is in progress.

## State Descriptions

### 1. **Check Door**
   - **Conditions**: Ensures the door is closed before starting the washing cycle.
   - **Actions**: Locks the door and moves to the `Fill Water` state.

### 2. **Fill Water**
   - **Conditions**: Fills the drum with water.
   - **Actions**: Once filled, either proceeds to add detergent or directly to the wash cycle depending on the soap wash status.

### 3. **Add Detergent**
   - **Conditions**: Waits for detergent to be added.
   - **Actions**: Once added, transitions to the wash cycle.

### 4. **Cycle**
   - **Conditions**: Performs the washing cycle.
   - **Actions**: Once the cycle is complete, transitions to draining the water.

### 5. **Drain Water**
   - **Conditions**: Drains the water from the drum.
   - **Actions**: If a water wash is required, refills water; otherwise, proceeds to the spin cycle.

### 6. **Spin**
   - **Conditions**: Spins the drum to remove excess water.
   - **Actions**: Once the spin is complete, the washing process ends.

### 7. **End**
   - **Conditions**: The washing process is complete.
   - **Actions**: Unlocks the door and signals completion.

## Testbench Simulation

The `new_test` module is a testbench used to simulate the FSM. It provides the necessary inputs over time and monitors the outputs, verifying the correct behavior of the washing machine FSM.

### Test Sequence

1. The system starts in the reset state.
2. The `start` and `door_close` signals are set, simulating the user starting the machine with the door closed.
3. The machine transitions through states, simulating filling, washing, draining, and spinning.
4. The simulation monitors the outputs to ensure correct FSM behavior.

## How to Run

### Prerequisites

- **Verilog Simulator**: Use a Verilog simulator such as ModelSim, Vivado, or any other compatible tool.

### Steps

1. **Compile the Design**: Compile the `automatic_washing_machine_HDL.v` file.
2. **Run the Simulation**: Run the `new_test.v` testbench to simulate the washing machine FSM.
3. **Analyze the Results**: Observe the output waveform or log to verify that the FSM transitions correctly between states.

## Results

The simulation should demonstrate the washing machine's operation, transitioning through each state in the correct order. The outputs should reflect the expected behavior based on the inputs provided by the testbench.

## Future Enhancements

- **Multiple Washing Modes**: Implement different washing modes based on fabric type, temperature, and cycle intensity.
- **Error Handling**: Add states for handling errors such as door opening during the cycle or insufficient water.
- **User Interface Integration**: Extend the design to include a user interface for setting wash parameters.

## Contributing

Contributions are welcome! If you have ideas for improving the project or adding new features, please feel free to submit a pull request or open an issue.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

This README should provide clear guidance and detailed information to anyone looking to understand or contribute to your project. Feel free to modify sections to better suit your project's needs!

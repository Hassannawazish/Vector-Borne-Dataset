# ODE Dataset: Vector-Borne Disease Model

## 📊 Dataset Overview

This dataset contains time-series data generated from a system of Ordinary Differential Equations (ODEs) modeling a vector-borne disease transmission dynamics. The model represents the interactions between human and vector populations.

### Variables Mapping

| Original | New Name | Description | Units |
|----------|----------|-------------|-------|
| A | S(t) | Susceptible Humans | count |
| B | I_h(t) | Infected Humans | count |
| C | R_h(t) | Recovered Humans | count |
| D | S_v(t) | Susceptible Vectors | count |
| E | I_v(t) | Infected Vectors | count |

## 📁 Dataset Files

### 1. `ode_dataset.csv`
Complete time-series dataset with all variables over the simulation period.

**Columns:**
- `Time` - Simulation time (0 to 30 units)
- `S(t)` - Susceptible human population
- `I_h(t)` - Infected human population
- `R_h(t)` - Recovered human population
- `S_v(t)` - Susceptible vector population
- `I_v(t)` - Infected vector population

### 2. `supervised_learning_dataset.csv`
Input-output pairs for supervised machine learning tasks. Each row uses the current state to predict the next state.

**Columns:**
- `S(t)_input`, `I_h(t)_input`, `R_h(t)_input`, `S_v(t)_input`, `I_v(t)_input` - Current state features
- `S(t)_target`, `I_h(t)_target`, `R_h(t)_target`, `S_v(t)_target`, `I_v(t)_target` - Next state targets

### 3. `supervised_learning_with_time.csv`
Same as above but includes temporal information.

**Columns:**
- `Time_input` - Current time
- `Time_target` - Next time step
- Feature and target columns as above

### 4. `ode_solution_plot.png`
Visualization of all variables over time.

## 🔬 Mathematical Model

The system is described by the following differential equations:

### Human Population
dS/dt = 100 - (0.0008 + 0.5·I_v)·S
dI_h/dt = 0.5·S·I_v - 0.5808·I_h
dR_h/dt = 0.08·I_h - 0.0008·R_h


### Vector Population
dS_v/dt = 100 - 0.005·I_h·S_v - 0.6614·S_v
dI_v/dt = 0.005·I_h·S_v - 0.6614·I_v

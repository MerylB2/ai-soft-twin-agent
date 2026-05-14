# Architecture Notes

## Purpose

This document describes the initial architecture direction for `ai-soft-twin-agent`.

The goal is to keep the project simple, modular, and easy to evolve as the first experiments are added.

## Core Pipeline

```txt
simulation -> environment interface -> AI / RL agent -> evaluation
```

More explicitly:

```txt
[ Soft Robot Simulation ]
          |
          v
[ Environment Wrapper ]
          |
          v
[ Agent / Policy / RL Loop ]
          |
          v
[ Metrics / Evaluation / Logs ]
```

## Main Components

### `simulation/`

Contains the simulation side of the project.

Possible responsibilities:

- soft-robotics scene setup
- simulation parameters
- deformable body definitions
- physics-related configuration

### `env/`

Defines the interface between simulation and agent logic.

Possible responsibilities:

- observation extraction
- action formatting
- reward definition
- reset / step API

### `agent/`

Contains decision-making logic.

Possible responsibilities:

- rule-based baselines
- reinforcement learning policies
- agent wrappers
- training helpers

### `experiments/`

Contains experiment entry points and evaluation routines.

Possible responsibilities:

- training scripts
- experiment configs
- result summaries
- reproducible run definitions

## Design Principles

- Start minimal
- Keep interfaces explicit
- Separate simulation from agent logic
- Prefer readable experiment structure over premature complexity
- Document assumptions as the project evolves

## First Practical Target

A first useful milestone would be:

1. define one simulated soft-robotics task
2. expose observations, actions, and rewards
3. connect a minimal baseline agent
4. log and compare simple results

## Future Extensions

- SOFA-based simulation integration
- digital twin synchronization ideas
- sim-to-real inspired evaluation
- multiple control strategies
- experiment tracking and visualization

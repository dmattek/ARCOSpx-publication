# Wave Simulation

This folder contains Python scripts to simulate various wave patterns using a cellular automaton model. The simulations include circular waves, directional waves, target patterns, and chaotic patterns. The results of these simulations can be tracked with ARCOS.px and subsequently evaluated using py-motmetrics.

## Contents

- `cellular_automaton.py`: Contains the main functions for running the wave simulations.
- `simulation_tracking.py`: The code to run different simulations and track the emergent dynamics using ARCOS.px.
- `evaluation_metrics_bbox.py`: Script for evaluating simulation metrics results using py-motmetrics.
- `submit_evaluation_batch_bbox.sh`: Example shell script for submitting batch evaluations with slurm.
- `submit_simulation_run_snr_batch.sh`: Example shell script for submitting simulations on a slurm cluster.
- `plot_eval.ipynb`: Jupyter notebook for plotting and evaluating multiple simulation runs.

## Predefined Simulation Functions

The following simulation functions are defined in `cellular_automaton.py`:

- `sim_chaotic(seed, grid_size=(512, 512), num_steps=500)`: Simulates chaotic wave patterns.
- `sim_circles(seed, grid_size=(512, 512), num_steps=500)`: Simulates circular wave patterns.
- `sim_target_pattern(seed, grid_size=(512, 512), num_steps=500)`: Simulates target wave patterns.
- `sim_directional(seed, grid_size=(512, 512), num_steps=500)`: Simulates directional wave patterns.

## Running Simulations

To run a simulation and track the results using ARCOS.px, use the `simulation_tracking.py` script. You can specify the simulation function index and the signal-to-noise ratio as command-line arguments. For example, to run a circular wave simulation with infinite signal-to-noise ratio, use the following command:

```
python simulation_tracking.py --sim_function_index 0 --signal_to_noise_ratio inf
```

where `sim_function_index` is the index of the simulation function to use (0 for circular waves, 1 for directional waves, 2 for target patterns, 3 for chaotic patterns), and `signal_to_noise_ratio` defines the amount of added noise to the simulation.

## Evaluation

To evaluate the results of the simulations, you can use the `evaluation_metrics_bbox.py` script. This uses py-motmetrics to compute various metrics such as MOTA, MOTP:

```
python evaluation_metrics_bbox.py --sim_function_index 0 --signal_to_noise_ratio inf
```

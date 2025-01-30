# Parallel Heat Distribution Simulator

This project implements a parallel heat distribution simulation using a 5-point stencil method. It models the behavior of a hot plate with configurable boundary temperatures and visualizes the heat distribution patterns that emerge over time.

## Overview

The simulator uses a parallel processing approach with pthreads to compute the temperature evolution of a 2D plate. It employs a simple 5-point stencil method where each cell's temperature is updated by averaging its current temperature with its four neighboring cells (North, East, West, South).

## Features

- Configurable NxN grid size
- Customizable boundary temperatures (8 boundary points)
- Parallel processing using pthreads for improved performance
- Output visualization support (generates data for heatmap visualization)
- Performance analysis and execution time measurements

## Requirements

- C++ compiler with pthread support
- Python3 (for visualization)
- Make sure you have the necessary permissions to compile and run the program

## Building the Project

To build the project, use:

```bash
c++ hotplate.cpp -o hotplate -pthread
```

## Usage

The program can be run with the following command format:

```bash
./hotplate N B0 B1 B2 B3 B4 B5 B6 B7 inner steps output.dat [tasks]
```

Parameters:
- `N`: Size of the NxN grid
- `B0-B7`: The 8 boundary temperatures (corners and edges)
- `inner`: Initial temperature for inner cells
- `steps`: Number of simulation steps
- `output.dat`: Output file for the temperature data
- `tasks`: (Optional) Number of parallel tasks to use

Example:
```bash
./hotplate 100 1 1 1 1 1 100 100 100 1 1000 output.dat
```

This creates a 100x100 grid with a hot bottom edge (100°) and other boundaries at 1°.

## Visualization

To visualize the results, use the provided Python script:

```bash
python3 heatmap.py --data=output.dat --png=pretty.png
```

This will generate a heatmap visualization of the final temperature distribution.

## Project Structure

- `hotplate.cpp`: Main simulation code
- `PerformanceAnalysis.pdf`: Detailed analysis of the program's performance
- `Data_Execution_Time_and_Speedup.pdf`: Performance metrics and speedup analysis
- `pretty.png`: Example visualization output

## How It Works

1. The program initializes a grid with specified boundary conditions
2. Uses multiple threads to parallelize the computation
3. Each thread processes a portion of the grid
4. At each time step, new temperatures are calculated using the 5-point stencil method
5. The process continues for the specified number of steps
6. Final temperature distribution is written to the output file

## Performance

The program includes performance measurements and supports parallel execution for improved speed on multi-core systems. Refer to the performance analysis documents for detailed benchmarks and speedup metrics.

## License

This project is provided as-is for educational and research purposes.

## Contributing

Feel free to submit issues and enhancement requests. 
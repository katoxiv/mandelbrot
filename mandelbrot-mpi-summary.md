# Mandelbrot Set Calculation using MPI Manager-Worker Pattern

## Program Description

This program calculates the Mandelbrot set using a manager-worker pattern with MPI (Message Passing Interface) for parallel computation.

## Compilation and Execution

- Compile: `mpicc -o mandelbrot_mpi_mw mandelbrot_mpi_mw.c -lm`
- Run: `sbatch run_mandelbrot_mw.sh`

## Key Components

### Constants and Global Variables

- `N_RE`: 12000 (intervals on real axis)
- `N_IM`: 8000 (intervals on imaginary axis)
- `nIter`: 2D array to store iteration counts
- `z_Re`, `z_Im`: Arrays for points on real and imaginary axes
- Domain: Real [-2.0, 1.0], Imaginary [-1.0, 1.0]

### Main Functions

1. `calc_vals(int i)`: Calculates iterations for a given real axis index
2. `do_communication(int myRank)`: (Not used in current implementation)
3. `write_to_file(char filename[])`: Writes results to a file
4. `main(int argc, char *argv[])`: Main function implementing the manager-worker pattern

## Algorithm Overview

1. Initialize MPI environment
2. Manager process (rank 0):
   - Distributes work to worker processes
   - Collects results
3. Worker processes:
   - Request work from manager
   - Perform calculations
   - Send results back to manager
4. Write results to file (if enabled)
5. Finalize MPI environment

## Performance Measurement

The program measures execution time using `MPI_Wtime()`.

## Notes

- The `do_communication` function is present but not used in the current implementation.
- File I/O is optional and controlled by the `doIO` flag.
- Verbose output can be enabled with the `verbose` flag.

## Potential Improvements

- Remove or update the unused `do_communication` function
- Implement dynamic load balancing for better performance
- Add error handling and input validation
- Optimize the Mandelbrot set calculation algorithm


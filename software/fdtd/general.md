FDTD Solutions  is a commercial 3D FDTD-method Maxwell solver for the design, analysis and optimization of nanophotonic devices, processes and materials software package from Lumerical
https://www.lumerical.com/


## How to use

To see what versions of FDTD Solutions are available on each machine use the command
module avail FDTD

# Running on Tegner
To run on FDTD Solutions you first need to create the fsp file as
normal using the GUI. That fsp file can then be run using the queue
system by creating by submitting a job script using
```
sbatch jobscript.sh
```
Note currently only single node runs (upto 24 cores) are supported.
Example Job script
#!/bin/bash
# The name of the script is myjob
#SBATCH -J myjob
# Only 1 hour wall-clock time will be given to this job
#SBATCH -t 1:00:00
# set the project to be charged for this
# should normally be of the format 2015-1 or 2015-16-1 or similar
#SBATCH -A <project name>
# Number of nodes
#SBATCH --nodes=1
# Number of MPI processes per node (24 is recommended for most cases)
# 48 is the default to allow the possibility of hyperthreading
#SBATCH --ntasks-per-node=24
# Number of MPI processes.
module load FDTD/8.15
ulimit -s unlimited
fdtd-run-local.sh -n 24 Example.fsp


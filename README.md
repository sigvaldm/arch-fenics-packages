# Stable Arch packages for FEniCS

## Install using pacman

## Install using makepkg

First, make sure the following packages are installed from the official Arch repository:

	* `gcc-fortran`
	* `python-mpi4py`
	* `python-matplotlib`
	* `python-scipy`
	* `python-sympy`
	* `hdf5-openmpi`
	* `fftw`
	* `valgrind`

This is done as usual, by running e.g. `pacman -S gcc-fortran` for `gcc-fortran` (use several arguments to install several packages at the same time). 

Then, the packages in this repository can be installed in the following order (this order takes into account dependencies):

	* `parmetis-sm`
	* `superlu-sm`
	* `scalapack-sm`
	* `scotch-sm`
	* `hypre-sm`
	* `mumps-par-sm`
	* `petsc-sm`
	* `slepc-sm`
	* `python-instant`
	* `python-ufl`
	* `python-dijitso`
	* `python-fiat`
	* `python-ffc`
	* `dolfin`
	* `python-mshr`

This is done by entering the respective directory in this repository and running `makepkg -sri`.

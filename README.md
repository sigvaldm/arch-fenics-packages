# Stable FEniCS for Arch Linux with frozen dependencies
FEniCS and many of its numerous dependencies are under very active development by leading scientists in the field. Unfortunately, these packages ofte lack good practices for ensuring backwards compatibility (such as semantic versioning). This makes FEniCS break frequently, especially on a bleeding edge, rolling release system such as Arch Linux (though, on the whole, I must say that Arch Linux far supersedes its rumour in this respect. I usually only have problems with FEniCS).

This is a repository of Arch Linux packages (PKGBUILDs) for FEniCS and its dependencies. Most of them are the same packages as the ones on the Arch User Repository (AUR), being git submodules, but they are frozen to a specific version to ensure that they do not break FEniCS. Some packages on the AUR are broken, out-of-date, or somehow breaks FEniCS. For these packages I have made an alternative to the AUR packages with a suffix `-sm`.

Why don't I put the `-sm` packages on the AUR? Because it's considered bad practice with duplicate packages. The preferred method is to make sure the ones that are there are up-to-date. Unfortunately, when I don't maintain those packages there's little I can do but notify the maintainer. It often (understandably) takes quite a while before they get fixed, if at all, and in the meanwhile, FEniCS will remain broken. AUR also don't freeze packages.

## Installing FEniCS

First, make sure the following packages are installed from the official Arch repository:

	* `gcc-fortran`
	* `python-mpi4py`
	* `python-matplotlib`
	* `python-scipy`
	* `python-sympy`
	* `hdf5-openmpi`
	* `fftw`
	* `valgrind`
	* `suitsparse`

This is done as usual, by running e.g. `pacman -S gcc-fortran` for `gcc-fortran` (use several arguments to install several packages at the same time).

Then, the packages in this repository can be installed in the following order (this order takes into account dependencies):

	* `parmetis-sm`
	* `superlu`
	* `scalapack`
	* `scotch-sm`
	* `hypre-sm`
	* `mumps-par`
	* `petsc`
	* `slepc`
	* `petsc4py`
	* `slepc4py`
	* `python-ufl`
	* `python-dijitso`
	* `python-fiat`
	* `python-ffc`
	* `dolfin`
	* `python-dolfin`
	* `mshr`
	* `python-mshr`

This is done by entering the respective directory in this repository and running `makepkg -sri`.

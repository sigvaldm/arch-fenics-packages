# Stable FEniCS 2019.1.0.post0 for Arch Linux with frozen dependencies
FEniCS and many of its numerous dependencies are under very active development by leading scientists in the field. Unfortunately, these tools often lack good practices for ensuring backwards compatibility (such as semantic versioning). This makes FEniCS break frequently, especially on a bleeding edge, rolling release system such as Arch Linux (though, on the whole, I must say that Arch Linux far supersedes its rumour in this respect. I usually only have problems with FEniCS).

This is a repository of Arch Linux packages (PKGBUILDs) for FEniCS and its dependencies. Most of them are the same packages as the ones on the Arch User Repository (AUR). In fact, they are just clones (or git submodules), but they are frozen to a specific version to ensure that they work with FEniCS. Some packages on the AUR are broken, out-of-date, or somehow breaks FEniCS. For these packages I have made an alternative to the AUR packages with a suffix `-sm`.

Why don't I put the `-sm` packages on the AUR? Because it's considered bad practice with duplicate packages. The preferred method is to make sure the ones that are there are up-to-date. Unfortunately, for the packages I don't already maintain myself, there's little I can do but notify the maintainer. It often (understandably) takes quite a while before they get fixed, if at all, and in the meanwhile, FEniCS will remain broken. But not here.

## Installing FEniCS

First, make sure the following packages are installed from the official Arch repository (the command can be copy-pasted):

```
sudo pacman -S \
    gcc-fortran \
    python-mpi4py \
    python-matplotlib \
    python-scipy \
    python-sympy \
    hdf5-openmpi \
    fftw \
    valgrind \
    suitesparse
```
This should cover missing dependencies from the AUR packages, as well as optional dependencies which are nice to have. (There may be fewer missing dependencies now than when I made this list, but it doesn't hurt to install them in advance anyway).
Next, clone this repository, including all the git submodules:
```
git clone --recurse-submodules https://github.com/sigvaldm/arch-fenics-packages.git
```
If you forgot `--recurse-submodules` most folders will be empty. No worries. You can still their contents by running `git submodule init` followed by `git submodule update`.

Then, install the packages in the following order (this order takes into account dependencies):

- `parmetis-sm`
- `superlu`
- `scalapack`
- `scotch-sm`
- `hypre-sm`
- `mumps-par`
- `petsc`
- `slepc`
- `petsc4py`
- `slepc4py`
- `python-ufl`
- `python-dijitso`
- `python-fiat`
- `python-ffc`
- `dolfin`
- `python-dolfin`
- `mshr`
- `python-mshr`

This is done by entering the respective directory in this repository and running `makepkg -sri`.

I might try to make this less cumbersome in the future, but it should work for now.

## Gmsh notes

Note on Gmsh: the `dolfin-convert` command appears to have issues with `.msh` files generated using Gmsh 4. You cam use Gmsh 3.0.6 instead. The package `gmsh-bin` on AUR currently provides this.

To provide `.msh` files with Gmsh 4 that can be parsed by `dolfin-convert`, you should run Gmsh with the following flags:
```
gmsh -format msh2 <input_file>.geo
```

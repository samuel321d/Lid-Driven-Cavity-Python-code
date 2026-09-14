# Lid-Driven Cavity CFD Solver

A finite-volume, vorticity–stream function solver for the classic **lid-driven cavity flow** problem, implemented from scratch in Python, with heat transfer coupling and validation against benchmark data.

## Background

The lid-driven cavity problem is a classic benchmark case in computational fluid dynamics (CFD). Although the geometry is simple, it captures complex physical phenomena, such as vortex formation, whose behavior strongly depends on the Reynolds number ($Re$).

This case is also widely used as a reference for validating new numerical algorithms, thanks to the results reported by Ghia et al. (1982) [1], who studied the cavity flow numerically and experimentally for several values of $Re$.

This work validates an in-house CFD code by comparing its results against those reported by Ghia et al. (1982) for $Re = 100$ and $Re = 400$. Heat transfer inside the cavity is also analyzed, considering horizontal walls held at different temperatures and adiabatic vertical walls.

The mesh generation code and the solver were both implemented in Python. A mesh independence study was carried out using three grid resolutions ($20\times20$, $40\times40$, and $80\times80$), comparing velocity profiles at $x/L = 0.5$ as well as the average Nusselt number ($\overline{Nu}$).

## Features

- Custom 2D structured mesh generator (finite-volume cells, faces, and neighbor connectivity)
- Vorticity–stream function formulation solved via finite volumes
- Upwind convection scheme with central differencing for diffusion
- Coupled heat transfer (advection–diffusion of temperature) with Dirichlet and adiabatic boundary conditions
- Mesh independence study ($20\times20$, $40\times40$, $80\times80$)
- Validation against Ghia et al. (1982) benchmark data and ANSYS Fluent reference results

## Repository Structure

```
.
├── CAVITY_CFD.ipynb        # Main notebook: mesh, solver, post-processing
├── data/                   # Fluent validation CSV files (u_x05.csv, v_x05.csv, etc.)
├── requirements.txt
├── LICENSE
└── README.md
```

## Requirements

- Python 3.9+
- See [`requirements.txt`](requirements.txt) for exact package versions

Install dependencies with:

```bash
pip install -r requirements.txt
```

## Usage

1. Clone the repository:
   ```bash
   git clone https://github.com/YOUR_GITHUB_USERNAME/YOUR_REPO_NAME.git
   cd YOUR_REPO_NAME
   ```
2. Make sure the Fluent validation CSV files are inside the `data/` folder.
3. Open and run `CAVITY_CFD.ipynb` in Jupyter, JupyterLab, or VS Code, cell by cell, from top to bottom.

## Results

The notebook produces, for each mesh resolution and Reynolds number:

- Stream function ($\Psi$) contours and streamlines
- Vorticity ($\omega$) contours
- Velocity magnitude ($|V|$) contours
- Temperature ($\theta$) contours
- Velocity profile comparisons ($u^*$, $v^*$ at $x/L = 0.5$) against Ghia et al. (1982) and ANSYS Fluent
- Average Nusselt number ($\overline{Nu}$) vs. mesh resolution

## Validation

Results are cross-checked against two independent references:

- **Ghia, Ghia & Shin (1982)** — benchmark tabulated velocity profiles for $Re = 100$ and $Re = 400$
- **ANSYS Fluent** — an independent CFD simulation of the same case, used as a secondary check

## References

[1] Ghia, U., Ghia, K. N., & Shin, C. T. (1982). High-Re solutions for incompressible flow using the Navier-Stokes equations and a multigrid method. *Journal of Computational Physics*, 48(3), 387–411.

## Author

**Julian Samuel Prieto León**
Aerospace Engineering student, University of Antioquia
📧 samuel.prieto@udea.edu.co

## License

This project is licensed under the MIT License — see [`LICENSE`](LICENSE) for details.

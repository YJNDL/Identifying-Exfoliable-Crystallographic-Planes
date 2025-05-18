# Bond Density Evaluation and Crystallographic Plane Exfoliation

This repository provides methods to identify promising crystallographic planes for exfoliation in non-van der Waals (non-vdW) bulk materials by evaluating bond density and systematically performing structural exfoliation simulations.

---

## Bond Density Evaluation and Plane Selection

To efficiently screen and identify exfoliable crystallographic planes, the following steps are employed:

---

1. **Simulate XRD Patterns**

```bash
python simulate_xrd.py
```

2. **Identify Crystallographic Planes**

```bash
python identify_planes.py
```

3. **Bond Density Analysis**

```bash
python bond_density_scan.py
```

Bond density $\rho$ is defined by:

```math
\rho = \frac{N(R_i, R_j)}{A}, \quad (i \neq j)
```

* $R$ represents the coordinates of neighboring atoms on opposite sides of the plane.
* $N$ is the number of intersecting chemical bonds within one periodic unit.
* $A$ is the planar area spanned by these bonding atoms.

Planes identified with relatively low $\rho$ values are considered promising for exfoliation.

---

## Step-wise Exfoliation Procedure

**Note:** *DFT-D3 van der Waals corrections are integrated into all exfoliation simulations.*

Follow these steps to simulate exfoliation:

1. **Align Structure**

Rotate the structure such that the target exfoliation face aligns perpendicular to the c-axis.

2. **Stretch and Relax Structure**

Gradually stretch the lattice normal to the target plane, moving the outermost atomic layer approximately 0.2 Å per step. Relax the structure at each increment.

Incremental energy change $\Delta E(j)$ is calculated by:

```math
\Delta E(j) = \frac{1}{A} \sum_{j \geq i \geq 0}(E_{i,1}-E_{i,0})
```

* $E_{i,0}$ is the instantaneous stable state energy at the initial state.
* $E_{i,1}$ is the energy of the stretched and relaxed state.
* $A$ is the area of the crystal face per unit period.

Exfoliation energy $E_{\text{exf}}$ is the sum of incremental energy changes, indicating the energy required to separate the layer:

```math
E_{\text{exf}} = \sum \Delta E(j) \quad \text{when} \quad E_{i,1} \leq E_{i,0}
```

---

## Dependencies

* Python 3.9~3.12
* Required Python libraries: numpy scipy matplotlib pymatgen ase

```bash
pip install numpy scipy matplotlib pymatgen ase
```

---

## References

The methodologies herein incorporate established computational techniques and energy calculations as referenced in relevant literature (DFT-D3, etc.). Ensure proper referencing when utilizing this approach in publications.

---

## License

This project is licensed under the MIT License.

```
```

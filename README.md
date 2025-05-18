# Bond Density Evaluation and Crystallographic Plane Exfoliation

This repository provides computational methods to identify crystallographic planes suitable for exfoliation from non-van der Waals (non-vdW) bulk materials by evaluating bond density and performing systematic structural exfoliation simulations.

---

## Bond Density Evaluation and Plane Selection

Efficiently screen and identify exfoliable crystallographic planes through the following workflow:

### 1. Simulate XRD Patterns

```bash
python simulate_xrd.py
```

### 2. Identify Crystallographic Planes

```bash
python identify_planes.py
```

### 3. Bond Density Analysis

```bash
python bond_density_scan.py
```

The bond density ($\rho$) is defined as:

$$
\rho = \frac{N(R_i, R_j)}{A}, \quad (i \neq j)
$$

* $R$: Coordinates of neighboring atoms located on opposite sides of the plane.
* $N$: Number of intersecting chemical bonds within one periodic unit.
* $A$: Planar area spanned by these bonding atoms.

Planes exhibiting relatively low bond density $\rho$ are promising for exfoliation.

---

## Step-wise Exfoliation Procedure

> **Note:** DFT-D3 van der Waals corrections are integrated into all exfoliation simulations.

Follow these detailed steps to simulate the exfoliation process:

### 1. Align Structure

Rotate the crystal structure to align the targeted exfoliation plane perpendicular to the c-axis.

### 2. Stretch and Relax Structure

Incrementally stretch the lattice normal to the exfoliation plane, moving the outermost atomic layer approximately 0.2 Å per step, followed by structural relaxation at each increment.

The incremental energy change ($\Delta E(j)$) is computed as:

$$
\Delta E(j) = \frac{1}{A} \sum_{j \geq i \geq 0}(E_{i,1}-E_{i,0})
$$

* $E_{i,0}$: Instantaneous stable state energy at the initial configuration.
* $E_{i,1}$: Energy of the stretched and subsequently relaxed configuration.
* $A$: Area of the crystal face per unit periodicity.

The exfoliation energy ($E_{\text{exf}}$) indicates the total energy required to separate layers:

$$
E_{\text{exf}} = \sum \Delta E(j) \quad \text{when} \quad E_{i,1} \leq E_{i,0}
$$

---

## Dependencies

* Python version: 3.9–3.12
* Required Python libraries: `numpy`, `scipy`, `matplotlib`, `pymatgen`, `ase`

Install dependencies via:

```bash
pip install numpy scipy matplotlib pymatgen ase
```

---

## References

The methodologies used incorporate established computational techniques, including DFT-D3 for energy calculations. Please ensure proper referencing when using these methodologies in your publications.

---

## License

This project is licensed under the MIT License.

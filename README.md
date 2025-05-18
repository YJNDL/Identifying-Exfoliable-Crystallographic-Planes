# High-throughput exfoliation

Bond density evaluation and crystallographic plane selection
    
	1) Use simulate_xrd.py to simulate the XRD diffraction pattern of the material.

	2) Apply identify_planes.py to identify the crystal plane indices corresponding to the diffraction peaks.

	3) Use bond_density_scan.py to perform a bond density scan on the specified crystal planes obtained in Step 2.

Step-wise exfoliation (Cautian! The DFT-D3 vdW corrections are considered during this process)

	1) Rotate the structure so that the crystal face to be peeled faces the c-axis.
		
	2) Stretch the lattice along the direction normal to the crystal face, with the outermost atomic layer movement by ~0.2 Å at each step.

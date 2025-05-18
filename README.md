# High-throughput exfoliation

Crystal plane select
    Step 1: Use xxx.py to simulate the XRD diffraction pattern of the material.

    Step 2: Apply XXX.py to identify the crystal plane indices corresponding to the diffraction peaks.

    Step 3: Use XXX.py to perform a bond density scan on the specified crystal planes obtained in Step 2.

Step-wise exfoliation
	Modeling and DFT calculation operations are performed based on the low-bond density crystal face obtained in the previous step, which are specifically manifested as follows:
		
		1) Rotate the structure so that the crystal face to be peeled faces the z-axis
		
		2) Stretch the lattice along the direction normal to the crystal face, with the outermost atomic layer movement by ~0.2 Å at each step.
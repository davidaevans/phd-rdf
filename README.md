# RDF Calculation

Code in C to calculate the radial distribution function in 2D using LAMMPS trajectories

---

## Compiling

To compile:
```
make clean
make
```

The executable created is `rdf`.

## Options

When running the code, it looks for a file called `options` where you need to specify 3 things:

```
binsize 0.01
filename traj.dat
sweeps 1000
```

The `binsize` is the width of the bins in the same units as the box size. `sweeps` is the number of frames in the trajectory file. The `filename` is the name of the trajectory file which has to be in the following format:

```
ITEM: TIMESTEP
0
ITEM: NUMBER OF ATOMS
5200
ITEM: BOX BOUNDS pp pp pp
0.0000000000000000e+00 1.0000000000000000e+02
0.0000000000000000e+00 1.0000000000000000e+02
0.0000000000000000e+00 5.0000000000000000e-01
ITEM: ATOMS id type xu yu zu vx vy vz 
1 1 1.36778 1.36778 0 0 0 0.420505
```

There are 9 header lines which specify the timestep, number of particles and box size in 3 dimensions. The box size in the z direction should be set to the same size as the diameter. The z dimension is not read into the code.

## Output

The g(r) will be written to `rdf.dat`. The format is

```
# r g(r) no_of_samples
```
where the r is printed as the centre of its respective bin.

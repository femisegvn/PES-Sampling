
# Basin Hopping Algorithm for PES Global Optimisation

### Pertubation Methods
Considerations:
1. number of atoms to perturb
    - wild -- one
    - stretch -- all
    - sweep -- user-defined
    - swap -- two

2. selection criteria for perturbed atoms
    - wild -- random
    - stretch -- n/a -- all perturbed
    - sweep -- furthest from centroid
    - swap -- random

3. pertubation magnitude
        - wild -- random (within central box)
        - stretch -- random amount up to a user defined limit
        - sweep -- random up to a user defined limit
        - swap -- n/a -- swap

#### Wild
Randomly selects one atom and changes all of its coordinates randomly within a restricted box space (if it was moved randomly across the entire box space, it may move outside the cutoff of all atoms in the structure and effectively reduces the LJ19 cluster to an LJ18 cluster.) i.e. moves a random atom in a random direction by a random amount.


#### Stretch
Calculates the centroid of the cluster, then moves all the atoms away from that centroid before performing the energy minimisation. Additional parameter can control how far away all of the atoms are moved.

#### Sweep
Computes cluster centroid, moves the k-furthest atoms in a random direction by a random amount. Based on the idea that the core of the cluster is likely stable, but the outermost atoms are those that need to be displaced.

#### Swap
Exchanges two random atoms coordinates. e.g. randomly swap the x coordinate of atom a with the x coordinate of atom b, or randomly swap the y coordinate of atom a with the z coordinate of atom b
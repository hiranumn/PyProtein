# PyProtein

A bunch of scripts that makes feature extraction easier from pdbs.
``` Python
import pyprotein as pyp
from pyrosetta import *
pose = Pose()
pose_from_file(pose, "/net/scratch/hiranumn/raw_relaxed/1ezgA/tag0001.al_0001.pdb")
fa_scorefxn = get_fa_scorefxn()
```

## Example 1: Getting different types of distance maps
``` Python
# Get CB to CB distance map use CA if CB does not exist
x = pyp.get_distmaps(pose, atom1="CB", atom2="CB", default="CA")
# Get CA to CA distance map
x2 = pyp.get_distmaps(pose, atom1="CA", atom2="CA")
# Get Tip to Tip distancemap
x3 = pyp.get_distmaps(pose, atom1=pyp.dict_3LAA_to_tip, atom2=pyp.dict_3LAA_to_tip)
# Get Tip to CA distancemap
x4 = pyp.get_distmaps(pose, atom1=pyp.dict_3LAA_to_tip, atom2="CA")
```

## Example2: Getting Euler angles of rigid body transformation between two residues
``` Python
# Get sine and cosine of 6 angles per residue. This returns (num_res, 12) matrix.
output = pyp.getEulerOrientation(pose)  
```

## Example3: Getting 1/2 body energy terms per resdiue/residue-pair
``` Python
# Get energy map
output = pyp.getEnergy(pose, fa_scorefxn)
```

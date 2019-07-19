# PyProtein

## Getting different types of distance maps
```
import pyprotein as pyp
from pyrosetta import *

# Load a pdb file using pyrosetta
pose = Pose()
pose_from_file(pose, "/net/scratch/hiranumn/raw_relaxed/1ezgA/tag0001.al_0001.pdb")

# Get CB to CB distance map use CA if CB does not exist
x = pyp.get_distmaps(pose, atom1="CB", atom2="CB", default="CA")

# Get CA to CA distance map
x2 = pyp.get_distmaps(pose, atom1="CA", atom2="CA")

# Get Tip to Tip distancemap
x3 = pyp.get_distmaps(pose, atom1=pyp.dict_3LAA_to_tip, atom2=pyp.dict_3LAA_to_tip)

# Get Tip to CA distancemap
x4 = pyp.get_distmaps(pose, atom1=pyp.dict_3LAA_to_tip, atom2="CA")
```

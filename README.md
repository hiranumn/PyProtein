# PyProtein

A bunch of scripts that makes feature extraction easier from pdbs.
``` Python
import pyprotein as pyp
from pyrosetta import *
pose = Pose()
pose_from_file(pose, "/net/scratch/hiranumn/raw_relaxed/1ezgA/tag0001.al_0001.pdb")
fa_scorefxn = get_fa_scorefxn()
```

## get_distmaps(pose, atom1, atom2, default)
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

## get1hotAA(pose, indecies)
This function gets sine and cosine of 6 angles per residue and returns (num_res, 20) matrix.
You can specify indecies of amino acids via dictionary.
``` Python
x = pyp.get1hotAA(pose, indecies=pyp.dict_1LAA_to_num)
```

## getTorsions(pose)
This function gets phi psi omega angles of each residue and returns a (\[phi, psi, omega\], num_res) matrix.
``` Python
x = pyp.getTorsions(pose)
```

## getEulerOrientation(pose)  
This function gets sine and cosine of 6 angles per residue and returns (num_res, 12) matrix.
``` Python
output = pyp.getEulerOrientation(pose)  
```

## getEnergy(pose, fa_scorefxn)
This function gets 1 body and 2 body energy of pose given an energy function.
It returns a tuple of (num_res, 1) and (num_res, num_res) matrices.
``` Python
# Get energy map
output = pyp.getEnergy(pose, fa_scorefxn)
```

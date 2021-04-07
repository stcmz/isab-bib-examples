# IsAb example for Antibodies D44.1 and Cemiplimab

This repository contains the intermediate and output data involved in the design process of antibodies D44.1 and cemiplimab by IsAb protocol.

1_original_data_[step1]
---

This directory contains structure files of lysozyme, and three PD1 obtained from protein data bank. 

The sequence of antibodies D44.1 and cemiplimab were obtained from IMGT:

```
Cemiplimab
H: EVQLLESGGVLVQPGGSLRLSCAASGFTFSNFGMTWVRQAPGKGLEWVSGISGGGRDTYFADSVKGRFTISRDNSKNTLYLQMNSLKGEDTAVYYCVKWGNIYFDYWGQGTLVTVSS
L: DIQMTQSPSSLSASVGDSITITCRASLSINTFLNWYQQKPGKAPNLLIYAASSLHGGVPSRFSGSGSGTDFTLTIRTLQPEDFATYYCQQSSNTPFTFGPGTVVDFR
```

```
D44.1
H: QVQLQESGAEVMKPGASVKISCKATGYTFSTYWIEWVKQRPGHGLEWIGEILPGSGSTYYNEKFKGKATFTADTSSNTAYMQLSSLTSEDSAVYYCARGDGNYGYWGQGTTLTVSS
L: DIELTQSPATLSVTPGDSVSLSCRASQSISNNLHWYQQKSHESPRLLIKYVSQSSSGIPSRFSGSGSGTDFTLSINSVETEDFGMYFCQQSNSWPRTFGGGTKLEIK
```

2_modeling_3d_structure_[step2]
---

This directory contains 3D structrues of antibodies cemiplimab and D44.1 modelled from RosettaAntibody.

3_relaxed_structure_[step3]
---

This directory contains the structrues of lysozyme and three PD1 relaxed by RosettaRelax protocol. The script used to acquire this looks like

```
relax.static.linuxgccrelease \
-database rosetta_bin_linux_2020.08.61146_bundle/main/database \
-s PD1v2.pdb \
-in:file:fullatom \
-out:pdb \
-relax:thorough \
-relax:constrain_relax_to_start_coords \
-relax:ramp_constraints false \
-ex1 \
-use_input_sc -flip_HNQ \
-no_optH false \
-nstruct 10
```

4_global_docking_results_[step4]
---

This directory contains the global docking results of cemiplimab-PD1 and D44.1-lysozyme complexes from ClusPro.

5_local_docking_results_[step5]
---

This directory contains local docking results of cemiplimab-PD1 and D44.1-lysozyme complexes from SnugDock.

6_affinity_maturation_results_[step7]
---

This directory contains cemiplimab four point mutation and D44.1 double muations designed by affinity maturation protocol. The script of affinity maturation protocol. The script used to acquire this looks like

```
rosetta_scripts.static.linuxgccrelease \
-linmem_ig 100 \
-use_input_sc \
-ex1 \
-nstruct 10 \
-s proteins_0887.pdb \
-parser:protocol design.xml \
-out:suffix _design \
-scorefile proteins_0887.fasc
```
Present: *Lukas, Yannick, Alex, Frederik, Gavin, Konrad, Marius, Martin, Sebastian, Thomas, Nik*

# Repo cleanup: #
branches that are not taken care of at the moment:

* environment_control
* iv_javascript -> SciFi, can be merged at later point (Yannick/Lukas)
* hv_control
* odbxx_vector -> deleted
* combine_hamegs -> tagged, deleted

should we delete / merge / keep them ? 

With newer CMake versions, you get a lot of errors of the type:
```
CMake Warning (dev) at farm_pc/tools/CMakeLists.txt:6 (add_executable):
  Policy CMP0115 is not set: Source file extensions must be explicit.  Run
  "cmake --help-policy CMP0115" for policy details.  Use the cmake_policy
  command to set the policy and suppress this warning.
```

* Solution 1: Set CMP0115 and continue using implicit file extensions
* Solution 2: Clean up the corresponding CMakeLists.txt and write file extensions explicitly (recommended by CMake)
* Solution 3: Live with wall of warnings

Prefernce for solution two, solution one for where MIDAS is concerned.

# Integration run analysis #

* Marius and Thomas are working on the run list, including pixel masking and translating this into json readable by the analyzer
* Hot pixel masking needed before final conversion
* Marius put instructions for the converter at [manalyzer Mu3e](manalyzer Mu3e)

# Next developments #

* Clock Box II being readied in Mainz
* Switching PC in Mainz ordered
* HD preparing a telescope adapter for the FEB backplane (ready in autumn)
* Lukas has prepared an online version with external MIDAS, docu to be updated, will be merged into new development branch
* Alex collecting everything from the integration run today, will change to new branch/tag naming scheme after that
* Yannick is setting up the DAQ chain in Geneva, SMBs to be fetched from PSI
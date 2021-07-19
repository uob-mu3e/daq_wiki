Present:

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

# Integration run analysis #

# Integration run soft- and firmware consolidation #

# Next developments #

* Clock Box II
* Switching PC in Mainz
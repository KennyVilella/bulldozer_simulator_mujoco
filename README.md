# bulldozer_simulator_mujoco
This repository implements a simulator of a bulldozer including the soil dynamics.
The simulator is built on the top of a customized version of [MuJoCo][MuJoCo], available [here][Mujoco2].
The only modification of this customized version is a better visualization of floating soil.

The soil dynamics is modeled using [soil_dyanmics_cpp][soil simulator] and a custom soil plugin serves as an interface with [MuJoCo][MuJoCo].
A description of the soil plugin as well as an usage example is provided [here][soil README].
A bulldozer model is also included that is thoroughly described in the corresponding [README](model/bulldozer/README.md).

A customized executable to launch [MuJoCo][MuJoCo] is also provided, as the default executable does not include the update of `HField`.

# Installation
A bash script is provided to make the installation of the simulator easier.
To install the simulator, simply execute the following command
```
bash <path_to_repo>/build.bash
```

This script would:
- (if necessary) clone the [soil_dyanmics_cpp][soil simulator] repository and move it to the appropriate folder.
- Build the simulator with CMake.
- Copy the custom plugin library to the appropriate folder.
- Copy the custom executable to the appropriate folder.

# Running the simulator
To run the simulator, simply execute the following command
```
.<path_to_repo>/build/bin/bulldozer_simulator <path_to_repo>/model/bulldozer/bulldozer.xml
```

A window will open with the bulldozer.
It is suggested to toggle on the "Wireframe" view in the "Rendering" section in order to better visualize the soil.
The bulldozer can be actuated using the three sliders in the "Control" section.
Note that the bulldozer locomotion may be challenging on rugged terrain (for more details, see the "Locomotion" section of the [model README](model/bulldozer/README.md)).

# To-do list
There are several important features that are yet to be implemented.
These include, in order of priority:

- Improve the soil plugin. In particular, add more check to ensure the plugin is properly connected.
- Improve bulldozer locomotion.
- Add reaction force from the soil.

[MuJoCo]: https://mujoco.org/
[MuJoCo2]: https://github.com/KennyVilella/mujoco
[soil simulator]: https://github.com/KennyVilella/soil_dynamics_cpp
[soil README]: plugin/soil/README.md

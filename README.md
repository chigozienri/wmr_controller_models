# wmr_controller_models
How to get STL format files of Windows Mixed Reality (WMR) controllers

I wanted to find models of the WMR controllers in a usable 3D format, so that I could model accessories for them. This was surprisingly difficult.

The BabylonJS github repo contains models of the standard (HP, Lenovo, etc.) controllers and the Samsung Odyssey controllers here https://github.com/BabylonJS/Babylon.js/tree/master/assets/meshes/controllers/microsoft in .glb format. This is the format that the controller models are provided to software using the Motion Controller prefab from the Mixed Reality Toolkit as described here: https://docs.microsoft.com/en-us/windows/mixed-reality/gestures-and-motion-controllers-in-unity#rendering-the-motion-controller-model-in-unity and here: https://github.com/Microsoft/MixedRealityToolkit/tree/master/SpatialInput/Samples/RenderController , so I believe this is the origin of these files.

Unfortunately, glb/gltf is not a format that behaves very well in CAD software. It imported into Fusion, but would not display.
Eventually I used assimp (https://github.com/assimp/assimp) to convert to STL.
This was achieved (on OS X) by the following workflow:

Download source of latest stable assimp from https://github.com/assimp/assimp
# Build:
```
cd assimp-version
cmake CMakeLists.txt -G 'Unix Makefiles'
make
```
# Run:
```
./bin/assimp export /foo/bar.glb /foo/bar.stl
```

I'm not sure of the license on the original models, but the BabylonJS repo has Apache License 2.0, so I believe it is OK to host the models here. If it turns out that this is not the case, and I delete the models, following the above procedure should result in a usable model.

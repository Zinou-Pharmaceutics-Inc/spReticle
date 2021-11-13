### spReticle

spReticle is a camera reticle for Maya, for Maya 2018-2022.

Originally developed at Sony Pictures Imageworks, imageworks-maya-reticle (spReticle) is a Maya C++ plugin plus MEL code which creates a reticle for a camera. It allows for various camera reference masks to be displayed when looking through the camera, such as filmback, projection gate, and pan-and-scan attributes.  The value of predefined parameters can be displayed in selectable areas, such as the camera focal length and name, current aspect ratio; frame number, name of the show and shot, Maya scene file name, current user name, etc. Finally, arbitrary textual information can be displayed as well.

You can see a short video on how to create a spReticle in Maya and set some of
the parameters here:

**Demo Video**

- http://vimeo.com/6186489 (from August 2009)

**Project Home**

- http://code.google.com/p/imageworks-maya-reticle

<br>

### Video

Here's what it looks like Maya 2020.

https://user-images.githubusercontent.com/2152766/141614140-444bd2ba-93f1-4ae5-928e-31d8eaa6977b.mp4

<br>

### Build

Use any Maya devkit from 2018 and above along with CMake to build on any platform.

```bash
git clone https://github.com/mottosso/spReticle.git
cd spReticle
mkdir build
cd build
export DEVKIT_LOCATION=/path/to/mayadevkit/2020/linux
cmake .. -GNinja
```

- **Linux** users, the above instructions are for you
- **MacOS** users, the above instructions are for you too
- **Windows** users, use `$env:DEVKIT_LOCATION` to set a variable with PowerShell
- **Windows** users, use `set DEVKIT_LOCATION` to set a variable with cmd.exe

The `defines.h` file concentrates all of the defines that can be used to
tailor the spReticle to your environment.

<br>

### Usage

spReticle consists of 3 files relevant for use.

1. `spReticleLoc.mll` goes into your `~/maya/2020/plug-ins` directory
1. `spReticleLoc.mel` goes into your `~/maya/scripts` directory
1. `AEspReticleLocTemplate.mel` goes into your `~/maya/scripts` directory

```py
from maya import cmds
cmds.loadPlugin("spReticleLoc")
cmds.createNode("spReticleLoc")
```

Alternatively, you can load `spReticleLoc.mll` from your build-directory by also adding the `.mel` files to your script path.

```py
import os
os.environ["MAYA_SCRIPT_PATH"] += os.pathsep + "C:\github\mottosso\spReticle"
cmds.loadPlugin("spReticleLoc")
```

<br>

### Texture Font Information

The freetype-gl library was used to generate most of font.h which contains
a texture font atlas.  The original copyright information is contained within
the header of the file.

<br>

### Code Structure

All of the source code files are located under the src directory.

| Source | Description
|:-------|:----
| `spReticleLoc`     | Main classes
| `GPURenderer`      | Abstract class for handling GPU Rendering
| `V2MUIDrawMgr`     | Handles VP2.0 rendering using the `MUIDrawManager` class in Maya 2018+
| `util.h`           | Utility classes
| `defines.h`        | Defines to drive compilation/options
| `spReticleLoc.mel` | MEL code to create a spReticle and potentially be invoked on `spReticleLoc` node instantiation to drive dynamic configuration
| `AEspReticleLocTemplate.mel` | Attribute Template for spReticle


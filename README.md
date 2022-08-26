# MXE: Multiple External Editors for [Houdini](https://www.sidefx.com/products/houdini/)
This is a modified version of [CGToolbox Houdini Expression Editor](http://cgtoolbox.com/houdini-expression-editor/) for Houdini that ships with [SideFXLabs](https://github.com/sideeffects/SideFXLabs). 

The main changes are:
1. Separate external editors for Python and VEX
2. Small changes to context menus to be more accessible
3. Uses Houdinis package system

There is a comparison of external editors and instructions to make them work with autocompletion and some other nice features for VEX and Python below. 

You can also use these instructions if you're using the original version of this extension that ships with SideFXLabs.

## Installation:

1. [Download the .zip file](https://github.com/peterprickarz/mxe/archive/refs/heads/main.zip)
2. Copy the "MXE" and "packages" folder to $HOME/houdiniXX.X folder(the houdini folder in your documents)

## Setting External Editors:

1. Open Houdini
2. Go to ```Edit``` -> ```Preferences``` -> ```MXE: Set Editor(Python)``` and select the executable of the editor you want to use.
3. Go to ```Edit``` -> ```Preferences``` -> ```MXE: Set Editor(Other)``` and select the executable of the editor you want to use.

## Usage:

### To edit Python SOP and Attribute Wrangle code:
1. Right click the code parameter field(or label) and select ```MXE: Edit```
2. Alternatively, create a hotkey for it under ```Edit``` -> ```Hotkeys``` and press it while holding your mouse above the parameter label

### To edit the hou.session module:
1. Go to ```Windows``` -> ```MXE: Python Source```

### To edit Python Modules of HDAs(Viewerstates, HDA Module, OnCreated etc):
1. Right click the HDA in the network pane
2. Hit ```MXE: Extra Sections```
3. Pick the module you want to modify and hit accept

**NOTE: The module has to exist beforehand. Create it inside the HDAs Type Properties!**

### To edit shelf tools:
1. Right click the Shelf Tool and hit ```MXE: Edit```

### Sending code back to Houdini:
To send the modified code from your editor to Houdini, just save it in your editor. The extension works using a filewatcher.

You can use autosave features of your editor as a sort of live editing feature. I don't recommend this though.


## Recommended editors to use:

|        |                                       [VSCode](https://code.visualstudio.com/)                                       |                                                        [PyCharm](https://www.jetbrains.com/pycharm/)                                                       |                                           [Sublime Text](https://www.sublimetext.com/)                                          |
|--------|:----------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------:|
| **Python** |                                          ✔️                                         |                                                            ✔️                                                           |                                                  ✔️                                                 |
| Pros   | - Great Autocompletion with Pylance <br> - Fast startup <br> - Decent project management features <br> - Clean UI  | - Great Autocompletion <br> - Relatively simple setup <br> - Great features for Python development <br> - You probably use it already anyways |                              - Fast startup <br> - Clean UI                              |
| Cons   |                 - Complex setup <br> - Lacks features compared to PyCharm                  |                                - Slow startup time <br> - Can be convoluted for simple scripts                                 |                              - Lacks basic features <br> - Bad Autocompletion                              |
| **VEX**    |                                          ✔️                                         |                                                            ❌                                                           |                                                  ✔️                                                 |
| Pros   |             - Good Autocompletion <br> - Plugin for opening docs of functions              |                                                            -                                                           | - Good Autocompletion <br> - Snippets(for loops etc.) <br> - VEX documentation in editor |
| Cons   |                            - No documentation in editor                             |                                                            -                                                           |                                       - Not free                                                           |

As you can see, VSCode is decent for both VEX and Python and has the advantage that you can do both in one editor. However, PyCharm is equally good or better for Python and Sublime Text is better for VEX. I recommend deciding this the following way:

Do you use PyCharm for other Python projects anyways? Use PyCharm for Python and Sublime Text for VEX.

You don't use PyCharm anyways? Choose freely between VSCode and PyCharm for Python.

Picked VSCode for Python? Choose VSCode for VEX aswell if you like to have everything in one editor. If you don't care, choose Sublime Text.

Picked PyCharm for Python? Use Sublime Text for VEX.

**NOTE: These are just my opinions, feel free to disagree and use whatever you want.**

## Configuration of external editors:

This section includes the configuration of all relevant external editors for Houdini. It's completely optional but I highly recommend it if you are going to use one of these.

### VSCode for Python:

#### Plugins:

1. [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
2. [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)

#### Autocompletion for hou module:

1. Go to ```File``` -> ```Preferences``` -> ```Settings```
2. Search for "extra paths"
3. Click on ```Edit in settings.json```
4. Add "$HFS/houdini/python3.7libs" to your "python.autoComplete.extraPaths"
5. Add "$HFS/houdini/python3.7libs" to your "python.analysis.extraPaths"
6. Set "python.defaultInterpreterPath" to "$HFS/python37/python.exe"
7. Restart VSCode

As an example, this is how it looks in my case(Note: Your paths should use ```\\``` or ```/```, not ```\```):
~~~    
{
    "python.autoComplete.extraPaths": [
      "C:\\Program Files (x86)\\Steam\\steamapps\\common\\Houdini Indie\\houdini\\python3.7libs"
    ],
    "python.defaultInterpreterPath": "C:\\PROGRA~2\\Steam\\STEAMA~1\\common\\HOUDIN~1\\python37\\python.exe",
    "python.analysis.extraPaths": [
      "C:\\Program Files (x86)\\Steam\\steamapps\\common\\Houdini Indie\\houdini\\python3.7libs"
    ],
}
~~~
### VSCode for VEX:

#### Plugins:

1. [VEX](https://marketplace.visualstudio.com/items?itemName=melmass.vex)
2. [Houdini Vex Help](https://marketplace.visualstudio.com/items?itemName=cgtoolbox-guillaume-jobst.houdinivexhelp)

### PyCharm for Python:

#### Autocompletion for hou module:

1. Go to ```File``` -> ```Settings```
2. Search for "interpreter" and select the Python Interpreter under your Project settings
3. Select "$HFS/python37/python.exe" as Python interpreter <br> (Example: ```C:\Program Files (x86)\Steam\steamapps\common\Houdini Indie\python37\python.exe```)
4. Click on the gear next to it and choose ```Show All...```
5. In the new window, click the ```Show paths for selected interpreter``` button(It's the last button in the row at the top)
6. In the new window, click the ```+``` button and navigate to your "$HFS/houdini/python3.7libs" folder and hit ```OK```<br>(Example: ```C:\Program Files (x86)\Steam\steamapps\common\Houdini Indie\houdini\python3.7libs```)
7. Apply your settings
8. Go to ```Help```->```Edit custom properties...```
9. Add the line ```idea.max.intellisense.filesize=5000```(The hou module exceeds the default limit) and save
10. Restart PyCharm

**NOTE: You can't be in LightEdit mode to set this up, you have to open files as a project!**

### Sublime Text for VEX:

1. Install the [VEX Plugin](https://github.com/teared/VEX) according to the instructions on that page
2. I recommend adding ```"auto_complete_use_history": true,``` to the settings under ```Preferences``` -> ```Settings```. Otherwise, the ordering of the autocomplete is not the best.

Example:
~~~
{
	"auto_complete_use_history": true,
}
~~~

### Sublime Text for Python:

1. Install the [Jedi Plugin](https://packagecontrol.io/packages/Jedi%20-%20Python%20autocompletion) according to the instructions on that page,
2. Go to ```Preferences``` -> ```Package Settings``` -> ```Jedi``` -> ```Settings - User```
3. Add "$HFS/houdini/python3.7libs" to your "python_package_paths"

Example:
~~~
{
  "python_package_paths": [       
    "C:/Program Files (x86)/Steam/steamapps/common/Houdini Indie/houdini/python3.7libs",
  ],
}
~~~

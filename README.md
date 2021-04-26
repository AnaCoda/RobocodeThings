# RobocodeThings
For putting my Robocode robots and setup instructions
https://robocode.sourceforge.io/

## Making robots outside of the default editor (Visual Studio Code)

### Compiling
Here is the line I use to compile my robocode robots from CMD (my robocode installation is in C:\Programs):\
`javac -verbose -encoding UTF-8 -classpath C:\Programs\robocode\libs\robocode.jar;C:\Programs\robocode\robots C:\Programs\robocode\robots\AD\RobotName.java`

The command that was run by the built-in IDE is\
`javac -verbose -encoding UTF-8 -classpath libs\robocode.jar;C:\Programs\robocode\robots C:\Programs\robocode\robots\sample\Corners.java`
which doesn't work if you don't run it from the robocode directory because of the relative libs\ path.

### Referencing the Robocode library in VSCode
When I first opened an example Robocode bot in VSCode, it looked like this:
![image](https://user-images.githubusercontent.com/20260142/116006447-96fae780-a5c8-11eb-9414-f4ef560c27d7.png)

If you don't already have it (I didn't) get the "Java Extension Pack" from the extension manager.
To add libs\robocode.jar as a library, expand Java projects on the left and click the '+' next to Referenced Libraries to choose it.
![image](https://user-images.githubusercontent.com/20260142/116006395-3d92b880-a5c8-11eb-84ae-065c88b4f568.png)\
Once it's added, all the Robocode library errors should go away.

### Compiling your robot with a simple shortcut
If you don't want to have to copy the compile command every time you start a new instance of VSCode or click into the terminal every time you want to compile, you can change keybindings.json to run the command when you press a shortcut.

Using the command palette, select "Preferences: Open Keyboard Shortcuts (JSON)"
![image](https://user-images.githubusercontent.com/20260142/116006583-1dafc480-a5c9-11eb-93d3-594dc1ca4216.png)

Choose the shortcut you want to use and add the command like this (edit the args compile line if your robocode installation is in a different location than mine):
```
// Place your key bindings in this file to override the defaults
[
    {
        "key": "ctrl+shift+j",
        "command": "workbench.action.terminal.sendSequence",
        "args": { "text": "javac -verbose -encoding UTF-8 -classpath C:\\Programs\\robocode\\libs\\robocode.jar;C:\\Programs\\robocode\\robots ${file}\u000D" }
    }
]
```

Now, when I press ctrl+shift+j, the robot.java file I'm viewing will be compiled. Hope this helps~

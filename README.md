# muddler

muddler is a build tool for Mudlet package developers. It aims to provide a development environment that will feel familiar for many developers and also be intuitive enough to pick up for those who have primarily done scripting for Mudlet.

## Goals and/or features

* Convention over configuration
  * Provide a standard directory and file structure for 'compiling' files into a Mudlet package
  * Allow the editing of your project and code in the editor of your choice, while still producing Mudlet objects
* Provide for the description of all standard mudlet objects in json format
* In particular allow for describing triggers in a clear Parent<->child manner, with all the options available in the UI in a json file. This is something I find it particularly onerous to do in pure Mudlet lua.
* provide a file which can be distributed across the platforms Mudlet is available for (Windows/OSX/Linux) and act as a build tool similar to maven or gradle. This is being accomplished using the gradle shadow plugin (<https://github.com/johnrengelman/shadow>) to create a fat jar during testing and distribution archives containing start scripts for multiple platforms.

## Usage

First, if you need help come find me on my discord: <https://discord.gg/SRRBpbxe34>
It is probably the fastest way to get ahold of me and get a resolution to your issue.
muddler largely relies upon adherence to the muddler convention. For instance, the filetree for animated timers looks like this:

```txt
C:\ANITIMERS
│   mfile
│
└───src
    ├───aliases
    │   └───AnimatedTimers
    │           aliases.json
    │           anitimer_demo.lua
    │
    ├───resources
    │       test1.jpg
    │       test5.jpg
    │
    ├───scripts
    │   └───AnimatedTimers
    │           code.lua
    │           scripts.json
    │
    └───timers
        └───AnimatedTimers
                animate.lua
                timers.json
```

Once your project is configured, simply `muddle` in the root directory and it will create a build directory, inside of which will be the .xml and .mpackage files it created.

There's more information in the wiki (if there isn't, sorry), be sure to check it out for better documentation.

## Currently working

* Scripts
* Triggers
* Aliases
* Timers
* Keybindings

## To-do

* Package uploads (with Mudlet package for accessing/searching the uploaded packages)
* Option to pull mudlet package apart and produce muddler project
* Variables? (is anyone using this in distribution packages?)
* Buttons
* I'm sure plenty of bug fixes

## Contributing

### Prerequisites

* Java JDK 8
* A Text Editor
* And a dream!
  * Ok maybe some groovy and/or java knowledge would help

### Building

`./gradlew clean shadowJar` produces an executable jar file with all of the depenendencies. This can be run using `java -jar </path/to/jarfile`

Alternately, `./gradlews clean dockerTest` will create the demonnic/muddler:test docker image locally for you to use in testing.

### Pull Requests

TODO: probably just don't be a dick and make sure you include information on how you tested it

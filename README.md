[![Known Vulnerabilities](https://snyk.io/test/github/intersystems-community/vscode-objectscript/badge.svg)](https://snyk.io/test/github/intersystems-community/vscode-objectscript)
![Visual Studio Marketplace Version](https://img.shields.io/visual-studio-marketplace/v/daimor.vscode-objectscript.svg)
[![](https://img.shields.io/visual-studio-marketplace/i/daimor.vscode-objectscript.svg)](https://marketplace.visualstudio.com/items?itemName=daimor.vscode-objectscript)

[![](https://img.shields.io/badge/InterSystems-IRIS-blue.svg)](https://www.intersystems.com/products/intersystems-iris/)
[![](https://img.shields.io/badge/InterSystems-Caché-blue.svg)](https://www.intersystems.com/products/cache/)
[![](https://img.shields.io/badge/InterSystems-Ensemble-blue.svg)](https://www.intersystems.com/products/ensemble/)

# vscode-objectscript

[InterSystems](http://www.intersystems.com/our-products/) ObjectScript language support for Visual Studio Code.


[CaretDev](https://caretdev.com/#products) provides commercial support services. [Request a Quote](https://caretdev.com/contact-us/).

On-line course from CaretDev - [Developing with VSCode ObjectScript – Easy Start](https://caretdev.com/courses/).


## Features

- InterSystems ObjectScript code highlighting support.
  ![example](https://raw.githubusercontent.com/intersystems-community/vscode-objectscript/master/images/screenshot.png)
- Debugging ObjectScript code
- Intellisense support for commands, system functions, and class members.
- Export existing sources to the working directory: press Cmd/Ctrl+Shift+P, type 'ObjectScript', press Enter.
- Save and compile a class: press <kbd>Ctrl</kbd>+<kbd>F7</kbd> (<kbd>⌘</kbd>+<kbd>F7</kbd>) or select "ObjectScript: Save and compile" from <kbd>Cmd</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> menu.
- Server Explorer with possibility to export items![ServerExplorer](https://raw.githubusercontent.com/intersystems-community/vscode-objectscript/master/images/explorer.png)
- Edit directly on server

## Installation

Install [Visual Studio Code](https://code.visualstudio.com/) first.

Open VSCode. Go to extensions and search for "ObjectScript" like it is shown on the attached screenshot and install it.
Or install from ObjectScript extension page on [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=daimor.vscode-objectscript)
![installation](https://raw.githubusercontent.com/intersystems-community/vscode-objectscript/master/images/installation.gif)

## Configure connection

To be able to use many plugin features, you need to configure the connection to Caché/IRIS server first. You can create or edit existing `.vscode/settings.json` file. So, your settings file may look something like this.
  ```JSON
  "objectscript.conn": {
    "active": true,
    "label": "LOCAL",
    "host": "127.0.0.1",
    "port": 52773,
    "username": "user",
    "password": "password",
    "ns": "USER",
    "https": false
  }
  ```

Or you can edit it through settings editor. Which you can open from menu *Code* > *Preferences* > *Settings* for macOS or *File* > *Preferences* > *Settings* for Windows, search for "workspace settings" through Command Palette [<kbd>⌘⇧P</kbd>/<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>] or by shortcut [<kbd>⌘</kbd>+<kbd>,</kbd>/<kbd>Ctrl</kbd>+<kbd>,</kbd>].

- Find a 'objectscript', do not forget to set `active` to `true`
  `port` should follow to web port of instance (usually by default, `57772` for Caché/Ensemble, `52773` for IRIS) ![Settings UI](https://raw.githubusercontent.com/intersystems-community/vscode-objectscript/master/images/settings.png)
- Change settings according to your Caché/IRIS instance
- You will see related output in "Output" while switched to "ObjectScript" channel (right drop-down menu on top of the output window)

## Notes

For Caché/IRIS instance with maximum security level, add `%Development` role for `/api/atelier/` web-application ( [More](https://community.intersystems.com/post/using-atelier-rest-api) )
If you are getting `ERROR #5540: SQLCODE: -99 Message: User xxx is not privileged for the operation` when you try to get/refresh class/routine/includes lists, grant a following SQL Procedure to your user on target namespace.
```SQL
GRANT EXECUTE ON %Library.RoutineMgr_StudioOpenDialog TO xxx
```

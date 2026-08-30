# MAME

A MAME emulator with mobile compatibility designed for running in pure JavaScript pre-ECMAScript 2015 (no WebAssembly). Simply open the link below, click the red icon, and select a ROM file in `ZIP` format from your computer; it will be loaded and booted automatically. For Neo Geo games, you must have the `neogeo.zip` BIOS file and add its contents to the game's ROM `ZIP` file.

## Links:

- [MAME emulator](https://lrusso.github.io/MAME/MAME.htm)
- [Demo booting a sample game](https://lrusso.github.io/MAME/MAME.htm?demo)

## Screenshots:

![alt screenshot1](https://lrusso.github.io/MAME/SCREENSHOT1.jpg)

![alt screenshot2](https://lrusso.github.io/MAME/SCREENSHOT2.jpg)

![alt screenshot3](https://lrusso.github.io/MAME/SCREENSHOT3.jpg)

![alt screenshot4](https://lrusso.github.io/MAME/SCREENSHOT4.jpg)

## How to use it:

Examples of loading local and online files can be found [here](https://github.com/lrusso/MAME/blob/main/MAME.htm#L137-L175) and [here](https://github.com/lrusso/MAME/blob/main/MAME.htm#L203-L236).

```js
embedMAME({
  container: "game",
  name: "samsho.zip",
  rom: romFile,
  soundEnabled: true,
  showMobileControls: true,
  backText: "BACK",
  soundText: "SOUND",
  loadText: "LOAD",
  saveText: "SAVE",
  coin: "Digit1",
  player1: {
    up: "ArrowUp",
    down: "ArrowDown",
    left: "ArrowLeft",
    right: "ArrowRight",
    start: "Enter",
    button1: "KeyA",
    button2: "KeyS",
    button3: "KeyD",
    button4: "KeyQ",
    button5: "KeyW",
    button6: "KeyE",
  },
  cbStarted: function cbStarted() {
    console.log("Emulator started.")
  },
})
```

| Parameter          |    Type     | Required | Default value | Description                |
| :----------------- | :---------: | :------: | :-----------: | :------------------------- |
| container          |   string    |   yes    |       –       | Target element ID.         |
| name               |   string    |   yes    |       –       | Zip filename.              |
| rom                | ArrayBuffer |   yes    |       –       | ROM file.                  |
| soundEnabled       |   boolean   |    no    |     true      | Initial sound state.       |
| showMobileControls |   boolean   |    no    |     false     | Show mobile controls.      |
| backText           |   string    |    no    |     BACK      | Text for the Back button.  |
| soundText          |   string    |    no    |     SOUND     | Text for the Sound button. |
| loadText           |   string    |    no    |     LOAD      | Text for the Load button.  |
| saveText           |   string    |    no    |     SAVE      | Text for the Save button.  |
| player1            |   object    |    no    |       –       | Player 1 keys.             |
| player2            |   object    |    no    |       –       | Player 2 keys.             |
| player3            |   object    |    no    |       –       | Player 3 keys.             |
| player4            |   object    |    no    |       –       | Player 4 keys.             |
| cbStarted          |  function   |    no    |       -       | Called on emulator start.  |

## Special keys:

| Action          | macOS Shortcut | Windows Shortcut | Safari Shortcut |
| :-------------- | :------------: | :--------------: | :-------------: |
| Save state      |  Command + 1   |     Ctrl + 1     |    Ctrl + 1     |
| Load state      |  Command + 2   |     Ctrl + 2     |    Ctrl + 2     |
| Toggle sound    |  Command + 3   |     Ctrl + 3     |    Ctrl + 3     |
| Fullscreen mode |  Command + F   |     Ctrl + F     |    Ctrl + F     |
| Reset game      |  Command + R   |     Ctrl + R     |    Ctrl + R     |

## Author's note:

This emulator is compatible with both Android and iOS devices. However, WebKit on iOS has historically lagged behind; for instance, it took nearly a decade for Apple to allow developers to set a custom download filename for an `a` tag. This feature was implemented recently on iOS, so you can now download the game state. Another three iOS quirks: 1) if a slow connection causes the script to take several seconds to load, WebKit may fail to initialize the AudioContext; 2) if you send Safari to the background and return to it, there will be no audio; 3) if you click on the file selector and it takes you several seconds to choose a ROM file, there will be no audio. In any case, a manual tap on the screen is required to enable or re-enable the audio.

## Main differences with the original project:

- Transpiled JS to pre-ES2015 via `node ConverterES5.js fbalpha2012.js`.
- Fixed graphical glitches in Caveman Ninja.

## This is a modified version of fbalpha2012:

https://github.com/lrusso/fbalpha2012

**NOTE:** Emscripten 4.0.23 was used to build the emulator.

## Virtual joystick code:

https://github.com/lrusso/VirtualJoystick

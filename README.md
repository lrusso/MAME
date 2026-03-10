# MAME

A MAME emulator designed for running in vanilla JavaScript pre-ECMAScript 2015 (no WebAssembly). Simply open the link below, click the red icon, and select a ROM file in `ZIP` format from your computer; it will be loaded and booted automatically. For Neo Geo games, you must have the `neogeo.zip` BIOS file and add its contents to the game's ROM `ZIP` file.

## Links:

- [MAME emulator](https://lrusso.github.io/MAME/MAME.htm)
- [Demo booting a sample game](https://lrusso.github.io/MAME/MAME.htm?demo)

## Screenshots:

![alt screenshot1](https://lrusso.github.io/MAME/SCREENSHOT1.jpg)

![alt screenshot2](https://lrusso.github.io/MAME/SCREENSHOT2.jpg)

![alt screenshot3](https://lrusso.github.io/MAME/SCREENSHOT3.jpg)

## How to use it:

Examples of loading local and online files can be found [here](https://github.com/lrusso/MAME/blob/main/MAME.htm#L128-L160) and [here](https://github.com/lrusso/MAME/blob/main/MAME.htm#L188-L215).

```js
embedMAME({
  container: "game",
  name: "samsho.zip",
  rom: romFile,
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

| Parameter |    Type     | Required | Default value | Description               |
| :-------- | :---------: | :------: | :-----------: | :------------------------ |
| container |   string    |   yes    |       –       | Target element ID.        |
| name      |   string    |   yes    |       –       | Zip filename.             |
| rom       | ArrayBuffer |   yes    |       –       | ROM file.                 |
| player1   |   object    |    no    |       –       | Player 1 keys.            |
| player2   |   object    |    no    |       –       | Player 2 keys.            |
| player3   |   object    |    no    |       –       | Player 3 keys.            |
| player4   |   object    |    no    |       –       | Player 4 keys.            |
| cbStarted |  function   |    no    |       -       | Called on emulator start. |

## Special keys:

| Action          | macOS Shortcut | Windows Shortcut | Safari Shortcut |
| :-------------- | :------------: | :--------------: | :-------------: |
| Save state      |  Command + 1   |     Ctrl + 1     |    Ctrl + 1     |
| Load state      |  Command + 2   |     Ctrl + 2     |    Ctrl + 2     |
| Toggle sound    |  Command + 3   |     Ctrl + 3     |    Ctrl + 3     |
| Fullscreen mode |  Command + F   |     Ctrl + F     |    Ctrl + F     |
| Reset game      |  Command + R   |     Ctrl + R     |    Ctrl + R     |

## Main differences with the original project:

- Transpiled JS to pre-ES2015 via `node ConverterES5.js fbalpha2012.js`.

## This is a modified version of fbalpha2012:

https://github.com/lrusso/fbalpha2012

**NOTE:** Emscripten 4.0.23 was used to build the emulator.

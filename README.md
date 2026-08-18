<p align="center">
  <img src="https://raw.githubusercontent.com/baonnecalt/potassium-bridge-releases/main/logo.png" width="110">
</p>

<h1 align="center">Potassium Bridge</h1>

<p align="center">
  <b>
  <a href="#install">install</a> ·
  <a href="#what-it-does">what it does</a> ·
  <a href="#shortcuts">shortcuts</a> ·
  <a href="#settings">settings</a>
  </b>
</p>

<p align="center">
  <a href="https://github.com/baonnecalt/potassium-bridge-releases/releases/latest">
    <img src="https://img.shields.io/github/downloads/baonnecalt/potassium-bridge-releases/total?style=for-the-badge&label=downloads&color=2ea043&v=2">
  </a>
  <a href="https://github.com/baonnecalt/potassium-bridge-releases/releases/latest">
    <img src="https://img.shields.io/github/v/release/baonnecalt/potassium-bridge-releases?style=for-the-badge&label=version&color=007ec6&v=2">
  </a>
  <img src="https://img.shields.io/badge/license-MIT-4c1?style=for-the-badge">
  <img src="https://img.shields.io/badge/platform-windows-0078d4?style=for-the-badge">
</p>

Save a Lua file in VS Code and it runs in Potassium. The roblox console comes back into
the editor, so you can stop alt-tabbing to press F9.

## install

1. Grab the `.vsix` from [the latest release](https://github.com/baonnecalt/potassium-bridge-releases/releases/latest).
2. In VS Code: `Ctrl+Shift+P` -> `Extensions: Install from VSIX...` -> pick the file.
   Or from a terminal:

   ```
   code --install-extension <indirdigin-dosya>.vsix
   ```
3. Run `Potassium Bridge: Install/update the roblox bridge script` from the command
   palette, restart VS Code, then start Potassium and inject.

The status bar reads `Connected to Potassium` when both sides can see each other.

## what it does

- **Save and run.** Every `.lua`, `.luau` or `.txt` you save is executed. Prefer a
  button? Set `mode` to `button` and one shows up in the status bar.
- **Console in the editor.** A `Potassium` tab in the terminal panel: `print` in white,
  `warn` in yellow, errors in red, no timestamps or prefixes.
- **Errors point at the line.** Turn on `problems` and a runtime error underlines the
  exact line and lists it in the Problems panel. Editing the file clears the marks.
- **Rejoining does not break it.** The link comes back on its own and anything you saved
  while the game was loading runs once you are in.
- **Discord presence**, off by default. Shows the file you are editing and whether the
  bridge is connected.
- **A kill switch.** Click the status bar text to stop sending, click again to resume.

## shortcuts

| | |
|---|---|
| `Ctrl+Alt+Enter` | run the current file |
| `Ctrl+Alt+O` | open the console |

Everything else is in the command palette under `Potassium Bridge:`.

## settings

| | default | |
|---|---|---|
| `potassiumBridge.mode` | `on save` | `on save` or `button` |
| `potassiumBridge.logs` | `mine` | `mine`, `all` or `off` |
| `potassiumBridge.problems` | `false` | mark errors in the code |
| `potassiumBridge.discord` | `false` | rich presence |

## how it works

No socket, no server. The extension drops your file into Potassium's workspace folder
and a Lua script in autoexec picks it up, runs it and deletes it. Files are written as
`.tmp` and renamed after, so the reader never sees half a script. Console output is
batched into a log file a few times a second and the editor tails it.

## author

Made by **baonnec**. MIT licensed.

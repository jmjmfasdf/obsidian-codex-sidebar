# Codex Sidebar

Run OpenAI Codex CLI in your Obsidian sidebar.

Based on Claude Sidebar by Derek Larson.

![Codex Sidebar](screenshot-obsidian.png)

## Features

- **Embedded terminal** - Full terminal in your Obsidian sidebar
- **Auto-launches Codex** - Codex CLI starts automatically
- **Multiple tabs** - Run multiple Codex instances side by side
- **Folder context menu** - Right-click any folder to open Codex in that directory
- **YOLO mode** - Launch Codex with `--yolo` via right-click menus

## Requirements

- macOS, Linux, or Windows (Windows is experimental)
- Python 3
- [Codex CLI](https://developers.openai.com/codex/cli)

## Installation

### Quick Install (macOS/Linux)

In your vault folder, run:
```bash
curl -sL https://github.com/jmjmfasdf/obsidian-codex-sidebar/archive/refs/heads/main.tar.gz | tar -xz -C .obsidian/plugins && mv .obsidian/plugins/obsidian-codex-sidebar-main .obsidian/plugins/codex-sidebar
```

Then in Obsidian: Settings ¡æ Community Plugins ¡æ Refresh ¡æ Enable "Codex Sidebar"

**Windows:** See [Windows Setup](#windows-setup-experimental) below.

### Manual Installation

1. Download `main.js`, `manifest.json`, and `styles.css` from the [latest release](https://github.com/jmjmfasdf/obsidian-codex-sidebar/releases)
2. Create folder: `<your-vault>/.obsidian/plugins/codex-sidebar/`
3. Copy the downloaded files into that folder
4. Reload Obsidian and enable the plugin in Settings ¡æ Community Plugins

### From Community Plugins

Once approved, you'll be able to search for "Codex Sidebar" in Community Plugins ¡æ Browse.

## Updating

In your vault folder, run:
```bash
cd .obsidian/plugins/codex-sidebar
curl -LO https://github.com/jmjmfasdf/obsidian-codex-sidebar/releases/latest/download/main.js
curl -LO https://github.com/jmjmfasdf/obsidian-codex-sidebar/releases/latest/download/manifest.json
curl -LO https://github.com/jmjmfasdf/obsidian-codex-sidebar/releases/latest/download/styles.css
```

Then restart Obsidian or disable/re-enable the plugin.

## Usage

- Click the bot icon in the left ribbon to open Codex
- Right-click the bot icon for YOLO mode (`--yolo`)
- Right-click any folder for "Open Codex here" or "Open Codex here (YOLO)"
- Use Command Palette (`Cmd+P`) for:
  - **Open Codex CLI** - Open or focus Codex panel
  - **New Codex Tab** - Open additional Codex instance
  - **Close Codex Tab** - Close current Codex tab (when focused)
  - **Toggle Focus: Editor ¡ê Codex** - Quick switch between editor and Codex
- Press `Shift+Enter` for multi-line input
- Set your own hotkeys in Settings ¡æ Hotkeys

## Platform Support

| Platform | Status |
|----------|--------|
| macOS | ? Supported |
| Linux | ? Supported |
| Windows | ?? Experimental |

### Windows Setup (Experimental)

Windows requires additional dependencies:

1. Install Python 3 from [python.org](https://python.org)
2. Install pywinpty:
```bash
pip install pywinpty
```

3. Install Codex CLI:
```bash
npm i -g @openai/codex
```

4. Install the plugin (run from your vault folder in PowerShell):
```powershell
$u="https://github.com/jmjmfasdf/obsidian-codex-sidebar/archive/main.zip"; Invoke-WebRequest $u -OutFile s.zip; Expand-Archive s.zip .obsidian\plugins -Force; Move-Item ".obsidian\plugins\obsidian-codex-sidebar-main" ".obsidian\plugins\codex-sidebar" -Force; Remove-Item s.zip
```

**Note:** Codex CLI on Windows is experimental. For the best experience, use Codex in a WSL workspace.

## How It Works

- [xterm.js](https://xtermjs.org/) for terminal emulation
- Python's built-in `pty` module for pseudo-terminal support (macOS/Linux)
- [pywinpty](https://github.com/andfoy/pywinpty) for Windows PTY support

## Development

The PTY scripts (`terminal_pty.py` for Unix, `terminal_win.py` for Windows) are embedded as base64 in `main.js` for Obsidian plugin directory compatibility. To rebuild after modifying:

```bash
./build.sh
```

## Contributing

Issues and PRs welcome at [github.com/jmjmfasdf/obsidian-codex-sidebar](https://github.com/jmjmfasdf/obsidian-codex-sidebar)

## License

MIT

# rclone WFX Plugin for Double Commander

A file system plugin that integrates [rclone](https://rclone.org/) with Double Commander, allowing you to browse and manage cloud storage remotes directly from the file manager.

## Features

- Browse all rclone-configured remotes
- Download files (F5 or drag)
- Upload files (F5 or drag)
- Create directories (F7)
- Delete files and directories (F8)
- Rename/Move files within the same remote (Shift+F6)
- Background transfers with progress reporting

## Prerequisites

- [rclone](https://rclone.org/install/) installed and configured with at least one remote
- [Double Commander](https://doublecmd.sourceforge.io/)

## Building

### Prerequisites

The plugin requires the Double Commander SDK headers. Clone the Double Commander source and place this plugin in the correct location:

```bash
# Clone Double Commander source
git clone https://github.com/doublecmd/doublecmd.git
cd doublecmd

# Clone this plugin into the plugins directory
git clone https://github.com/miklos-szel/rclone-wfx.git plugins/wfx/rclone
```

The expected directory structure:
```
doublecmd/
├── sdk/                    # SDK headers (from Double Commander source)
└── plugins/
    └── wfx/
        └── rclone/         # This plugin
```

### macOS

```bash
cd plugins/wfx/rclone/build
./build_macos.sh
```

The script will use `lazbuild` if available, or fall back to `fpc`, or offer to install via Homebrew.

To remove build artifacts:
```bash
./build_macos.sh clean
```

### Output

The compiled plugin is created at:
```
doublecmd/plugins/wfx/rclone/rclone.wfx
```

## Installation

1. Copy `rclone.wfx` and `rclone.ico` to Double Commander's plugins directory:

   **macOS:**
   ```bash
   mkdir -p ~/Library/Application\ Support/doublecmd/plugins/wfx/rclone
   cp rclone.wfx rclone.ico ~/Library/Application\ Support/doublecmd/plugins/wfx/rclone/
   ```

2. Register the plugin in Double Commander:
   - Open **Configuration** → **Options**
   - Navigate to **Plugins** → **File system plugins**
   - Click **Add** and select `rclone.wfx`

## Usage

1. Press `Cmd+L` (macOS) or `Ctrl+L` (Linux) to open the directory bar
2. Type `rclone://` and press Enter
3. Browse your configured remotes

## Troubleshooting

**No remotes shown:**
```bash
rclone listremotes
```
If empty, configure a remote with `rclone config`.

**rclone not found:**
Ensure rclone is in your PATH or install it from https://rclone.org/install/

## Author

Miklos Mukka Szel <contact@miklos-szel.com>

## License

Copyright (c) 2025 Miklos Mukka Szel

LGPL v2.1 or later. See [COPYING.LESSER.txt](COPYING.LESSER.txt).

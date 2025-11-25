# DBC Signal Viewer

A desktop application for viewing and exploring CAN DBC files.

## Features

- Load and parse DBC files
- Browse messages and signals in a tree view
- View signal details (start bit, length, factor, offset, unit, range)
- Extensible signal decoding via plugins
- J1939 SPN decoder included

## Screenshot

<!-- Screenshot will be added once UI is complete -->

## Usage

1. Open the application
2. File → Open DBC
3. Browse messages in the left panel
4. Click a signal to see details

## Requirements

- Windows 10/11
- .NET 8.0 Runtime

## Building from Source

```bash
git clone https://github.com/username/dbc-signal-viewer.git
cd dbc-signal-viewer
dotnet build
```

Or open `DbcSignalViewer.sln` in Visual Studio and build.

## Creating Plugins

See [ARCHITECTURE.md](ARCHITECTURE.md) for technical details on the plugin system.

## License

MIT

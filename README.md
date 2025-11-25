# DBC Signal Viewer

WPF application for viewing CAN DBC files with plugin-based signal decoding.

## Projects

| Project | Type | Description |
|---------|------|-------------|
| DbcSignalViewer | WPF App | Main host application |
| DbcSignalViewer.Contracts | Class Library | Shared interfaces for plugins |
| DbcSignalViewer.Plugins.J1939 | Class Library | J1939 SPN decoder plugin |

## Requirements

- .NET 8.0 SDK
- Windows (WPF)
- Visual Studio 2022 (recommended)

## Build

```bash
dotnet build DbcSignalViewer.sln
```

Or open `DbcSignalViewer.sln` in Visual Studio and build.

## Architecture

This project demonstrates plugin architecture in WPF:

```
DbcSignalViewer.Contracts    (Shared interfaces)
        │
        ├──────────────────────────┐
        │                          │
        ▼                          ▼
DbcSignalViewer              DbcSignalViewer.Plugins.J1939
(Host WPF App)               (Plugin - loaded at runtime)
```

- Host discovers plugins at runtime from the `plugins/` folder
- Plugins implement `ISignalDecoder` from Contracts
- Host and plugins communicate only through shared interfaces
- New plugins can be added without modifying the host

## NuGet Packages

| Package | Project | Purpose |
|---------|---------|---------|
| CommunityToolkit.Mvvm | Host | MVVM framework |
| Microsoft.Extensions.DependencyInjection | Host | Dependency injection |
| DbcParserLib | Host | DBC file parsing |

## License

MIT

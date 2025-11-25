# Architecture

Technical documentation for developers.

## Projects

| Project | Type | Description |
|---------|------|-------------|
| DbcSignalViewer | WPF App | Main host application |
| DbcSignalViewer.Contracts | Class Library | Shared interfaces for plugins |
| DbcSignalViewer.Plugins.J1939 | Class Library | J1939 SPN decoder plugin |

## Plugin Architecture

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

## Project References

| Project | References |
|---------|------------|
| Contracts | Nothing |
| DbcSignalViewer (Host) | Contracts |
| Plugins.J1939 | Contracts only |

**Rule:** Plugins never reference the Host.

## NuGet Packages

| Package | Project | Purpose |
|---------|---------|---------|
| CommunityToolkit.Mvvm | Host | MVVM framework |
| Microsoft.Extensions.DependencyInjection | Host | Dependency injection |
| DbcParserLib | Host | DBC file parsing |

## Creating a New Plugin

1. Create a new Class Library project targeting .NET 8.0
2. Reference only `DbcSignalViewer.Contracts`
3. Implement `ISignalDecoder` interface
4. Build and copy DLL to `plugins/` folder

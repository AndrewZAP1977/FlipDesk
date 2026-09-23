# Changelog

All notable user-facing changes to FlipDesk are documented here.

## [0.1.0]

Initial public release of FlipDesk for Windows 11 x64.

### Added

- Real Windows Explorer Desktop integrated into the FlipDesk page sequence without replacing or redirecting the native Desktop.
- Additional virtual desktop pages with stable page identity and independent contents/layout.
- Page creation, rename, delete, reorder, direct page selection, and Page Manager.
- Keyboard and mouse page navigation.
- Built-in help overlay.
- Single and multiple item selection, Ctrl-click, rectangle/lasso selection, and item repositioning on virtual pages.
- File, folder, shortcut, and external-reference support.
- External and broken-reference indicators.
- Shell context-menu integration with a safe fallback menu.
- Explicit transfer UI for moving or copying selected objects between the real Desktop and virtual pages.
- Windows-like collision naming such as `name (1).ext`.
- Native Desktop icon placement through the supported Windows Shell API.
- Settings, tray icon, optional autostart, light/dark theme, and Russian/English interface.
- Single-instance activation.
- State backups, full backups, Backup Center, and guarded restore/restart flows.
- Separate Development and Release runtime profiles so development builds do not share Release pages, settings, backups, autostart identity, or single-instance identity.
- Versioned self-contained Windows 11 x64 release packaging.
- Inno Setup installer packaging with SHA-256 checksum generation.

### Safety and data handling

- FlipDesk does not replace the Windows Desktop with a junction or symlink.
- FlipDesk does not redirect the Windows Desktop Known Folder through the Registry.
- Files are not automatically moved away from the real Desktop.
- Moving a Desktop object to a virtual page requires an explicit user action and is limited to supported regular filesystem objects.
- Public Desktop and Windows shell/system objects are not physically moved by the transfer flow.
- Removing an ordinary external reference from a virtual page does not delete its original external file.
- Uninstall is designed to preserve FlipDesk user pages, settings, and backups.

# Changelog

All notable user-facing changes to FlipDesk are documented here.

## [0.1.2]

Maintenance release simplifying FlipDesk global input and startup architecture.

### Fixed

- Fixed Ctrl+Alt+mouse-wheel page navigation, Ctrl+Alt+Shift help, and Ctrl+Alt+middle-click Desktop navigation when an elevated application owns the foreground.

### Changed

- FlipDesk now runs elevated in production instead of relying on a separate elevated InputBroker.
- Removed the InputBroker process, executable, IPC bridge, startup gate, runtime-loss monitoring, and broker scheduled task from the production architecture.
- Start with Windows now uses a per-user scheduled task with interactive logon and highest privileges so elevated FlipDesk can start without a UAC prompt at sign-in.
- Debug builds remain non-elevated and keep their separate development autostart behavior.
- Release packaging is simplified to a single `FlipDesk.exe`.
- The installer removes obsolete InputBroker components from previous installations while preserving FlipDesk user data and the previous autostart preference.

## [0.1.1]

Maintenance release focused on reliable global input after Windows sign-in.

### Fixed

- Fixed Ctrl+Alt+mouse-wheel page navigation when another elevated application owns the foreground immediately after sign-in.
- Fixed the Ctrl+Alt+Shift help overlay and Ctrl+Alt+middle-click Desktop jump in the same elevated-foreground scenario.
- FlipDesk now fails clearly at startup instead of silently running with incomplete global controls when its required input component is unavailable.
- FlipDesk now also reports and closes if the required input component stops unexpectedly while FlipDesk is running.

### Changed

- Added a required elevated InputBroker for global keyboard/modifier and mouse input while the main FlipDesk process remains non-elevated.
- The installer now uses a protected Program Files installation and configures the InputBroker to start at logon with highest privileges.
- Upgrading from the per-user 0.1.0 installation migrates to the protected installation while preserving FlipDesk user data.
- Release packaging now includes both `FlipDesk.exe` and `FlipDesk.InputBroker.exe` inside the installer build.

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

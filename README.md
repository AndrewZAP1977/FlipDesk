# FlipDesk

[English](#readme-en) | [Русский](#readme-ru)

<a id="readme-en"></a>

## English

**Virtual desktop pages for Windows 11**

FlipDesk is a Windows application that adds additional desktop pages while keeping the real Windows Explorer Desktop intact.

It is designed for users who want more room for desktop files, folders and shortcuts without replacing the native Desktop folder or redirecting Windows shell paths.

### What FlipDesk does

FlipDesk provides:

- the real Windows Desktop as part of the page sequence;
- additional virtual desktop pages with their own items and icon layout;
- page creation, rename, deletion and reordering;
- direct page selection through Page Manager;
- keyboard and mouse navigation between pages;
- files, folders, shortcuts and external references on virtual pages;
- multiple selection, rectangle/lasso selection and item positioning;
- explicit transfer of selected objects between the real Desktop and FlipDesk pages;
- settings, tray icon and optional autostart;
- light and dark themes;
- Russian and English interface;
- separate State V2 and Full V2 backup histories;
- guarded restore and recovery flows;
- single-instance activation.

FlipDesk does **not** replace the Windows Desktop with a junction or symlink and does not redirect the Windows Desktop Known Folder.

### Navigation

Keyboard shortcuts:

- `Ctrl+Alt+Left` — previous page;
- `Ctrl+Alt+Right` — next page;
- `Ctrl+Alt+Up` — real Windows Desktop;
- `Ctrl+Alt+S` — transfer selected objects;
- `Ctrl+Alt+P` — open or close Page Manager / settings;
- `Ctrl+Alt+Shift+Left` — create a page on the left;
- `Ctrl+Alt+Shift+Right` — create a page on the right;
- `Ctrl+Alt+Shift+X` — delete the current virtual page;
- `Ctrl+Alt+Shift+Q` — exit FlipDesk.

Hold `Ctrl+Alt+Shift` to display the built-in help overlay.

While holding `Ctrl+Alt`:

- mouse wheel forward/up — next page;
- mouse wheel backward/down — previous page;
- middle mouse button — real Windows Desktop.

### Moving objects between Desktop and FlipDesk

Transfers are always explicit. FlipDesk does not automatically move files away from the real Desktop.

For supported regular files and folders on the user's Desktop:

- **Copy to a FlipDesk page** keeps the original object on the Desktop;
- **Move to a FlipDesk page** moves the object into FlipDesk-owned page storage;
- **Copy an external reference back to Desktop** creates a Windows shortcut (`.lnk`) to the original object;
- **Move an external reference back to Desktop** creates the shortcut and removes the reference from the FlipDesk page; the original external object is not moved.

Windows shell/system items and unsupported Desktop objects are not physically moved.

### Data safety

Release data is stored separately from the installed program:

- settings and application state: `%LOCALAPPDATA%\FlipDesk\`;
- FlipDesk-owned page files: `%USERPROFILE%\FlipDesk\Pages\`;
- State V2 snapshots: `%LOCALAPPDATA%\FlipDesk\Backups\V2\State\`;
- Full V2 snapshots: by default, `%LOCALAPPDATA%\FlipDesk\Backups\V2\Full\`. A user-selected Full backup location uses a separate V2 store.

When daily Full V2 backups are enabled, FlipDesk creates a daily snapshot when due (no more than one per day). An initial snapshot can be large, depending on the desktop files included. State V2 snapshots are maintained separately and can also be saved manually.

Uninstalling FlipDesk is designed to remove the application itself, **not** your page files, settings or backup data. V2 does **not** automatically migrate, restore or delete older V1 backup archives.

<details>
<summary><h3>Backup and recovery (0.1.4 / V2)</h3></summary>

Open **Settings → Backup Center**. There are two separate histories:

| Backup | Includes | Best for |
| --- | --- | --- |
| **FlipDesk settings (State V2)** | Page list/order, virtual-page layout/references and application settings; **not** the contents of Windows documents. | Rolling back FlipDesk settings without changing original files. |
| **Desktop files and settings (Full V2)** | Copyable files within the backup plan (including Desktop content), together with the same FlipDesk state. Some external references are recorded as metadata only. | Recovering documents or returning both supported files and FlipDesk settings to an earlier snapshot. |

**State V2 — FlipDesk settings**

- Use **Back up now**, select a saved snapshot, then **Restore** or **Delete copy**. Deletion affects only the selected State V2 snapshot.
- State snapshots can also be created automatically when the application state changes. There is no requirement to type a technical snapshot ID.
- Restoring a selected State V2 snapshot requires confirmation and a FlipDesk restart. It **does not overwrite Windows user files**.

**Full V2 — desktop files and settings**

- **Back up now** saves a manual snapshot. The lock symbol identifies a manual copy **protected from automatic daily cleanup**; it can still be deleted manually after confirmation.
- When enabled, a daily Full V2 snapshot is created when due. Automatic retention keeps the newest **7 daily copies**. **Clean up storage…** removes excess daily copies, never manual ones; unreferenced stored file data is reclaimed.
- **Restore** first verifies the snapshot and previews counts of files to replace, missing files to return, unchanged files, and files/directories excluded for safety. Nothing is changed before the final confirmation.
- Confirmed **Restore** returns eligible files to their **original paths** and applies the saved FlipDesk state after restart. Files that exist now but were not in the snapshot are **not deleted**. Existing files being replaced are retained for transaction rollback if recovery fails.
- Automatic restore is limited to permitted paths within the user's profile. **Public Desktop** items and other restricted locations may be backed up but are **skipped during automatic restore**, with a warning in the preview.
- **Extract to folder…** copies the selected Full V2 snapshot to a **new separate folder**, including its files, three State JSON files and an `original-paths.json` map. It verifies copied data and does not overwrite the live Desktop. Use this method to retrieve individual files or skipped Public Desktop items manually.
- There is **no separate “Files only” whole-snapshot restore mode** or direct single-file restore action in the V2 backup history. For individual-file recovery, extract the backup first.

**Important limitations:** Native Windows Explorer Desktop icon positions are **not restored** by State V2 or Full V2. Older V1 backups remain untouched and cannot be restored through the V2 interface.

</details>

### System requirements

- Windows 11 x64;
- no separate .NET installation is planned to be required for the normal release package because FlipDesk is packaged as a self-contained application.

### Download and installation

Download the installer from the GitHub [Releases](https://github.com/AndrewZAP1977/FlipDesk/releases) page.

Each release includes a SHA-256 checksum for verification.

### Reporting problems

Report bugs and suggest improvements through [GitHub Issues](https://github.com/AndrewZAP1977/FlipDesk/issues).

When reporting a problem, please include:

- FlipDesk version;
- Windows 11 version/build;
- what you expected;
- what actually happened;
- exact steps to reproduce the problem.

### Changelog

Information about changes in published FlipDesk versions is provided in [CHANGELOG.md](CHANGELOG.md).

### Repository scope

This public repository is used for:

- published FlipDesk releases;
- release notes and changelog;
- user-facing documentation;
- issue tracking.

[Back to languages](#flipdesk)

---

<a id="readme-ru"></a>

## Русский

**Виртуальные страницы рабочего стола для Windows 11**

FlipDesk — это приложение для Windows, которое добавляет дополнительные страницы рабочего стола, сохраняя настоящий рабочий стол Windows Explorer без изменений.

Программа предназначена для пользователей, которым нужно больше места для файлов, папок и ярлыков рабочего стола без замены системной папки Desktop и без перенаправления путей Windows Shell.

### Что делает FlipDesk

FlipDesk предоставляет:

- настоящий рабочий стол Windows как часть общей последовательности страниц;
- дополнительные виртуальные страницы рабочего стола со своим содержимым и раскладкой значков;
- создание, переименование, удаление и изменение порядка страниц;
- прямой выбор страницы через Page Manager;
- навигацию между страницами с клавиатуры и мыши;
- работу с файлами, папками, ярлыками и внешними ссылками на виртуальных страницах;
- множественное выделение, прямоугольное/lasso-выделение и размещение объектов;
- явный перенос выбранных объектов между настоящим Desktop и страницами FlipDesk;
- настройки, значок в системном трее и опциональный автозапуск;
- светлую и тёмную темы;
- русский и английский интерфейс;
- отдельные истории резервных копий State V2 и Full V2;
- защищённые сценарии восстановления;
- single-instance activation.

FlipDesk **не** заменяет настоящий рабочий стол Windows через junction или symlink и не перенаправляет системную папку Desktop через Windows Registry.

### Навигация

Горячие клавиши:

- `Ctrl+Alt+Left` — предыдущая страница;
- `Ctrl+Alt+Right` — следующая страница;
- `Ctrl+Alt+Up` — настоящий рабочий стол Windows;
- `Ctrl+Alt+S` — перенос выбранных объектов;
- `Ctrl+Alt+P` — открыть или закрыть Page Manager / настройки;
- `Ctrl+Alt+Shift+Left` — создать страницу слева;
- `Ctrl+Alt+Shift+Right` — создать страницу справа;
- `Ctrl+Alt+Shift+X` — удалить текущую виртуальную страницу;
- `Ctrl+Alt+Shift+Q` — выход из FlipDesk.

При удержании `Ctrl+Alt+Shift` отображается встроенная справка.

При удержании `Ctrl+Alt`:

- колесо мыши вперёд/вверх — следующая страница;
- колесо мыши назад/вниз — предыдущая страница;
- средняя кнопка мыши — настоящий рабочий стол Windows.

### Перенос объектов между Desktop и FlipDesk

Все операции переноса выполняются только явно по команде пользователя. FlipDesk не переносит файлы с настоящего рабочего стола автоматически.

Для поддерживаемых обычных файлов и папок пользовательского Desktop:

- **Copy на страницу FlipDesk** оставляет исходный объект на Desktop;
- **Move на страницу FlipDesk** физически переносит объект в хранилище, принадлежащее FlipDesk;
- **Copy внешней ссылки обратно на Desktop** создаёт ярлык Windows (`.lnk`) на исходный объект;
- **Move внешней ссылки обратно на Desktop** создаёт ярлык и удаляет ссылку с виртуальной страницы; исходный внешний объект не перемещается.

Системные объекты Windows Shell и неподдерживаемые объекты Desktop физически не перемещаются.

### Безопасность данных

Данные Release-версии хранятся отдельно от установленной программы:

- настройки и состояние приложения: `%LOCALAPPDATA%\FlipDesk\`;
- файлы страниц, принадлежащие FlipDesk: `%USERPROFILE%\FlipDesk\Pages\`;
- копии State V2: `%LOCALAPPDATA%\FlipDesk\Backups\V2\State\`;
- копии Full V2: по умолчанию `%LOCALAPPDATA%\FlipDesk\Backups\V2\Full\`. Для выбранного пользователем места хранения применяется отдельное V2-хранилище.

Если ежедневное копирование Full V2 включено, FlipDesk создаёт копию при наступлении очередного дня (не более одной за день). Первая копия может занимать значительный объём — в зависимости от файлов рабочего стола. Копии настроек State V2 хранятся отдельно, их также можно создавать вручную.

При удалении FlipDesk должны сохраняться **файлы страниц, настройки и резервные копии**. Старые архивы V1 новая система V2 автоматически не переносит, не восстанавливает и не удаляет.

<details>
<summary><h3>Резервное копирование и восстановление (0.1.4 / V2)</h3></summary>

Открой **«Настройки» → «Резервное копирование»**. В программе две отдельные истории:

| Тип копии | Что сохраняется | Когда использовать |
| --- | --- | --- |
| **Настройки FlipDesk (State V2)** | Список и порядок страниц, раскладка и ссылки на виртуальных страницах, настройки программы. **Содержимое документов Windows не копируется.** | Вернуть прежние настройки FlipDesk без изменения оригинальных файлов. |
| **Файлы рабочих столов и настройки (Full V2)** | Копируемые файлы из плана резервирования (включая файлы рабочего стола) и состояние FlipDesk. Некоторые внешние ссылки сохраняются только как сведения о путях. | Получить файлы или восстановить разрешённые файлы вместе с настройками программы. |

**State V2 — настройки FlipDesk**

- Кнопка **«Сохранить сейчас»** создаёт копию. В истории можно выбрать копию и нажать **«Восстановить»** или **«Удалить копию»**. Удаляется только выбранная копия.
- Копии состояния могут также создаваться автоматически после его изменений. Вводить технический идентификатор копии не требуется.
- Восстановление требует подтверждения и перезапуска FlipDesk. **Исходные пользовательские файлы Windows при этом не перезаписываются.**

**Full V2 — файлы рабочих столов и настройки**

- **«Сохранить сейчас»** создаёт ручную копию. Замочек обозначает защиту **от автоматической очистки**, но не запрещает удаление вручную после подтверждения.
- При включённой настройке ежедневная копия создаётся при наступлении нового дня. Автоматически хранятся **7 последних ежедневных копий**. Кнопка **«Очистка хранилища…»** удаляет лишние ежедневные копии, не затрагивая ручные; невостребованные данные в хранилище очищаются.
- **«Восстановить»** сначала проверяет копию и показывает число заменяемых, отсутствующих и неизменённых файлов, а также объектов, исключённых по требованиям безопасности. До окончательного подтверждения файлы не меняются.
- После подтверждения поддерживаемые файлы возвращаются **на исходные пути**, а настройки FlipDesk применяются после перезапуска. Новые файлы, отсутствовавшие в копии, **не удаляются**. Для заменяемых файлов предусмотрено сохранение предыдущих версий для аварийного отката.
- Автоматическое восстановление разрешено только в защищённой области личного профиля. Файлы **общего рабочего стола (`Public Desktop`)** и другие запрещённые пути могут входить в копию, но при автоматическом восстановлении **пропускаются** с предупреждением.
- **«Извлечь в папку…»** создаёт **отдельный новый каталог** с файлами, тремя JSON-файлами состояния и картой `original-paths.json`. Данные проверяются при извлечении, исходные файлы рабочего стола не перезаписываются. Так можно вручную получить отдельный файл или объект из `Public Desktop`.
- В истории Full V2 **нет отдельного режима «Только файлы»** и кнопки прямого восстановления одного файла. Для выборочного получения документов сначала используй извлечение в отдельную папку.

**Важные ограничения:** расположение значков настоящего рабочего стола Windows Explorer **не восстанавливается** из State V2 или Full V2. Старые архивы V1 не изменяются и не поддерживаются интерфейсом восстановления V2.

</details>

### Системные требования

- Windows 11 x64;
- отдельная установка .NET для обычного Release-пакета не планируется, так как FlipDesk собирается как self-contained приложение.

### Загрузка и установка

Официальный установщик доступен на странице GitHub [Releases](https://github.com/AndrewZAP1977/FlipDesk/releases).

Каждый релиз также содержит контрольную сумму SHA-256 для проверки файла.

### Сообщение о проблемах

Сообщайте об ошибках и предлагайте улучшения через [GitHub Issues](https://github.com/AndrewZAP1977/FlipDesk/issues).

При сообщении об ошибке желательно указать:

- версию FlipDesk;
- версию/сборку Windows 11;
- что ожидалось;
- что произошло фактически;
- точные шаги для воспроизведения проблемы.

### История изменений

Сведения об изменениях в опубликованных версиях FlipDesk приведены в [CHANGELOG.md](CHANGELOG.md).

### Назначение репозитория

Этот публичный репозиторий используется для:

- опубликованных релизов FlipDesk;
- release notes и истории изменений;
- пользовательской документации;
- учёта проблем через Issues.

[К выбору языка](#flipdesk)
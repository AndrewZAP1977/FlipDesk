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
- guarded Full V2 restore of eligible Desktop files, settings and saved Explorer icon positions;
- protected pre-restore safety snapshots and recovery flows;
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
<summary><h3>Backup and recovery (0.1.5 / V2)</h3></summary>

Open **Settings → Backup Center**. There are two separate backup histories:

| Backup | Includes | Best for |
| --- | --- | --- |
| **FlipDesk settings (State V2)** | Page list and order, virtual-page layout/references and application settings; **no Windows document contents**. | Restoring FlipDesk settings without changing user files. |
| **Desktop files and settings (Full V2)** | Supported files from the backup plan, FlipDesk settings and, when present, saved native Explorer Desktop icon positions. Some external references are metadata only. | Restoring eligible Desktop files, settings and saved icon positions together. |

**State V2 — FlipDesk settings**

- **Back up now** saves settings. Select a snapshot to **Restore** or **Delete copy**; deletion affects only the selected snapshot.
- State snapshots may also be created automatically when settings or pages change.
- Restoring State V2 requires confirmation and a FlipDesk restart. It **does not overwrite Windows documents or restore native Explorer Desktop icon positions**.

**Full V2 — Desktop files, settings and saved icon positions**

- **Back up now** creates a manual backup. A lock means protection from automatic daily cleanup, **not** from confirmed manual deletion.
- When daily backups are enabled, FlipDesk keeps the **7 most recent daily Full V2 backups**. **Clean up storage…** removes excess daily copies and unreferenced stored data; manual and pre-restore safety copies are excluded from automatic daily cleanup.
- Select a backup and click **Restore**. FlipDesk validates it and shows a compact confirmation. Optional **What will change?** details show files to replace, restore, leave unchanged or skip.
- **Before changing any files**, FlipDesk creates and validates a separate **Full V2 safety backup of the current files, settings and native icon layout**. If this fails, restoration does not begin. Safety copies stay in history until manually deleted; new labels show both the safety-copy time and the selected backup's time.
- After confirmation, eligible files return to their **original paths** and FlipDesk settings are restored through a guarded restart. Native Explorer icon positions are checked and restored **after restart**, when the chosen backup has compatible saved layout data.
- If another icon occupies a saved position, FlipDesk tries to move it to a safe free position. **New files are not deleted.** If safe placement is impossible, it does not force icon movement. Validation, durable recovery records and rollback safeguards protect the operation.
- **Full V2 backups made with 0.1.4 remain usable for restoring files and settings.** Older backups may lack saved native icon positions; in that case, FlipDesk reports this and does not restore the native icon layout.
- Full V2 can restore backed-up **Public Desktop** files to their original paths when Windows permits writing there (administrator rights may be required). Protected shell/system items and unsupported locations remain excluded. Skipped files can be retrieved using **Extract to folder…**.
- **Extract to folder…** exports the selected Full V2 backup into a **separate new folder** with supported files, State JSON files and an original-path map, without overwriting the live Desktop. Use this for individual-file recovery.
- Backup history has **no separate Files-only full-snapshot restore mode** and no direct one-file restore button.

**Important:** State V2 does not restore native Explorer Desktop icon positions. Full V2 can restore them only if the selected backup contains supported layout data and the current Desktop configuration passes safety checks. Legacy V1 archives remain untouched and cannot be restored through the V2 interface.

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
- защищённое восстановление файлов, настроек и сохранённого расположения значков Explorer из Full V2;
- страховочные копии перед восстановлением и аварийную защиту;
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
<summary><h3>Резервное копирование и восстановление (0.1.5 / V2)</h3></summary>

Открой **«Настройки» → «Резервное копирование»**. В программе две отдельные истории:

| Тип копии | Что сохраняется | Когда использовать |
| --- | --- | --- |
| **Настройки FlipDesk (State V2)** | Список и порядок страниц, расположение объектов на виртуальных страницах, ссылки и настройки программы; **без содержимого документов Windows**. | Вернуть настройки без изменения пользовательских файлов. |
| **Файлы рабочих столов и настройки (Full V2)** | Поддерживаемые файлы из плана резервирования, настройки FlipDesk и, при наличии, сохранённые координаты значков настоящего Desktop в Explorer. Часть внешних ссылок записывается только как метаданные. | Восстановить разрешённые файлы, настройки и расположение значков вместе. |

**State V2 — настройки FlipDesk**

- **«Сохранить сейчас»** создаёт копию настроек. Выбранную копию можно **восстановить** или **удалить**, не затрагивая остальные.
- Копии состояния также могут создаваться автоматически после изменения страниц и настроек.
- Для восстановления требуются подтверждение и перезапуск FlipDesk. **Файлы документов Windows не перезаписываются, а координаты значков настоящего Desktop не восстанавливаются.**

**Full V2 — файлы, настройки и расположение значков**

- **«Сохранить сейчас»** создаёт ручную копию. Замочек обозначает защиту от автоматической очистки, **но выбранную копию можно удалить вручную после подтверждения**.
- При включённом ежедневном резервировании хранятся **7 последних ежедневных копий Full V2**. **«Очистка хранилища…»** удаляет лишние ежедневные копии и невостребованные данные, не затрагивая автоматически ручные и страховочные копии.
- Выбери копию и нажми **«Восстановить»**. FlipDesk проверит её и покажет компактное подтверждение. Подробности о заменяемых, возвращаемых, неизменённых и пропускаемых файлах доступны в разделе **«Что изменится?»**.
- **До изменения файлов** FlipDesk создаёт и проверяет отдельную **страховочную полную копию текущих файлов, настроек и расположения значков**. Если это не удалось, восстановление не начинается. Страховочная копия сохраняется до ручного удаления; новые названия содержат время её создания и дату выбранной копии.
- После подтверждения поддерживаемые файлы возвращаются **на исходные пути**, а настройки FlipDesk применяются через защищённую процедуру с перезапуском. Сохранённая расстановка значков настоящего Desktop проверяется и восстанавливается **после перезапуска**, если в выбранной копии есть совместимые данные.
- Если нужное место занято другим значком, FlipDesk пытается перенести его в безопасную свободную ячейку. **Новые файлы не удаляются.** При невозможности безопасного размещения принудительная перестановка не выполняется. Предусмотрены проверки, журналы восстановления и защита с откатом.
- **Копии Full V2, созданные в 0.1.4, остаются пригодными для восстановления файлов и настроек.** В старых копиях может не быть координат Explorer; тогда программа сообщит об этом и не будет восстанавливать расстановку значков.
- Full V2 может восстанавливать сохранённые файлы **общего рабочего стола (Public Desktop)** на исходные пути, если Windows разрешает запись (могут потребоваться права администратора). Системные объекты Explorer и другие защищённые или неподдерживаемые пути по-прежнему исключаются. Пропущенные файлы можно получить через **«Извлечь в папку…»**.
- **«Извлечь в папку…»** создаёт **отдельную папку** с поддерживаемыми файлами, JSON-файлами состояния и картой исходных путей, не перезаписывая действующий Desktop. Так можно получить отдельные документы.
- В Full V2 **нет отдельного режима «Только файлы»** и кнопки прямого восстановления одного файла.

**Важно:** State V2 не восстанавливает расположение значков настоящего рабочего стола. Full V2 делает это только при наличии совместимых данных в выбранной копии и прохождении проверок безопасности Explorer. Старые архивы V1 остаются нетронутыми и не восстанавливаются через интерфейс V2.

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
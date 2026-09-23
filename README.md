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
- state and full backup support;
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
- state/full backups: under FlipDesk backup storage or a user-selected backup location.

On first launch, FlipDesk automatically creates an initial full backup of the user's Windows Desktop and the Public Desktop. This backup serves as a recovery point in case the user later decides to remove FlipDesk after moving items to virtual pages, or needs to restore the original desktop state. The size of the first backup depends on the amount of data stored on the desktops and may be significant.

Uninstalling FlipDesk is designed to remove the application itself, **not** your pages, settings or backups. The initial backup therefore remains on disk and can be used for later recovery, including after reinstalling FlipDesk.

<details>
<summary><h3>Backup and recovery</h3></summary>

FlipDesk uses two separate backup layers:

| Backup type | What it protects | When to use it |
| --- | --- | --- |
| **FlipDesk restore point** | FlipDesk settings, page list/order, and virtual-page layout/references. **Real user files are not included.** | When you need to roll back FlipDesk settings or page structure without restoring files. |
| **Full file backup** | Copyable real files covered by the backup plan, plus FlipDesk state. System-managed paths can be stored as references only. | When you need to recover real files, or restore files and FlipDesk state together. |

**FlipDesk restore points**

- Restore points are small and are created automatically around FlipDesk state changes.
- Up to **20** restore points are retained.
- **Restore state** restores FlipDesk settings/page state only; it does not restore real user files.
- Applying a restore point uses the guarded restore flow and restarts FlipDesk.

**Full backups**

- **Daily full backup** runs on the first FlipDesk launch of the day when enabled.
- FlipDesk keeps the latest **7 daily** full snapshots.
- **Manual** backups and **safety** snapshots are not removed by the daily retention cycle.
- **Create backup** creates a full snapshot manually.
- Full-backup storage is content-addressed: unchanged files are not duplicated, so later snapshots add only new or changed data.

**Restoring from a full backup**

The full-backup history can restore an individual missing file, resolve a changed-file conflict, or restore an entire snapshot.

For a whole-snapshot restore:

- **Files only** restores the snapshot's files but leaves the current FlipDesk settings and page state unchanged.
- **Files + state** restores the files and the FlipDesk state stored in the same snapshot, then restarts FlipDesk.
- Extra current files that are not present in the selected snapshot are **not deleted**.
- Before a whole-snapshot restore changes anything, FlipDesk automatically creates a new full **safety snapshot** of the current files.

> **Quick guide:** use a **restore point** for FlipDesk settings/pages, a **full backup** for real files, and **Files + state** when you want both files and FlipDesk returned to the same earlier point.

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
- state/full backup;
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
- state/full backups: во внутреннем хранилище резервных копий FlipDesk или в папке, выбранной пользователем.

При первом запуске FlipDesk автоматически создаёт исходную полную резервную копию пользовательского рабочего стола Windows и общего Public Desktop. Эта копия служит точкой восстановления на случай, если после переноса объектов на виртуальные страницы пользователь решит отказаться от FlipDesk или потребуется вернуть исходное состояние рабочего стола. Размер первой резервной копии зависит от объёма данных на рабочих столах и может быть значительным.

Удаление FlipDesk рассчитано на удаление самого приложения, **но не** страниц пользователя, настроек и резервных копий. Поэтому исходный backup остаётся на диске и может быть использован для последующего восстановления, в том числе после повторной установки FlipDesk.

<details>
<summary><h3>Резервное копирование и восстановление</h3></summary>

FlipDesk использует два отдельных уровня защиты:

| Тип резервной копии | Что защищает | Когда использовать |
| --- | --- | --- |
| **Точка восстановления FlipDesk** | Настройки FlipDesk, список и порядок страниц, раскладку и ссылки на виртуальных страницах. **Реальные пользовательские файлы в неё не входят.** | Когда нужно вернуть настройки или структуру страниц FlipDesk, не восстанавливая файлы. |
| **Полная резервная копия файлов** | Реальные копируемые файлы, входящие в план резервного копирования, а также состояние FlipDesk. Для системных путей может сохраняться только ссылка. | Когда нужно вернуть реальные файлы либо одновременно восстановить файлы и состояние FlipDesk. |

**Точки восстановления FlipDesk**

- Это небольшие точки, которые автоматически создаются при изменениях состояния FlipDesk.
- Хранятся до **20** последних точек восстановления.
- **Восстановить состояние** возвращает только настройки и состояние страниц FlipDesk; реальные пользовательские файлы при этом не восстанавливаются.
- Восстановление выполняется через защищённый механизм, после чего FlipDesk перезапускается.

**Полные резервные копии**

- **Ежедневная полная резервная копия** создаётся при первом запуске FlipDesk за день, если эта функция включена.
- FlipDesk хранит последние **7 ежедневных** полных копий.
- Созданные **вручную** и **страховочные** копии автоматической ротацией ежедневных копий не удаляются.
- Кнопка **Создать копию** позволяет создать полную резервную копию вручную.
- Хранилище использует дедупликацию: неизменившиеся файлы повторно не сохраняются, поэтому следующие копии добавляют только новые или изменённые данные.

**Восстановление из полной резервной копии**

Из истории полных копий можно восстановить отдельный отсутствующий файл, безопасно разрешить конфликт изменённого файла или восстановить всю выбранную копию.

При восстановлении всей копии доступны два режима:

- **Только файлы** — восстанавливает файлы из выбранной копии, но оставляет текущие настройки и состояние страниц FlipDesk без изменений.
- **Файлы + состояние** — восстанавливает и файлы, и сохранённое в этой же копии состояние FlipDesk, после чего приложение перезапускается.
- Лишние текущие файлы, которых нет в выбранной резервной копии, **не удаляются**.
- Перед восстановлением всей копии FlipDesk автоматически создаёт новую полную **страховочную копию** текущих файлов.

> **Коротко:** для настроек и страниц FlipDesk используй **точку восстановления**; для реальных файлов — **полную резервную копию**; если нужно вернуть и файлы, и FlipDesk к одному предыдущему состоянию — **Файлы + состояние**.

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
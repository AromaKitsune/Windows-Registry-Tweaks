# Windows Registry Tweaks
A small collection of various Windows Registry tweaks that might be useful.

> [!WARNING]
> Create a system restore point before modifying the regsitry in case you screw up something.

The REG files are provided here so you can just import it, including those that undo the tweaks.


## Custom Property Lists

Show folder sizes in File Explorer's Tiles view, Content view, and Status Bar

The following programs and plugin are required:
* [Windhawk](https://windhawk.net/)
* "[Better file sizes in Explorer details](https://windhawk.net/mods/explorer-details-better-file-sizes)" mod for Windhawk
* voidtools' [Everything](https://www.voidtools.com/)

Refer to the Windhawk mod description for setup instructions.

Folder sizes work only on Windows 10 and 11.

This Windhawk mod's "Show folder sizes" option only applies to File Explorer's Details view.
The registry tweaks also enable showing folder sizes in File Explorer's Tiles view and Content view
by adding the `System.Size` property to those property lists.
Refer to the [Microsoft documentation](https://learn.microsoft.com/en-us/windows/win32/properties/core-bumper) for a list of core properties.

### Other tweaks include
* InfoTip: Show a folder size in a folder ToolTip via Everything instead of slowly calculating it
  * On registry import, this disables the "Display file size information in folder tips" option in Folder Options.
* PreviewDetails: Show the total size of selected items (up to 99) in status bar, even if folders are selected
* StatusBar: Show a current folder's size, disk's free space, and disk usage indicator in status bar
  * Folder size also works with:
    * Bottom details pane (enabled via [OldNewExplorer](https://www.majorgeeks.com/files/details/oldnewexplorer.html) )
    * Classic status bar (enabled via [Open-Shell](https://open-shell.github.io/Open-Shell-Menu/) )

[REG file](/registration-entries/PropertyLists-Custom.reg)
| [Reset to default (Win11)](/registration-entries/PropertyLists-DefaultWin11.reg)
| [Reset to default (Win10)](/registration-entries/PropertyLists-DefaultWin10.reg)

**Details view**
![](/screenshots/FileExplorerDetailsView.png)

**Tiles view**
![](/screenshots/FileExplorerTilesView.png)

**Content view**
![](/screenshots/FileExplorerContentView.png)


## Hide Items from Modern Context Menu

Hide the items from the Windows 11 context menu

In the registry key, `HKCU\Software\Microsoft\Windows\CurrentVersion\Shell Extensions\Blocked`, you can hide the modern context menu items
by adding a `REG_SZ` value with CLSID as a name.

| Menu Item            | CLSID                                    |
| -------------------- | ---------------------------------------- |
| Ask Copilot          | `{CB3B0003-8088-4EDE-8769-8B354AB2FF8C}` |
| Create with Designer | `{7A53B94A-4E6E-4826-B48E-535020B264E5}` |
| Edit in Notepad      | `{CA6CC9F1-867A-481E-951E-A28C5E4F01EA}` |
| Move to OneDrive     | `{1FA0E654-C9F2-4A1F-9800-B9A75D744B01}` |
| Edit with Paint      | `{2430F218-B743-4FD6-97BF-5C76541B4AE9}` |
| Edit with Photos     | `{BFE0E2A4-C70C-4AD7-AC3D-10D1ECEBB5B4}` |

[REG file](/registration-entries/ModernContextMenu-HideItems.reg)
| [Restore menu items](/registration-entries/ModernContextMenu-RestoreItems.reg)

To find a CLSID for a menu item that you want to hide, go to `HKLM\SOFTWARE\Classes\PackagedCom\ClassIndex` and press `Ctrl`+`F` to search for a key by program name.


## Custom File Type Descriptions

Customise the descriptions of file types

Those file descriptions are changed to match the ones in Linux file managers such as Dolphin :)

| Original Description   | Custom Description | File Extensions
| ---------------------- | ------------------ | ---------------
| Application            | Executable         | `exe`
| Application extension  | Shared Library     | `dll`, `rll`
| File folder            | Folder             |

[REG file](/registration-entries/FileTypeDescriptions-Custom.reg)
| [Reset to default](/registration-entries/FileTypeDescriptions-Default.reg)

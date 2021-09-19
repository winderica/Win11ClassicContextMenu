# Win11ClassicContextMenu

Get back the classic context menu in Windows 11

## Disclaimer

It is only tested in Windows 11 build 22000.160 and may or may not work in other versions. Use at your own risk.

## Usage

1. Download `Windows.UI.FileExplorer.dll` [here](https://github.com/winderica/Win11ClassicContextMenu/releases)
2. (Recommended) Make a backup of `C:\Windows\System32\Windows.UI.FileExplorer.dll`
3. (Optional) Compare the downloaded file with the original one using some hex editors if you don't trust me
4. Run the following commands in cmd as Administrator:
```bat
cd %SystemRoot%\System32
icacls Windows.UI.FileExplorer.dll /save %Temp%\perms.txt
takeown /f Windows.UI.FileExplorer.dll
echo Y| cacls Windows.UI.FileExplorer.dll /G %USERNAME%:F
taskkill /f /im explorer.exe
echo Y| move <PATH_TO_THE_DOWNLOADED_FILE> Windows.UI.FileExplorer.dll
start explorer.exe
icacls . /restore %Temp%\perms.txt
```

## Related Projects

* [llccd/Shell32Patcher](https://github.com/llccd/Shell32Patcher): it hooks `explorer.exe` dynamically, which might be more elegant in some senses

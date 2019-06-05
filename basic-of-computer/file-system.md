# File System

## Linux File System

在 unix-like 系統 \(Ubuntu, CentOS, Redhat, MacOS, ...etc.\) 中，檔案系統皆由根目錄 \(root\) 開頭，不論是主機板上的硬碟或是外接硬碟，皆會被掛載至根目錄中特定的位置。 例如："/mnt" 為根目錄下 mnt 資料夾。

以 Ubuntu 為例，使用者在打開終端機 \(terminal\) 時，預設會進入使用者的家目錄 \(home directory\) ，路徑位置為 "/home/usr/user-name"，其中 user-name 為使用者自行定義的名稱。

In unix-like operating system, like Ubuntu, CentOS, RedHat, MacOS, ...etc, the top directory of file system is "root". No matter what type of hard drive you use, they will be mount on the specific path in root. For example, "/mnt" is the mnt directory in root.

In Ubuntu, when user open the terminal, the default of system will make user path is in home directory. The path of user home is "/home/usr/user-name", the user-name is the name of user define.

## Windows File System

Windows 系統中，所有的硬碟都會被獨立掛載成 C、D、E 等等硬碟代碼。例如："C:\Program Files"為 C 槽下，Program Files資料夾。

在 Windows 中，使用者目錄為"C:\home\user\user-name"，其中 user-name 為使用者自行定義的名稱。

In Windows operating system, all drivers will be mount at C, D, E, ... etc independently. For example, "C:\Program Files" is the Program Files directory in C drive.

The home directory path in Windows is "C:\home\user\user-name", the user-name is the name of user define.

## Reference

* [鳥哥的私房菜](http://linux.vbird.org/linux_basic/0210filepermission.php)
* [Windows 系統上的檔案路徑格式](https://docs.microsoft.com/zh-tw/dotnet/standard/io/file-path-formats)


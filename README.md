# Folder Locker

This simple batch script enables you to lock and unlock a folder with a password in Windows. It provides basic security for your sensitive files by renaming the folder and hiding it, making it accessible only with the correct password.

## Usage

### Locking the Folder

1. Run the script by double-clicking the `.cmd` file.
2. If the folder named "Private" does not exist, the script will create it.
3. Confirm if you want to lock the folder by typing 'Y' or 'N'.
4. If 'Y' is selected, the folder will be renamed and hidden.

### Unlocking the Folder

1. Run the script by double-clicking the `.cmd` file.
2. Enter the correct password when prompted.
3. If the password is correct, the folder will be unlocked.

## Password

- The default password in the script is set to "iwmvictor". You can change it by modifying the script.

## Repository Information

- **Repository Name:** FolderLocker
- **Description:** Securely lock and unlock folders on Windows with a password using this simple batch file.
- **Author:** ([Iwmvictor]](https://github.com/iwmvictor))
- **Company:** Meyvn ([@meyvndev](https://github.com/meyvndev))
- **Email:**
  - General: info.meyvn@gmail.com
  - Personal: isingizwemunezerovictor5@gmail.com

## Disclaimer

This script provides basic security and is not foolproof. Use it at your own risk.

Feel free to contribute or report issues!

## Batch Script

```batch
@ECHO OFF
if EXIST "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}" goto UNLOCK
if NOT EXIST Private goto MDPrivate
:CONFIRM
echo Are you sure to lock this folder? (Y/N)
set/p "cho=>"
if %cho%==Y goto LOCK
if %cho%==y goto LOCK
if %cho%==n goto END
if %cho%==N goto END
echo Invalid choice.
goto CONFIRM
:LOCK
ren Private "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"
attrib +h +s "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"
echo Folder locked
goto End
:UNLOCK
echo Enter password to Unlock Your Secure Folder
set/p "pass=>"
if NOT %pass%== iwmvictor goto FAIL
attrib -h -s "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}"
ren "Control Panel.{21EC2020-3AEA-1069-A2DD-08002B30309D}" Private
echo Folder Unlocked successfully
goto End
:FAIL
echo Invalid password
goto end
:MDPrivate
md Private
echo Private created successfully
goto End
:End

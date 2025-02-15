---
description: Moves an item or items to this folder.
ms.assetid: 07723dc1-5d9d-4f32-ab18-52617b0988c4
title: Folder.MoveHere method (Shldisp.h)
ms.topic: reference
ms.date: 05/31/2018
topic_type: 
- APIRef
- kbSyntax
api_name: 
- Folder.MoveHere
api_type: 
- COM
api_location: 
- Shell32.dll
---

# Folder.MoveHere method

Moves an item or items to this folder.

## Syntax


```JScript
Folder.MoveHere(
  vItem,
  [ vOptions ]
)
```



## Parameters

<dl> <dt>

*vItem* \[in\]
</dt> <dd>

Type: **Variant**

The item or items to move. This can be a string that represents a file name, a [**FolderItem**](folderitem.md) object, or a [**FolderItems**](folderitems.md) object.

</dd> <dt>

*vOptions* \[in, optional\]
</dt> <dd>

Type: **Variant**

Options for the move operation. This value can be zero or a combination of the following values. These values are based upon flags defined for use with the **fFlags** member of the C++ [**SHFILEOPSTRUCT**](/windows/desktop/api/Shellapi/ns-shellapi-shfileopstructa) structure. These flags are not defined as such for Visual Basic, VBScript, or JScript, so you must define them yourself or use their numeric equivalents.

<dt>



 (4)


</dt> <dd>

Do not display a progress dialog box.

</dd> <dt>



 (8)


</dt> <dd>

Give the file being operated on a new name in a move, copy, or rename operation if a file with the target name already exists.

</dd> <dt>



 (16)


</dt> <dd>

Respond with "Yes to All" for any dialog box that is displayed.

</dd> <dt>



 (64)


</dt> <dd>

Preserve undo information, if possible.

</dd> <dt>



 (128)


</dt> <dd>

Perform the operation on files only if a wildcard file name (\*.\*) is specified.

</dd> <dt>



 (256)


</dt> <dd>

Display a progress dialog box but do not show the file names.

</dd> <dt>



 (512)


</dt> <dd>

Do not confirm the creation of a new directory if the operation requires one to be created.

</dd> <dt>



 (1024)


</dt> <dd>

Do not display a user interface if an error occurs.

</dd> <dt>



 (2048)


</dt> <dd>

[Version 4.71.](versions.md) Do not copy the security attributes of the file.

</dd> <dt>



 (4096)


</dt> <dd>

Only operate in the local directory. Do not operate recursively into subdirectories.

</dd> <dt>



 (8192)


</dt> <dd>

[Version 5.0.](versions.md) Do not move connected files as a group. Only move the specified files.

</dd> </dl> </dd> </dl>

## Return value

This method does not return a value.

## Remarks

> [!Note]  
> Not all methods are implemented for all folders. For example, the [**ParseName**](folder-parsename.md) method is not implemented for the Control Panel folder (CSIDL\_CONTROLS). If you attempt to call an unimplemented method, a 0x800A01BD (decimal 445) error is raised.

 

## Examples

The following example uses **MoveHere** to move the file Temp.txt from the root directory of the C drive to the C:\\Windows folder. Proper usage is shown for JScript, VBScript, and Visual Basic.

JScript:


```JScript
<script language="JScript">
    var FOF_NOCONFIRMATION = 16;

    function fnFolderObjectMoveHereJ()
    {
        var objShell  = new ActiveXObject("shell.application");
        var objFolder = new Object;
        
        objFolder = objShell.NameSpace("C:\\WINDOWS");
        if (objFolder != null)
        {
            objFolder.MoveHere ("C:\\temp.txt", FOF_NOCONFIRMATION);
        }
    }
</script>
```



VBScript:


```VB
<script language="VBScript">
    private const FOF_NOCONFIRMATION = 16
    
    function fnFolderObjectMoveHereVB()
        dim objShell
        dim objFolder

        set objShell = CreateObject("shell.application")
        set objFolder = objShell.NameSpace("C:\WINDOWS")

        if (not objFolder is nothing) then
            objFolder.MoveHere "C:\temp.txt", FOF_NOCONFIRMATION
        end if

        set objFolder = nothing
        set objShell = nothing
    end function
</script>
```



Visual Basic:


```VB
Private Const FOF_NOCONFIRMATION = &H10

Private Sub btnMoveHere_Click()
    Dim objShell  As Shell
    Dim objFolder As Folder

    Set objShell = New Shell
    Set objFolder = objShell.NameSpace("C:\WINDOWS")

    If (Not objFolder Is Nothing) Then
        objFolder.MoveHere "c:\temp.txt", FOF_NOCONFIRMATION
    End If

    Set objFolder = Nothing
    Set objShell = Nothing
End Sub
```



## Requirements



| Requirement | Value |
|-------------------------------------|----------------------------------------------------------------------------------------------------------------|
| Minimum supported client<br/> | Windows 2000 Professional, Windows XP \[desktop apps only\]<br/>                                         |
| Minimum supported server<br/> | Windows 2000 Server \[desktop apps only\]<br/>                                                           |
| Header<br/>                   | <dl> <dt>Shldisp.h</dt> </dl>                           |
| IDL<br/>                      | <dl> <dt>Shldisp.idl</dt> </dl>                         |
| DLL<br/>                      | <dl> <dt>Shell32.dll (version 4.71 or later)</dt> </dl> |



 

 





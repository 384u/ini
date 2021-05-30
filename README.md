# INI Read/Write Library (License: WTFPL)
I was looking for .ini read/write library but I didn't find anything useful, decided I then to write own version.
This library will preserve comments, or any typos, and parsing ini file will also parse `[section]dasdsa` properly, and upon writing, `dasdsa` will also be preserved.
## Coding Style
The Library uses quite "odd" naming style, but is a new standard I started applying in order for me to flawlessly convert the code into another language without worrying about forbidden words as variable name, and the standard is used so it brings more understanding what the code does.

## All usage examples
```vb
Set ini = new IniFile
ini.Open "test.ini"

' set/add values to ini
ini.SetValue "general", "key1", "value1"
ini.SetValue "general", "key1", "value12"

' retrieve value by key "a" from section "general"
WScript.Echo "Get value:" & vbNewLine & ini.GetValue("general", "a")
' here we list all sections,
' includes empty section name if there was no first section name
WScript.Echo "Sections:" & vbNewLine & Join(ini.GetSections(), ",")

' IF you need to get key/values by section name, do this:
' vLine(0=Section, 1=Key, 2=Value, 3=Line, 4=Comment, 5=DefineSectionBool)
For Each vLine In ini.GetLinesBySection("general")
	' index 1 is key name
	' index 2 is value
	If "" <> vLine(1) Then
		' display it like this: key=value
		MsgBox vLine(1) & "=" & vLine(2)
	End If
Next

' To save opened file:
' Write 0
' To save in new file:
' Write "newfile.ini"
ini.Write 0
```

# INI Read/Write Library (License: WTFPL)
I was looking for .ini read/write library but I didn't find anything useful, decided I then to write own version.
This library will preserve comments, or any typos, and parsing ini file will also parse `[section]dasdsa` properly, and upon writing, `dasdsa` will also be preserved.
## Coding Style
The Library uses quite "odd" naming style, but is a new standard I started applying in order for me to flawlessly convert the code into another language without worrying about forbidden words as variable name, and the standard is used so it brings more understanding what the code does.

## All usage examples
```vb
Set x = new IniFile
x.Open "test.ini"

' set/add values to ini
x.SetValue "general", "key1", "value1"
' then we assign new value
x.SetValue "general", "key1", "value12"

' retrieve value by key "a" from section "general"
WScript.Echo "Get value:" & vbNewLine & x.GetValue("general", "a")
' here we list all sections,
' includes empty section name if there was no first section name
WScript.Echo "Sections:" & vbNewLine & Join(x.GetSections(), ",")

' we specify 0 to say just save file
' we can add custom filename, yes
x.Write 0
```

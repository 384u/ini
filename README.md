# ini

```vb
Set x = new IniFile
x.Open "test.ini"

' set/add values to ini
x.SetValue "general", "key1", "value1"
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

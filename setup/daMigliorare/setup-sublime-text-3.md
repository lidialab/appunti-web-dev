# setup Sublime Text 3

## Info
by Sublime HQ Pty Ltd

https://www.sublimetext.com/

Linux, Mac, Win

## Pacchetti

- Package Control
- Emmet
- Sidebar Enhancements
- Advanced New File
- HTTP Requester
---------------------------
- Sublime Code Intel
- Git Gutter
- DocBlockr
- SublimeLint
- PHP CS
- JSLint
- Linter
- Prefixr
- Live Reload + estensione browser

wordpress 

## Temi e Sintassi



## CheatSheet, Reference

Preferenze > Settings :
  
  ```
{
	"auto_find_in_selection": true,
	"auto_id_class": true,
	"bold_folder_labels": true,
	"color_scheme": "Packages/Base16 Color Schemes/Themes/base16-material-darker.tmTheme",
	"fade_fold_buttons": false,
	"font_size": 14,
	"highlight_modified_tabs": true,
	"ignored_packages":
	[
		"Vintage"
	],
	"indent_to_bracket": true,
	"margin": 3,
	"match_brackets_angle": true,
	"show_encoding": true,
	"tab_size": 3,
	"translate_tabs_to_spaces": true,
	"theme": "Adaptive.sublime-theme"
}
  ```
  
```"auto_id_class": true,``` --> per Emmet

**Reindentare**:
edit > line > reindent

**Scorciatoie da tastiera**

```
[
{ "keys": ["control+keypad_divide"],"command": "toggle_comment", "args": {"block": false} },
{ "keys": ["shift+control+keypad_divide"],"command": "toggle_comment", "args": {"block": true}},
{ "keys": ["alt+keypad_multiply"], "command": "insert_snippet", "args": {"name": "Packages/User/lidialab-parentesi.sublime-snippet"} }
]
```

**Scorciatoie** da memorizzare:

ctrl+m va alla parentesi che chiude

ctrl+shift+v incolla e indenta

**Percorso pacchetti installati**:

Linux: ~/.config/sublime-text-3

OS X: ~/Library/Application Support/Sublime Text 3

Windows: %APPDATA%\Sublime Text 3

### Emmet
**Personalizzazione snippet HTML (!)**

Preferences > Package Settings > Emmet > Settings User
```
{
   "snippets": {
      "html": {
         "snippets": {
            "!": "<!DOCTYPE html>\n<html lang=\"it\">\n\n<head>\n\t<title>Titolo della pagina</title>\n\n\t<meta charset=\"utf-8\">  <!-- lasciare entro i primi 1024 byte -->\n\t<meta name=\"viewport\" content=\"width=device-width, initial-scale=1\">\n\n\t<base href=\"http://nomedominio.ext/percorso/\">\n\n\t<link rel=\"stylesheet\" href=\"../../lib/cssLLreset/LLreset.css\">\n\t<link rel=\"stylesheet\" href=\"stile.css\">\n\n</head>\n\n<body>\n\n</body>\n\n</html>"
         }
      }
   }
}
```

**Cartella snippet in Windows**

```C:\Users\nomeutente\AppData\Roaming\Sublime Text 3\Packages\User

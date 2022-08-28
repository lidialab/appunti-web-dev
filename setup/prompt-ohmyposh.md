# Configurazione del prompt di invito con Oh My Posh

## Progetto ohmyposh
https://ohmyposh.dev/

### per Windows

#### Installazione

Nel sito https://ohmyposh.dev/ ci sono chiare istruzioni per l'installazione tramite WINGET (che ho utilizzato)

```
winget install JanDeDobbeleer.OhMyPosh -s winget
```

o tramite Windows Store (link nel sito di oh-my-posh) o ancora tramite metodo manuale da prompt di PowerShell.

Viene raccomandato di utilizzare le shell tramite *Windows Terminal*.

#### Configurazione per Powershell 7.2.5 (pwsh.exe)

File del profilo di Powershell ($Home\Documents\PowerShell\Microsoft.PowerShell_profile.ps1)
```
Import-Module oh-my-posh
oh-my-posh --init --shell pwsh --config ~/lltheme.omp.json | Invoke-Expression
```
Tema (es: lltheme.omp.json)
```
{
  "$schema": "https://raw.githubusercontent.com/JanDeDobbeleer/oh-my-posh/main/themes/schema.json",
  "blocks": [
    {
      "alignment": "left",
      "segments": [
        {
          "background": "lightRed",
          "foreground": "#ffffff",
          "properties": {
            "template": " {{ .UserName }} "
          },
          "style": "powerline",
          "type": "session"
        },
        {
          "background": "#FF5722",
          "foreground": "#FFFFFF",
          "powerline_symbol": "\ue0b0",
          "properties": {
            "folder_separator_icon": " \ue0b1 ",
            "home_icon": "~",
            "style": "folder",
            "template": " \uf74a  {{ .Path }} "
          },
          "style": "powerline",
          "type": "path"
        },
        {
          "background": "#FF5722",
          "foreground": "#FFFFFF",
          "powerline_symbol": "\ue0b0",
          "properties": {
            "root_icon": "\uf0ad",
            "template": " \uf0e7 "
          },
          "style": "powerline",
          "type": "root"
        },
        {
          "background": "lightYellow",
          "foreground": "darkGray",
          "powerline_symbol": "\ue0b0",
          "properties": {
            "charged_icon": "\ue22f ",
            "charging_icon": "\ue234 ",
            "discharging_icon": "\ue231 ",
            "template": " {{ if not .Error }}{{ .Icon }}{{ .Percentage }}{{ end }}{{ .Error }}\uf295 "
          },
          "style": "powerline",
          "type": "battery"
        },
        {
          "background": "lightGreen",
          "foreground": "#ffffff",
          "powerline_symbol": "\ue0b0",
          "properties": {
            "time_format": "02 Jan 06 - 15:04:05"
          },
          "style": "powerline",
          "type": "time"
        },
        {
          "background": "lightBlue",
          "foreground": "#ffffff",
          "powerline_symbol": "\ue0b0",
          "properties": {
            "always_enabled": true,
            "template": "\u2800{{ .FormattedMs }}\u2800"
          },
          "style": "powerline",
          "type": "executiontime"
        },
        {
          "background": "#8f43f3",
          "foreground": "#ffffff",
          "powerline_symbol": "\ue0b0",
          "properties": {
            "precision": 2,
            "template": " {{ round .PhysicalPercentUsed .Precision }}% "
          },
          "style": "powerline",
          "type": "sysinfo"
        }
      ],
      "type": "prompt"
    }
  ],
  "console_title": true,
  "console_title_style": "template",
  "console_title_template": "{{ .Shell }} in {{ .Folder }}",
  "final_space": true,
  "version": 1
}

```

Nelle impostazioni di Windows terminal impostare un font adatto a visualizzare le icone per PowerShell 7.2.5.


#### Configurazione per Powershell 5.1 (powershell.exe)

Da PS lanciata in modalità amministratore, ho cambiato la seguente policy:
```
Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope CurrentUser
```
File del profilo di Powershell 5.1 ($Home\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1)
```
oh-my-posh --init --shell pwsh --config ~/lltheme.omp.json | Invoke-Expression
```

Nelle impostazioni di Windows terminal impostare un font adatto a visualizzare le icone per PowerShell 5.1.

#### Configurazione per WSL2 Debian

##### Installare oh-my-posh

```
sudo wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/posh-linux-amd64 -O /usr/local/bin/oh-my-posh
```

modificare il file .bashrc

```
sudo nano /home/lidia/.bashrc
```

ATTENZIONE modificare SOLO da wsl, NON da Windows, rif: https://devblogs.microsoft.com/commandline/do-not-change-linux-files-using-windows-apps-and-tools/

Installare i font powerline (o quelli utilizzati):

```
sudo apt install fonts-powerline -y
```

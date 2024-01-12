# Windows
## Prompt dei comandi cmd

## Cartelle esecuzione automatica di programmi in Windows 10
### Cartella startup utente
CTRL+R
```
shell:startup
```
### Cartella startup computer
CTRL+R
```
shell:common startup
```
### Cartella APP
```
shell:AppsFolder
```
## Comandi
### mklink
```
mklink /J "\link\da\creare" "\percorso\target\"
```

## Script per avviare unità virtuali BitLocker
### File da far eseguire alla shell diskpart (es: "vdisk.txt")
```
select vdisk file="c:\vdisk.vhd"
attach vdisk
```
### File da far eseguire al logon dell'utente in Windows via task scheduler con privilegi elevati (la password andrà inserita a mano, !)
```
diskpart /s c:\vdisk.txt
:Label99
manage-bde -unlock K: -pw
IF %ERRORLEVEL% NEQ 0 GOTO Label99
Exit 0
```
Per non ricevere il popup di errore di apertura dell'unità disabilitare l'avvio automatico delle unità removibili

## PowerShell
### Visualizzare hash di un file
``get-filehash -Algorithm SHA512 .\nome-file.ext  | Format-List``

## Winget
```winget list```
```winget list --upgrade-available```
```winget upgrade nome-pacchetto```
```winget upgrade --all ```

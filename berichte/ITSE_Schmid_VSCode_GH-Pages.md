| Name          | Klasse | Fach         | Thema       | Datum      | Lehrkraft     |
| ------------- | ------ | ------------ | ----------- | ---------- | ------------- |
| Cedric Schmid | 4AHITS | ITSE-Übungen | Git, VSCode | 06.10.2025 | Franz Matejka |

## Aufgabenstellung

Arbeitsvorbereitung:

Installiere Kali und Metasploitable (falls noch nicht geschehen)
Stelle beide VMs auf Bridged ins Labor-Netz

Installiere Visual Studio Code auf Kali Linux

Klone das Github Projekt in Kali, nimm mit VS Code eine Änderung im Markdown vor, führe add, commit und push durch und prüfe ob die Änderungen in der generierten html Seite ankommen (kurze Wartezeit)

Nimm nun über die GitHub Oberfläche eine Änderung vor und prüfe ob diese per git pull in den Klon auf Kali übernommen werden.

Dokumentiere alles wesentliche in einem Arbeitsbericht.

## Git-Setup

```bash
# SSH Keys
ssh-keygen -t ed25519 -C EMAIL
# ~/.ssh/id_ed25519.pub bei Github zu dem SSH-Keys hinzufügen
# ~/.ssh/id_ed25519 ist private key

# Git einrichten
git clone git@github.com:USERNAME/REPO-NAME.git

cd REPO-NAME

git config --local user.name USERNAME
git config --local user.email EMAIL

# Git testen
echo hi > hi.txt
git add .
git commit -m "add hi.txt"
git push
rm hi.txt
git add .
git commit -m "rm hi.txt"
git push
```

## VSCode-Setup

```bash
# Download
wget -O vscode.deb 'https://code.visualstudio.com/sha/download?build=stable&os=linux-deb-x64'

# Installieren
sudo apt install ./vscode.deb
```

Mit VSCode nun den Ordner von Github öffnen, man könnte jetzt über die GUI `git` nutzen


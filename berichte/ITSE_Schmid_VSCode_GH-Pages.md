| Name          | Klasse | Fach         | Thema       | Datum      | Lehrkraft     |
| ------------- | ------ | ------------ | ----------- | ---------- | ------------- |
| Cedric Schmid | 4AHITS | ITSE-Übungen | Git, VSCode | 06.10.2025 | Franz Matejka |

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


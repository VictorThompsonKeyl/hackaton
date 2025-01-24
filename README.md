# HACKATON

# Installation de MicroPython

Ce guide explique comment installer MicroPython sur une carte compatible, comme l'ESP32 ou l'ESP8266.

## Matériel requis
- Carte microcontrôleur (ESP32, ESP8266, etc.)
- Câble USB pour connecter la carte à l'ordinateur
- Logiciel pour flasher le firmware (`esptool.py`)

## Étapes d'installation

### 1. Télécharger le firmware MicroPython
- Accédez au site officiel : [https://micropython.org/download/](https://micropython.org/download/).
- Choisissez votre carte (ESP32, ESP8266, etc.) et téléchargez le fichier `.bin` correspondant.

### 2. Installer `esptool.py`
- Assurez-vous que Python est installé sur votre ordinateur.
- Installez `esptool` en exécutant la commande suivante dans un terminal :
  ```bash
  pip install esptool
  ```

### 3. Connecter la carte et effacer la mémoire
- Connectez votre carte à l’ordinateur avec un câble USB.
- Identifiez le port série de la carte :
  - **Windows** : via le Gestionnaire de périphériques.
  - **macOS/Linux** : avec la commande `ls /dev/tty*` ou `dmesg`.
- Effacez la mémoire flash avec la commande suivante (remplacez `<nom_du_port>` par le port série de votre carte, ex. : `COM3` ou `/dev/ttyUSB0`) :
  ```bash
  esptool.py --port <nom_du_port> erase_flash
  ```

### 4. Flasher le firmware
- Chargez le firmware MicroPython sur la carte avec cette commande :
  ```bash
  esptool.py --port <nom_du_port> --baud 460800 write_flash -z 0x1000 <chemin_vers_le_fichier_bin>
  ```
  - Remplacez `<nom_du_port>` par le port série de la carte.
  - Remplacez `<chemin_vers_le_fichier_bin>` par le chemin du fichier `.bin` téléchargé.

### 5. Tester l'installation
- Ouvrez un terminal série avec un outil comme `PuTTY`, `minicom`, ou `screen` :
  ```bash
  screen <nom_du_port> 115200
  ```
- Si tout est correctement configuré, vous verrez le prompt MicroPython (`>>>`).

## Ressources utiles
- [Documentation officielle](https://docs.micropython.org/)
- [Téléchargement des firmwares](https://micropython.org/download/)

## Problèmes fréquents
- **Carte non détectée** : Assurez-vous que les pilotes USB sont installés.
- **Câble non fonctionnel** : Vérifiez que le câble USB supporte la transmission de données.

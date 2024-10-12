# Affichage Lycée

## 1. Prérequis
* Téléchargez le système d'explotation de raspbian via ce lien:
https://www.raspberrypi.org/downloads/raspbian/

## 2. Configurer la carte SD
Après avoir créer la carte SD bootable avec Raspberry Pi Imager.
Insérez la carte SD dans votre Raspberry Pi.
Puis booter.

## 3. Configurer le système Raspbian
### Vérification de l'internet
Vérifiez si la connection internet est OK.

### Mettre à jour la Pi
Tapez `sudo apt-get update && sudo apt-get upgrade -y`.

## 4. Configurer le site à afficher 

### Téléchargez & configurer Apache2 pour le localhost (serveur web)
Tapez `sudo apt install apache2 -y`.

Tapez `sudo sudo chmod -R 777 /var/www/html`.

#### Importer la page web
Dans le projet, vous trouverez des fichier HTML/CSS/JS.
Vous devez télécharger le dossier du projet en entier puis le mettre dans la répértoire `var/www/html/`.
Extraire tout les fichiers dans ce dossier `html`.

### Configurer la météo et le Slide
Ouvrez le fichier dans le dossier js, `config.js`.
Il faudra modifier les coordonnées pour obtenir la météo de la ville désiré et modifier le lien du slide.

### Apercevoir le site sur le navigateur
Dans la barre de recherche, tapez `localhost`, et vous allez voir votre site.


## 5. Configurer le mode Kiosque

## Télécharger Pi-Apps : 
Tapez `wget -qO- https://raw.githubusercontent.com/Botspot/pi-apps/master/install | bash`

## Télécharger Autostar à partir de Pi-Apps : 
Lisez cette répertoire: https://github.com/Botspot/autostar

## Ajouter une tâche au démarrage:
![image](https://github.com/user-attachments/assets/2c8a8abb-0efc-4de6-8f1d-8b1f513d94d7)
# Instructions:
* Cliquer sur '+ add'
*  Filename: `kiosk.desktop` 
*  Display name: `kiosk startup` 
*  Command to run: `chromium-browser --fullscreen --noerrordialog --kiosk http://localhost/`
*  Puis `OK`

# Vous pouvez maintenant redémarrer la Raspberry


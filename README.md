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

### Initialisation
Tapez `sudo raspi-config` dans le terminal.

#### Pour changer la langue du clavier
Choisissez `Localisation Options`.

Choisissez `Keyboard Layout`.

Continuez le processus de configuration tout en sélectionnant la disposition de clavier souhaitée.

Dans mon cas : disposition Azerty avec clavier français.

#### Change timezone
Il sera nécessaire d’avoir une date/heure fiable sur votre écran.

Choisissez `Localisation Options`.

Choisissez `Timezone`.

Selectionnez your Country/City.

Dans mon cas : Europe/Paris.

### Mettre à jour la Pi

Tapez `sudo apt-get update && sudo apt-get upgrade -y`.

## 4. Configurer le site à afficher 

### Téléchargez & configurer Apache2 pour le localhost (serveur web)

Tapez `sudo apt install apache2 -y`.

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

## Télécharger un système permettant d'afficher après le boot
Dans le terminal, tapez :

`sudo apt-get install unclutter`

`sudo apt-get install x11-xserver-utils`

## Créer les répertoires suivants :
Dans le terminal, tapez:

`mkdir ~/.config/lxsession`

`mkdir ~/.config/lxsession/LXDE-pi`

## Puis créer et éditer le fichier autostart : 
Tapez `nano ~/.config/lxsessions/LXDE-pi/autostart`

Y placer le texte suivant :
```
#@lxpanel --profile LXDE-pi
#@pcmanfm --desktop --profile LXDE-pi
#@xscreensaver -no-splash	

@xset s off
@xset -dpms
@xset s noblank
@unclutter -idle 0
@chromium-browser --noerrdialogs --start-fullscreen https://localhost/
@xscreensaver -no-splash	
```

## Configurer le temps de rafraichissement du slide
Pour que le Google Slide soit rafraichit pour pouvoir afficher le contenu modifié, veuillez partir dans le fichier `index.html` vers la ligne 308.
Entrez le temps souhaité, par défaut il est à 5 min. 

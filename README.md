# snips-metro
Assistant Snips en Python3 pour Ubuntu

## Installation de Snips sur Ubuntu 18.04

### Dépendances
```bash
sudo apt-get update
sudo apt-get install -y dirmngr apt-transport-https
sudo bash -c  'echo "deb https://debian.snips.ai/stretch stable main" > /etc/apt/sources.list.d/snips.list'
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F727C778CCB0A455

sudo apt-get update
sudo apt-get install -y snips-platform-voice
# sudo apt-get install -y snips-tts (est installé par le paquet précédent)

# Paquet qui installe l'assistant de démo SnipsDemoWeatherAssistant
sudo apt-get install -y snips-platform-demo

sudo apt-get install -y snips-watch
sudo apt-get install -y snips-template
sudo apt-get install -y snips-skill-server
```
A l'issue de cette installation, on retrouve les services suivants :

    sudo systemctl | grep snips
```
snips-asr.service               loaded activating auto-restart Snips ASR
snips-audio-server.service      loaded active     running      Snips Audio Server
snips-dialogue.service          loaded activating auto-restart Snips Dialogue
snips-hotword.service           loaded active     running      Snips Hotword
snips-injection.service         loaded activating auto-restart Snips Injection
snips-nlu.service               loaded activating auto-restart Snips NLU
snips-skill-server.service      loaded active     running      Snips Skill Server
snips-tts.service               loaded active     running      Snips TTS 
```
### Répertoires des skills et des actions
Pour ma part j'ai installé le projet Github sous ce répertoire

    /var/lib/snips/skills/<projet>/
        action-<nom action>.py
        ...

### Répertoire de l'assistant 

    /usr/share/snips/assistant/
        assistant.json
        ...

Le paquet ```snips-platform-demo``` a installé l'assistant de démo dans ce répertoire

L'assistant téléchargé téléchargé à partir de la console Snips https://console.snips.ai/ devra écraser l'assistant de démo

### Initialisation de l'assistant

- Je me donne les droits sur le répertoire des skills :

    ```sudo chown $USER /var/lib/snips/skills```

- Copie de mon skill dans ce répertoire
- Installation du skill

    ```sudo -u _snips-skills snips-skill-server install_skills```




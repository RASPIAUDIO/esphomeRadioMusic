# RASPIAUDIO Radio Music Assistant / Sendspin

Firmware ESPHome pour la RASPIAUDIO Radio à ESP32-S3, utilisable comme lecteur
synchronisé Music Assistant grâce au protocole Sendspin.

## Compatibilité

- ESPHome 2026.8.0 ou plus récent ;
- Home Assistant avec l'intégration ESPHome ;
- Music Assistant avec le fournisseur Sendspin.

Sendspin, `speaker_source`, `audio_file`, le mixer et le resampler sont désormais
les composants natifs d'ESPHome. Seule l'initialisation ES8388 spécifique à la
Radio reste externe ; sa révision est épinglée dans le YAML afin de rendre les
compilations reproductibles.

Le Wi-Fi fonctionne sans économie d'énergie et la lecture continue si Home
Assistant est momentanément indisponible.

## Affichage

Le titre, l'artiste, l'album et la durée sont reçus directement de Music
Assistant par Sendspin. Aucune entité Home Assistant ne doit être indiquée dans
le YAML pour alimenter l'écran.

## Préréglages des quatre boutons radio

La méthode recommandée fonctionne comme les mémoires d'un autoradio :

1. lancer la station voulue dans Music Assistant sur la Radio ;
2. maintenir le bouton choisi pendant environ deux secondes ;
3. relâcher lorsque l'écran indique `MEMO x OK` ;
4. utiliser ensuite un appui court pour rappeler cette station.

La Radio interroge automatiquement la file Music Assistant en cours, mémorise
l'URI exacte de la station et retient l'entité MA réellement associée à
l'appareil. Elle ne dépend donc plus d'un nom d'entité codé en dur. Si aucune
station n'est en cours ou si Home Assistant n'est pas joignable, l'écran indique
`AUCUNE RADIO`. Aucun accès à la fiche de la station n'est nécessaire.

Les quatre champs `Station bouton 1` à `Station bouton 4` restent accessibles
sous **Paramètres → Appareils et services → ESPHome → Raspiaudio Radio Music →
Configuration** pour consulter ou modifier manuellement les préréglages. Les
valeurs sont conservées par la Radio.

Un appui sur le bouton correspondant lance directement la station sur l'entité
Music Assistant détectée, sans automation Home Assistant. Dans la configuration
de l'intégration ESPHome, activez une fois
**Autoriser l'appareil à effectuer des actions Home Assistant**.

La configuration de test porte la version `2026.8.7`. Ne remplacez pas
`update_firmware.bin`, `radio_music.bin` ni `manifest_update.json` avant la
validation matérielle.

## Publication après validation

1. Compiler `radio_music.yaml`.
2. Copier le fichier `firmware.ota.bin` produit vers `update_firmware.bin`.
3. Calculer `md5sum update_firmware.bin`.
4. Reporter la version et le MD5 dans `manifest_update.json`.

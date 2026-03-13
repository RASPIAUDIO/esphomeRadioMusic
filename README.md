# esphomeRadioMusic

esphomeRadioMusic is an audio application that uses the Sendspin protocol within Music Assistant. It allows for multiroom and synchronized listening on several devices (for Raspiaudio: Luxe, MangaCast, and now Radio...).

It's a somewhat experimental application that will be improved based on user feedback.

Currently, if you use the pre-compiled binary (radio_music.bin) directly, you'll get a fully functional app, but with limited screen display (volume and battery level).

To achieve full functionality (with a complete display of all the characteristics of what's being played), you'll need to customize your software by compiling it (with the `esphome` command) and passing a specific parameter ("entity ID," which is the Music Assistant object containing all the audio characteristics to be displayed).

The command to use is:

esphome -s music_assistant_player_entity <my_entity> run radio_music.yaml

<my_entity> should look like the following line:
media_player.raspiaudio_radio_music_abcdef_2

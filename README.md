# esphomeRadioMusic

***esphomeRadioMusic*** is an audio application that uses the Sendspin protocol within Music Assistant. It allows for *multiroom and synchronized* listening on several devices (for Raspiaudio: Luxe, MangaCast, and now Radio...).

It's a somewhat experimental application that will be improved based on user feedback.

**Currently,** if you use the pre-compiled binary (radio_music.bin) directly, you'll get a fully functional app, but with ***limited screen display*** (volume and battery level).

**To achieve full functionality** (*with a complete display of all the characteristics of what's being played*), you'll need to customize your software by compiling it (with the *esphome* command) and passing a specific parameter ("entity ID" which is the Music Assistant object containing all the audio characteristics to be displayed).

For example, the Linux command to use is: ==> ***esphome -s music_assistant_player_entity <my_entity> run radio_music.yaml***

***<my_entity>*** looks like the following line: ***media_player.raspiaudio_radio_music_abcdef_2***

***How do you get the value of <my_entity>***?

It's simple, but for now, it can't be automated. 

On your HA server, follow this path: 

***Home Assistant --> Settings --> Developer tools --> States***

There, you can easily identify the entity in question by its format (***see above***) and by its state ("playing" or "idle") depending on your radio's activity.

***Try it and let me know what you think!***

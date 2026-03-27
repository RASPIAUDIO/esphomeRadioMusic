# Radio Music Application (Experimental)

This is an experimental application that we are actively improving based on user feedback. 

Currently, you have two ways to install the app, depending on the level of detail you want on your display:

## 1. The Quick Method (Basic Display)

If you flash the pre-compiled binary (`radio_music.bin`) directly, you will get a fully functional radio. However, the screen display will be limited to basic information: **volume** and **battery level**.

---

## 2. The Advanced Method (Full Display)

To unlock the full display—which shows all the details of the track currently playing—you need to compile the software yourself using ESPHome. This allows you to link the code to your specific Music Assistant player. 

### Step A: Find your Entity ID

Currently, this step cannot be automated, so you will need to manually locate your radio's Entity ID in Home Assistant. 

1. Open Home Assistant.
2. Navigate to **Developer tools** > **States**.
3. Look for an entity formatted like this: `media_player.raspiaudio_radio_music_abcdef_2`.
4. Verify it is the correct entity by checking its state (it will show as **playing** or **idle** depending on your radio's activity).

### Step B: Compile with ESPHome

Once you have your Entity ID, use the following Linux command to compile the software. Replace `<my_entity>` with the ID you found in Step A.
=======
> **Example Command:**
> ```bash
> esphome -s music_assistant_player_entity <my_entity> run radio_music.yaml
> ```


***Try it and let me know what you think!***
















/////////////////////////////////////////////////////////////////////////////////
// reminder UPDATE
/////////////////////////////////////////////////////////////////////////////////
(First Change the project version in the yaml file)
1. .bin ..../.esphome/build/raspiaudio-radio/.pioenvs/raspiaudio-radio/firmware.ota.bin ===> update_firmware.bin
2. calcul parité ==> >> md5sum update_firmware.bin
3. modifier avec le résultat la ligne "md5": de manifest_update.json
/////////////////////////////////////////////////////////////////////////////////


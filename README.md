## How to Update
1. Discard changes in submodule
```shell
git submodule foreach --recursive git reset --hard
```
2. Pull updates for submodules
```shell
git submodule update --init --recursive
```
3. Reapply changes in submodules
   1. Comment/remove following lines in `./ref/duino-coin/ESP_Code/Settings.h`:
      ```
      extern const char DUCO_USER[] = "my_cool_username";
      extern const char MINER_KEY[] = "mySecretPass";
      extern const char RIG_IDENTIFIER[] = "None";
      extern const char SSID[] = "SSID";
      extern const char PASSWORD[] = "PASSW0RD";
      ```
   2. Add OTA password in `./ref/duino-coin/ESP_Code/ESP_Code.ino` before the `ArduinoOTA.begin()`
      ```
      ArduinoOTA.setPassword(OTA_PASSWORD);
      ```

## Upload via usb:

```bash
RIG_ID=esp_32-xxx OTA_PASSWORD=zzzz pio run -e usb --target upload
```

## Issues:
1. WebView not working
2. OTA not working
3. It has lower Hashrate in comparison to the original Arduino build
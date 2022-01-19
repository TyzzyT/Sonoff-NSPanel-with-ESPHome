# Sonoff NSPanel with ESPHome and Home Assistant

In this Github repo you can find my [Sonoff NSPanel](https://sonoff.tech/product/smart-wall-swtich/nspanel/) config with [ESPHome](https://esphome.io/) and [Home Assistant](https://www.home-assistant.io/).\
This config is based on the [NSPanel-MF](https://github.com/marcfager/nspanel-mf) config from [marcfager](https://github.com/marcfager), with the [color picker config](https://github.com/MMMZZZZ/Random-Stuff/tree/master/Nextion%20HSV%20Test) from [MMMZZZZ](https://github.com/MMMZZZZ).\
I want to thank everyone on the [Unofficial Nextion Discord](https://discord.gg/98V7qp4), I couldn't have done this without you!\
Last but not least, huge thanks to [Chris Masto](https://github.com/masto/NSPanel-Demo-Files/) for all his hard work. It was him who got me started with the Nextion Editor, after the amazing Youtube video's!

## What is included in my NSPanel configuration
- Dashboard with weather data, indoor temperature, outdoor temperature
- Lights page, where you can tap to toggle the light and long-press to get a detailed overview of the light
- Light detail page, where you can set brightness, color and color temperature
- Media page, where you can select a playlist, view the current playing song and artist, and control the music (work in progress)
- Thermostat page, with the option to view/control the temperature inside the house
- Power monitor page, where you can see the current usage and daily usage (work in progress)
- Swipe navigation. With a control centre if you swipe down, where you can control the brightness and screen timeout
- Screen saver, with the option to change the timeout (1-10 minutes)
- Alarm page, which is being displayed while the home alarm is active (may be used later as an alarm arm/disarm page)
- Notifications! You can send a notification from Home Assistant to the NSPanel, which then plays a sound and displays the notification on the screen

## Remarks
Some parts (especially entity IDs) are in Dutch, but I tried to write as much as possible in English. All comments inside the configuration files are in English.\
I tried to write as much comments as possible, because this can help you understand the configuration. If you still don't understand anything, please let me know.\
Because I'm running two Home Assistant instances (one test and one production), I can't use the homeassistant service directly inside the ESPHome config. Because that way it will toggle the light twice and thus not do anything. That's why I only defined the binary sensors inside ESPHome and did all the automation inside Home Assistant.\
To make sure that all data on the display is being updated, I'm using a template switch called nextion_init. All values are only being send to the display after this switch is turned on. Switch will automatically turn on once the API has an active connection.

## Installation
*See [masto's Youtube video](https://youtu.be/Kdf6W_Ied4o) for details on how to do this*
1. Install and configure ESPHome. You need to change the TFT URL to fit your situation
2. Flash the NSPanel with the ESPHome firmware
3. Compile the Nextion HMI to a TFT file
4. Upload your custom TFT to a webserver (can be Home Assistant)
5. Add the NSPanel ESPHome as an integration to Home Assistant
7. Flash the Nextion display with your custom firmware. This can be triggered from within Home Assistant, with the TFT Upload button
8. Add the [automations](https://github.com/TyzzyT/Sonoff-NSPanel-with-ESPHome/blob/main/Home%20Assistant/automations.yaml) to Home Assistant

## Pictures
![Dashboard](https://github.com/TyzzyT/Sonoff-NSPanel-with-ESPHome/blob/main/images/page-dashboard.png?raw=true)\
![Livingroom](https://github.com/TyzzyT/Sonoff-NSPanel-with-ESPHome/blob/main/images/page-livingroom.png?raw=true)\
![Lightdetails](https://github.com/TyzzyT/Sonoff-NSPanel-with-ESPHome/blob/main/images/page-lightdetails.png?raw=true)\
![Media](https://github.com/TyzzyT/Sonoff-NSPanel-with-ESPHome/blob/main/images/page-media.png?raw=true)\
![Thermostat](https://github.com/TyzzyT/Sonoff-NSPanel-with-ESPHome/blob/main/images/page-thermostat.png?raw=true)\
![Settings](https://github.com/TyzzyT/Sonoff-NSPanel-with-ESPHome/blob/main/images/page-settings.png?raw=true)\
![Notification](https://github.com/TyzzyT/Sonoff-NSPanel-with-ESPHome/blob/main/images/page-notification.png?raw=true)

## To-do list
- Create nicer UI elements. The slider doesn't really fit the theme, but main focus was getting it to work technically
- Configure the media page, currently it can only do play/pause and volume up/down
- Send the current page to ESPHome, so ESPHome knows which page is currently active. This can be useful when sending a notification
- Display CO2 livingroom value on the dashboard/livingroom page
- Maybe change the rendered color field into a static image
- Maybe change the color temperature buttons into a slider
- Maybe create an equipment page, to control the vacuum robot and other equipment

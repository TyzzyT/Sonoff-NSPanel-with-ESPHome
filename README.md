# Sonoff-NSPanel-with-ESPHome

In this Github repo you can find my [Sonoff NSPanel](https://sonoff.tech/product/smart-wall-swtich/nspanel/) config with [SPHome](https://esphome.io/) and [Home Assistant](https://www.home-assistant.io/).
This config is based on the [NSPanel-MF](https://github.com/marcfager/nspanel-mf) config from [marcfager](https://github.com/marcfager), with the [color picker config](https://github.com/MMMZZZZ/Random-Stuff/tree/master/Nextion%20HSV%20Test) from [MMMZZZZ](https://github.com/MMMZZZZ).
I want to thank everyone on the [Unofficial Nextion Discord](https://discord.gg/98V7qp4), I couldn't have done this without you!

# What I included in my NSPanel configuration
- Dashboard with weather data, indoor temperature, outdoor temperature
- Lights page, where you can tap to toggle the light and long-press to get a detailed overview of the light
- Light detail page, where you can set brightness, color temperature, light color
- Media page, where you can select a playlist, view the current playing song and artist, and control the music (work in progress)
- Thermostat page, with the option to view/control the temperature inside the house
- Power monitor page, where you can see the current usage and daily usage (work in progress)
- Swipe navigation. With a control centre if you swipe down, where you can control the brightness and screen timeout
- Screen saver, with the option to change the timeout (1-10 minutes)
- Alarm page, which is being displayed while the home alarm is active (may be used later as an alarm arm/disarm page)
- Notifications! You can send a notification from Home Assistant to the NSPanel, which then plays a sound and displays the notification on the screen

# To-do list
- Configure the media page, currently it can only do play/pause and volume up/down
- Display CO2 livingroom value on the dashboard/livingroom page
- Maybe change the rendered color field into a static image
- Maybe change the color temperature buttons into a slider

# Remarks
I tried to write as much comments as possible, because this can help you understand the configuration. If you still don't understand anything, please let me know.
Because I'm running two Home Assistant instances (one test and one production), I can't use the homeassistant service directly inside the ESPHome config. Because that way it will toggle the light twice and thus not do anything. That's why I only defined the binary sensors inside ESPHome and did all the automation inside Home Assistant.

# Pictures

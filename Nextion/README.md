Here you can find my Nextion config (.HMI file). It's a bit complex, so I tried to write as much comments inside the code as possible. But I'll still explain a bit on this page too. If you have any questions, please let me know!\
\
To use variables more easily, I created a lot of global variables under the program's tab. There are things like: brightness setting, screen timeout, swipe navigation, etc.\
![progams-variables](https://github.com/TyzzyT/Sonoff-NSPanel-with-ESPHome/blob/main/images/programs-variables.png?raw=true)
There is a TouchCap on every page where swipe navigation is needed. You can define the go-to page under the _Touch Release Event_ tab of the TouchCap (tc0). The timer tm0 is used to make sure that the touch event has stopped.\
\
There is a timer called sleep_timer on every page where screen timeout is wanted. When the timer has finished, it saves the current page in a global variable and then goes to the screensaver page.\
\
On the livingroom page, there is a timer called but_timer with a time of 1,2 seconds. This is used to determine whether the light button is tapped (to toggle) or long-pressed which takes you to the light-details page.\
If you have lights that are only on/off (no brightness, cold/warm white, color, etc.), you can disable the light-details page by setting but_timer.en=0 on the Touch Press Event of the light icon. This is done on the 1st button.\
If you have lights that don't support one of the options, you can hide that specific item (brightness) by setting _lightdetails.vis_bright.val=1_ (visible) or _lightdetails.vis_bright.val=0_ (not visible).\
\
If you change anything on the settings page or the lightdetails page, you may need to change the slider IDs in the TouchCap on that page. To prevent that using the slider will navigate to another page.\
\
When pressing the screen on the alarm page, it will light up the screen to the original brightness. It will get back to 5% brightness when you stop touching the screen.\
\
On the notification page, there is a Touch Release Event that takes you to the page _dashboard_, so you can stop the notification from showing. If you don't touch the display, it'll go back after 20 seconds (timer set in ESPHome config).

# Glance

Glance is the firmware of the Glance Display, a small desk display with seven screens and a full-screen alert system:

- **Clock and weather**: a 12 hour clock, the date, and the weather for your city.
- **Calendar**: the month at a glance, with today ringed.
- **Prayer times**: calculated on the display from your location, with a Ramadan mode.
- **Claude usage**: how much of your Claude Code session and weekly limits you have used, and when they reset.
- **PC temps**: CPU and GPU temperatures and RAM use from your Windows PC or Mac.
- **Parcels**: where your deliveries are, from Paperfly, DigiBox, Carrybee, Steadfast, RedX, AliExpress and more.
- **Pinned parcel**: one parcel of your choice on a screen of its own.
- **Alerts**: earthquakes, storms, floods and "rain soon" take over the whole screen, then close by themselves.

It is set up from a web page or from the free Glance Manager desktop app, and updates over WiFi. Nothing to open, flash by cable or solder.

Meet Pico, the little coral owl who keeps you company when a screen has nothing to show.

Source and releases: [github.com/zhtipu/glance](https://github.com/zhtipu/glance)

## What you need

- A **Glance Display**.
- A 2.4 GHz WiFi network (the Glance Display cannot use 5 GHz).
- Optional: **Glance Manager** on your PC. It feeds the Claude usage, PC temps, parcels, prayer comparison and alert screens, and manages the Glance Display.

## Updating the firmware

1. Open `http://<your Glance Display's address>/update` in a browser. The address is shown on the Glance Display while it starts, on the Connected screen, and on the clock screen.
2. Choose `glance-0.14.1.bin` and upload it. Keep the Glance Display powered. It restarts by itself after about 30 seconds.
3. Done. Your settings are kept.

You can also update from Glance Manager: Device > System > Firmware update > Choose file > Install.

`glance-0.14.1-turbo.bin` is the same firmware running the processor at 160 MHz. It redraws slightly faster and runs a little warmer. If you are not sure, use the normal file.

To go back to an earlier version, upload that version's `.bin` file in the same way.

## First setup

1. Power the Glance Display. On first start (or when it cannot find your WiFi) it shows a **Setup mode** screen.
2. On your phone or PC, join the WiFi network called **Glance-Setup**.
3. A setup page opens. Pick your home WiFi, enter the password and save. The Glance Display restarts and joins your network.
4. The Glance Display shows its address on the **Connected** screen. Open it in a browser to reach the settings page and set your city.

If the clock stays on "Syncing time..." for more than a minute, check that your WiFi has internet access.

## The screens

Press the Glance Display's button to move to the next screen. You can also turn on automatic rotation in the settings and choose which screens take part. Hold the button for about 1.5 seconds to show the network info screen (address, signal strength, firmware, memory) for 20 seconds.

Words are set in Segoe UI Variable and numbers and headings in Bebas Neue.

### Clock and weather

- Big 12 hour clock with the date row (`SUN, OCT 18 | AM`) and a seconds bar.
- The weather card shows the temperature, the conditions, your city and a matching icon. The icon is a sun by day and a moon at night.
- The bottom line rotates through the high and low, chance of rain, the next sunrise or sunset, a rain warning and the address. Each line can be turned off, and you choose how long each stays.
- Set your city in the settings, or let Glance find it from your internet connection. Weather comes from Open-Meteo by default, which needs no account. You can use OpenWeatherMap instead if you add your own key.
- The time zone is found automatically from your city. You can pick one by hand if you prefer.
- Every color on this screen can be changed, with a color picker and presets.

### Calendar

The month grid with today ringed in a gently pulsing circle. Weeks start on Sunday or Monday, as you choose.

### Prayer times

Times are worked out on the Glance Display itself from its location and clock, so they keep updating without internet. Glance Manager can compare several sources (the display, AlAdhan, UmmahAPI and a calculation on your PC), pick the time most of them agree on, add your own minute adjustments, and send the display seven days at a time.

Three layouts, switchable in the settings:

- **5 Prayer List**: all five prayers in one list.
- **Prayer Card Carousel**: the prayers as cards, two at a time, flipping every 8 seconds.
- **Active Prayer Card**: the prayer that is on now, and the next one coming up.

The next prayer has a blinking border. The header shows a mosque and the live time. **Ramadan mode** adds Sunrise, Suhoor and Iftar cards, last-hour countdowns and a faded mosque skyline. Choose the calculation method, Asr school, Hijri date correction and Ramadan mode in the settings.

### Claude usage

Shows two meters, **Session** (5 hours) and **Weekly**, with the percentage used and the time until each resets, and the time with AM or PM in the header. A line at the bottom shows what Claude is "doing".

This screen needs Glance Manager running on the PC where you use Claude Code. It reads your usage and sends it to the Glance Display every 20 seconds. If the Glance Display stops getting data, it shows **Stale** after 90 seconds, then Pico waits for Claude after 3 minutes.

### PC temps

Shows CPU and GPU temperature and load and RAM use, with an icon for Windows or macOS, and the time with AM or PM. Data comes from Glance Manager on Windows (or the small script in `pc_agent` on a Mac). When no data arrives for a minute, Pico waits for your PC.

### Parcels

Add a tracking number or link in the **Parcels** page of Glance Manager. The app checks the courier about every 45 minutes and sends a short summary to the Glance Display, which shows:

- a list of up to three parcels per page (it flips pages if you have more), each with a name, a short status and a five-step bar, plus a live or offline note
- a full-screen **On its way** with a parcel box and speed lines when a parcel is out for delivery
- a full-screen **Delivered** with a parcel box, a tick and confetti when your only parcel has arrived
- Pico, blinking, and "No parcels" when the list is empty

Only a name and a short status are sent to the Glance Display: never addresses, phone numbers or rider names. The Parcels screen is skipped by automatic rotation when there are no parcels.

### Pinned parcel

One parcel gets a screen to itself, with a large parcel icon, its stage, name, courier and a journey bar. Pin it in Glance Manager or on the settings page. It is skipped by automatic rotation when nothing is pinned.

### Alerts

An alert takes over the whole screen with a big icon, one main reading and a few short words, inside a blinking border. It closes by itself after 30 seconds (you can change that) and the Glance Display goes back to the screen it was on. There is no button to press.

- **Earthquakes** (USGS): shows the magnitude, how far away and in which direction. You choose the smallest magnitude and how far away to care about.
- **Storms, floods, volcanoes and tsunamis** (GDACS): shows the alert level and distance. You choose the lowest level and the range.
- **Rain soon**: worked out on the display from the minute-by-minute forecast, once for each rain spell. You choose how much rain counts.

The first two are fetched by Glance Manager and sent to the display, because the display cannot open secure web pages. Alert colors follow the level (red, orange, blue) and can be changed. You can also set quiet hours and send test alerts from the settings.

### Themes

One tap recolors every screen: backgrounds, panels, text and the accent. Choose **Clay** (the default), **Ocean**, **Forest**, **Amoled** or **Mono** on the Display tab, in the web page or in Glance Manager. Status colors such as green, amber and red, parcel stages and weather icons keep their meaning in every theme. A theme also fills in the clock screen's own colors, which you can still fine tune afterwards.

## Settings page

Open `http://<your Glance Display's address>` in any browser on your network. There is one tab per screen:

| Tab | What it does |
| --- | --- |
| Overview | Status of the Glance Display and a quick screen switch |
| Clock & weather | City, weather source, time zone, units, bottom line, colors |
| Prayer | Layout, calculation method, Asr school, Ramadan mode, minute adjustments |
| Alerts | What to be warned about, how far, how long, quiet hours, colors, test buttons |
| Claude usage | When to show "stale" and when to show Pico |
| PC temps | Units and when to show Pico |
| Parcels | Takeover options and adding parcels for Glance Manager to track |
| Display | Theme, brightness, automatic rotation, screen clearing |
| WiFi | Scan and join a different network, or forget the current one |
| System | Restart, factory reset, firmware update, memory and health numbers |

Every tab with defaults has a reset button, so you can always go back to how it came.

## Glance Manager (desktop app)

Glance Manager finds your Glance Display on the network, feeds the Claude usage, PC temps, parcels, prayer and alert screens, and gives you the same settings as the web page with a nicer layout, including one-click themes. It also shows your Claude usage on your PC and can install new firmware for you. Start it, leave it in the tray, and the Glance Display keeps itself up to date. Its own README covers building and running it.

## Tips and fixes

- **Screen is black after installing:** open the settings page and press Save once. The brightness is applied on the first save.
- **Weather says "Loading" for a long time:** make sure the Glance Display has internet, then press "Refresh weather" on the Clock & weather tab. Check the city spelling.
- **The time is wrong:** set the city or pick a time zone by hand. Press "Sync clock" to try again.
- **Prayer times are a minute or two off:** use the minute adjustments on the Prayer tab, or let Glance Manager compare sources.
- **A faint trace of another screen shows behind the cards:** this can happen on IPS panels that show the same image for a long time. Use Display > Clear ghosting. It cycles solid colors for a few seconds.
- **The Glance Display does not show the Claude, PC, parcel or alert screens' data:** these need Glance Manager running on your PC, on the same network.
- **The Glance Display shows SAFE MODE:** it restarted after a problem. Unplug it for a few seconds. If it comes back, install the firmware again from the System tab or the `/update` page.
- **Lost the address:** hold the button for about 1.5 seconds. The Glance Display shows its address for 20 seconds.
- **Wrong WiFi or moved house:** use the WiFi tab to forget the network. The Glance Display restarts and opens **Glance-Setup** again.

## Good to know

- Glance only talks to the internet for weather, your location (if you let it find it), and the time. Your Claude usage, PC temps and parcels stay on your own network, except for the courier look-ups Glance Manager makes.
- The settings page has no password. Anyone on your WiFi can open it, so do not expose the Glance Display to the internet.
- Settings are saved on the Glance Display and survive restarts and firmware updates.
- The bottom 10 pixels or so of the glass are hidden by the case, so screens keep their content above that line.

## For developers

- Built with PlatformIO, the Arduino core for ESP8266 and TFT_eSPI. Build with `pio run -e glance` (add `-e glance_turbo` for the 160 MHz build, `-e loader` for the recovery image).
- The web page source is in `web/index.html` and is compressed into the firmware at build time.
- Fonts and icons are generated, not hand-edited: `tools/gen_clock_fonts.py` writes `src/ckfonts.h` (Bebas Neue from the `font` folder, and Segoe UI Variable from the Windows copy, for personal use), `tools/gen_font.py` writes `src/dsp.h`, and `tools/gen_icons.py` writes `src/icons.h`. Pico's sprites are in `src/pico.h`.
- Colors come from a theme table in `src/main.cpp` (`THEMES`, setting key `th`). Screens read the live palette (`C_BG`, `C_PANEL`, `C_TEXT`, `C_SOFT`, `C_TRACK`, `C_CLAY`); status colors are fixed on purpose.
- Prayer math is in `src/prayer.h`. The display answers `GET /api/prayer?n=` with its own times and accepts `POST /api/prayer/push` from Glance Manager. Alerts arrive on `POST /api/alerts` (with `/api/alerts/test` and `/api/alerts/clear`).
- The Claude usage feed is a plain `POST /api/usage` with `{"s":..,"sr":..,"w":..,"wr":..,"st":..,"ok":true}`. PC temps use `POST /api/temps`.
- Mockups of every screen, approved one by one, are in `mockups/`.
- `pio run -e loader` builds a small recovery image (`glance-loader.bin`) that joins WiFi, shows the address to open and serves `/update`, for a display that needs the full firmware put back. The build refuses anything over the flash limit.
- If the display restarts by itself, `GET /api/diag` shows `lastCrash` (what the last crash left behind, kept across the restart), `contMin` (the least free loop stack seen) and the reset reason. The loop stack is only 4 KB, so keep big buffers and copies out of handlers and out of `loop()` (static or heap), and mark large helpers `NOINL`.
- There is no TLS on the display. Anything that needs HTTPS is fetched by Glance Manager and pushed.

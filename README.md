# Standing Desk Interval Coach

**AppADay 166** | Category H (Health) | No AI

A sit, stand, and walk interval timer for desk work with a walking pad. Pick a preset, press Start, and the screen shifts color and chimes when it is time to change posture. Everything stays on your device.

**Live app:** https://augustineiacopelli.github.io/appaday-166-standing-desk-interval-coach/
**Portfolio:** https://augustineiacopelli.github.io/appaday/

## Features

**Presets.** Three built in presets, all editable and restorable with Restore defaults: Cornell 20/8/2 (sit 20, stand 8, walk 2), Simple 30/30 (sit 30, stand 30), and Walking Pad (sit 20, walk 10, stand 15, with a 10 minute break every 3 cycles). Make your own with New preset, add or remove segments, and set a break every N cycles.

**Honest overtime.** When a segment runs past its planned length, the clock keeps counting as visible overtime, a due banner appears with an oversized Switch button, and the log records what you actually did, not what the plan said.

**Nudges.** Each posture has its own Web Audio chime (Sit descends, Stand rises, Walk plays three rising notes, Break rings a bell) and its own vibration pattern on phones that support it. A pulse overlay flashes the color of the next posture. Reminders repeat every 2 minutes of overtime, up to 3 more times. Optional notifications fire when the tab is hidden (desktop and Android only).

**Walking pad speed.** Speed runs from 0.5 to 4.0 mph in 0.1 steps and can be set in three places: a default speed in Settings (with an Apply to all presets button), a speed on each Walk row of the preset editor, and large minus and plus buttons on the Walk screen. Live changes are debounced for 1.5 seconds so a burst of taps creates one log boundary. Incline (0 to 15 percent in half steps) has a default in Settings and its own stepper on the Walk screen, debounced together with speed. Turn on Remember this speed and incline to write the live settings back to the preset. Distance is computed from time and speed.

**Calories.** Enter your body weight (lb or kg) in Settings to see approximate calories. Sitting at a desk uses 1.3 METs and standing desk work 1.8 METs (Compendium of Physical Activities), and breaks count at the sitting rate. Walking uses the ACSM walking equation, VO2 = 3.5 + 0.1 x speed + 1.8 x speed x grade (speed in meters per minute), at about 5 kcal per liter of oxygen, so both pad speed and incline change the burn. The Today panel shows total calories, the extra burned versus sitting the whole time, the standing and walking shares of that extra, and sit and stand calories per hour at your weight. The Walk screen shows calories per hour at the current settings and the running total for the current walk. These are population estimates, not measurements.

**Posture chips.** Before a session, tapping Sit, Stand, or Walk only selects the posture to begin with (tap again to clear it); nothing starts or logs until you press Start. Selecting Walk shows the speed and incline controls so you can set them first. During a session, a chip switches posture right away, and the plan picks up afterward at the next segment with a different posture.

**Stats.** Today's sit, stand, walk, and break minutes, miles, and switch count; a progress bar toward the daily stand plus walk goal (60 minutes by default); a timeline bar with hour ticks; Last 7 Days bars that stack standing and walking minutes as progress toward the daily goal, filling to the top and outlined in green only on days the goal is met, and rescaling whenever the goal changes; and a streak. Choose your streak days in Settings by tapping any combination of the seven days, or use the Weekdays, Every day, Mon Wed Fri, and Tue Thu shortcuts (Weekdays is the default). A day off your schedule never breaks the streak but still counts if you meet the goal, and today stays pending until midnight. Entries that cross midnight are split between days.

**Reliability.** Elapsed time is always computed from the clock, so backgrounding the tab never loses time. The screen wake lock keeps the display on while running (status shown in the pill). If the page is reopened more than 20 minutes after it was last seen with a segment still running, it asks whether to end the segment at the last seen time or keep it running through now.

**Data.** Settings, presets, the current session, and up to 120 days of history are stored in localStorage (keys sdic-settings, sdic-presets, sdic-state, sdic-log). Export and import JSON, or clear all data, from Settings.

## Testing

Add `?scale=60` (up to 600) to the URL to compress time: at scale 60 a planned minute lasts one second and reminders repeat every two seconds. A TEST badge appears in the header. Logged history still records real elapsed time.

## Tech

Single `index.html` with inline CSS and vanilla JavaScript. Google Fonts (Sora, DM Sans). Web Audio API, Screen Wake Lock API, Vibration API, and Notifications API, each used only where available. Includes the AppADay home screen icon tags and the shared Save to Phone script.

Part of [AppADay](https://augustineiacopelli.github.io/appaday/), one app shipped every day.

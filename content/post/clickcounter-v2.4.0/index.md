---
title: "Click Counter v2.4.0 Release"
date: 2023-06-23T12:00:00-04:00
lastmod: 2023-06-23T12:00:00-04:00

description: "Right clicks, general refactor, more stable/modern codebase, QOL features."
image: "featured-image.png"

tags: ["Minecraft", "Modding", "Updates"]
categories: ["clickcounter"]
---

{{< param description >}}

<!--more-->

Formally known as Left Click Counter Mod, Click Counter counts your left and right clicks and displays them on your Minecraft HUD. Version 2.4.0 saw the introduction of right clicks, a general refactor, a more stable/modern codebase, and QOL features. Note: a migration of your previous config is needed (located in `.minecraft/config/LeftClickCounter.cfg`). Copy the value in the `SHHH...` key to value in `Clicks` under the `Left` catergory (located in `.minecraft/config/Clicks.cfg`).

## Changelog

### General
  - New
    - Added right clicks
    - Option to toggle the display of left/right clicks
  - Changes
    - Renamed to Click Counter Mod
    - Removed unused assets
    - Removed support for other Minecraft versions (I welcome pull requests with ports to other versions)
    - MIT Open Source License
    - Forge 1.8.9 Gradle MDK included
    - Note: Java 1.8 is required for this Gradle to work, the Gradle project must not be imported into IntelliJ
    - `.gitignore` excludes project generated files
  - Overhaul
    - Settings/config file has been heavily refactored
  - Known Bugs
    - Older configs no longer work (won't fix)

### Positioning
  - New
    - Added "Go back" button to return to the main page
  - Overhauls
    - Clicking and dragging the text moves it around and saves its position on release
    - Previously: A left click on the text selected it and and right clicked saved it in a new position, no feedback was given to the user on if the text was moving
  - Known Bugs
    - Both lines of text can be moved at the same time, leading to them always being selected together after saving (planned for 2.4.1)

### Colors
  - Changes
    - Friendly naming for chroma and shadow options
  - Fixes
    - Chroma and shadow options are now reflected in the "Test Color" text
    - The "Refresh Color" button is more stable and will no longer crash from text input errors
  - Planned
    - Remove the "Refresh Color" button and update the colors on the fly (planned for 2.4.1)

### Prefixes
  - Changes
    - Removed the symbol option and merged it with the entire prefix
    - Note: a space should be included and must be done so by the user

### Update Checking
  - Overhauls
    - Updates are now checked through GitHub's REST API
    - Removed auto checking for updates on server join (prone to crashes with a race condition if the response from the API was recieved before the game server loaded)
    - Failed update checks are sent silently to the console
  - Known Bugs
    - No response for if there are no updates avaible (planned for 2.4.1)
    - Older users are no longer notified of updates (won't fix)

## Downloads
[Release Page](https://github.com/joshuafhiggins/clickcounter/releases/tag/v2.4.0)
[Click.Counter.v2.4.0.jar](https://github.com/joshuafhiggins/clickcounter/releases/download/v2.4.0/Click.Counter.v2.4.0.jar) (from GitHub)

## Source Code
The source code for Click Counter is avaible [on GitHub](https://github.com/joshuafhiggins/clickcounter/) under the MIT License.
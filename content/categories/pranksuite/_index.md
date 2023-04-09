---
title: "Prank Suite"
---
*[Formally, Weeb Detector](https://www.youtube.com/embed/grI_YSRRoBY) was a prank I made to use on my brother, since he started watching anime. He deserved this punishment fully. I made a video on how to set it up and a code walk-through aswell.*

NOTE: This software can be used maliciously. I am no way responsible for the use of this software and encourage its use in good faith.

## Features
- See and close open user's windows
- Trigger popups with custom text
- Trigger HTML popups
- Remotely play sounds
- Remotely change the user's wallpaper

## Changes since Weeb Detector
- Trigger HTML popups
- Remotely play sounds
- UI Redesign for ease of pranking
- Ability to transfer files for all pranks

## Setup
1. Download the source code from [GitHub](https://github.com/higgy999/PrankSuite)
2. Open the project in IntelliJ and change the `SERVER_IP` in `PSClient.java` to your computers local IP address
3. Build the server and client artifacts
4. Download [JavaFX SDK](https://gluonhq.com/products/javafx/) and extract it somewhere safe
5. When running the client and server, add `--module-path .\PATH_TO\javafx-sdk-XX.X.X\lib` and `--add-modules=javafx.controls,javafx.fxml,javafx.web` to the run command
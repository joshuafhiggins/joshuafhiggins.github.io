---
title: "Prank Suite"
image: "featured-image.webp"
---
NOTE: This software can be used maliciously. I am no way responsible for the use of this software and encourage its use in good faith.

## Features
- See and close open user's windows
- Trigger popups with custom text
- Trigger HTML popups
- Remotely play sounds
- Remotely change the user's wallpaper
- UI Redesign for ease of pranking
- Ability to transfer files for all pranks

## Setup
1. Download the source code from [GitHub](https://github.com/joshuafhiggins/PrankSuite)
2. Open the project in IntelliJ and change the `SERVER_IP` in `PSClient.java` to your computers local IP address
3. Build the server and client artifacts
4. Download [JavaFX SDK](https://gluonhq.com/products/javafx/) and extract it somewhere safe
5. When running the client and server, add `--module-path .\PATH_TO\javafx-sdk-XX.X.X\lib` and `--add-modules=javafx.controls,javafx.fxml,javafx.web` to the run command
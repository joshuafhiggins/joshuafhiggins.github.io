---
title: "Prank Suite Release"
date: 2023-04-08T22:12:00-04:00
lastmod: 2023-04-08T22:12:00-04:00
# date: YEAR-MONTH-DAYTHOUR:MINUTE:SECOND-04:00
draft: false

# author: "LitlToast"
# authorLink: "https://higgy999.github.io"
description: "The next step in pranking your friends and family."
image: "featured-image.png"

tags: ["Releases"]
categories: ["pranksuite"]
---

{{< param description >}}

<!--more-->

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
1. Download the source code from [GitHub](https://github.com/joshuafhiggins/PrankSuite)
2. Open the project in IntelliJ and change the `SERVER_IP` in `PSClient.java` to your computers local IP address
3. Build the server and client artifacts
4. Download [JavaFX SDK](https://gluonhq.com/products/javafx/) and extract it somewhere safe
5. When running the client and server, add `--module-path .\PATH_TO\javafx-sdk-XX.X.X\lib` and `--add-modules=javafx.controls,javafx.fxml,javafx.web` to the run command

## The Development Path
By default, Kyronet doesn't support sending files across the network. Although this post is being made way after release, I remember this process being hard to debug, but this isn't a fault of Kyronet. Both the client and server are kept in one source file. I never want to design an app like this again, but it was a carryover from Weeb Detector which was smaller in scope. Like most things, I want to remake this in Rust and have an easier way of changing the supplied IP address to the client.
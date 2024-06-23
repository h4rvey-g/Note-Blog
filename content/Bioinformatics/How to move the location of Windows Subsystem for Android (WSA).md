---
author: Harvey Guo
created: 2023-10-23 10:24
modified: 2023-10-23 10:24
aliases: Untitled
share: true
---
1. Install/register WSA in your preferred location (I used MagiskOnWSALocal so it's installer script takes care of that).
2. Make sure that WSA is actually turned off (e.g. _WSA Settings -> System -> Turn off_).
3. Move the _userdata.vhdx_ & _metadata.vhdx_ files from `%LOCALAPPDATA%\Packages\MicrosoftCorporationII.WindowsSubsystemForAndroid_8wekyb3d8bbwe\LocalCache` to somewhere else (if not present in the beginning then start WSA for the first time, then turn it off and check again).
4. Create symbolic links for them in their usual places. You can use [Link Shell Extension](https://schinagl.priv.at/nt/hardlinkshellext/linkshellextension.html) to add context menu entries for this (_Pick Link Source_, then _Drop Symbolic Link_).

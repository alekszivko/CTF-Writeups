# Emoji Hunt

![Challenge Description](https://raw.githubusercontent.com/acoozi/CTF-Writeups/main/SquareCTF2022/ressources/emoji_hunt_challenge_description-0.png)


As in the challenge description written, there are a couple of emojis that are containing parts of the flag. 

Looking at the slack workspace and searching for the keyword flag shows us some emojis named as :he-brings-you-\*, as well square-ctf-\*. Both of them show a flag on the emoji.

![he-brings-you-\*](https://raw.githubusercontent.com/acoozi/CTF-Writeups/main/SquareCTF2022/ressources/emojis_he-brings-you1-1.png)
![square-ctf-\*](https://raw.githubusercontent.com/acoozi/CTF-Writeups/main/SquareCTF2022/ressources/emojis_squarectf-.png)


Downloading some of them and taking a look at their metadata using exiftool it shows that there is an entry " FL :" followed by a short string which has to be part of the flag. 

![metadata](https://raw.githubusercontent.com/acoozi/CTF-Writeups/main/SquareCTF2022/ressources/metadata_1-0.png)

Unfortunately the emojis downloaded don't have the whole flag, which means that there has to be more custom emojis containing parts of the flag.

Now we need to download all custom emojis and check their metadata. I have decied to choose a chrome extension called [Save all Resources](https://chrome.google.com/webstore/detail/save-all-resources/abpdnfjocnmdomablahdcfnoggeeiedb?hl=en) which adds a registercard to chromes developertools and lets us download all resources that where loaded by our browser.

After we installed the extions we go to slack and download all emojis. We only need to make sure that we scroll to all the custom ones in order to have the browser load them, so the extions can download them all.

1. Check the sources registercard in dev-tools. There you can see the page emoji.slack-edge.com. Expanding the entry and the folders beneath thats where the emojis are stored. The paths is as follows <page/workspacename/emojiname/emoji.png>. While its not needed here we can check if emojis are loaded as we scroll through them.

![dev-tools](https://raw.githubusercontent.com/acoozi/CTF-Writeups/main/SquareCTF2022/ressources/dev_tools-0.png)

2. Now that we have scrolled through them we move to the extensions registercard and save all resources, which creates an app.slack.com zip file with the content.

![extensioin: save all resources](https://github.com/acoozi/CTF-Writeups/blob/main/SquareCTF2022/ressources/resources_saver-0.png)

After unziping the file, the folder app.slack.com"/emoji.slack-edge.com"/TDJ19TTMW/ contains all emojis in subfolders. With an one liner we can then search for the needed metadata and get the flag.

![oneliner & flag](https://raw.githubusercontent.com/acoozi/CTF-Writeups/main/SquareCTF2022/ressources/oneliner_flag-0.png)

# Emoji Hunt

![Challenge Description](https://raw.githubusercontent.com/acoozi/CTF-Writeups/main/SquareCTF2022/ressources/emoji_hunt_challenge_description-0.png)


As in the challenge description written, there are a couple of emojis that are containing parts of the flag. 

Looking at the slack workspace and searching for the keyword flag shows us some emojis names as :he-brings-you-\*. As well as some named as square-ctf-\*. Both of them showing a flag on the emoji. 



Downloading some of them and taking a look at their metadata using exiftool it shows that there is an entry " FL :" followed by a short string which has to be parts of the flag. Unfortunately the emojis downloaded don't have the whole flags which means that there has to more emojis containing the parts of the flag.

Now in order to automate as much as possible we need to download all custom emojis and check all for metadata.

---Coming Soon---

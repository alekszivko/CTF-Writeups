# sqUARe paymenT terminal

![Challenge Description](https://raw.githubusercontent.com/acoozi/CTF-Writeups/main/SquareCTF2022/ressources/square_payment_terminal_description-0.png)

The challenges contains a Terminal_Cap.sal file. This file is a capture of an asynchronous serial communication. The uppercase letters "UAR" are actually a hint to
the UART protocol that stands for "Universal Asynchronous Receiver/Transmitter".

*Not needed for the challenge. Unpacking the file gives us 8 binary files numbered from 0 - 7. This file actually contains communication. The number at the end of each
file stands for a channel. So channel 0-7. For this challenge only the channel 0 was used.*

Now looking for software to analyze the file I found [Logic 2](https://www.saleae.com/downloads/) from salae. There might be other tools as well.

Opening the capture in the software it shows as 7 channels while only the channel 0 had some communication in the capture. Withe the software we can then setup an analyzer
in this case Async Serial. As for the settings most of them were default settings. Only the bitrate had to be changed. In order to get the bitrate right we need to
measure the fastest bits. In our case it is 38.4 kHz which is 38400 bits per second.

Check for further details the documentation on salaes website.

![Using Async Serial(Analyzer)](https://support.saleae.com/protocol-analyzers/analyzer-user-guides/using-async-serial)
![Decoding UART](https://support.saleae.com/protocol-analyzers/analyzer-user-guides/using-async-serial/decode-uart)


After adding an asynchronous analyzer

![Adding Analyzer](https://raw.githubusercontent.com/acoozi/CTF-Writeups/main/SquareCTF2022/ressources/uart-0.png)

and setting up our analyzer with 38400 bits/s

![Setup Analyzer](https://github.com/acoozi/CTF-Writeups/blob/main/SquareCTF2022/ressources/uart2-0.png)

We can see in our data table view on the right side hex data and have no framing errors (Happens due to wrong settings like bitrate etc.).

![data table view](https://github.com/acoozi/CTF-Writeups/blob/main/SquareCTF2022/ressources/uart3-0.png)

Now we could export the data and decode the hex data ourselves. But luckily the tool contains a terminal view which already decodes it for us and gives us the flag.

![Terminal View & Flag](https://raw.githubusercontent.com/acoozi/CTF-Writeups/main/SquareCTF2022/ressources/uart4-0.png)





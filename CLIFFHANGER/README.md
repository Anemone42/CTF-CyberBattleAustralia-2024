# Solution for CLIFFHANGER

Forensics the webm file, gives a zip file within the webm.
The video will not play its full duration due to corruption/incorrect data.

Carve out the zip file using dd, and place it back together.

`binwalk tutorial.webm`\
`dd if=tutorial.webm bs=1 count=20000 of=out1`\
`dd if=tutorial.webm bs=1 skip=70204 of=out2`\
`cat out1 out2 > fixed.webm`

fixed.webm will now play to its full duration.

Extract the zip file from tutorial.webm. (binwalk -e tutorial.webm | foremost -i tutorial.webm)

Play the fixed video and password for the zip file is "bruteforce-resistant". (without quotes)
![image](https://github.com/Anemone42/CyberAustralia/assets/47408478/d50c54d2-1b0d-45f0-a585-2633ea5f798c)

`strings data.raw | grep ctf`\
will grab the flag:
ctftech{divide_and_conquer}

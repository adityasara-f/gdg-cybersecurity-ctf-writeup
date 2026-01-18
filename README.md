GDG Cybersecurity Recruitments 2026
Task 1 CTF Writeup
Setup and Tools

I did this task using Ubuntu on WSL since I’m on Windows as I did not have enough time to install a VM


I mainly used basic Linux commands, Base64 decoding, image analysis tools, steganography tools, QR decoding tools, and Python for handling extracted data.

Part 1
The folder contained README.txt, app.py, and xotwod.txt.

I first went through all the files. The README hinted that things were not as simple as they looked. The file xotwod.txt was just song lyrics and didn’t contain anything hidden, so it was clearly a distraction.

The important file was app.py. While reading the code, I noticed a Base64 encoded string stored as a hint. There was another encoded string too, but decoding that gave a fake message, so it was meant to mislead.

After decoding it I got the first part.

Part 1 result
wait_what_if_there_are_disguised_filflags_in_the_data

Part 2
The second part had a single file called heheheha.png.

At first it looked like a normal image. I checked the metadata and also tried reading strings from it, but nothing useful showed up. There was no hidden metadata and the strings output was mostly random characters.

Next, I analyzed the image further and found that it contained compressed data. While extracting it, I ran into permission issues because the file was inside the Windows directory. I fixed this by copying the image into the Linux home folder and running the extraction again.

This gave me a file called 29.zlib. I tried decompressing it, but that failed because the data didn’t have proper headers. This meant the data was either raw or partially compressed.

Since normal methods weren’t working, I moved to image steganography. I checked the least significant bits of the image and was able to extract readable text hidden inside it.

Part 2 result
10:armyk n1f3_

Part 3
The final part contained an archive named qr_code_zipbomb.rar.

After extracting it, I found thousands of QR code images. The README made it clear that scanning them manually was not what we were supposed to do.

So instead, I decoded all the QR codes at once and saved the output into a single text file. I tried scrolling through the decoded output manually, but because there were so many repeated values, it was easy to miss something important. I scrolled through it twice and still couldn’t clearly find the right one. Then I copied the decoded output into Google Docs. Using Find and Replace, I removed repeated and similar decoded values. This helped clean up most of the noise. After eliminating most of the duplicates, one unique Base64 encoded string was left.

Decoding that string gave me the final part.

Part 3 result
gg1ol

Final Flag

After combining all three parts and fixing the formatting, the final flag was:
Gdg{wait_what_if_there_are_disguised_filflags_in_the_data_10:armykn1f3_gg1ol}


the google doc link in case needed: https://docs.google.com/document/d/1EWICKHxHvHR-a4xnFXDG70cjryPHyY2vQC2CUqV-EWY/edit?usp=sharing




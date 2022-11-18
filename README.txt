# Codecademy Coded Correspondence Project

## Project Overview

This project is part of Codecademy's Python Fundamentals II course in the Data Analyst career path. We were given different coded messages to decode using Python, and then challenged with coding our own messages using the ciphers. Messages were coded with Caeser Ciphers and the Vigener Cipher.

## Methodology

My approach to coding and decoding the messages was focused on finding and adjusting the indexes of the characters within the messages. 

For the Caeser Ciphers I defined a string that contained all letters of the alphabet, checked if the character in the message was in the alphabet, and if so, calculated the character's index in the alphabet, which I then used to find the decoded character's alphabetic index with the offset. If the character was not in the alphabet string (i.e. if it was a space or punctuation), it was added to the decoded message string as is.

For step four, I took a different approach than what's in the solution code. Rather than looping through all possible offsets, I reviewed the coded message string and noticed the substring "'ee" within the message. I assumed that would translate to "'ll" in the coded message, and used the letters "e" and "l" to determine the offset of the cipher and tested that offset with my decoder function, and it was successful!

To decode the Vigener Cipher, I used a similar approach to the Caeser Cipher. First, I iterated through each character in the coded message, and used the character's index in the message to construct the keyword phrase where each letter in the keyword phrase is aligned with a character in the message.

I struggled with constructing the keyword phrase for quite a bit. I found it difficult to construct the keyword phrase so the letters of the keyword aligned with the letters in the message, skipping over spaces and punctuation. At first I tried to use the index of the characters within the message to set the corresponding characters in the keyword phrase, but that didn't properly account for spaces and punctuation. Finally, I figured out that I needed to use a counter that increased with each letter in the message and did not increase with spaces and punctuation. The counter also needed to reset to 0 each time it became greater than the highest index in the keyword, which I accomplished with an if/else statement after adding the appropriate character to the keyword string.

The next challenge was actually decoding the message using the newly-constructed keyword phrase. My first instinct was to use 

    message.find(character)

to find the index of the character in the message, then use that index to find the corresponding character in the keyword phrase, find the character's alphabetic index, and then use the alphabetic index of the original character and the character in the keyword phrase to find the alphabetic index of the decoded character.

With this method, I was able to decode the first couple words or so of the message, but after that my decoder function failed. I double checked that the characters in the keyword phrase aligned with the characters in the coded message, that the function was returning the right number of indices for the decoded characters, and that the function was calculating the difference between the keyword alphabetic index and the message alphabetic index forrectly.

Finally I realized that the problem was with using the .find() method to find the index of the characters within the coded message. That method only finds the first instance of the character in the message! Of course! So the message indices I was finding were only for the first instance of the letter, meaning the further into the message I iterated, the further off those indices were from the indices of their corresponding characters in the keyword phrase.

To solve this, I employed the counter method again, which allowed me to select the characters from both the coded message and the keyword phrase in order, find their corresponding alphabetic indexes, then use those to determine the alphabetic index of the new character and add it to the decoded message string. I was thrilled to find this worked! I made copied the decoder function and made some adjustments so that it would work to code messages, and tested both functions on a message of my own.

## Conclusion

I was proud to find solutions to all of the problems in this project! When I started working on the first problem I wasn't sure how to move forward, but with some experimentation I was able to figure out how to decode the message, and as I moved along I built upon what I used earlier in the project to tackle the more complex problems later in the project.

I reviewed the solution code provided by Codecademy and found that my functions weren't as efficient as what Codecademy provided, and I'm looking forward to working on the efficiency of my code in future projects.
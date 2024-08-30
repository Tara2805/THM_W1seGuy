# CRYPTO CHALLENGE

## THM_W1seGuy

### Description
Yes, it's me again with another crypto challenge! Have a look at the source code

Your friend told me you were wise, but I don't believe them. Can you prove me wrong?

The server is listening on port 1337 via TCP

### Walkthrough

Lets go through the source code that was provided (source-code.py)

1. Various modules are imported for handling sockets, random number generation, and string manipulations. Reads a flag from a file named flag.txt and removes any extra whitespace.
2. At the start the code in encoding a message as bytes and sending it to the connected client.
3. Encrypts a hardcoded flag ('THM{thisisafakeflag}') using XOR with a given key and returns the result encoded as a hexadecimal string.
4. Starting the server and generates a random 5 character key, then Prompts the client to guess the encryption key.

By connecting to the server, we can see this code in action as it prompts us to enter the key.
- nc <ip_address> 1337

![alt text](/Images/step1.png)

So we know this is XOR encryption. I did read some other writeups and I am not a lover of all these equations! (Forgive me!) I thought lets have a look at CyberChef and try and implement what these scripts are trying to do but on a much simplier level.

So we have the encoded flag, we know the first 4 characters will be THM{. So lets use that to our advantage. Lets fire CyberChef up.

![alt text](/Images/cyber1.png)
1. Take the first 4 bytes of the encrypted flag and use them as our XOR Key and run it against the input THM{. We get the first 4 bytes of my key: O3v6

![alt text](/Images/cyber2.png)
2. Now I've mixed things up, incorporating the output key and using FROM HEX AND XOR. Since the source code specifies that the key length is 5 characters, the last character could be any letter or digit. So I've decided to brute force this last character and manually enter until the complete key pops up. 

![alt text](/Images/cyber3.png)
3. Yay so we've gotten our Flag! We also know the randomly generated key! Lets input that 5 character key into the running terminal. 

![alt text](/Images/flag2.png)

So we finally got the flag! Bear in mind, if the last character is a letter. You have a 50/50 chance of guessing it correctly as it could be upper case or lower case. Choosing the wrong one means you have to repeat the entire process again (Which I've sadly dealt with :D)






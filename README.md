# Decrypt-an-Encrypted-Message-in-Linux

<h2>Activity overview</h2>

Previously, I learned about cryptography and how encryption and decryption can be used to secure information online. I was also introduced to the Caesar cipher, one of the earliest cryptographic algorithms used to protect people’s privacy.

As a security analyst, it’s important that I understand the role of encryption to secure data online and that I’m familiar with the right security controls to do so.

In this lab activity, I’ll be guided through some basic cryptographic activities using Linux commands to decrypt files and reveal hidden messages.

<h2>Scenario</h2>

In this scenario, all of the files in my home directory have been encrypted. I’ll need to use Linux commands to break the Caesar cipher and decrypt the files so that I can read the hidden messages they contain.

Here’s how I’ll do this task: First, I’ll explore the contents of the home directory and read the contents of a file. Next, I’ll find a hidden file and decrypt the Caesar cipher it contains. Finally, I’ll decrypt the encrypted data file to recover my data and reveal the hidden message.

OK, it's time to decrypt some messages in Linux!

<h2>Task 1. Read the contents of a file</h2>

The lab starts in my home directory, /home/analyst, as the current working directory.

In this task, I need to explore the contents of my home directory and read the contents of a file to get further instructions.

1. Use the ```ls``` command to list the files in the current working directory.

Two files, Q1.encrypted and README.txt, and a subdirectory, caesar, are listed:

[]
The README.txt file contains an important message with instructions I need to follow.

2. Use the ```cat``` command to list the contents of the README.txt file.

The message in the README.txt file advises that the caesar subdirectory contains a hidden file.

In the next task, I’ll need to find the hidden file and solve the Caesar cipher that protects it. The file contains instructions on how to recover my data.

<h2>Task 2. Find a hidden file</h2>

In this task, I need to find a hidden file in my home directory and decrypt the Caesar cipher it contains. This task will enable me to complete the next task.

1. First, use the ```cd``` command to change to the caesar subdirectory of my home directory:

```cd caesar```

2. Use the ```ls -a``` command to list all files, including hidden files, in my home directory.

This will display the following output:

[]
Hidden files in Linux can be identified by their name starting with a period (.).

3. Use the ```cat``` command to list the contents of the .leftShift3 file.

The message in the .leftShift3 file appears to be scrambled. This is because the data has been encrypted using a Caesar cipher. This cipher can be solved by shifting each alphabet character to the left or right by a fixed number of spaces. In this example, the shift is three letters to the left. Thus "d" stands for "a", and "e" stands for "b".

4. I can decrypt the Caesar cipher in the .leftshift3 file by using the following command:

```cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"```

Note: The ```tr``` command translates text from one set of characters to another, using a mapping. The first parameter to the tr command represents the input set of characters, and the second represents the output set of characters. Hence, if I provide parameters “abcd” and “pqrs”, and the input string to the ```tr``` command is “ac”, the output string will be “pr".

In this case, the command ```tr "d-za-cD-ZA-C" "a-zA-Z"``` translates all the lowercase and uppercase letters in the alphabet back to their original position. The first character set, indicated by ```"d-za-cD-ZA-C"```, is translated to the second character set, which is ```"a-zA-Z"```

5. Now, return to my home directory before completing the next task:

```cd ~```.

[]
<h2>Task 3. Decrypt a file</h2>

Now that I have solved the Caesar cipher, in this task I need to use the command revealed in .leftshift3 to decrypt a file and recover my data so I can read the message it contains.

1. Use the exact command revealed in the previous task to decrypt the encrypted file:

```openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute```

Although I don't need to memorize this command, to help me better understand the syntax used, let's break it down.

In this instance, the ```openssl``` command reverses the encryption of the file with a secure symmetric cipher, as indicated by ```AES-256-CBC```. The ```-pbkdf2``` option is used to add extra security to the key, and ```-a``` indicates the desired encoding for the output. The ```-d``` indicates decrypting, while ```-in``` specifies the input file and ```-out``` specifies the output file. The ```-k``` specifies the password, which in this example is ```ettubrute```.

2. Use the ```ls``` command to list the contents of Ir current working directory again.

The new file Q1.recovered in the directory listing is the decrypted file and contains a message.

3. Use the ```cat``` command to list the contents of the Q1.recovered file.

<h2>Conclusion</h2>

I now have practical experience in using basic Linux Bash shell commands to

- list hidden files,
- decrypt a Caesar cipher, and
- decrypt an encrypted file.

This is an important milestone in my journey towards understanding encryption and decryption.




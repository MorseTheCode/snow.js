# SNOW.js - A web-based implementation of the SNOW whitespace steganography program.

A JavaScript and web UI port of the SNOW whitespace steganography program, originally written by Matthew Kwan.

This project condenses all of SNOW's functionality (including Huffman compression and ICE encryption) into a single HTML file that runs entirely in the browser, with no server required.

Overview

SNOW is a program that hides messages in text files by appending sequences of spaces and tabs to the end of lines. Since these characters are invisible to most viewers, they form a secret channel for concealing data.

SNOW.js recreates this functionality in a modern graphical interface, allowing you to:

Conceal text messages or files inside text "cover" files.

Extract hidden messages from text files.

Encrypt your data with a password using the ICE algorithm.

Compress your data using Huffman coding (optimized for English text) to save space.

Calculate the available steganographic storage space in a text file.

Features

Single File, Zero Dependencies: Everything is contained in snow_web.html. Just open it in a browser.

Total Privacy: All encoding, encryption, and decoding happen locally in your browser. No files or passwords are sent over the network.

Full Portability: Implements all major features of the original snow.exe:

Whitespace encoding/decoding.

Huffman Compression (-C): Uses the original Huffman table to compress data.

ICE Encryption (-p): Includes a complete port of the ICE block cipher algorithm and the 1-bit CFB mode.

Space Calculation (-S): Accurately estimates how much data a cover file can hold.

Modern Interface: A clean, tabbed UI built with Tailwind CSS.

How to Use

To Conceal a Message

Open snow_web.html in your browser.

Go to the "Conceal" tab.

1. Cover Text File: Load the .txt file you will use to hide the message (e.g., article.txt).

2. Message to Hide: Choose "Text Input" to type your secret message or "File Input" to load a file (like secret.txt or even a small image).

3. Options:

Password: (Optional, but recommended) Enter a password to encrypt the message.

Use Compression (-C): Check this box if your message is English text. Do not check if it is a .zip file, image, or already compressed data.

Max Line Length: Keep as 80 unless you know you need a different value.

Click "Conceal Message".

A "Download Result" link will appear. Click it to save your new file (e.g., snowed.txt). This file will look identical to the original but will contain your hidden message.

To Extract a Message

Open snow_web.html.

Go to the "Extract" tab.

1. Input File: Load the file that contains the hidden message (e.g., snowed.txt).

2. Options:

Password: Enter the same password you used to conceal the message (if any).

Use Decompression (-C): Check this box if the message was concealed with compression enabled.

Click "Extract Message".

The extracted message will appear in the text box below.

Technical Details

This project was an exercise in porting low-level C code (bit manipulation, cryptographic algorithms) to high-level JavaScript.

encode.c / main.c -> Main UI logic, bit pipeline, and the Encoder/Decoder in JS.

compress.c / huffcode.h -> Compressor/Decompressor classes in JS, using a Map for the Huffman table.

ice.c / encrypt.c -> A complete port of the ICE library and CFB encryption mode into JS classes (ICE_KEY, Encryptor, Decryptor).

Credits and License

All credit for the algorithm, concept, and original implementation goes to Matthew Kwan, the author of SNOW.

The original C code is licensed under the Apache License, Version 2.0. This JavaScript port maintains the spirit and functionality of that original work.

This project is a tribute to the ingenuity of SNOW and serves as a learning and demonstration tool.

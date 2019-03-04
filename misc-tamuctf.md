# TAMUctf 2019 - Misc - All challs excluding Onboarding Checklist

## Howdy
Welcome to TAMUctf!  
This year most of the challenges will be dynamically scored meaning the point value will adjust for everyone, including those have already solved the challenge, based on the number of solves.

The secure coding challenges will appear when you have solved their corresponding challenges.

If you have any questions or issues feel free to contact the devs on the discord.

Good luck and have fun!

The flag is: `gigem{H0wdy!}`

**Solve**
Obviously the flag is gigem{H0wdy!}

## Who am I?
What is the A record for `tamuctf.com`?  
(Not in standard `gigem{flag}` format)

**Solve**

    ping tamuctf.com

The flag is 52.33.57.247

## Who do i Trust?
Who issued the certificate to `tamuctf.com`?  
(Not in standard `gigem{flag}` format)

**Solve**
We just have to see the certificate on the browser

The flag is Let's Encrypt Authority X3

## Where am I?
What is the name of the city where the server for tamuctf.com is located?

(Not in standard gigem{flag} format)

**Solve**
With any random geo location tool or website we can find the flag.

The flag is Boardman

## I heard you like files.
Bender B. Rodriguez was caught with a flash drive with only a single file on it. We think it may contain valuable information. His area of research is PDF files, so it's strange that this file is a PNG.

**Solve**

    $ binwalk -e art.png
    $ DECIMAL       HEXADECIMAL     DESCRIPTION
    --------------------------------------------------------------------------------
    0             0x0             PNG image, 1920 x 1080, 8-bit/color RGBA, non-interlaced
    3408641       0x340301        PDF document, version: "1.5"
    3408712       0x340348        Zlib compressed data, default compression
    3412206       0x3410EE        Zlib compressed data, default compression
    3418964       0x342B54        Unix path: /Type/FontDescriptor/FontName/BAAAAA+NotoSans-Regular
    3419203       0x342C43        Zlib compressed data, default compression
    3419623       0x342DE7        Unix path: /Type/Font/Subtype/TrueType/BaseFont/BAAAAA+NotoSans-Regular
    3419994       0x342F5A        Zlib compressed data, default compression
    3428648       0x345128        Unix path: /Type/FontDescriptor/FontName/CAAAAA+DejaVuSerif
    3428883       0x345213        Zlib compressed data, default compression
    3429245       0x34537D        Unix path: /Type/Font/Subtype/TrueType/BaseFont/CAAAAA+DejaVuSerif
    3429667       0x345523        Unix path: /S/Transparency/CS/DeviceRGB/I true>>/Contents 2 0 R>>
    3430685       0x34591D        Zip archive data, at least v2.0 to extract, compressed size: 217, uncompressed size: 573, name: _rels/.rels
    3430943       0x345A1F        Zip archive data, at least v2.0 to extract, compressed size: 288, uncompressed size: 511, name: docProps/app.xml
    3431277       0x345B6D        Zip archive data, at least v2.0 to extract, compressed size: 356, uncompressed size: 731, name: docProps/core.xml
    3431680       0x345D00        Zip archive data, at least v2.0 to extract, compressed size: 222, uncompressed size: 663, name: word/_rels/document.xml.rels
    3431960       0x345E18        Zip archive data, at least v2.0 to extract, compressed size: 165, uncompressed size: 208, name: word/settings.xml
    3432172       0x345EEC        Zip archive data, at least v2.0 to extract, compressed size: 297, uncompressed size: 918, name: word/fontTable.xml
    3432517       0x346045        Zip archive data, at least v2.0 to extract, compressed size: 83172, uncompressed size: 84725, name: word/media/image1.png
    3515768       0x35A578        Zip archive data, at least v2.0 to extract, compressed size: 1138, uncompressed size: 4099, name: word/document.xml
    3516953       0x35AA19        Zip archive data, at least v2.0 to extract, compressed size: 605, uncompressed size: 2192, name: word/styles.xml
    3517603       0x35ACA3        Zip archive data, at least v2.0 to extract, compressed size: 352, uncompressed size: 1443, name: [Content_Types].xml
    3518004       0x35AE34        Zip archive data, at least v1.0 to extract, compressed size: 20, uncompressed size: 20, name: not_the_flag.txt
    3518847       0x35B17F        End of Zip archive

(I tried to grep for the flag before, but nothing brought the flag to us)

In word/media we have other png file, it's not necessary use binwalk, even if it's not a simple png again, just:

    cat image1.png

In the end of the file:

    ZmxhZ3tQMGxZdEByX0QwX3kwdV9HM3RfSXRfTjB3P30K

Clearly a base64:

The flag is flag{P0lYt@r_D0_y0u_G3t_It_N0w?}

## Hello World
My first program!

Difficulty: medium

**Solve**
We just have a simple C++ program, but with whitespaces before him, looks like a literally whitespace language:

I used this program to translate https://github.com/koturn/Whitespace

After translate in the file we can see the possible flag in table ASCII numbers:

    push(103);  
    push(105);  
    push(103);  
    push(101);  
    push(109);  
    push(123);  
    push(48);  
    push(104);  
    push(95);  
    push(109);  
    push(121);  
    push(95);  
    push(119);  
    push(104);  
    push(52);  
    push(116);  
    push(95);  
    push(115);  
    push(112);  
    push(52);  
    push(99);  
    push(49);  
    push(110);  
    push(103);  
    push(95);  
    push(121);  
    push(48);  
    push(117);  
    push(95);  
    push(104);  
    push(52);  
    push(118);  
    push(51);  
    push(125);  
    push(33);  
    push(101);  
    push(99);  
    push(97);  
    push(112);  
    push(115);  
    push(101);  
    push(116);  
    push(105);  
    push(104);  
    push(119);  
    push(32);  
    push(102);  
    push(111);  
    push(32);  
    push(116);  
    push(111);  
    push(108);  
    push(32);  
    push(97);  
    push(32);  
    push(115);  
    push(105);  
    push(32);  
    push(101);  
    push(114);  
    push(117);  
    push(115);  
    push(32);  
    push(116);  
    push(97);  
    push(104);  
    push(116);  
    push(32);  
    push(44);  
    push(101);  
    push(101);  
    push(103);  
    push(32);  
    push(121);  
    push(108);  
    push(108);  
    push(111);  
    push(103);  
    push(32);  
    push(116);  
    push(101);  
    push(101);  
    push(119);  
    push(115);  
    push(32);  
    push(108);  
    push(108);  
    push(101);  
    push(87);

Translating this:

gigem{0h_my_wh4t_sp4c1ng_y0u_h4v3}

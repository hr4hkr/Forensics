# Evil Crypter (InCTFi 2018)

This challenge basically dealt with dumping files from the given volatile memory and finding the flag. The flag had to found as two parts, one in a script and other from an image. Both files had to found and dumped from the memory dump given. Please read the writeup to this challenge.

After dumping we get 3 suspicios files, an image, a dcript and a text file.

The writeup to this challenge is  [here](https://volatilevirus.home.blog/2018/10/12/inctf-2018-evil-crypter-writeup/)

## Tools used 

### 1. Volatility
Volatility is an open-source memory analysis framework mainly used to analysing memory dumps of systems and malware analysis.
```bash
$ sudo apt install volatility
```
Plugins used to annalyse this memory dump.

| Plugins   | Purpose                            |
| -------   |----------------------------------- |
| pslist    |Print all running processes         |
| psscan    |Pool scanner for process            |
| imageinfo |Identify information for the image  |
| filescan  |Pool scanner for file objects       |
|           |                                    |

### 2. Steghide
It is a steganography program that hides data in various kinds of images and audios. It can be used to embed and extract data from a coverfile. Data is embeded using a password and can only be extracted using one as well.

```bash
$ sudo apt install steghide
```
The password is the first part of the flag that can be found from the script, which is *inctf{0n3_h4lf* 

## Scripts
In the challenge there is a script that is dumped from the memory dump and its output is also given (It can be seen  that the output is written into another file). Hence we have the encoding script and the output. Since the script is simple xoring and hex decoding it can be easily reversed to find the first part of the flag.

Script:
  ![alt](/Forensics/Memory/2018/InCTFi/img/script.png)

By putting the first part of the flag in steghide the final part is shown.Hence the flag is **inctf{0n3_h4lf_1s_n0t_3n0ugh}**

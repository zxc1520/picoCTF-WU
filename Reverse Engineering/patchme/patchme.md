# patchme
## Reverse Engineering

### Skor:
100 Points

### Author:
LT 'syreal' Jones

### Deskripsi:
Can you get the flag? Run this Python program in the same directory as this encrypted flag.

### Solusi
#### langkah-langkah
- Lihat kategori dari soal yang diberikan
- Pahami clue dari soal yang diberikan

Setelah mendownload kedua file tersebut, maka saya akan cek file type keseluruhan
```sh
┌──(afifgh21㉿AFIFGHULAM-PC)-[~/Documents/reverse/patchme]
└─$ file *
flag.txt.enc:    data
patchme.flag.py: ASCII text, with CRLF line terminators
```
diberikan 2 file dengan type data dan juga file python, kemudian saya cek dibagian source code-nya

```sh
### THIS FUNCTION WILL NOT HELP YOU FIND THE FLAG --LT ########################
def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])
###############################################################################
flag_enc = open('flag.txt.enc', 'rb').read()

def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "ak98"
        "ak98" + \
        "-=90" + \
        "adfhgj321" + \
        "sleuth9000"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), "utilitarian")
        print(decryption)
        return
    print("That password is incorrect")
```
kode tersebut berisikan algoritma untuk melakukan pengecekan password, bisa dilihat dalam fungsi `level_1_pw_check` maka saya akan melakukan cek memasukkan password, namun hasilnya nihil

```sh
┌──(afifgh21㉿AFIFGHULAM-PC)-[~/Documents/reverse/patchme]
└─$ python3 patchme.flag.py
Please enter correct password for flag: ak98
That password is incorrect
```
lalu saya coba kombinasikan string yang berada di parameter pengecekan password

```sh
┌──(afifgh21㉿AFIFGHULAM-PC)-[~/Documents/reverse/patchme]
└─$ python3 patchme.flag.py
Please enter correct password for flag: ak98-=90adfhgj321sleuth9000
That password is incorrect
```
password salah! ada jalan lain yang bisa ditempuh yakni dengan memodifikasi parameter pengecekan password tersebut
```py
def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "ak98"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), "utilitarian")
        print(decryption)
        return
    print("That password is incorrect")
```
saya memodifikasi agar variabel `user_pw` menerima inputan `"ak98"` maka akan diloloskan pengecekannya. Setelah itu jalankan kembali file tersebut dan masukkan string `"ak98"` maka terdapat string yang muncul seusai password yang dimasukkan benar, yaitu flag!!!

```sh
┌──(afifgh21㉿AFIFGHULAM-PC)-[~/Documents/reverse/patchme]
└─$ python3 patchme.flag.py
Please enter correct password for flag: ak98
Welcome back... your flag, user:
picoCTF{p47ch1ng_l1f3_h4ck_f01eabfa}
```
## Flag
```sh
picoCTF{p47ch1ng_l1f3_h4ck_f01eabfa}
```
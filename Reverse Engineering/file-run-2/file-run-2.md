# file-run-2
## Reverse Engineering

### Skor:
100 Points

### Author:
Will Hong

### Deskripsi:
Another program, but this time, it seems to want some input. What happens if you try to run it on the command line with input "Hello!"? Download the program here.

### Solusi
#### langkah-langkah
- Lihat kategori dari soal yang diberikan
- Pahami clue dari soal yang diberikan

Didapatkan file serupa dengan file-run-1, setelah dicek benar, file tersebut adalah file executable.
```sh
┌──(afifgh21㉿AFIFGHULAM-PC)-[~/Documents/reverse]
└─$ file run.1
run.1: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=689b8959bc0a65415698970bbb93ed2788442ffb, for GNU/Linux 3.2.0, not stripped
```

ganti file permission terlebih dahulu agar dapat menjalankan file tersebut dengan baik
```sh
┌──(afifgh21㉿AFIFGHULAM-PC)-[~/Documents/reverse]
└─$ sudo chmod +x run.1
```
jalankan file tersebut sesuai dengan deskripsi diatas dengan parameter hello
```sh
┌──(afifgh21㉿AFIFGHULAM-PC)-[~/Documents/reverse]
└─$ ./run.1 hello
Won't you say 'Hello!' to me first?
```
tidak ada tanda tanda flag yang muncul, kemudian ketikkan Hello! sesuai perintah diatas
```sh
┌──(afifgh21㉿AFIFGHULAM-PC)-[~/Documents/reverse]
└─$ ./run.1 Hello!
The flag is: picoCTF{F1r57_4rgum3n7_96f2195f}
```
eureka ! flag telah ditemukan 
## Flag
```sh
picoCTF{F1r57_4rgum3n7_96f2195f}
```
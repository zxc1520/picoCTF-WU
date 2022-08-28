# file-run-1
## Reverse Engineering

### Skor:
100 Points

### Author:
Will Hong

### Deskripsi:
A program has been provided to you, what happens if you try to run it on the command line? Download the program here.

### Solusi
#### langkah-langkah
- Lihat kategori dari soal yang diberikan
- Pahami clue dari soal yang diberikan

Diberikan sebuah file bertipe executable ELF
```sh
┌──(afifgh21㉿AFIFGHULAM-PC)-[~/Documents/reverse]
└─$ file run
run: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=9fa9c4d805e9a77142375b406526cb97b1aae60b, for GNU/Linux 3.2.0, not stripped
```

untuk menjalankannya maka diharuskan untuk merubah file permission tersebut agar bisa dijalankan di lokal komputer

```sh
┌──(afifgh21㉿AFIFGHULAM-PC)-[~/Documents/reverse]
└─$ sudo chmod +x run
```
setelah itu jalankan file dan terdapat flag yang didapatkan secara gratis ketika menjalankan sebuah file tersebut.
```sh
┌──(afifgh21㉿AFIFGHULAM-PC)-[~/Documents/reverse]
└─$ ./run
The flag is: picoCTF{U51N6_Y0Ur_F1r57_F113_e5559d46}
```
## Flag
```sh
picoCTF{U51N6_Y0Ur_F1r57_F113_e5559d46}
```
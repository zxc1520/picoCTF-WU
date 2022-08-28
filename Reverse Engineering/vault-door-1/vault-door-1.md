# vault-door-1
## Reverse Engineering

### Skor:
100 Points

### Author:
Mark E. Haase

### Deskripsi:
This vault uses some complicated arrays! I hope you can make sense of it, special agent. The source code for this vault is here: VaultDoor1.java

### Solusi
#### langkah-langkah
- Lihat kategori dari soal yang diberikan
- Pahami clue dari soal yang diberikan

setelah mendownload file tersebut, ternyata file tersebut berisikan kode java yang terdapat sebuah clue yang mengarah ke charAT.
```java
public boolean checkPassword(String password) {
        return password.length() == 32 &&
               password.charAt(0)  == 'd' &&
               password.charAt(29) == '3' &&
               password.charAt(4)  == 'r' &&
               password.charAt(2)  == '5' &&
               password.charAt(23) == 'r' &&
               password.charAt(3)  == 'c' &&
               password.charAt(17) == '4' &&
               password.charAt(1)  == '3' &&
               password.charAt(7)  == 'b' &&
               password.charAt(10) == '_' &&
               password.charAt(5)  == '4' &&
               password.charAt(9)  == '3' &&
               password.charAt(11) == 't' &&
               password.charAt(15) == 'c' &&
               password.charAt(8)  == 'l' &&
               password.charAt(12) == 'H' &&
               password.charAt(20) == 'c' &&
               password.charAt(14) == '_' &&
               password.charAt(6)  == 'm' &&
               password.charAt(24) == '5' &&
               password.charAt(18) == 'r' &&
               password.charAt(13) == '3' &&
               password.charAt(19) == '4' &&
               password.charAt(21) == 'T' &&
               password.charAt(16) == 'H' &&
               password.charAt(27) == 'f' &&
               password.charAt(30) == 'b' &&
               password.charAt(25) == '_' &&
               password.charAt(22) == '3' &&
               password.charAt(28) == '6' &&
               password.charAt(26) == 'f' &&
               password.charAt(31) == '0';
    }
```

saya curiga dengan pengecekan kode tersebut mengandung karakter unik melambangkan sebuah flag, dan ternyata benar, di dalam fungsi tersebut terdapat sebuah string yang diacak. Saya menggunakan kode python untuk menyelesaikannya.

```py
arr = [
    "d",
    "3",
    "5",
    "c",
    "r",
    "4",
    "m",
    "b",
    "l",
    "3",
    "_",
    "t",
    "H",
    "3",
    "_",
    "c",
    "H",
    "4",
    "r",
    "4",
    "c",
    "T",
    "3",
    "r",
    "5",
    "_",
    "f",
    "f",
    "6",
    "3",
    "b",
    "0",
]

ans="".join([str(i) for i in arr])
print(ans)
```

didapatlah sebuah string `d35cr4mbl3_tH3_cH4r4cT3r5_ff63b0` maka saya akan mencocokannya dengan menjalankan kode java tersebut
```sh
┌──(afifgh21㉿AFIFGHULAM-PC)-[~/Documents/reverse]
└─$ java VaultDoor1
Enter vault password: picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_ff63b0}
Access granted.
```
dan ternyata benar.

## Flag
```sh
picoCTF{d35cr4mbl3_tH3_cH4r4cT3r5_ff63b0}
```
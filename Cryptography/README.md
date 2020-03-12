# Cryptography challenges

## Character Encoding

This challenge tells us that the following code `41 42 43 54 46 7B 34 35 43 31 31 5F 31 35 5F 55 35 33 46 55 4C 7D` is ASCII encoded (American Standard Code Information Interchange), so all you would have to do is go find an ASCII table, and decode the string. You can do this manually, or write a simple bash script.

```shell
#!/bin/bash
string="41 42 43 54 46 7B 34 35 43 31 31 5F 31 35 5F 55 35 33 46 55 4C 7D"
string=' ' read -ra num <<< "$string"

for i in "${num[@]}"
do
   echo 0x$i | xxd -r
done
```

<img src="images/CharacterEncoding-1.png">

The flag for this level is `ABCTF{45C11_15_U53FUL}`

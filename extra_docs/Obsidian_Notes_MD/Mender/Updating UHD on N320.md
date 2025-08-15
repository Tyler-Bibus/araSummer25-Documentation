*note: turn off radio using `shutdown -h now`*

For MENDER we can use the guide here:
https://kb.ettus.com/USRP_N300/N310/N320/N321_Getting_Started_Guide

~~This is naively supported, meaning we wont have to do anything very crazy to get the artifacts and then load it onto the server to upload :D.~~

We can easily use mender for the FileSystem, but the FPGA images we need to use uhd_image_loader. I believe we can still use mender, to first update the filesystem and then use a script to load the fpga image

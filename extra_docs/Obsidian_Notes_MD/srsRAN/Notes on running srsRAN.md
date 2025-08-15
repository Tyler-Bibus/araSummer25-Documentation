Without Docker: 
- Download and install UHD drivers
- **if necessary set up a core network (open5GS)
- Download srsRAN release 23_10
- Apply POWDER patch to code and build
- modify pins as needed, for our case ATR_XX is the attribute, set the pins you want to use
- Should be good!

With Docker:
***NOTE: DOCKER OS VERSION MUST NOT BE GREATER THAN HOST VERSION!***
- Download docker image
- Modify pins as needed and rebuild as needed. *note: if you are on a different CPU architecture you will need to delete /build/* 
- Should be good!
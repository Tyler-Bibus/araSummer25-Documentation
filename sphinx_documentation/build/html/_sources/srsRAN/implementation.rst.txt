.. _srsran_implementation:

################
Implementation
################

To replicate this work, a new user can follow these steps.

**Without Docker:**
1.  Download and install the necessary UHD drivers for your USRP device.
2.  If required, set up a 5G core network. open5GS is a viable option.
3.  Download srsRAN release 23_10.
4.  Apply the POWDER patch to the source code and build the project.
5.  Modify the pin configuration as needed. In our case, the ``ATR_XX`` attribute was used to set the desired pins.

**With Docker:**
*Note: The Docker OS version must not be greater than the host OS version.*
1.  Download the appropriate Docker image.
2.  Modify the pin configurations and rebuild the image if necessary. If you are using a different CPU architecture, you will need to delete the ``/build/`` directory before rebuilding.

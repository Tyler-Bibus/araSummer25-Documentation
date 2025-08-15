.. _srsran_method:

###########
The Method
###########

The solution involved modifying the srsRAN source code to control the GPIO pins in synchronization with the 5G Time Division Duplexing (TDD) frame structure. The key steps were:

1. **GPIO Control:** The first step was to figure out how to programmatically control the GPIO pins on the USRP hardware.
2. **Timing Synchronization:** Once basic control was established, the GPIO pin toggling had to be aligned with the 5G TDD frame to ensure the amplifier was active only during downlink (DL) transmissions. This was initially attempted by adding a function call in ``lib/radio/uhd/radio_uhd_tx_stream.cpp``, but the timing was incorrect. A correct implementation was achieved by adapting a patch from the POWDER testbed for srsRAN release 23_10.
3. **Troubleshooting:** A significant issue arose where the gNodeB would get stuck in an ``UNDERFLOW_RECOVERY`` state, causing transmissions to fail. This was resolved by commenting out the code related to this state in the POWDER patch. Another issue that caused radio errors was resolved by reducing the tx_gain from 50 to 45 in the configuration.

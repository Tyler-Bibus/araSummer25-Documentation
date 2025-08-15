.. _srsran_results:

#########
Results
#########

The project was successful in achieving its main goal. The modified srsRAN now works with amplifiers, enabling outdoor deployments.

- **GPIO Control:** Successfully figured out how to control GPIO pins on the UHD.
- **Timing:** Aligned GPIO pin timing with the 5G TDD frame.
- **Testing:**
    - Tested connectivity with and without an amplifier.
    - Verified functionality with a USRP N320 and amplifier.
    - Successfully connected with both 500 and 510 Quectel COTS UEs.
    - Successfully tested outdoors with a stable connection.

The final deployment onto the ARA Network is still in progress and involves containerizing the experiments.

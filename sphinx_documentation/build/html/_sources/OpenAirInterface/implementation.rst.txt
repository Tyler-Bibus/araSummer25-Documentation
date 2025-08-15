.. _oai_implementation:

################
Implementation
################

The primary implementation detail of this project was adding configurable values for Msg2 and Msg3 scheduling.

The values `msg2_slot` and `k2_msg3` were added to the `nr_mac_config_t` structure. This allows them to be set in the configuration file and accessed within the OAI source code.

**File Modifications:**

1. **`/openair2/GNB_APP/gnb_paramdef.h`:** The new configuration parameters were added to this file.

2. **`/openair2/GNB_APP/gnb_config.c`:** Code was added to this file to read the new parameters from the configuration file.

The values can now be accessed in the code using:
`RC.nrmac[module_id]->radio_config.k2_msg3`
`RC.nrmac[module_id]->radio_config.msg2_slot`

Two approaches were considered for the configuration:
1.  Defining `msg2_slot` and `k2_msg3`.
2.  Defining `msg2_slot` and `msg3_slot`.

The second approach was deemed more intuitive for the end user. If the values are left undefined in the configuration, OAI falls back to its default calculation method.

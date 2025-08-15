.. _oai_method:

###########
The Method
###########

The project involved several stages of development and debugging.

1.  **Patch Update:** The old patch was forward-ported to the latest develop branch. This involved applying the GPIO and UE patches, as well as a modified version of the gNB patch.
2.  **Debugging:**
    - A segmentation fault was occurring immediately after the Msg4 Acknowledgement. Using gdb, this was traced to a null pointer exception caused by improper memory allocation for a struct. The issue was resolved by using the correct function to allocate the struct.
    - A Hybrid Automatic Repeat Request (HARQ) issue was severely limiting throughput to about 2 Mbps. This was fixed by re-adding a TDA index that had been accidentally removed.
3.  **Configuration Values:** To remove hardcoded values, a method was developed to add them to a configuration file. This involved modifying the `nr_mac_config_t` structure. Initially, there were difficulties in modifying the necessary structs, but a working solution was eventually found.

.. _srsran_problem:

################
The Problem
################

The stock version of srsRAN does not have the native capability to control General Purpose Input/Output (GPIO) pins on USRP SDRs. This is a significant limitation for outdoor deployments, as it prevents the use of external amplifiers which are necessary to boost the signal for long-range communication. These amplifiers require precise timing signals, typically delivered via GPIO, to switch between transmitting and receiving modes.

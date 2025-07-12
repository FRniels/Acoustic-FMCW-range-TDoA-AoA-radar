# Dual power supply

The Tx and Rx amplifying circuits require dual power supplies to power their internal op-amps.
To be cost efficient, one MAX 1771 CPA DC/DC converter is used instead of two.
The lowest rail voltage of -5V will be generated for the Tx circuit and the -3.3V needed for the Rx circuits will created using an LDO.

## Total current

The MAX 1771 CPA is should be able to provide the necesarry current for 4x Rx and 2x Tx circuits.

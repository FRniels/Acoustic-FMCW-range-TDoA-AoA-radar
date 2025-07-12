# Analog mixing

## Due to high cost of analog mixers, here is a possible setup using 1x AD633 multiplier to try in the future:

Use an Analog Switch + 1 AD633

Use 1x AD633 analog multiplier and connect it to 4 Rx channels one-by-one using a 74HC4052 dual 4-to-1 analog switch.
Multiply each Rx with Tx in a loop and multiplex the analog mixer with the used microcontroller.

Cost:
1x AD633 (€16)		 => 4x analog mixers would be: 64€ !!!
1x 74HC4052 (€0.50)

## Conclusion:
Digital mixing and low pass filtering will be first used to verify if the Tx and Rx circuits work in the first place.
If the whole setup works, the pros vs cons of analog vs digital mixing and low pass filtering should be reconsidered
to see if analog is actually better, and if so, is it enough to justify the high cost.
In the case of going for analog, is the 1x AD633 + 74HC4052 worth the cost, or should one immediately go for 4x 74HC4052.
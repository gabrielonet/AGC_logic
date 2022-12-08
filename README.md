# AGC_logic
For a nice audio output , a receiver need an AGC automatic gain controll system.
In my radio I use a AD8307 log detector connected to audio signal after DSP..
This Log detector produce a DC output in range of 0.4 - 2.4 V in range of 90 dB range.
AD8703 output is tied to A3 analog pin as input and MCP4725 output is tied to AD603 I.F. chain as inverse relation. (the more input, less output should produce)
If signal is bigger than previous one then instantly produce AGC kick in (knee time), and set a variable as current millis() .
If signal is less than previous and time delta is greater that preset time( I will use another digital pin to select fast or slow),
then AGC is decaying to current signal level after time constant value.

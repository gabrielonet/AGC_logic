# AGC_logic
For a nice audio output , a receiver need an AGC automatic gain controll system.
In my radio I use a AD8310 fast log detector connected to the output of last IF amp.
This Log detector produce a DC output in range of 0.4 - 2.4 V in range of 90 dB range.
This DC is delivered to a voltage inverter built on a 2n2222 transistor , 2 trim pots and a 10 K rezistor. in order to generate a reverse
voltage in 8 -2 V , voltage applied to IF AD602 gain controll.
So far so good, but this would be too fast without some time delay.I tried to insert a capacitance on this AGC line and the decay time was
satisfactory but it introduced a delay in attack time too ,so on high level bursts, the audio becomes a bit anoyng due to clipping (Loud output
at the burst begining until AGC kicked in)
So I decided to remove capacitors and use an arduino nano as time const logic.
Basicaly , I used an analog pin as input and another analog pin as output , so if signal is bigger than previous one then instantly
produce AGC decay, and set a variable as current millis() .
If signal is less than previous and time delta is greater that decay preset time( I use another digital pin to select fast or slow),
then AGC is decaying to current signal level



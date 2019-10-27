# Introduction

Shoyu/Shouyu (he has spelled his name in roughly equal proportion) Li has contacted me by email, recently, to attempt to use my work implementing the simplified real frequency technique (SRFT algorithm) to solve his network matching problem.

# Problem Description

Below is a word-for-word paste of the problem description as emailed to me (John Rinehart) at ~13:17 UTC on October 25, 2019. This will be used as the starting point for the work in this repository.

> I've thought that in order to let you easier to understand my problem, I should demonstrate my problem in a more direct way. So below are what have been troubling me.

> The aim is to design a broad band matching network for the following circuit which is the equivalent circuit of a broad band hydroacoustic transducer. Now I know the conductance and susceptance data of the transducer. Regretfully, even though I know the method to derive the parameters of the circuit from the conductance and susceptance data of the transducer, yet I don't have enough time. But this doesn't trouble much because it is only matter of time to acquire the exact parameters of the circuit. What's more, the interested frequency band is from 7khz to 16khz. The transducer has two resonant frequencies at about 10000hz and 14300hz. And the rest parameter that I know is the resistance of the transducer at 14300hz,and its value is 150 ohms. And inspired by other papers, I'd like to make the matching network provide a resistance of 150 ohms at 14300hz. However, the amplifier which is for the use of amplifying the input signal in order to drive the transducer is an integrated power amplifier which has an output impedance of about 4-8 ohms. So according to the theory of power transmitting, I need to do an impedance convertion to fully utilize the power and better drive the transducer. And I want to use a transfromer between the amplifier and the matching network and make the output impedance be 300 ohms at the secondary coil end.

> So my problem arises. In your paper, 6 breakpoints were rasied to optimize the transmitting power gain(TPG). And the normalized frequencies of them are 0, 0.25, 0.5, 0.75, 1.0 and 1.25. And the source is expressed by R0 with a value of 2.2 ohms. But the paper only provides me with the normalized frequencies, so I want to know the exact frequencies. As I learned from other papers, the initial values of the matching network's resistance at the breakpoints are usually choosed by calculating the resistance values of the load at the same frequencuies respectively. However, I have calculated the resistance of the load using the formula: zload = ((1+1 i∗w∗1.2).ˆ−1+1i∗w∗2.3) , but I can't acquire the value 1.9 (2.2-0.3), 1.5 (2.2-0.3-0.4), 1.2 (similarly acquired) , 0.6 and 0 ohms (the Dinit=[-.3; -.4; -.3; -.6; -.6] in program Example9_2_1). So I wonder what criteria have you used to acquire the initial resistance values at the break points.

> Another problem has already given to you. That is, why do you use '[Ds, TG] = fmincon( objective , Dinit , sum constraint ,R0−. 3 , [ ] , [ ] , [ ] , [ ] , @CheckDecreasing) ; ' in the line 27 in the program Example9_2_1? I want to just do a little change of your program to solve my problem. And what should I do to suit my system?

> The last problem is how to solve the establishment of my matching network system.

This emailed included two attachments, one inline and one external: [image.png](./schematics/image.png) and [02.PNG](./schematics/02.PNG). These are included in the `schematics/` folder at the root of this repository.

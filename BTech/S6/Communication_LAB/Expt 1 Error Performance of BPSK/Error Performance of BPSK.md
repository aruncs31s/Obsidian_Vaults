# Error Performance of BPSK

## Contents
- [CodeFile Github](https://github.com/aruncs31s/BtechEC/blob/S6/Communication%20Lab/Expt_1_Generation_and_Detection_of_BPSK/generation_and_Detection_of_BPSK.m)
- 

*BPSK stands for Binary Phase Shift Keying. It's a type of digital modulation technique in which a carrier signal is modulated to convey information. The carrier signal's phase is changed between two discrete states to represent the binary data being transmitted. This technique is used in various communication systems, such as wireless and satellite communication*

---


Aim: 
1. Generate a string of message bits.
2. Encode using `BPSK` with energy per bit `Eb` and represent it using points in a signal-space.
3. Simulate transmission of the `BPSK` modulated signal via an [[AWGN]] channel with variance `N0/2`.
4. Detect using an ML decoder and plot the probability of error as a function of [[BTech/S6/Communication_LAB/Expt 1 Error Performance of BPSK/SNR]] per bit `Eb/N0`.
---

#### Theory 
In a coherent binary PSK system, the pair of signals S1(t) and S2 (t) used to represent binary symbols
1 & 0 are defined by
$$ S1 (t) = √2Eb/τb Cos 2πfct $$
$$S2 (t) =√2Eb/Tb (2πfct+π)$$
$$ = - √ 2Eb/Tb Cos 2πfct$$
*where 0 ≤ t< Tb and*
*Eb = Transmitted signed energy for bit*
*In BPSK, there is only one basis function of unit energy.*
$$Øb (t) = √2/Tb cos 2fπct\ \ \ \ \ for\ \ \  0 \ ≤  \ t \ < Tb$$
$$S1 (t) = √Eb Ø1 (t) 0≤ t ≤Tb$$
$$S2 (t) = √Eb Ø1 (t) 0≤ t< Tb$$
*The signal space is 1dimensional (N=1) having two message points (M = 2)*

---

- Modulation : bpskMod()
- Demodulation : bpskDemod()
#wholeCode
```python
clear;
clc;
 
N=10000000;
EbN0dB = -6:2:10;
%---------------------------------------------
data=randn(1,N)>=0; bpskModulated = 2*data-1;
M=2;
Rm=log2(M);
Rc=1;
BER = zeros(1,length(EbN0dB));
index=1;
for k=EbN0dB,
EbN0 = 10.^(k/10);
noiseSigma = sqrt(1./(2*Rm*Rc*EbN0)); noise = noiseSigma*randn(1,length(bpskModulated));
received = bpskModulated + noise;
 
estimatedBits=(received>=0);
 
BER(index) = sum(xor(data,estimatedBits))/length(data);
index=index+1;
end
 
plotHandle=plot(EbN0dB,log10(BER),'r--');
set(plotHandle,'LineWidth',1.5);
title('SNR per bit (Eb/N0) Vs BER Curve for BPSK Modulation Scheme');
xlabel('SNR per bit (Eb/N0) in dB');
ylabel('Bit Error Rate (BER) in dB');
grid on;
hold on;
theoreticalBER = 0.5*erfc(sqrt(10.^(EbN0dB/10)));
plotHandle=plot(EbN0dB,log10(theoreticalBER),'k*');
set(plotHandle,'LineWidth',1.5);
legend('Simulated','Theoretical');
grid on;

```

#output

![output](https://github.com/aruncs31s/BtechEC/blob/S6/Communication%20Lab/Expt_1_Error_Performance_of_BPSK/expt1_graph.png?raw=true)


#steps
- Req { msg_signal};

1. Generate Random Number
*Note* : Transmission  in done in bipolar => convert to bipolar
*Messge Snl* = [0,1]

```Matlab

data = randn(1,N)>=0 ;

```
<details><summary>Explanation</summary>
`data = randn(1,N)>=0` Sets the data variable if the generated randn()'s output > mdcmd
 0 and resets(value will be equal to 0) if its output < 0
</summary>

2. Make data => 1,-1

```Matlab
bpskModulated = 2*data-1;
```

2. Define channel add noise to it
*Req* : Length of message signale and noise should be equal


```matlab

noiseSigma = sqrt(1./(2*Rm*Rc*EbN0))
noise = noiseSigma * randn(2,length(bpskModulated)) % length... = 10



```


 
3. Identify The messege
*Note* :  Threshold Detection is used to identify the recieved signal

```matlab
recieved  = bpskModulated + noise
```

- Threshold detector
```matlab
estimatedBits = (received>=0)
```


- Detect No of Error Bits
XOR Tx and Rx , take sum = Bit error




### Aim
1. Plot [[BTech/S6/Communication_LAB/Expt 1 Error Performance of BPSK/SNR]] vs [[Bit error rate]]
SNR 1/o< Bit Error rate (o< = propotional)
- Specs

- Steps
1.

DB <= Linear Scale ; 10 .^(k/20)



Notes -

#?define
```matlab
 BER = zeros(1,length(EbN0dB))
```
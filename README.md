# DSB--SC-MODULATION-AND-DEMODULATION-USING-PYTHON

__AIM__:

To generate a Double Sideband Suppressed Carrier (DSB-SC) signal in Python (Google Colab), transmit it (optionally add noise), and recover the message using coherent (synchronous) demodulation with a low-pass filter. Observe time and frequency domain waveforms and measure demodulation performance

__APPARATUS REQUIRED__:

Google Colab (or any Python environment)

Python libraries: numpy, matplotlib, scipy (scipy.signal)

__Theory__:

DSB-SC signal: s(t) = m(t) · cos(2πf_c t)
Coherent demodulation: multiply received s(t) by a synchronized carrier cos(2πf_c t) then low-pass filter (LPF) to remove double-frequency components:

r(t) = s(t)·cos(2πf_c t) = m(t)·cos²(2πf_c t) = 0.5 m(t) + 0.5 m(t)·cos(4πf_c t)
LPF extracts 0.5·m(t) → scale by 2 to recover m(t).

__Procedure__:

1) Import libraries and set parameters
2) Define message and carrier signals
3) Generate DSB-SC signal (modulation)
4) View spectra (FFT) of message and DSB-SC
5) (Optional) Add noise
6) Coherent demodulation (multiply by synchronized carrier)
7) Low-pass filter to recover message

__Program__:

```
import numpy as np
import matplotlib.pyplot as plt

Am=13.5
fm=720
fc=7200
fs=477000
t=np.arange(0,2/fm,1/fs)
m=Am*np.sin(2*np.pi*fm*t)
plt.subplot(3,1,1)
plt.plot(t,m)
plt.grid()
Ac=27
c=Ac*np.sin(2*np.pi*fc*t)
plt.subplot(3,1,2)
plt.plot(t,c)
plt.grid()
s1=(Ac+m)*np.sin(2*np.pi*fc*t)
s2=(Ac-m)*np.sin(2*np.pi*fc*t)
s=s1-s2
plt.subplot(3,1,3)
plt.plot(t,s)
plt.grid()
```
__Tabulation__:

   <img width="773" height="629" alt="image" src="https://github.com/user-attachments/assets/1067f0d1-7de7-4d30-81c7-b66572f5ab99" />

__Output__:

<img width="1042" height="783" alt="image" src="https://github.com/user-attachments/assets/bec783a3-739e-4548-a42c-ed4e6ee1fcc7" />

__Result__:

Thus the Double SideBand supress carrier(DSBSC)  using Python is Obtained and verified.

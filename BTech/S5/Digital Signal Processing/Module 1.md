# Module 1

## Contents
- [Syllabus](#syllabus)
- 
## Syllabus

- Basic Elements of a DSP system
- Typical DSP applications
- Finite-length discrete transforms
- Orthogonal transforms 
- The Discrete Fourier Transform: DFT as a linear transformation (Matrix relations).
- Relationship of the DFT to other transforms
- IDFT, Properties of DFT and examples.
- Circular convolution
- Linear Filtering methods based on the DFT
- linear convolution using circular convolution
- Filtering of long data sequences,
- overlap save and overlap add methods
- Frequency Analysis of Signals using the DFT (concept only required)

### Fourier Series
The Fourier series is a mathematical tool used to ==represent a periodic function as the sum of simple sine and cosine functions==. It is named after Jean-Baptiste Joseph Fourier, who introduced the concept in the early 19th century. The Fourier series is particularly useful for ==analyzing signals that are periodic in nature==.
`FS` is represented by $f(t)$ with time period $T$ and it is equal to 
$$
f(t) = \frac{a_0}{2} + \sum_{n=1}^{\infty} [a_n \cos(n\omega_0 t) + b_n \sin(n\omega_0 t)]
$$
or
$$
x(t) = \sum_{k=-\infty}^\infty X[k]e^{jk\omega_0t}
$$
and 
$$
X[k] = {1 \over T} \int_{(t)} x(t)e^{-j\omega_0t} dt
$$
$x(t)$ has period T and $\omega_0 = {2 \pi \over T}$ 

> [!IMPORTANT] Applicability
> `Fourier Series` is only used for periodic signals 



### Fourier Transform
The Fourier Transform is a mathematical technique used in signal processing and image analysis, among other fields, ==to transform a function of time (a signl) into a function of frequency==

$$
F(\omega) = \int_{-\infty}^{\infty} f(t) e^{-j\omega t} dt\
$$
where 
- $F(\omega)$ Fourier transform coefficient of $f(t)$
- $\omega$ is the Frequency

> [!NOTE] FT
> The Fourier Transform decomposes a signal into its constituent
 frequencies,  allowing for the analysis of the signal's frequency
 components 
#### Inverse Fourier Transform

$$
f(t) = \frac{1}{2\pi} \int_{-\infty}^{\infty} F(\omega) e^{j\omega t} d
\omega\
$$

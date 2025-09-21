$$\textbf{Introduction}$$

The Bernoulli numbers, traditionally denoted as $B_n$, are a sequence of numbers that pop up frequently in analytic number theory, most notably in their relation to the Riemann zeta function, $B_n=-n\zeta(1-n)$.
Seeing as zeroes of the Bernoulli numbers would thus correspond with zeroes of the Riemann zeta function, it would be useful to find an expression for $B_n$ for non-integer values of $n$, for the purpose of studying the Riemann Hypothesis.
We take note of the generating function for the Bernoulli numbers

$$\frac{z}{e^z-1}=\sum \limits_{j=0}^\infty {\frac{B_j z^j}{j!}}  [\mathrm{I}]$$

Which implies that the nth Bernoulli number is the nth derivative of the generating function evaluated at a point tending towards 0 (because the function is undefined at x=0), i.e.,

$$B_n=lim_{a \to 0} \left. {\frac{d^n}{dz^n} \frac{z}{e^z-1}} \right|_{z=a}  [\mathrm{II}]$$

Evidently, we will need to generalize the derivative operator to non-integer values - that is, discover fractional calculus. There are a variety of ways we can proceed from here.

$$\textbf{Approach 1: Taylor Series}$$

We can use a Taylor series with center $k \neq 0$ to represent the Bernoulli numbers' generating function $\frac{z}{e^z-1}$ like so

$$\frac{z}{e^z-1} = \sum\limits_{j=0}^\infty {f^{(j)}(k) \frac{(z-k)^j}{j!}}  [\mathrm{I}]$$

Where $f^{(j)}(k)$ denotes the jth derivative of $\frac{z}{e^z-1}$ evaluated at $k$.

Converting the generating function into a power series is very convenient, as the power rule tells us

$$\frac{d^n x^j}{dx^n} = \frac{j ! x^{j-n}}{(j-n)!}  [\mathrm{II}]$$

Which can be extended to non-integer order derivatives by replacing the factorial with its analytic continuation, the gamma function $\Gamma(z)=\int_0^\infty e^{-t} t^{z-1} dt=(z-1)!$

$$\frac{d^n x^j}{dx^n} = \frac{\Gamma (j + 1) x^{j-n}}{\Gamma (j-n+1)}  [\mathrm{III}]$$

Applying this extended power rule to the formula from [I], and remembering the formula for the Bernoulli numbers given in [Introduction, II] we realize that

$$B_n=lim_{z \to 0} \left. \sum\limits_{j=0}^\infty {f^{(j)}(k) \frac{\Gamma (j+1)(z-k)^{j-n}}{j! \Gamma(j-n+1)}} \right  [\mathrm{IV}]$$

This is the value computed by BernoulliContinued.nb, albeit to a finite precision.

![4d9e2cb2-b581-4343-82a9-9b1e98e3220c 1280x1280](https://github.com/user-attachments/assets/7f340134-dd31-4fba-89c1-24e6df14e2df)

$$\textbf{Approach 2: Fourier Series}$$

Though the Taylor series approach has proven to be computationally viable, I am a bit skeptical of its integrity due to possible variance under choice of center $k$, and the poles of the gamma function. It would be convenient to formulate the generating function of the Bernoulli numbers in terms of not only polynomials, but in terms of exponentials, as the extended power rule for exponential functions does not require the use of a non-holomorphic function such as the gamma function:

$$\frac{d^n e^{\alpha x}}{dx^n} = \alpha^n e^{\alpha x}  [\mathrm{I}]$$

And luckily there is a series expansion - the Fourier series expansion - which can locally represent certain functions as an infinite sum of complex exponentials

$$f(z)=\frac{1}{2T}\sum \limits_{j=-\infty}^\infty {e^{ijz} \int_{-T}^{T} {f(t)e^{-ijt}dt}}, z \in (-T, T)  [\mathrm{II}]$$

Where $T$ is a real number greater than zero. Remember from [Introduction, II] that we are only interested in points arbitrarily close to $z=0$, so there is no problem with demanding $z$ to be within $(-T, T)$.

Plugging in the generating function to [II] gives us

$$\frac{z}{e^z-1}=\frac{1}{2T}\sum \limits_{j=-\infty}^\infty {e^{ijz} \int_{-T}^{T} {\frac{te^{-ijt}}{e^t-1}dt}}, z \in (-T, T)  [\mathrm{III}]$$

Since everything is constant with respect to $z$ except the exponential term, we can easily use [I] to take the fractional derivative, and yield the Bernoulli numbers by [Introduction, II]

$$B_n=lim_{z \to 0} \left. {\frac{1}{2T}\sum \limits_{j=-\infty}^\infty {(ij)^n e^{ijz} \int_{-T}^{T} {\frac{te^{-ijt}}{e^t-1}dt}}} \right  [\mathrm{IV}]$$

We can allow the integral interval to exclude $t=0$, since the measure of a countable - let alone finite - set is zero.

This was the method used by another Mathematica program of mine, titled BernoulliFourier.nb, but I accidentally broke the code of that one, and due to its poor results I never bothered to rebuild the program. The derivatives of finite-precision Fourier series are actually very poor at approximating the derivatives of the original function; this is known as the Gibbs phenomenon, as can be seen in the low-amplitude high-frequency perturbations of the Fourier series of a square wave:

<img width="1280" height="640" alt="Gibbs_phenomenon_50 svg" src="https://github.com/user-attachments/assets/12b3bcbb-b47f-4936-9f7c-5571facb6ada" />

Performing a moving average on the series could smooth out the perturbations induced by the Gibbs phenomenon, but this would be too computationally expensive for my resources. Thus, Fourier series is not an ideal approach for the computation of Bernoulli numbers; for pure mathematics, where we can have sums without an upper bound, it may be more useful.

$$\textbf{Closing Remarks}$$

Therefore, by applying fractional derivative operators to series expansions for the generating function of the Bernoulli numbers, we may be able to obtain Bernoulli numbers $B_n$ of non-integer index $n$, which would be useful for identifying the zeroes of the Riemann zeta function, since $B_n=-n\zeta(1-n)$. Nevertheless, there are potential issues with these purported methods in addition to computational limitations, as infinite series are unfortunately eager to diverge, and polynomials with non-integer degree terms tend to ramify in the complex plane.

More generally than the extension of the Bernoulli numbers to non-integer indices, or the extension of derivatives to non-integer orders, whenever I come across a discrete structure in mathematics one of the first things that comes to my mind is, "How can I generalize this to become continuous, if not to all complex numbers?" For the integers are but particular cases of the complex numbers, so by understanding the complex numbers we can a fortiori understand the integers - this is the essence of analytic number theory. Generalization - this is the essence of mathematics. Henri Poincaré said it best:

$$\textbf{“Mathematics is the art of giving the same name to different things.”}$$

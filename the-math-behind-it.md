$$\textbf{Introduction}$$

The Bernoulli numbers, traditionally denoted as $B_n$, are a sequence of numbers that pop up frequently in analytic number theory, most notably in their relation to the Riemann zeta function, $B_n=-n\zeta(1-n)$.
Seeing as zeroes of the Bernoulli numbers would thus correspond with zeroes of the Riemann zeta function, it would be useful to find an expression for $B_n$ for non-integer values of $n$, for the purpose of studying the Riemann Hypothesis.
We take note of the generating function for the Bernoulli numbers

$$\frac{z}{e^z-1}=\sum \limits_{i=0}^\infty {\frac{B_i z^i}{i!}}  [\mathrm{I}]$$

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

$$B_n=lim_{a \to 0} \left. \sum\limits_{j=0}^\infty {f^{(j)}(k) \frac{\Gamma (j+1)(z-k)^{j-n}}{j! \Gamma(j-n+1)}} \right|_{z=a}  [\mathrm{IV}]$$

This is the value computed by BernoulliContinued.nb, albeit to a finite precision.

$$\textbf{Closing Remarks}$$

Lorem ipsum.

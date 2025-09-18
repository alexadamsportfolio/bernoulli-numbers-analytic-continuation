$$\textbf{Introduction}$$

The Bernoulli numbers, traditionally denoted as $B_n$, are a sequence of numbers that pop up frequently in analytic number theory, most notably in their relation to the Riemann zeta function, $B_n=-n\zeta(1-n)$.
Seeing as zeroes of the Bernoulli numbers would thus correspond with zeroes of the Riemann zeta function, it would be useful to find an expression for $B_n$ for non-integer values of $n$, for the purpose of studying the Riemann Hypothesis.
We take note of the generating function for the Bernoulli numbers

$$\frac{z}{e^z-1}=\sum \limits_{i=0}^\infty {\frac{B_i z^i}{i!}}$$

Which implies that the nth Bernoulli number is the nth derivative of the generating function evaluated at a point tending towards 0 (because the function is undefined at x=0), i.e.,

$$B_n=lim_{a \to 0} \left. {\frac{d^n}{dz^n} \frac{z}{e^z-1}} \right|_{z=a}$$

Evidently, we will need to generalize the derivative operator to non-integer values - that is, discover fractional calculus. There are a variety of ways we can proceed from here.

$$\textbf{Approach 1: Taylor Series}$$

Lorem ipsum

$$\textbf{Closing Remarks}$$

Lorem ipsum.

Though the-math-behind-it.md delineates the mathematics most necessary to the behavior of this project, it would be a shame for a STEM portfolio not to have some mention of my less successful findings - after all, the end is the smallest, and arguably the most trivial, stage in mathematics. 
This is a gallery of the surviving minority of my incomplete, if not incorrect, attempts on the bernoulli-numbers-analytic-continuation project; but they are no less interesting.

Recalling [Part 1, IV] in the-math-behind-it.md we arrive at the following Taylor series expansion for the Bernoulli numbers of non-integer index:

$$B_n=lim_{z \to 0} \left. \sum\limits_{j=0}^\infty {f^{(j)}(k) \frac{\Gamma (j+1)(z-k)^{j-n}}{j! \Gamma(j-n+1)}} \right.$$

However, I have been very skeptical of this result, partially due to the ambiguity in the choice of the center of the series $k$; this has led me to attempt to prove that the sum is invariant under choice of center, i.e. $\frac{\partial B_n}{\partial k} = 0$, as reflected in the below scratch paper:

![102f3847-3410-452a-b04d-b3c38a3239f9 1280x1280](https://github.com/user-attachments/assets/8ad3adf0-69c0-4121-9b62-aff1efa84423)

Though it would be convenient for such a proof if $-kf^{(j+1)}(k)=f^{(j)}(k)$, this is very unlikely to be the case, even if the sum was invariant under choice of $k$.

On another note, in [Part 2, IV] in the-math-behind-it.md we arrive at the following Fourier series expansion for the Bernoulli numbers of non-integer index:

$$B_n=lim_{z \to 0} \left. {\frac{1}{2T}\sum \limits_{j=-\infty}^\infty {(ij)^n e^{ijz} \int_{-T}^{T} {\frac{te^{-ijt}}{e^t-1}dt}}} \right. $$

Though I doubt that the integral is an elementary function, it looked very interesting, prompting the following attempt on it:

![f95d5372-f864-42be-b8a1-b504eb0ca12b 1280x1280](https://github.com/user-attachments/assets/84cee557-df31-4826-b436-88d6fc0589ae)

If you couldn't tell by now, one of my favorite techniques for computing nonelementary integrals is to expand them into infinite series of elementary integrals.
It works, though I'm hoping to discover more sophisticated methods going forward.

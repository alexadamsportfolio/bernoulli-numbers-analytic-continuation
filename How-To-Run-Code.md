You might be able to upload the BernoulliContinued.nb file to the Wolfram Cloud, but if that doesn't work you could just copy and paste the following code to whatever Mathematica system you're using:

```
f[z_]:=z/(E^z-1)
c[k_, j_]:=D[f[z], {z, j}]/. z -> k
b[z_, n_, k_]:=Sum[c[k, j]*(z-k)^(j-n)/Gamma[j-n+1], {j, 0, PRECISION}]
k=POSITION-PARAMETER
Table[N[b[0, i, k]], {i,TABLE-MIN, TABLE-MAX, TABLE-STEP}]
Plot[{b[0, x, k]}, {x, PLOT-MIN, PLOT-MAX}]
```

Of course, prior to running the code you have to configure the following required parameters:

- Precision: How many terms of the infinite series expression for my attempted continuation of the Bernoulli numbers you would like to run. I have stuck to 100, due to computational limitations.
- Position-Parameter: Analogous to the center of a series around which a Taylor series is generated. I frequently use the value -5 for no particular reason. NOTE: 0 DOES NOT WORK.
- Table-Min, Table-Max, & Table-Step: The table returns discrete values along the curve, which has been convenient for bypassing computational limitations. Table-Min is the minimum value, Table-Min the maximum, and Table-Step the size of the steps that partition the interval.
- Plot-Min & Plot-Max: The minimum and maximum values of the interval along which the plot of the curve is generated. The plot is continuous rather than discrete, making it very computationally heavy; I frequently use the interval $[0,5]$.

Below is an example output:

<img width="779" height="675" alt="image28" src="https://github.com/user-attachments/assets/e407fe92-0fe0-460d-8c89-778af013ea19" />

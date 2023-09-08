# Modelling the joint dynamics of Exchange rates, Interest rates and Oil prices using Vector Autoregression

Vector Autoregressive (VAR) analysis is implemented to study how a system of variables interact with each other over time. These variables are implemented into a system of equations to understand how each variable and their past values affect one another. VAR analysis is perfectly catered to study the joint evolution of oil prices, exchange rates and interest rates. I hypothesize that the relationships between oil prices, exchange rates and interest rates differ across oil-producing countries. I investigate this hypothesis for three countries namely: United States, Venezuela and Saudi Arabia.

## Fractional Differentiation

When we say stationarity is satisfied in a data set, we imply that the assumption that the statistical properties of the time series do not change over time are met. Methods such as differencing or taking the logarithmic values of data, are often used used to transform a non-stationary data to achieve stationarity. In this study, I apply the fractional differecing method to stationarize some of my data sets before running analysis on the data.

To define the process of fractional differentiation I extend the differencing operator so that I can apply it a fractional amount of times. Therefore, I define $D^{d}$ for non-integer values of $d$, hopefully for a value in the interval of [0,1]. This process enables us to reach a compromise between losing information and getting stationary data

### An example of fractional differentiation
In calculus the general power rule is defined as, 

$\frac{{d}}{{dx}}(x^{n}) = n \cdot x^{n-1}$

Differentiating using integer values,

$\frac{{d}^{2}}{{d}^{2}{x}}(x^{n})= n(n-1) \cdot x^{n-2}$

$\frac{{d}^{3}}{{d}^{3}{x}}(x^{n}) = n(n-1)(n-2) \cdot x^{n-3}$

Rewriting the third order differentiation

$\frac{{d}^{3}}{{d}^{3}{x}}(x^{n}) = \frac{n(n-1)(n-2)(n-3)\dots(1)}{(n-3)(n-4)\dots(1)} \cdot x^{n-3}$

Giving us,

$\frac{{d}^{3}}{{d}^{3}{x}}(x^{n}) = \frac{n!}{(n-3)!} \cdot x^{n-3}$

Inferring from the equation above, a general form can be written, 

$\frac{{d}^{k}}{{d}^{k}{x}}(x^{n}) = \frac{n!}{(n-k)!} \cdot x^{n-k}$

The general form equation is similar to fractional differential function formed in the previous section. Now if the case $k,n \in \mathbb{R}$ is true and inferring from Euler's integral proof, 

$n! \cong \Gamma(n + 1)$

Where, 
    
$\Gamma(n + 1) = \int_{0}^{\infty}x^{n} \cdot e^{-x}dx$

Giving the power rule for fractional differentiation, 

$\frac{{d}^{k}}{{d}^{k}{x}}(x^{n}) = \frac{\Gamma(n + 1)}{\Gamma(n + 1 - k)} \cdot x^{n-k}$

Using the equation we can find the differential value of $\frac{{d}^{1/2}}{{d}^{1/2}{x}}(x^{5})$

$\frac{{d}^{1/2}}{{d}^{1/2}{x}}(x^{5}) = \frac{\Gamma(5 + 1)}{\Gamma(5 + 1 - 1/2} \cdot x^{5 - 1/2}$
$=\frac{\Gamma(6)}{\Gamma(11/2)} \cdot x^{9/2}$
$= \frac{5/2}{21\sqrt{\pi}} \cdot x^{9/2}$

### Fractionally differentiating a dataset

Fractionally differentiating a dataset retains comparitively more information or memory.On the contrary, integer-differentiated series such as returns exhibit a finite memory span, meaning that historical data is completely discarded after a certain sample window. When stationarity transformations erase all data memory, statisticians turn to intricate mathematical methods to capture any remaining residual signals, often leading to suprious results.
We can note from the picture differences the immense amount of memory retained.
<img width="1014" alt="IS-RD(USOIL)" src="https://github.com/angad7071/IndependentStudyThesis/assets/74730257/5033c55e-25ab-4da0-aee2-3d040e84338f">
<img width="1013" alt="IS-RD(VEIN)" src="https://github.com/angad7071/IndependentStudyThesis/assets/74730257/054e55a5-6a49-491a-b84b-87692783143a">
<img width="1012" alt="IS-RD(VOIL)" src="https://github.com/angad7071/IndependentStudyThesis/assets/74730257/650af25f-298e-4b81-b6a6-35f960135294">



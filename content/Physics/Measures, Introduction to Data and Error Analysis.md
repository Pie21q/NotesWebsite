
+++
title = 'Measures, Introduction to Data and Error Analysis'
date = 2024-10-05T12:08:51+02:00
draft = false
math = true 
+++



## Error Analysis
- Calculate the mean between the different measures
- Calculate the residuals X<sub>n</sub> - Mean of X's `the sum of the residuals should approximate to 0, but its not a very good rapresentation`
- Calculate the standard deviation `Rapresentation of how much the data deviates from the Mean value`

Standard deviation Formula
$$ S_x = \sqrt \frac{\sum^n_{i=1} (X_i - \bar x)^2}{n-1}$$
## Representing Data
- Tables `not very efficient nor readable`
- Histograms `Graphical rapresentation of Data, Easier to compare`
> Normalized Histograms are used to represent the frequency of every measure, `The data is averaged in Bins, which range from 2 values`

As the number of measurements approaches infinity, and the size of the bins approaches 0, the Histogram approaches a curve, called ==Limiting Distribution== `In the case of limited, small errors they become negligible, and the Histogram approaches a curve known as Normal distribution or Gaussian Function`

[![Normal Distribution | Examples, Formulas, & Uses](https://www.scribbr.de/wp-content/uploads/2023/01/standard-normal-distribution-example.webp)

$$ f(x)=\frac{1}{\sigma\sqrt{2\pi}}e^(-\frac{1}{2}(\frac{x-\mu}\sigma)$$

==We can also calculate the error on the mean value using the formula below

$$\sigma_\bar{x} = \frac{\sigma_x}{\sqrt{N}} $$

>__Always keep in minds that errors aren't necessarily mistakes, but uncertainties in the measures

## Absolute Errors Vs Relative Errors
- Absolute errors is the same and doesn't depend on the measure we're taking `0,003m of errors while measuring the Earth's circunference is very good, the same error on hair thickness doesn't really make sense`
- The error shouldn't have more significant digits than the mean value, While at the same time a mean value with more significant value should be rounded up to the same as the error

## Error Propagation
Taking 2 different measures in the lab and combining them will lead to a third value with a different error than the other two
>`For example we could find the new error by summing (in case our first operation was sum) the 2 errors on the 2 measurements, but that's could lead to over-estimation of the final error

There are 2 different formulas


Addition
$$value= \bar{z} + \bar{x} = \bar{y}, \space\space uncertainty = \sigma_x = \sqrt{(\sigma_x)^2 +(\sigma_y)^2}$$
Multiplication
$$value= \bar{z} * \bar{x} = \bar{y}, \space\space uncertainty = \sigma_x = \sqrt{(\frac{\sigma_x}{\bar{x}})^2 +(\frac{\sigma_y}{\bar{y}})^2}$$

`A generic formula using derivatives is also available`

Special Cases
- In case of a measure times  a constant you just multiply the measure by the constant

## Systematic Errors
Type of error dependent on the tool we use to measure and not on our measuring technique `eg. a ruler which has wrong markings`


## Error Compatibility
we can measure the compatibility between 2 errors by measuring the discrepancy

## Weighted Average
Allows us to combine different measures with different values of precision
>`Combining averages taken in 2 differents labs, possibly with 2 different methods can reduce not only measure errors but also systematic ones

first we calculate weight 

$$w = \frac{1}{\sigma^2}$$

We can them combine the two weighted measurements in a weighted average usng
$$x_{w.a.}= \frac{w_ax_a+w_bx_b}{w_a+w_b}$$
at last we can measure the new, `propagated`, error by using
$$\sigma_{w.a.}= \frac{1}{\sqrt{w_a+w_b}}$$
## Values relationships
Being given a set of points on a graph
- We need to find a line which best suits our dataset `We can do that by using the method of the least squares, helping us to find the best values of A and B for y=Ax + B`
- After finding the parameters we can calculate the error present in the parameters we found
# The rule of 72 - why it works and when


<!-- hack for removing extra bullets from ToC -->
<style>
#TableOfContents ul { 
  list-style-type: none; 
}

#TableOfContents ul ul { 
  list-style-type: none; 
}

#TableOfContents ul ul ul { 
  list-style-type: disc; 
} 
</style>

<script type="text/x-mathjax-config">
  MathJax.Hub.Config({
    tex2jax: {
      inlineMath: [ ['++','++'] ],
      processEscapes: true
    }
  });
</script>
<script type='text/javascript' src='http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML'></script>

### What is the rule of 72

The well known rule of ++72++ estimates the time it takes for an investment to
double with compounding. Simply put it states, that if an investment has a
return of ++r++% year on year, the investment will double in roughly
++\frac{72}{r}++ years. Combined with basic knowledge of compounding, the rule
is both simple and useful enough to perform a number of wide variety of
approximations without having to use a calculator. Let us run through two
illustrative examples:

#### Example 1
Q) At a 6% rate of return, how much money will $100,000 grow to in 30 years?

The rule of 72 tells us that a return of 6% compounded should double in about
12 years. Hence, it should grow about 4x in 24 years, making it a sum of
$400,000 in 4 years. 

The remaining 6 years is (luckily) half the doubling time. We can approximate
the effect of these 6 years again using the inverse rule of 72. Assuming 6
years to be a time period we know that the investment doubles in two time
periods (12 years), i.e, ++2 = \frac{72}{r}++.

This gives us a growth of 36% in one time period (6 years) - note that the
result of the application of this rule of 72 is the same as simple interest of
6% for 6 years and is hence a bad one. We will come back to this later, and
learn about when the rule of 72 does badly. Thus the sum of $400,000 will grow
by another 36% in the last 6 years, giving us a value of $544,000 after the
full 30 years.

#### Example 2

Q) What will $100 be worth in 50 years at an inflation of 3%?

Asked another way, since inflation of 3% is equal to a negative -3% return, we
are looking for the present value of a future value of $100 at 3%. The rule
of 72 tells us that a 3% return should double in about 24 years. Hence the
investment should should grow 4x in about 48 years. In other words, the $100
dollar bill should be worth only about $25 in real terms after 48 years.

We can perform a simple interest calculation for the remaining two years (ignoring
compound interest). The $100 bill should be worth about 6% less than $25 or
roughly $23.5.[^2].
  
#### Approximation Errors

Let us proceed to see what the actual results to both problems are. Using
python, the answer to the first problem is <small><tt>400e3 *
(1.06)\*\*30</tt></small> or $574,000 (rounded to the nearest 1000 dollars).
Similarly, the answer to the second problem is <small><tt>100 /
(1.03)\*\*50</tt></small> or $22.8 (rounded to the nearest ten cents).

Both results are close enough to illustrate the power of 72.

### Deriving the rule of 72 - Doubling under compounding

The rule of compound interest tells us that a sum of ++x++ after ++t++ years
compounding at a rate of ++r++ becomes:

$$x * (1+\frac{r}{100})^{t}$$

Given that the sum has doubled over ++t++ years, we are wish to find ++t++ such
that:

$$x *(1+\frac{r}{100})^{t} = 2x$$

Dividing by ++x++ on both sides and writing ++\frac{r}{100}++ as ++R++, we wish
to find ++t++ such that:

$$(1 + R)^{t} = 2$$

Taking the natural logarithm on both sides and transposing to make ++t++ the
subject of the equation, we get:

$$t = \frac{ln 2}{ln(1+R)}$$

Let us approximate ++ln(1+R)++. Assuming ++R++ to be small, we may ignore the
higher order terms in the [Maclaurin
series](https://en.wikipedia.org/wiki/Taylor_series#List_of_Maclaurin_series_of_some_common_functions)
expansion of ++ln(1+R)++. This gives us ++ln(1+R) \approx R++. For small ++R++, we may write:

$$t \approx \frac{ln 2}{R} \approx \frac{0.693}{R} \approx \frac{0.693}{\frac{r}{100}} \approx \frac{69.3}{r}$$

In other words, **the rule of 72 is actually the rule of 69.3**! 72 is generally
chosen as an approximation to the numerator since it has a large number of
factors - 2, 3, 4, 6, 8, 12, 24 and 36.

I prefer to use the rule of 70 when I am dealing with an interest rate of 5% or
7% and the rule of 72 otherwise.

### How well does the rule of 72 hold up?

In general, approximations are only as good as the regime in which the
assumptions hold - in our case, the assumption is small enough ++R++. We can
compare the validity of the rules of 72 and 69.3 by comparing their results
against an actual compounding calculation:

<table class="table table-bordered table-striped table-condensed">
<colgroup>
  <col class="col-md-3"><col class="col-md-3"><col class="col-md-3"><col class="md-3">
</colgroup>
<thead>
  <tr><th><center>Interest Rate</center></th>
      <th colspan="3"><center>Time to Double in Years</center></th></tr>
  <tr><td></td>
      <th><center>Without approximation</center></th>
      <th><center>Rule of 69.3</center></th>
      <th><center>Rule of 72</center></th></tr>
</thead>
<tbody>
<tr><td>100% </td><td>1.00    </td><td>0.69    </td><td> 0.72     </td></tr>
<tr><td>75%  </td><td>1.24    </td><td>0.92    </td><td> 0.96     </td></tr>
<tr><td>50%  </td><td>1.71    </td><td>1.39    </td><td> 1.44     </td></tr>
<tr><td>25%  </td><td>3.11    </td><td>2.77    </td><td> 2.88     </td></tr>
<tr><td>20%  </td><td>3.80    </td><td>3.47    </td><td> 3.60     </td></tr>
<tr><td>15%  </td><td>4.96    </td><td>4.62    </td><td> 4.80     </td></tr>
<tr><td>12%  </td><td>6.12    </td><td>5.78    </td><td> 6.00     </td></tr>
<tr><td>10%  </td><td>7.27    </td><td>6.93    </td><td> 7.20     </td></tr>
<tr><td>8%   </td><td>9.01    </td><td>8.66    </td><td> 9.00     </td></tr>
<tr><td>6%   </td><td>11.90   </td><td>11.55   </td><td> 12.00    </td></tr>
<tr><td>4%   </td><td>17.67   </td><td>17.33   </td><td> 18.00    </td></tr>
<tr><td>3%   </td><td>23.45   </td><td>23.10   </td><td> 24.00    </td></tr>
<tr><td>2%   </td><td>35.00   </td><td>34.65   </td><td> 36.00    </td></tr>
<tr><td>1%   </td><td>69.66   </td><td>69.30   </td><td> 72.00    </td></tr>
<tr><td>0.50%</td><td>138.98  </td><td>138.60  </td><td> 144.00   </td></tr>
<tr><td>0.10%</td><td>693.49  </td><td>693.00  </td><td> 720.00   </td></tr>
</tbody> </table>

In general, the rule of 72 holds up pretty well except for the high interest rates:

![Validity of the Rule of 72](https://docs.google.com/spreadsheets/d/193WmHjVE3e6sZPDcj1zhol29T2evt-C6EO9CCDiK8Y4/pubchart?oid=718855741&format=image)

While the Rule of 69.3 always underestimates the actual time to double, the
rule of 72 tends to overestimate the time to double for low interest rates and
underestimates it otherwise:

![Underestimation Percentage Error](https://docs.google.com/spreadsheets/d/193WmHjVE3e6sZPDcj1zhol29T2evt-C6EO9CCDiK8Y4/pubchart?oid=2098081227&format=image)

If you are curious, the rule of 72 matches the without-approximation
calculation at an interest rate of around 7.85%. Incidentally, in the range of
practically occuring interest rates (between 2% and 10%), the rule of 72 is
more precise than the rule of 69.3!

#### Doubling in 2 time periods

Thankfully, high interest rates do not occur too frequently practice. However,
a very useful special case to know is the half life of doubling. Consider an
investment that is set to double in k years, it will grow by ++\sqrt{2}++ in
the first ++\frac{k}{2}++ years, and another ++\sqrt{2}++ in the next
++\frac{k}{2}++ years - i.e, by 41.4% in each ++\frac{k}{2}++ period. A similar
formula holds with thirds of a doubling period and ++\sqrt[3]{2}++.

Knowledge of 41% as the doubling rate would have allowed us to better appromixate
the solution to Example 1 as $400,000 * 1.41 = $564,000, a number that is even
closer to the actual answer of $574,000.

[^2]: The astute reader will realize that we are making yet another approximation here. We ideally want ++\frac{25.00}{1.06}++ - instead we settle with ++25.00 * (1 - 0.06)++ since ++\frac{1}{1+x}++ roughly equals ++1 - x++ for small values of x.


# Choosing intuitive axes


Earlier today, the New York times [published](http://nyti.ms/1LLH6ml) a
wonderful visualization on how family income affects children's college
chances. The visualization uses a new you-draw-it-first paradigm, where the
reader guesses the expected relationship / trend before being shown the actual
data. I found the idea very cool. Go ahead and try it, I'll wait.  It's easy to
see why this is easily one of my favourite NY Times visualizations ever.

Except, they chose the wrong dataset to exhibit the you-draw-it-first paradigm.

### Spoiler Alert

After you proceed to draw your guess, you find out that the relationship
between "Percent of children who attend college" and "Parents' income
percentile" turns out to be surprisingly[^1] linear. Apart from the article
itself calling the result "astonishing", the aggregate responses given by NY Times
readers (as of my writing the post) looks like the shaded region in this[^3]:

![Aggregate of Trends drawn by NY Times Readers - 10:45 PM PDT](/images/post-photos/NYTimesAggregate.png)

As it turns out, the linearity arises only because of a few tricks
at play here:

* *Income Rank* in the US is distributed ~log(*Dollar Income*).
* The original paper, [Chetty, Hendren, Kline](http://www.equality-of-opportunity.org/images/mobility_geo.pdf),
talks about the quality of college attended as well, which the NYTimes article leaves it out.
* The original paper defines attending college as the mere presence of one or more
  [1098-T filing](http://www.irs.gov/uac/Form-1098-T,-Tuition-Statement)
  for a child. This definition is very broad and includes everything from
  universities to vocational schools.

### Let's choose an x-axis we intuitively understand

Let's really dig in and see if this is as unintuitive as the
article makes it seem.  First let's collect centile income data from Raj
Chetty's [Equality of Opportunity](www.equality-of-opportunity.org). Since raw
data of college attendance and quality is not readily avaiable, let's
reconstruct them off of the graphs in the paper[^2].

To verify our data, let's first plot College and Attendence vs Rank as the paper does:

![Attendance, Quality vs Rank (Reproduced as in Chetty's paper)](https://docs.google.com/spreadsheets/d/1jD87QN3pPZjoefrAm4E_OR9UD_rjwae9Gd7MbpjjrNs/pubchart?oid=1826330590&format=image)

Here's the same chart drawn against actual Income Dollars as opposed to Income
Rank on the horizontal axis:

![Attendance, Quality vs Income Dollars](https://docs.google.com/spreadsheets/d/1jD87QN3pPZjoefrAm4E_OR9UD_rjwae9Gd7MbpjjrNs/pubchart?oid=544948064&format=image)

This is immediately easier to relate to as the horizontal axis is far more intuitive.
We all know how much a thousand dollars is (as opposed to an income centile), and
how hard it is to get a $1000 raise as opposed to how hard it is to get one that will push us
up by one percentile[^3].

### What does a percentile amount to?

The article states, "Moving up a single percentile on the family-income
distribution makes enrolling in college about 0.7 percentage points more
likely". That's incredibly hard to wrap my head around. How much is a
percentile in dollar terms? Again, quoting, "About $2,400 in annual
income separates the bottom two dots, while nearly $1 million separates the top
two".

Asking the reader to guess the relationship against *Income Rank* as opposed to
*Income Dollars* is the difference between asking users to draw f(x) against
log(x) as opposed to x!

Using the right axes matter!

### Are we measuring the right thing?

College quality and attending college only tell part of the story.  What's
really important is how much these children make when they are older. Chetty,
Hendren, Klein do collect and present how "Family Income of Child at age of 31"
varies with Parent's Income Rank. Here's a Google Sheets rendition of their
data:

![Attendance, Quality, Family Income of Child vs Rank](https://docs.google.com/spreadsheets/d/1jD87QN3pPZjoefrAm4E_OR9UD_rjwae9Gd7MbpjjrNs/pubchart?oid=1014863741&format=image)

Here's the same data plotted against our preferred horizontal axis of Parent Income Dollars:

![Attendance, Quality, Family Income of Child vs Rank](https://docs.google.com/spreadsheets/d/1jD87QN3pPZjoefrAm4E_OR9UD_rjwae9Gd7MbpjjrNs/pubchart?oid=455844899&format=image)

This graph is far easier to understand! In fact, it begin to tell a story. A
story of a world where the challenges of pursuing a quality college[^4]
education bottoms out with income, but at the same time, a world where the
money one is likely to make is directly proportional to the financial resources
one has growing up.

If you made it this far,
[here's](https://docs.google.com/spreadsheets/d/1jD87QN3pPZjoefrAm4E_OR9UD_rjwae9Gd7MbpjjrNs/pubhtml)
the data along with interactive charts. As a bonus,
[here's](http://thewireless.co.nz/articles/the-pencilsword-on-a-plate) a sweet
treat for you - a Toby Morris comic that tells a similar story.

[^1]: The entirety of the charm of a you-draw-it-first charm presumably lies in a surprise such as this. With that considered, the surprise isn't that surprising after all.

[^2]: Extrapolation was easy since the paper mentions that college attendance is linear with rank, and college quality is quadratic.

[^3]: Yep, my intention was to draw an S curve - but my impatience got the better of me!

[^4]: By college, we really mean an educational institution that had to file a Form 1098-T.


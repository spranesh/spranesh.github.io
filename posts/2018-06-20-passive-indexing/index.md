# An estimate of the size of passive indexing


With low fees, excellent diversification, and probabilities in the investor's
favor, indexing and passive investing have been on the rise for the last 40
years. [Vanguard](http://www.vanguard.com) is a leader in this field, offering
investors access to the world's stocks for less than a tenth of a percent.

A common question that repeatedly arises is "What if everybody indexes?".
While I don't think this is an issue (since prices are set at the margin and
more that 95% of trading on the exchanges is the result of active flows) this
question is not without merit. To even begin answering this question, it is
important to understand the current size of passive indexing. This is not as
obvious as it may initially seem.  FT reports that passive investing is a
[third of the
market](https://www.ft.com/content/4cdf2f88-7695-11e6-b60a-de4532d5ea35),
another source says it's
[24%](https://mathinvestor.org/2018/03/does-indexing-threaten-the-market/),
while another estimate says it's less than
[10%](https://www.reuters.com/article/us-funds-blackrock-passive/less-than-18-percent-of-global-stocks-owned-by-index-investors-blackrock-idUSKCN1C82TE).
So, which is it?

In order to answer this, a ground up approach is required. The key is that most
passive investing happens at the large fund houses, and these are listed in
13-D and 13-F filings at the SEC. One can also look at an aggregator like
Morningstar for some of this data. To estimate this, I looked at three large
stocks, and made a best effort to classify the largest institutional holders as
active vs passive. I chose GE, Apple, and Microsoft in order to avoid dealing
with significant [float
adjustments](https://us.spindices.com/documents/index-policies/methodology-sp-float-adjustment.pdf).

As an example, here is the table for GE along with my best effort
classification of passive vs active nature of the institutional holder.

<div class="row">
<div class="col-sm-2"></div>
<div class="col-sm-8">
<table class="table table-bordered table-striped table-condensed">
<thead><tr><th>Institution</th><th>Weight</th><th>Passive</th></tr></thead><tbody>
 <tr><td>Vanguard Group Inc</td><td>7.00</td><td>Yes</td></tr>
 <tr><td>State Street Corp</td><td>3.85</td><td>Yes</td></tr>
 <tr><td>GE Savings and Security Program</td><td>4.29</td><td>No</td></tr>
 <tr><td>BlackRock Institutional Trust Company NA</td><td>2.64</td><td>Yes</td></tr>
 <tr><td>Capital World Investors</td><td>1.81</td><td>No</td></tr>
 <tr><td>Capital Research Global Investors</td><td>1.49</td><td>No</td></tr>
 <tr><td>Northern Trust Investments N A</td><td>1.34</td><td>No</td></tr>
 <tr><td>Fidelity Management and Research Company</td><td>1.07</td><td>Yes</td></tr>
 <tr><td>Harris Associates L.P.</td><td>1.01</td><td>No</td></tr>
 <tr><td>Geode Capital Management, LLC</td><td>0.99</td><td>No</td></tr>
 <tr><td>Government Pension Fund of Norway - Global</td><td>0.7</td><td>No</td></tr>
 <tr><td>State Street Global Advisors (Aus) Ltd</td><td>1.28</td><td>Yes</td></tr>
 <tr><td>Trian Fund Management LP</td><td>0.82</td><td>No</td></tr>
 <tr><td>Franklin Advisers Inc</td><td>0.79</td><td>Yes</td></tr>
 <tr><td>T. Rowe Price Associates, Inc.</td><td>0.68</td><td>Yes</td></tr>
 <tr><td>Managed Account Advisors LLC</td><td>0.68</td><td>No</td></tr>
 <tr><td>Merrill Lynch & Co Inc</td><td>0.59</td><td>No</td></tr>
 <tr><td>Wellington Management Company LLP</td><td>0.59</td><td>No</td></tr>
 <tr><td>Morgan Stanley Smith Barney LLC</td><td>0.56</td><td>No</td></tr>
 <tr><td>Barrow Hanley Mewhinney & Strauss LLC</td><td>0.75</td><td>No</td></tr>
</tbody></table></div>
<div class="col-sm-2"></div>
</div>

Adding only the passive ownership, we get the following:

<div class="row">
<div class="col-sm-3"></div>
<div class="col-sm-6">
<table class="table table-bordered table-striped">
<thead>
 <tr><th>Average</th><th>19.4%</td></th></thead><tbody>
  <tr><td>Apple</td><td>20.25%</td></td>
 <tr><td>Microsoft</td><td>20.75%</td></tr>
 <tr><td>GE</td><td>17.31%</td></tr>
</tbody></table></div>
<div class="col-sm-3"></div>
</div>

However, we must not forget that there are several passive funds that aren't on
the list above. We can adjust for this by using the [pareto
rule](https://en.wikipedia.org/wiki/Pareto_principle). We also need to adjust
for the fact that all passive focused institutions including Vanguard
themselves have several active funds. In fact, Vanguard itself has around 20%
of it's AUM in active funds
([$1T](https://institutional.vanguard.com/VGApp/iip/site/institutional/researchcommentary/article/InvComActiveMgmtInfographic)
/ [$5T](https://about.vanguard.com/who-we-are/fast-facts/)).

<div class="row">
<div class="col-sm-2"></div>
<div class="col-sm-5">
<table class="table table-bordered table-striped">
<tbody>
 <tr><td>Average</td><td>19.4%</td></tr>
 <tr><td>Adjust for Tail (Pareto rule)</td><td>24.30%</td></tr>
 <tr><td>Passive Multiplier</td><td>0.7</td></tr>
 <tr><th>Passive Indexing</th><th>17%</th></tr>
</tbody></table></div>
<div class="col-sm-5"></div>
</div>

Thus, the estimate for passive indexing is **~17%**. This is not a large number
by any means and I suspect that it will ebb and flow with the markets itself.
Passive indexing is efficient in many ways, including costs, diversification,
and portfolio risk, but on it's own, it does not remove the behavioral
fragilities of the individual investor!


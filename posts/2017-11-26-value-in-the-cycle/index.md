# Value investing during the last bull cycle


Recently, there have been many pieces that claim that value investing has not
worked this cycle. [Einhorn][1] questioned if value investing is dead and
[Goldman Sachs][2] mulled it.

Others have suggested that value works, but it has evolved. The claim is that
quantitative measures no longer work (certainly not P/B, at least) and
identifying value is about qualitative analysis. For example, growing companies
with wide moats and ability to reinvest capital are regularly mispriced. All of
this appeals to intuition. Several value managers have underperformed and some
others have closed shop. But is it true?

To find out, I ran a few backtests. Quite immediately, it was clear that P/B
has not worked as well as it used to. This is a well known fact, and the
diminishing nature of this factor on large cap stocks is referenced in What
Works On Wall Street (James O' Shaughnessy).

In the same book, the author suggests using a Value Composite. Such a
methodology ranks all stocks on P/B, P/E, and P/FCF, and uses the sum of these
ranks to decide the final ranking. The book itself was written in the 90s (and
updated hence), so any strategy that we pick from the original version is
hindsight-bias free.

The Value Composite has worked wonders in the last 10 years.  The backtests I
ran showed 10-year CAGR of ~8% and a 5-year CAGR of 15%, heftily beating the
index. To make sure that my data was survivorship bias free, and my code was
error free, I investigated other ways of verifying the effectiveness of the
value anamoly.

I didn't have to look far, since the [MSCI's enhanced value index][3] (pdf)
uses a methodology that is very similar in spirit:

1. Rank stocks based on the z-scores of P/B, Forward P/E, and EV/CFO
2. Average these scores for each stock.
3. Within a sector, scale and cap these scores to make it comparable.
4. Build a value-cum-market weighted index of the top ~100 securities.

This simple, quantitative method, holding a diversified portfolio, beats the
market cap weighted index:

![Relative outperformance of MSCI Enhanced Value](https://i.imgur.com/312KqN5.png)

Now, obviously an index is gross of fees, and cannot be invested in directly.
However, the MSCI Enhanced Value Index has ETFs tracking it. [VLUE][4] in
particular, is a low cost (~15 bps) ETF offered by iShares that tracks the
benchmark fairly closely.

In short, even quantitative value investing on a diversified portfolio has
performed quite well. Value investing is dead, long live value investing
([link][5]).

[1]: https://www.cnbc.com/2017/10/24/david-einhorn-value-investing-may-be-dead-and-amazon-and-tesla-killed-it.html
[2]: https://www.bloomberg.com/news/articles/2017-06-08/goldman-sachs-mulls-death-of-value-investing-after-losing-decade
[3]: https://www.msci.com/documents/10199/4769bda4-d57e-4933-9971-8609cec2653b
[4]: https://www.ishares.com/us/products/251616/ishares-msci-usa-value-factor-etf
[5]: https://seekingalpha.com/article/4109735-value-investing-dead-long-live-value-investing


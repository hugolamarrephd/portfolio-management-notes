---
tags:
  - global
---
# Conventions
Convention for quotes, the number of "measurement" currency per "quoted" currency is given by
$$
S = \text{quoted} : \text{measurement} = q:m
$$
$$
S = \text{measurement}/\text{quoted} = m/q
$$
Note also that
$$
a:b = \frac{1}{b:a}
$$
* *The quoted currency is what an investor buys (at the ask price) or sells (at the bid price).
* The measurement currency is what is used to "settle" the transaction

For example, if two parties exchange 1.33 CAD  for 1 USD, we have
* USD:CAD = 1.33 
* CAD:USD = 1/1.33 = 0.75
* 1.33 CAD/USD
* 1/1.33 = 0.75 USD/CAD
# Changes in Exchange Rates
A "quoted" currency *depreciates* relative to a "measurement" currency if 
$$
\text{quoted} : \text{measurement} \downarrow
$$
or equivalently
$$
\text{measurement}/\text{quoted} \downarrow
$$
For example, CAD *depreciates* relative to USD if 
* CAD:USD *decreases*
* or equivalently USD/CAD *decreases*

When computing period rates of appreciation, the rate will depend on the "direction" of the quotation. In particular,
$$
\frac{S(t+1, a:b) - S(t, a:b)}{S(t, a:b)} \neq \frac{S(t+1, b:a) - S(t,b:a)}{S(t,b:a)}
$$
In fact, we have
$$
\frac{S(t+1, b:a) - S(t,b:a)}{S(t,b:a)} =\frac{S(t+1, a:b)^{-1} - S(t, a:b)^{-1}}{S(t, a:b)^{-1}} = \frac{S(t,a:b)-S(t+1,a:b)}{S(t+1,a:b)}
$$
Note that this is not an issue if we use *continuously compounded rates of change* as 
$$
\log S(t+1, a:b) - \log S(t, a:b) = \log S(t, a:b)^{-1} - \log S(t+1,a:b)^{-1} = \log S(t,b:a) - \log S(t+1,b:a)
$$
# Direct Quotes
A *direct* quote is one for which the foreign currency is quoted:
$$
\text{foreign} : \text{domestic}
$$
For example, USD:CAD = 1.33 means that we must pay 1.33CAD to purchase 1USD.
On the contrary, the *indirect* quote CAD:USD = 0.75 tells us how much USD we can get for 1CAD.

* The foreign currency *depreciates* if the *direct* quote decreases because purchasing 1USD costs less.
 * The domestic currency *depreciates* if the *indirect* quote *decreases* because we get less USD for 1CAD.

# Cross-Rates

By basic arithmetic rules, we have
$$
a:c = a:b \times b:c
$$
since $c/a = b/a \times c/b$ by definition of $:$, and
$$
a: c = {b:c} \div {b:a}
$$
or since $c/a = {c/b} \div {a/b}$ by definition of $:$.

# Forex Market

Quoted currencies in seniority order are: GBP, EUR, USD. Traded FX rates are thus:
* GBP:EUR
* GBP:USD
* EUR:USD

For all other currencies,  USD is the *quoted* currency, e.g.
* USD:CAD
* USD:JPY
* etc.

## Spreads

Dealers move the center of the bid-ask spread in reaction to changes in their inventories, but they do *not* widen the spread itself. Increasing spreads compared to other market participants would lead to no trading at all!

Here are the available quotes:

| Rate | bid | ask |
|------|-----|-----|
| USD:CAD | 1.33 | 1.34 |
| EUR:USD | 1.09 | 1.10 |

The bid of $a:b$ is the ask of $b:a$. For example, 1/1.33 is the *ask* of CAD:USD. Indeed, if we are willing to buy 1USD in exchange for 1.33CAD, we are also willing to sell 1CAD in exchange for 1/1.33=0.75USD.

> When **buying** the quoted currency, we divide our "investment" by the ask price e.g. 1CAD $\rightarrow$ $\div$ 1.34 = 0.746USD
> When **selling** the quoted currency, we multiple our "investment" by the bid price e.g. 1USD $\rightarrow$ $\times$ 1.33 = 1.33CAD

##  Cross-Rates and Spreads

For example, let's assume a Canadian investor wants to exchange some CAD for some EUR. Recall that USD:CAD and EUR:USD are traded on forex markets. 

The investor
1. buys some USD at the ask price of 1.34CAD per USD - i.e. worst possible price
2. buys some EUR at the ask price of 1.10USD per EUR - i.e. worst possible price

The investor ends up paying 1.34 USD:CAD $\times$ 1.10 EUR:USD = 1.47 EUR:CAD, i.e. a *direct* quote of 1.47 CAD per EUR, which is equivalent to an *indirect* quote of 1/1.47=0.68 CAD:EUR

> **Tip:** Investor buys(sells) at the highest(lowest) possible price. In other words, the cross-rate spread is always maximized.

1. From [cross-rates rules](#cross-rates), the direct quote is EUR:CAD = USD:CAD $\times$ EUR:USD
2. By maximizing the spread, we find
 	Minimum EUR:CAD bid = USD:CAD bid $\times$ EUR:USD bid = 1.33 $\times$ 1.09 = 1.45CAD
 	Maximum EUR:CAD ask = USD:CAD ask $\times$ EUR:USD ask = 1.34 $\times$ 1.10 = 1.47CAD
3. Our investor is buying EUR:CAD so she pays the (highest) ask price of 1.47CAD per EUR as computed previously.

Now let's assume a Canadian investor wants to exchange some CAD for some AUD and following quotes are available:

| Rate | bid | ask |
|------|-----|-----|
| USD:CAD | 1.33 | 1.34 |
| USD:AUD | 1.53 | 1.54 |

By [cross-rates rules](#cross-rates), the direct quote is AUD:CAD = USD:CAD $\div$ USD:AUD such that we now have

* Minimum AUD:CAD bid = USD:CAD bid $\div$ EUR:USD **ask** = 1.33 $\div$ 1.54 = 0.86CAD
* Maximum AUD:CAD ask = USD:CAD ask $\div$ EUR:USD **bid** = 1.34 $\div$ 1.53 = 0.88CAD

A Canadian investor would thus pay the (highest) ask price of 0.88CAD per AUD.
## Triangular Arbitrage

If a bank provides a EUR:CAD quote outside of the (cross-rate) quote available on the forex market, there is an arbitrage opportunity.
For example let's say the bank quotes 1.43-1.44, which is outside the (cross-rate) quote of 1.45-1.47. An investor could buy EUR with CAD at a price of 1.44CAD and sell EUR for CAD at a price of 1.45CAD. 

To profit from this opportunity, a Canadian investor would have to 
1. **Buy Low**: Buy EUR from bank at 1.44CAD
2. **Sell High**:
	1. Sell EUR on forex market at 1.09USD
	2. Sell USD on forex market at 1.33CAD
	3. For an overall rate of 1.09 $\times$ 1.33 = 1.45CAD
We thus have the following sequence, which results in a riskless arbitrage:
1CAD $\rightarrow$ $\div$ 1.44 = 0.69EUR $\rightarrow$ $\times$ 1.09 = 0.756USD $\rightarrow$ $\times$ 1.33 = 1.006CAD.

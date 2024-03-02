---
tags:
  - global
---
We focus on the rate DC:FC where DC stands for domestic currency and
FC stands for foreign currency.
The quoted currency is the domestic currency (e.g. CAD)
and the measurement currency is the foreign currency (e.g. USD).
From a Canadian investor perspective, we could e.g. think of DC:FC as CAD:USD,
namely the price of 1$ CAD denominated in USD.
You may recognize type of quote as an [[currency-fundamentals#Direct Quotes|indirect quote]].

$F$ denotes the forward price of DC:FC (with maturity $\tau$)
and $S$ denotes the corresponding spot price.
# Summary
Assuming frictionless markets,
* When Investing in a country with a high interest rate, we expect a currency depreciation that will perfectly offset the interest rate differential
* **But** the high interest is a sure thing and the depreciation is uncertain.
* Currency risk reduces to inflation uncertainty; in particular, **real** expected return on risk-free bills should be the same in all countries
* Currencies have no risk premium; in particular, currency hedging is free.
* Higher real rate is good for currency, but higher inflation is bad for currency.
# Covered Interest Rate Parity
$$
\text{forward discount} \leftrightarrow \text{interest rates}
$$
Covered interest rate parity is related to [[currency-forwards]]. From absence of cash-and-carry-type arbitrage, we have
$$ \frac{F}{S} = \frac{1+r_{FC}}{1+r_{DF}} $$
such that the forward premium (or discount) is given by
$$
f \equiv \frac{F-S}{S} = \frac{r_{FC}-r_{DC}}{1+r_{DC}} \approx r_{FC}-r_{DC}
$$
where $r$ denotes interest rates. In words, **gain on interest rate differential means loss on forward discount.**
# Purchasing Power Parity
$$
\text{change in currency rate} \leftrightarrow \text{inflation rates}
$$
> Idea. *Real price of a good must be the same in all countries* (assuming no trade restrictions).
## Absolute Purchasing Power Parity
Exchange rate should be equal to the **ratio** of the **average price levels** in the two countries.
## Relative Purchasing Power Parity
Exchange rate movements should exactly offset any inflation differential between the two countries:
$$
\frac{S_1}{S_0} = \frac{1+i_{FC}}{1+i_{DC}}
$$
where $i$ denotes inflation rates.

For example, if inflation is high in Canada ($i_{DC} \gg i_{FC}$), CAD:USD should decrease to compensate for the fact that Canadian goods are getting more costly, such that the cost (in USD) is stable for an American Buyer. Otherwise, arbitrage opportunities would arise such as buying goods in the US to sell them in Canada.

Or equivalently, looking at percentage changes in exchange rates, we have
$$
s \equiv \frac{S_1 - S_0}{S_0} = \frac{i_{FC} - i_{DC}}{1+i_{DC}} \approx i_{FC} - i_{DC}
$$
If relative PPP holds, **the real return on any asset is identical for investors from any country** since the real return for a foreign investor is
$$
r_{DC} + s - i_{FC} = r_{DC} + i_{FC} - i_{DC} - i_{FC} = r_{DC} - i_{DC}
$$
where $r_{DC}$ denotes the nominal return in the domestic country
i.e. what we would usually think of as the yield of a bond or the return of a stock!

>For example, assume an investment opportunity in Canada has a nominal yield of 20%.
>If inflation in Canada is 2.5%, the real return for a Canadian is simply 20%-2.5%=17.5%.
>Now, what is the real rate of return for a foreign investor if inflation is 1.3% in the foreign country?
>
>If PPP holds, the currency is expected to *depreciate* by 1.3%-2.5%=-1.2%.
>This depreciation will generate a loss of roughly 1.2% for the foreign investor,
>as converting CAD back to USD will be less favorable at the moment the asset is sold.
>Hence, the nominal return for an American investor would be
>	(20%-currency depreciation of 1.2%)=18.8%
>and the *real* return would be
>	(18.8%-inflation in the US of 1.3%)=17.5%.

# International Fisher
$$
\text{interest rates} \leftrightarrow \text{inflation expectations}
$$
Let
$$
(1+r) = (1+\rho)(1+E[i])
$$
where $\rho$ is the real interest rate and $E[i]$ is the expected inflation (usually based on some forecast in practice).

>Idea. Real interest rates are stable over time and equal across the world.

Hence, changes in rates are caused by changes in inflation expectations and 
$$
\frac{1+r_{FC}}{1+r_{DC}} = \frac{1+E[i_{FC}]}{1+E[i_{DC}]}
$$
or with a linear approximation
$$
r_{FC} - r_{DC} \approx E[i_{FC}] - E[i_{DC}]
$$
*Interest rates differ across the world because inflation rates differ.*
Otherwise, capital flows towards high real interest countries until the opportunity disappears and real rates are equalized.
# Uncovered Interest Rate Parity
$$
\text{currency return expectations} \leftrightarrow \text{interest rates}
$$
Assuming the relative purchasing power parity relationship holds *in expectation*, we get
$$
\frac{E[S_1]}{S_0} = \frac{1+E[i_{FC}]}{1+E[i_{DC}]}
$$
which can be related to the international Fisher relationship
$$
\frac{E[S_1]}{S_0} = \frac{1+r_{FC}}{1+r_{DC}}
$$
or with a linear approximation,
$$
E[s] \approx r_{FC} - r_{DC}
$$
*We expect the foreign currency movement to be equal to the interest rate differential between the two countries.*

This relationship relies on a frictionless world where:
1) You can buy goods in the country with the lower real price and ship them for sale in the country with the higher real price and make an arbitrage profit without costs
2) If the currency rate does not line up with the rate differential, you can borrow in the lower interest rate country and lend in the higher interest rate country to make an arbitrage profit without costs.

# Foreign Exchange Expectations
$$
\text{forward discount} \leftrightarrow \text{currency return expectations}
$$
Under the same assumptions as [[#Uncovered Interest Rate Parity]], we have
$$
F = E[S_1]
$$
which also means that $E[S_1/F -1] = 0$, i.e. there is no risk premium in the currency market.

*There is no reward for bearing foreign exchange uncertainty and there is no cost to hedging currency risk!*

In other words, if uncovered parity holds, we expect the forward price will "realize" at maturity,
such that forward prices are **unbiased forecasts** of future spot currency rates.

Equivalently, we have
$$
f = \frac{F - S_0}{S_0} = E\left[\frac{S_1-S_0}{S_0}\right] =s
$$
i.e. *the expected spot return is equal to the forward discount (premium)*.
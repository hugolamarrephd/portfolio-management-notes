---
tags:
  - global
---
Rates contracted today for delivery in the future.
Forward rates are quoted as a premium to the spot:

$$
\text{premium} \equiv \frac{\text{forward} - \text{spot}}{spot}
$$

which can be annualized.
# Covered Interest Rate Parity
By absence of arbitrage, we must have

$$
\text{premium} = \frac{r_\text{measurement} - r_\text{quoted}}{1 + r_\text{quoted}}
$$

Or equivalently,

$$
\text{forward} = \text{spot} \frac{1+r_\text{measurement}}{1+r_\text{quoted}}
$$

where $r$ are (risk-rate) interest rates available in the "quoted" and "measurement" countries. 

**The forward premium is roughly equal to the interest rate differential.**
When the interest rate increases in the "quoted" country, the current forward price decreases:

$$
\text{Higher interest rate in "quoted" country} \implies \text{Discount}
$$

and vice-versa,

$$
\text{Lower interest rate in "quoted" country} \implies \text{Premium}
$$

## Arbitrage 
Forward contract is equivalent to spot transaction plus borrowing/lending in the two currencies.
Let's denote by $S$ the spot rate for $a:b$ and by $F$ the forward rate for $a:b$ with maturity $\tau$.
In other words, $a$ is the quoted currency and $b$ is the measurement currency.
### Long Forward Arbitrage
At time-0, we entre a long $a:b$ forward position $(XS_0)(1+r_a)$ contract at price $F$ and do the following:

| Time-0 Operation | Time-0 Cash Flow | Time-$\tau$ Operation | Time-$\tau$ Cash Flow |
|-----|-----|-----|-----|
| Borrow $a$  | $+Xa$ | Pay $a$-denominated debt back | $-X(1+r_a)a$ |
| Exchange $a$ for $b$ @ $S_0$ | $-Xa \rightarrow +XS_0b$|  Exchange $b$ for $a$ @ $F$ (settling forward position) | $-XS_0(1+r_b)b \rightarrow +\frac{XS_0}{F}(1+r_b)a$ |
| Lend $b$ | $-XS_0b$ | Get $b$-denominated investment back | $+XS_0(1+r_b)b$ |
|| $0$ || $\left(-X(1+r_a)+\frac{XS_0}{F}(1+r_b)\right)a$|
For absence of arbitrage, we must have

$$
-X(1+r_a)+\frac{XS_0}{F}(1+r_b) = 0 \implies S_0 = F\frac{1+r_a}{1+r_b} \implies F = S_0\frac{1+r_b}{1+r_a}
$$

since the initial investment is zero.

Hence,  **borrowing in $a$ and investing in $b$ is equivalent to a short $a:b$ forward position** (since it is perfectly offsetting a long forward position).
In particular, we win if $a:b$ depreciates as we are in a better spot to convert $b$ back to $a$ at maturity $\tau$.
### Short Forward Arbitrage
At time-0, we enter a short $a:b$ position with $\frac{X}{S_0}(1+r_a)a$ in notional value at price $F$ and do the following:

| Time-0 Operation | Time-0 Cash Flow | Time-$\tau$ Operation | Time-$\tau$ Cash Flow |
|-----|-----|-----|-----|
| Borrow $b$  | $+Xb$ | Pay $b$-denominated debt back | $-X(1+r_b)b$ |
| Exchange $b$ for $a$ @ $S_0$ | $-Xb \rightarrow +\frac{X}{S_0}a$|  Exchange $a$ for $b$ @ $F$ (settling forward position) | $-\frac{X}{S_0}(1+r_a)a \rightarrow +\frac{X}{S_0}(1+r_a)Fb$ |
| Lend $a$ | $-\frac{X}{S_0}a$ | Get $a$-denominated investment back | $+\frac{X}{S_0}(1+r_a)a$ |
|| $0$ || $\left(\frac{X}{S_0}(1+r_a)F-X(1+r_b)\right)b$|
For absence of arbitrage, we must have

$$
\frac{X}{S_0}(1+r_a)F-X(1+r_b) = 0 \implies F = S_0\frac{1+r_b}{1+r_a} 
$$

since the initial investment is zero.

Hence, **borrowing in $b$ and investing in $a$ is equivalent to a long $a:b$ forward position** (since it is perfectly offsetting a short forward position).
In particular, we win if $a:b$ appreciates as we are in a better spot to convert $a$ back to $b$ at maturity $\tau$.
## Replication
* You can replicate a short $a:b$ forward position by borrowing in $a$ and investing in $b$
* You can replicate a long $a:b$ forward position by borrowing in $b$ and investing in $a$

## Bid-Ask Spreads
Investor entering a **long forward** at ask price must be equivalent to
* Borrow *measurement* at **ask** price
* Convert *quoted* to *measurement* at **ask** rate (i.e. *dividing* borrowed amount by the *ask* rate)
* Lend *quoted* at **bid** price

Investor entering a **short forward** at bid price must be equivalent to
* Borrow *quoted* at **ask** price
* Convert *quoted* to *measurement* at **bid** rate (i.e. multiplying borrowed amount by the *bid* rate)
* Lend *quoted* at **bid** price

Another way to look at it is simply to minimize the bid and maximize the ask using

$$
F_{bid} = S_{0,bid} \frac{1+r_{measurement,bid}}{1+r_{quoted,ask}}
$$

and 

$$
F_{ask} = S_{0,ask} \frac{1+r_{measurement,ask}}{1+r_{quoted,bid}}
$$

# Summary
To replicate a long USD:CAD forward position, we must borrow in CAD and invest in USD. We lose money if USD:CAD depreciates, as the value of our USD-denominated investments decreases relative to CAD. 

In summary, we have

| Forward Position | Replication-Invest | Replication-Borrow | Depreciation in Quoted Currency |
|---|---|---|---|
| Short| measurement | quoted | Profits |
| Long | quoted | measurement  | Losses |

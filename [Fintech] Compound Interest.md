# Compound Interest Calculator

For this Fintech company, you need to build a compound interest calculator, using the four variables below as input:

- **Principal**: This is the starting amount you put into the account. It’s the base amount that will start earning interest right away.

- **Interest Rate**: This is the percentage of your current balance that the bank adds to your account as interest each year. For example, a 5% interest rate means the bank will add 5% of your balance to your account every year.

- **Annual Contribution**: This is a fixed amount you add to your investment at the end of each year, like a regular deposit you decide to make. Each time you make this contribution, it increases your balance, which in turn, increases the amount of interest you earn next year (since interest is calculated on the new, larger balance).

- **Years to Invest**: This is how long your money stays in the account, compounding annually. The longer you invest, the more times your balance grows, not only from the interest but also from the additional contributions.

## 🧮 Objective

Using these four values, calculate the final amount you’ll have after the specified number of years, with annual compounding. In other words, at the end of each year, you’ll earn interest on your current balance, then make an additional contribution.

Return the answer **rounded to two decimal places**.


```python

def compound_interest(principal, rate, contribution, years):
  for i in range(years):
    principal = (principal*(1+(rate/100)))
    principal= principal + (contribution)
  
  return round(principal,2)

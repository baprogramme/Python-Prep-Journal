# 🎁 FAANG VP's Holiday Gift Assignment Challenge

Imagine you're a **VP at a FAANG company**, and you want to reward your team with gifts at the end of the year during Christmas time. You check in with stingy HR, and the best they could do is scrounge up a limited set of **gift cards** – each with different values and to various stores.

Each teammate has **different expectations** for their end-of-year gift:
- Your **Director** expects a **$1000+** gift card for something luxurious.
- The **new grad** on your team would be thrilled with something as simple as a **$10** gift card to Starbucks.

You can only give **each person at most one gift card**, and if a gift card **doesn’t meet someone’s minimum expectation**, it’s **better not to give them one at all**, as we definitely don't want to disappoint.

---

### 🎯 Goal

Find a way to satisfy as **many teammates as possible** by assigning each one a gift card that **meets or exceeds** their expectation.

Return the **maximum number of teammates you can satisfy**.

---

### 🧠 Rules Recap
- Each gift card can only be used once.
- Each person can receive **at most one** gift card.
- A person is satisfied **only if** the gift card's value is **greater than or equal to** their expectation.
- If no suitable card exists for a person, **it's better to give them nothing**.

---

### 📥 Input

- `Expectations`: a list of integers representing the **minimum gift value** each team member expects.
- `Cards`: a list of integers representing the **value of available gift cards**.

---

### ✅ Output

- A single integer – the **maximum number of people** who can be satisfied.

---

## 🔍 Examples

### Example #1
**Input:**

Expectations = [5, 20, 1000]

Cards = [10, 15, 100]

**Output:**

2


**Explanation:**
- The team member expecting $5 can be satisfied with the $10 gift card.
- The one expecting $20 can be satisfied with the $100 card.
- The Director expecting $1000 is out of luck — nothing in stock meets their expectation.

---

### Example #2
**Input:**

Expectations = [10, 30, 100, 200]

Cards = [5, 2, 5, 3, 9]


**Output:**

0


**Explanation:**
None of the available gift cards can satisfy any expectations — even the lowest expectation is $10, while the highest gift card is only $9.

---

```python

def max_satisfied_teammates(expectations, cards):
    expectations.sort()
    cards.sort()

    i = 0  # index for expectations
    j = 0  # index for cards
    satisfied = 0

    while i < len(expectations) and j < len(cards):
        if cards[j] >= expectations[i]:
            satisfied += 1
            i += 1
            j += 1
        else:
            j += 1  # try next card

    return satisfied


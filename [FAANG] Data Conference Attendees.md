# Minimum Number of Conference Attendees

You're at a **Data Science conference** with an unknown number of attendees. The attendees have a wide range of titles, such as:

- Data Scientist  
- Data Analyst  
- ML Product Manager  
- ML Engineer  
- Founder  
- CTO  
- And others...

During the event, you ask a sample of `n` attendees the following question:

> "How many other people here have you met with the same title as you?"

Each response is recorded in the `answers` array, where `answers[i]` is the response of the `i-th` person you surveyed.  
Assume that **each person you surveyed has encountered every other person at the conference with the same title**.

Your task is to return the **minimum possible total number of attendees** at the conference.

---

## Examples

### Example 1:
**Input:**  
`answers = [2, 1, 1]`

**Output:**  
`5`

**Explanation:**  
- The first person (perhaps a Data Scientist) reports encountering 2 other people with the same title.  
  → This implies there are at least **3** people with this title.

- The second and third persons each report encountering 1 other person with their title.  
  → This implies at least **2** people with this shared title.

Therefore, the **minimum total number** of attendees is:  
**3 (from the first group) + 2 (from the second group) = 5**

---

### Example 2:
**Input:**  
`answers = [0, 0, 1]`

**Output:**  
`4`

**Explanation:**  
- The first two respondents each report 0 others with their title.  
  → Each has a **unique title**, so 1 person per title × 2 = **2** attendees.

- The third person reports encountering 1 other person with their title.  
  → At least **2** people share this title.

Total attendees = **2 (unique titles)** + **2 (shared title)** = **4**

---

## Constraints

- `1 <= answers.length <= 1000`
- `0 <= answers[i] <= 1000`

---

```python

from collections import Counter
import math

def minimum_attendees(answers):
    count_map = Counter(answers)
    total_attendees = 0

    for x, count in count_map.items():
        group_size = x + 1
        groups_needed = math.ceil(count / group_size)
        total_attendees += groups_needed * group_size

    return total_attendees

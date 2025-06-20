# 🖥️ GPU Scheduling Problem - No Overlap Allowed

At your big-tech company, teams are fighting tooth and nail to train their AI models on the company’s shiny new **NVIDIA GPUs**. It’s like the Hunger Games but with less archery and more coding.

The GPUs are in such high demand that some teams “accidentally” (totally on purpose) **overlap their training sessions**. It’s chaos. The GPU cluster is booked for days on end, and now everyone’s looking for gaps to squeeze in their own usage.

Unlike those greedy GPU hogs, **your team has been given strict instructions**: you can only run your training on days when **nobody else is using the GPUs**. Your VP made it crystal clear — **overlapping sessions are not an option**.

---

## 🔧 Problem

You’re given two things:

- An integer `days`, representing the total number of days the GPUs are available (from day 1).
- A 2D array `training_sessions` where `training_sessions[i] = [start_i, end_i]` shows when team `i` is hogging the GPUs.

Your mission is to **figure out how many days the GPUs are sitting idle**, so your team can swoop in and get some guilt-free training time.

---

## 🧪 Example 1

**Input:**

training_sessions = [[2, 4], [1, 5], [7, 8]]

days = 9

**Output:**
2

**Explanation:**
Day 6 and day 9 are the only days when the GPUs are free.


## 🧪 Example 2

**Input:**

training_sessions = [[1, 4]], 

days = 4

**Output:**: 

0

**Explanation:**

The GPUs didn’t get a single day off. Your team will just have to wait patiently until the chaos subsides.

## 💡 Goal

Return the number of idle days when no team is using the GPUs. These are the days your team can use the resources without any overlap.


```python

def gpu_idle_days(days, training_sessions):
    if not training_sessions:
        return days  # all days are free

    # Step 1: Sort the intervals by start time
    training_sessions.sort()
    
    # Step 2: Merge overlapping intervals
    merged_sessions = []
    start, end = training_sessions[0]
    
    for s, e in training_sessions[1:]:
        if s <= end:  # overlapping
            end = max(end, e)
        else:
            merged_sessions.append([start, end])
            start, end = s, e
    
    # Add the final merged session
    merged_sessions.append([start, end])
    
    # Step 3: Count used days
    total_used_days = sum(end - start + 1 for start, end in merged_sessions)
    
    # Step 4: Subtract from total
    return days - total_used_days

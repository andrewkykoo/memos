---
title: Procedural Programming
date: 2023/3/22
description: Stepping stone to object oriented programming.
tag: programming, procedural
author: Andrew K
---

# Procedural Programming

The main purpose of **programming paradigms** (e.g., procedural, functional, object-oriented) is to structure code.

Structure brings the following benefits to the code:

- Easy to update
- Create new functionality

**Procedural programming** structures code into procedures or subroutines. The code is made up of logical steps to complete a specific task.

**Example**: Let's apply procedural approach to calculate total bill and add tax. This will involve four subroutines that reduce the footprint of the code.

```
food_bill = {
  drink: 12.55,
  main: 35.12,
  dessert: 15.35
}
```

```
# 1. reuses food_bill
def bill_total(bill):
    total = 0.00
    for k, v in bill.items():
        total += v
    return total
```

```
# 2. reuses bill_total
def calculate_tax(percent, bill_total):
    return round((percent * bill_total) / 100.0, 2)
```

```
# 3. reuses bill_total and food_bill
food_total = bill_total(food_bill)
```

```
# 4. reuses food_total
tax_total = calculate_tax(9, food_total)
```

```
print("Overall: ", food_total + tax_total)
```

As shown above, procedures can be reused by other parts of the code, reducing duplication in the code. Also, it is easy to understand the code because each procedure is broken into specific tasks. However, there are **limitations**:

- Data is expoed throughout the whole program
- No hierarchy
- Heavy focus on instructions means it doesn't relate well to real-world objects

### Summary

Each programming paradigm brings advantages and disadvantages. It is up to the developer to decide which is the best approach to a specific task.

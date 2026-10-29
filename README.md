# Representation-of-a-Real-World-Problem-as-a-Markov-Decision-Process


## Aim

To represent a Package Delivery Robot as a Markov Decision Process (MDP) by defining its states, action space, transition probabilities, and reward function, and implementing the model using Python.

---

## Problem Statement

### Problem Description

A package delivery robot starts from a warehouse carrying a package. It moves along a path and stops at a checkpoint for verification. After verification, it continues to the final destination and delivers the package. The goal is to deliver the package safely with minimum cost and time while maximizing the total reward.


---

## MDP Components

A Markov Decision Process is represented as:


MDP = (S, A, P, R, gamma)


Where:

| Symbol | Meaning |
|---|---|
| S | Set of states |
| A | Set of actions |
| P | Transition probability function |
| R | Reward function |
| gamma | Discount factor |

---

## State Space

The state space represents the possible locations of the delivery robot.

Statespace format:

```text
S = {
    0: "Warehouse",
    1: "Checkpoint",
    2: "Destination"
}
```



---

## Sample State

A sample state is one specific example from the state space.

Checkpoint (State 1)
The robot has reached the checkpoint and is waiting for package verification before continuing to the destination.

---

## Action Space

The action space represents all possible actions available to the robot.

Example format:

```text
A = {
    0: "Move Forward",
    1: "Wait",
    2: "Deliver Package"
}
```


---

## Sample Action

Move Forward

When the robot is at the warehouse, it moves to the checkpoint. From the checkpoint, it moves to the destination.



---

## Transition Probability


If the delivery robot is at the **Warehouse** and chooses **Move Forward**, it reaches the **Checkpoint** with probability 1.0.

**P(Checkpoint | Warehouse, Move Forward) = 1.0**

If the robot is at the **Checkpoint** and chooses **Move Forward**, it reaches the **Destination** with probability 1.0.

**P(Destination | Checkpoint, Move Forward) = 1.0**

The transition probability explains how the robot moves from one state to another after an action is taken.

**General form:**

P(Next State | Current State, Action)

This means:

> Probability of reaching the next state after taking an action in the current state.
---

## Reward Function

```text
Successful Delivery = +100
Move Forward (uses time and energy) = -1
Unnecessary Waiting = -5
```
General form:


R(s,a,s')

```

+100 – Package successfully delivered.
-1 – Robot move forward.
-5 – waiting unnecessarily.


```

---

## Graphical Representation

<img width="932" height="992" alt="image" src="https://github.com/user-attachments/assets/328476f5-5733-42ba-8d5d-03c6cb980adf" />


---

## Python Representation


```python
# MDP Representation using Python
# Package Delivery Robot

# States
# 0 = Warehouse
# 1 = Checkpoint
# 2 = Destination

# Actions
# 0 = Move Forward
# 1 = Wait
# 2 = Deliver Package

P = {
    0: {
        0: [(1.0, 1, -1, False)],
        1: [(1.0, 0, -5, False)]
    },

    1: {
        0: [(1.0, 2, -1, False)],
        1: [(1.0, 1, -5, False)]
    },

    2: {
        2: [(1.0, 2, 100, True)]
    }
}

print("Package Delivery Robot MDP\n")

for state in P:
    print(f"{state}: ")
    print("  {")
    for action in P[state]:
        print(f"    {action}: {P[state][action]}")
    print("  }")
    print()


print("Name: Deepadharshini T      ")
print("Register Number: 212224230052    ")

```
---
## Output

<img width="292" height="355" alt="image" src="https://github.com/user-attachments/assets/9eb01c07-42f9-46f5-8434-56afcd8a973b" />



---

## Result

Thus, the Package Delivery Robot was successfully represented as a Markov Decision Process with three states: Warehouse, Checkpoint, and Destination. The action space, transition probabilities, reward function, graphical representation, and Python implementation were defined successfully.


---

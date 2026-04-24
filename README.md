# MDP REPRESENTATION

## Name: Nandakesore J
## Reg No: 212223240103

## AIM:
To model the Snake game as a Reinforcement Learning problem using a deterministic Markov Decision Process (MDP).

## PROBLEM STATEMENT:

### Problem Description
The objective is to design an agent that controls a snake in a grid environment to collect food while avoiding collisions with walls or its own body. The agent learns by interacting with the environment and receiving rewards.

### State Space 
Snake head position (x, y) <br>
Snake body positions<br>
Food position<br>
Current direction of movement<br>

### Sample State
Snake Head → (5,5) <br>
Food → (8,5) <br>
Direction → Right <br>
Body → (5,4)

### Action Space
Move Up <br>
Move Down <br>
Move Left <br>
Move Right 

### Sample Action
From state (5,5) with food at (8,5): <br>
Move Right

### Reward Function
+10 → Snake eats food <br>
-10 → Snake hits wall or itself <br>
-1 → Move away from the food <br>
+1 → Move towards the food <br>

### Graphical Representation
<img width="1569" height="921" alt="WhatsApp Image 2026-04-23 at 1 38 00 PM" src="https://github.com/user-attachments/assets/d210d375-3549-44bb-9125-5eb1cafbbeee" />


## PYTHON REPRESENTATION:
```
# Snake MDP Representation (Deterministic)

# State mapping
# 0 -> (5,5)  start
# 1 -> (6,5)
# 2 -> (7,5)
# 3 -> terminal state (food eaten OR crash)

P = {
    0: {  # S0 (5,5)
        0: [(1.0, 3, -10, True)],   # UP -> hits body
        1: [(1.0, 5, -1, False)],   # DOWN
        2: [(1.0, 6, -1, False)],   # LEFT
        3: [(1.0, 1, 1, False)]    # RIGHT -> (6,5)
    },

    1: {  # S1 (6,5)
        0: [(1.0, 7, -1, False)],   # UP
        1: [(1.0, 8, -1, False)],   # DOWN
        2: [(1.0, 3, -10, True)],   # LEFT -> hits body
        3: [(1.0, 2, 1, False)]    # RIGHT -> (7,5)
    },

    2: {  # S2 (7,5)
        0: [(1.0, 9, -1, False)],   # UP
        1: [(1.0, 10, -1, False)],  # DOWN
        2: [(1.0, 1, -10, False)],   # LEFT -> hits body
        3: [(1.0, 3, 10, True)]     # RIGHT -> food eaten
    },

    3: {  # Terminal state
        0: [(1.0, 3, 0, True)],
        1: [(1.0, 3, 0, True)],
        2: [(1.0, 3, 0, True)],
        3: [(1.0, 3, 0, True)]
    }
}

print(P)
```

## OUTPUT:
<img width="1234" height="94" alt="image" src="https://github.com/user-attachments/assets/778fb3d2-17b0-4a7d-af80-4ca0ba92edd8" />

## RESULT:
Thus the Snake game is successfully modeled and represented as a deterministic MDP.


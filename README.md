# Can You See The Forest From The Trees?

A certain forest is a perfect square of 101×101101 \times 101101×101 very thin trees in a square grid. Precisely at the center of the forest one tree is missing. If you stand exactly at that location, you can see many of the trees-- but not all, because trees in the exact same direction overlap.

How many trees can you see from this position?

Assumptions and hints

Regard the trees as infinitely thin. They either eclipse each other completely because they are in the exact same direction, or are visible as separate trees.

If the forest were 11×1111 \times 1111×11, you could see 80 trees, as shown in this sketch:

```python
  o o o o   o o o o  
o   o   o   o   o   o
o o   o o   o o   o o
o   o   o   o   o   o
o o o o o o o o o o o
        o x o
o o o o o o o o o o o
o   o   o   o   o   o
o o   o o   o o   o o
o   o   o   o   o   o
  o o o o   o o o o 
```

## Solution
### 1. Using Analytic Geometry and Numpy:
```python
import numpy as np
n = 101
v = np.concatenate([np.linspace(-50, 0, 51), np.linspace(1, 50, 50)])
x, y= np.meshgrid(v, v)
num_visible_trees = np.unique(np.arctan2(y, x)).shape[0]
print("You can see %d trees while standing at the origin." % num_visible_trees)
```

### 2. Using Number Theory and pure Python:
```python
import math 
n = 101
num_visible_trees = -4
for i in range(0, (n // 2 + 1)):
  for j in range(0, (n // 2 + 1)):
    if (math.gcd(i, j) == 1):
      num_visible_trees += 4
print("You can see %d trees while standing at the origin." % num_visible_trees)
```
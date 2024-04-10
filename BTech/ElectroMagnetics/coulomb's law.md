# Coulomb's Law
*Coulomb's law is an experimental law formulated in 1785 by Charles Augustin de Coulomb, then a colonel in the French army. It deals with the force a point charge exerts on another point charge* 
- point charge we mean a charge that is located on a body whose dimensions are much smaller than ota collection of electric
charges on a pinhead may be regarded as a point chargeher relevant dimensions ,a collection of electric charges on a pinhead may be regarded as a point charge

$$
F = \frac{k \cdot Q_1 \cdot Q_2}{r^2} , Unit = Coulomb
$$

Where $k = \frac{1}{4 \times \pi \in_0}$ or $k = 9 \times 10^{9}$ m/f  and $\in_0 = 8.854 \times 10^{-12}$

$q_{proton} = 1.6 \times 10^{-19}$ C , $q_{electron} = -q_{proton}$  and $q_{nuetron} = 0$
- 1 C(Coulomb) = $6 \times 10^{18}$ electrons



> [!IMPORTANT] Multiple Cargers 
> When dealing with multiple charges we use [SuperPosition](superposition%20princliple.md) principle


##### Coulomb vector force on point charges Q1 and Q2 .

```python
import numpy as np
import matplotlib.pyplot as plt
# Create multiple vectors

V = np.array([3,1])
W = np.array([2,3])

fig, ax = plt.subplots()

# Add vectors V and W to the plot
ax.quiver(0, 0, V[0], V[1], angles='xy', scale_units='xy', scale=1, color='r')
ax.quiver(0, 0, W[0], W[1], angles='xy', scale_units='xy', scale=1, color='b')
ax.quiver(2,3,1,-2,angles='xy',scale_units='xy',scale=1,color='r')
ax.set_xlim([-3, 5])
ax.set_ylim([-3, 3])

plt.grid()
plt.show()
```

```python
import numpy as np
import matplotlib.pyplot as plt

# Create vectors
V = np.array([3, 1])
W = np.array([2, 3])

# Calculate resultant vector
R12 = V + W

# Create plot
fig, ax = plt.subplots()

# Add vectors V and W to the plot
ax.quiver(0, 0, V[0], V[1], angles='xy', scale_units='xy', scale=1, color='r', label='q1')
ax.quiver(0, 0, W[0], W[1], angles='xy', scale_units='xy', scale=1, color='b', label='q2')
ax.quiver(W[0], W[1], 1,-2, angles='xy', scale_units='xy', scale=1, color='g', label='R12')
ax.annotate('q1', (V[0], V[1]), xytext=(-15, 15), textcoords='offset points', fontsize=12, color='r')
ax.annotate('q2', (W[0], W[1]), xytext=(-15, 15), textcoords='offset points', fontsize=12, color='b')
ax.annotate('R12', (R12[0], R12[1]), xytext=(-15, 15), textcoords='offset points', fontsize=12, color='g')

# Set plot limits
ax.set_xlim([-3, 5])
ax.set_ylim([-3, 6])

# Display grid
plt.grid()
plt.legend()
plt.show()

```
# Matlibplot

#### Ploting a Sine wave
```python

import matplotlib.pyplot as plt
import numpy as np

x = np.arange(0, 5 * np.pi, 0.1)
y = np.sin(x)

# Plotting Sine Graph
plt.plot(x, y, color="green")
plt.show()
```
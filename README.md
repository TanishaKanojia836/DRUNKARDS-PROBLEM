# DRUNKARDS-PROBLEM
import numpy as np
import matplotlib.pyplot as plt


steps = 1000
origin = np.array([[0, 0]])


directions = np.array([[0, 1], [0, -1], [1, 0], [-1, 0]])
random_indices = np.random.choice(len(directions), size=steps)
step_sequence = directions[random_indices]


path = np.concatenate([origin, step_sequence]).cumsum(axis=0)

plt.figure(figsize=(8, 8))
plt.plot(path[:, 0], path[:, 1], color='blue', alpha=0.7, label='Path')


plt.scatter(path[0, 0], path[0, 1], color='green', s=100, label='Start (0,0)', zorder=5)
plt.scatter(path[-1, 0], path[-1, 1], color='red', s=100, label='End', zorder=5)

plt.title(f"Random Walk Simulation ({steps} steps)")
plt.xlabel("X-axis")
plt.ylabel("Y-axis")
plt.grid(True, linestyle='--', alpha=0.6)
plt.legend()
plt.show()

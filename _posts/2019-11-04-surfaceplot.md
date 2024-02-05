---
layout: post
categories: posts
title: Surface plot in Python
tags: [Python]
date-string: November 04, 2019
---

## Data for plotting

| Kernel Size | Learning Rate | Performance (AUROC)  |
|-----:|-----:|-----:|
|3|1e-5|0.95156|
|3|5e-5|0.95310|
|3|1e-4|0.93255|
|3|5e-4|0.92108|
|3|1e-3|0.95051|
|3|5e-3|0.44844|
|5|1e-5|0.95316|
|5|5e-5|0.95563|
|...|...|...|
|13|5e-3|0.68930|

## Source Code

``` python
import numpy as np
import matplotlib.pyplot as plt
from matplotlib import cm

num_layer = 2
list_kernel_size = [3, 3, 3, 3, 3, 3, 5, 5, ..., 13]
list_learning_rate = [1e-5, 5e-5, 1e-4, 5e-4, 1e-3, 5e-3, 1e-5, 5e-5, ..., 5e-3]
list_auroc = [0.95156, 0.95310, 0.93255, 0.92108, 0.95051, 0.44844, 0.95316, 0.95563, ..., 0.68930]

unique_kernel_size, unique_learning_rate = \
  list(set(list_kernel_size)), list(set(list_learning_rate))
num_kernel, num_learng_rate = \
  len(unique_kernel_size), len(unique_learning_rate)


perform_matrix = np.ones((num_kernel, num_learng_rate))
for y in range(num_kernel):
    for x in range(num_learng_rate):
        perform_matrix[y, x] = list_auroc[(y*num_layer)+x]

fig = plt.figure()
ax = fig.gca(projection='3d')
X = np.arange(0, num_kernel, 1)
Y = np.arange(0, num_learng_rate, 1)
X, Y = np.meshgrid(X, Y)
surf = ax.plot_surface(X=X, Y=Y, Z=perform_matrix, \
  cmap=cm.viridis, linewidth=1, antialiased=True, vmin=0, vmax=1)

list_kernel_size.insert(0, list_kernel_size[0]-abs(list_kernel_size[0]-list_kernel_size[1]))
list_learning_rate.insert(0, list_learning_rate[0]-abs(list_learning_rate[0]-list_learning_rate[1]))
ax.set_xticklabels(list_kernel_size)
ax.set_yticklabels(list_learning_rate)

ax.set_xlabel("Kernel Size", labelpad=10)
ax.set_ylabel("Learning Rate", labelpad=10)
ax.set_zlabel("AUROC", labelpad=10)

ax.text(0, 0, 0, "%d-Block Neural Network\n(2 conv-layer/block)" %(num_layer), color='black')

ax.set_zlim(0, 1)
fig.colorbar(surf, shrink=0.5, aspect=10)

plt.tight_layout()
```

## Results

<div align="center">
  <img src="/images/2019-11-04/surface-roc-vae-lay0.png" width="250">
  <img src="/images/2019-11-04/surface-roc-vae-lay1.png" width="250">
  <img src="/images/2019-11-04/surface-roc-vae-lay2.png" width="250">
  <br>
  <img src="/images/2019-11-04/surface-prc-vae-lay0.png" width="250">
  <img src="/images/2019-11-04/surface-prc-vae-lay1.png" width="250">
  <img src="/images/2019-11-04/surface-prc-vae-lay2.png" width="250">
</div>

## Reference
<a href="https://matplotlib.org/mpl_toolkits/mplot3d/tutorial.html">Matplotlib</a>

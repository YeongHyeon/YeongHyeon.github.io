---
layout: post
categories: posts
title: Make Transparent Image in Python
tags: [Python]
date-string: APRIL 21, 2020
---

## Source Code
``` python
import numpy as np
import matplotlib.pyplot as plt

canvas = np.zeros((256, 256, 4))
canvas[:128, :128, 0] = 1
canvas[:128, 128:, 1] = 1
canvas[128:, :128, 2] = 1

canvas[:128, :128, 3] = 1
canvas[:128, 128:, 3] = 1
canvas[128:, :128, 3] = 1
print(canvas, canvas.shape)

plt.imsave("sample.png", canvas, cmap='Greys')
```
## Result
<img src="/images/2020-04-21/sample.png" width="300">

## Reference
[1] https://matplotlib.org/3.1.0/tutorials/colors/colormaps.html  
[2] https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.savefig.html

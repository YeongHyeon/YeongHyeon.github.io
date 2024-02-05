---
layout: post
categories: posts
title: Spline Interpolation in Python
tags: [Python]
date-string: OCTOBER 02, 2019
---

### Source code

``` python
import numpy as np
import matplotlib.pyplot as plt
from scipy.interpolate import CubicSpline

y = np.asarray([580, 630, 740, 150, 1030, 800, 800, 600, 550, 520, 450, \
    570, 470, 480, 460, 490, 550, 580, 710, 890, 710, 90, 50, 60])
x = np.arange(24)

cs = CubicSpline(x, y) # analyze the original values
xs = np.arange(0, 23, 0.1) # new x values
ys = cs(xs) # generate new y values

plt.subplot(2,1,1)
plt.title("True Samples")
plt.plot(x, y, 'o', color="blue")
plt.plot(x, y, color="blue")

plt.subplot(2,1,2)
plt.title("Spline Interpolation")
plt.plot(x, y, 'o', color="green")
plt.plot(xs, ys, color="green")

plt.show()
```

<center>
    <div>
        <img src="/images/2019-10-02/sample-spline.png">
    </div>
</center>

### Reference
<a href="https://docs.scipy.org/doc/scipy-0.18.1/reference/generated/scipy.interpolate.CubicSpline.html">Scipy</a>

---
layout: post
categories: posts
title: Plotting Text in Matplotlib Figure
tags: [Python]
date-string: OCTOBER 02, 2019
---

### Source code

``` python
import numpy as np
import matplotlib.pyplot as plt

n1, bins1, patches1 = plt.hist(contents1, bins=100, range=(0, 1), alpha=0.5, label='Normal')
n2, bins2, patches2 = plt.hist(contents2, bins=100, range=(0, 1), alpha=0.5, label='Abnormal')

h_inter = np.sum(np.minimum(n1, n2)) / np.sum(n1)

plt.xlabel("MSE")
plt.ylabel("Number of Data")
plt.legend(loc='upper right')

xmax = max(contents1.max(), contents2.max())
plt.xlim(0, xmax)
plt.text(x=xmax*0.01, y=max(n1.max(), n2.max()), s="Histogram Intersection: %.3f" %(h_inter))

plt.show()
```

<center>
    <div>
        <img src="/images/2019-10-02/histogram-test.png">
    </div>
</center>

### Reference
<a href="https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.hist.html">Matplotlib Histogram Function</a><br>
<a href="https://matplotlib.org/3.1.1/api/_as_gen/matplotlib.pyplot.text.html">Matplotlib Text Function</a>

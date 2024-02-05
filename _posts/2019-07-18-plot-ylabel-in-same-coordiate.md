---
layout: post
categories: posts
title: Plotting ylabel in Same Coordiate
tags: [Python]
date-string: JULY 18, 2019
---

When you draw the three figures respectively by single plotting function, you may encounter a situation where the location of the y labels are different. This post deal with how to align the location of y label via tricky method.

### Source code 1 - without alignment

``` python
plt.figure(figsize=(10, 2))

plt.plot(x_vote, linewidth=1)

plt.xlabel("x label")
plt.ylabel("y label")
plt.grid(color='lightgray', linestyle='-', linewidth=1)
plt.tight_layout()

plt.show()
```

<center>
    <div>
        <img src="/images/2019-07-18/qrs_voted.png"><br>
        <img src="/images/2019-07-18/qrs_lead_i.png"><br>
        <img src="/images/2019-07-18/qrs_lead_avr.png">
    </div>
</center>

### Source code 2 - with alignment

``` python
plt.figure(figsize=(10, 2))
ax1 = plt.subplot(1,1,1)

plt.plot(x_vote, linewidth=1)

ax1.set_xlabel("x label")
ax1.set_ylabel("y label", x=0)
ax1.yaxis.set_label_coords(-0.1,0.5)
plt.grid(color='lightgray', linestyle='-', linewidth=1)
plt.tight_layout()

plt.show()
```

<center>
    <div>
        <img src="/images/2019-07-18/align_qrs_voted.png"><br>
        <img src="/images/2019-07-18/align_qrs_lead_i.png"><br>
        <img src="/images/2019-07-18/align_qrs_lead_avr.png">
    </div>
</center>

### Reference
<a href="https://pythonmatplotlibtips.blogspot.com/2017/10/how-to-arrange-two-ylabels-using-python.html">Python Matplotlib Tips</a><br>
Preprocessing Method for Performance Enhancement in CNN-based STEMI Detection from 12-lead ECG <a href="https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8771175">[pdf]</a>

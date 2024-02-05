---
layout: post
categories: posts
title: Plotting radar chart in Python
tags: [Python]
date-string: JUNE 08, 2019
---

This post provides the sample source code for generating <strong>Radar Plot</strong>.

### Step 1. Define the data

Before plotting the data, you should prepare the dataset first.
The list of class names and data for each category are required.
The dimension of the class list and data must be the same.

``` python
classes = ['A','B','C','D','E','F','G','H','I']
data1 = [3.00, 0.00, 2.00, 1.00, 1.00, 1.00, 1.00, 1.00, 1.00]
data2 = [1.00, 1.00, 1.00, 1.00, 1.00, 3.00, 0.00, 2.00, 1.00]
```

### Step 2. Make a canvas

Then, you need a canvas to present the data.
Canvas shape is circle and it has reference lines for each class.
The reference line is made by the angle (360 / # of classes).

``` python
N = len(classes)
angles = [n / float(N) * 2 * pi for n in range(N)]
angles += angles[:1]
```

### Step 3. Present the data

Finally, you can present the data.

``` python
plt.clf()
ax = plt.subplot(polar=True)
ax.set_theta_offset(pi / 2)
ax.set_theta_direction(-1)

plt.xticks(angles[:-1], classes)

ax.set_rlabel_position(0)
plt.yticks([1, 2, 3], [1, 2, 3], color="grey", size=7)
plt.ylim(0, 3)

data1 += data1[:1]
ax.plot(angles, data1, 'magenta')
ax.fill(angles, data1, facecolor='magenta', alpha=0.3)

data2 += data2[:1]
ax.plot(angles, data2, 'cyan')
ax.fill(angles, data2, facecolor='cyan', alpha=0.3)

legends = ('Label A', 'Label B')
ax.legend(legends, loc=(0.9, .95),  labelspacing=0.1, fontsize='small')

plt.show()
```

If you want to present more than 2 categories, call the following python commands iteratively.

``` python
{data} += {data}[:1]
ax.plot({angles}, {data}, {color})
ax.fill({angles}, {data}, facecolor={color}, alpha={alpha})
```

### Step 4. Confirm the result

The above command will produce the following results.
You can use your own data for showing after this moment!

<center>
    <div>
        <img src="/images/2019-06-08/sample.png">
    </div>
</center>

### Full source code

``` python
classes = ['A','B','C','D','E','F','G','H','I']
data1 = [3.00, 0.00, 2.00, 1.00, 1.00, 1.00, 1.00, 1.00, 1.00]
data2 = [1.00, 1.00, 1.00, 1.00, 1.00, 3.00, 0.00, 2.00, 1.00]

N = len(classes)
angles = [n / float(N) * 2 * pi for n in range(N)]
angles += angles[:1]

plt.clf()
ax = plt.subplot(polar=True)
ax.set_theta_offset(pi / 2)
ax.set_theta_direction(-1)

plt.xticks(angles[:-1], classes)

ax.set_rlabel_position(0)
plt.yticks([1, 2, 3], [1, 2, 3], color="grey", size=7)
plt.ylim(0, 3)

data1 += data1[:1]
ax.plot(angles, data1, 'magenta')
ax.fill(angles, data1, facecolor='magenta', alpha=0.3)

data2 += data2[:1]
ax.plot(angles, data2, 'cyan')
ax.fill(angles, data2, facecolor='cyan', alpha=0.3)

legends = ('Label A', 'Label B')
ax.legend(legends, loc=(0.9, .95),  labelspacing=0.1, fontsize='small')

plt.show()
```

### Reference
<a href="https://matplotlib.org/gallery/api/radar_chart.html">Matplotlib</a><br>
<a href="https://python-graph-gallery.com/391-radar-chart-with-several-individuals/">The python graph gallery</a>

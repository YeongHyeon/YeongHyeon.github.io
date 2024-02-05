---
layout: post
categories: posts
title: Activate virtualenv in jupyter notebook
tags: [Python]
date-string: JUNE 09, 2020
---

### Create as a Jupyter Kernel
``` sh
source venv/bin/activate
python -m ipykernel install --user --name={kernel_name}
```

### Confirm Jupyter Kernel list
``` sh
$jupyter kernelspec list
Available kernels:
  {kernel_name}     /home/{user}/.local/share/jupyter/kernels/{kernel_name}
  python3.6    /home/{user}/jupyter/kernels/python3.6
  python3.7    /home/{user}/jupyter/kernels/python3.7
  python3.8    /home/{user}/jupyter/kernels/python3.8
```

### Remove Jupyter Kernel
``` sh
$jupyter kernelspec uninstall {kernel_name}
```

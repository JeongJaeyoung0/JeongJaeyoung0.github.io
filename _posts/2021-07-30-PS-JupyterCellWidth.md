---
layout: post
title: "[Setting] jupyter 셀 너비 조정"
subtitle: "JupyterCellWidth"
categories: python
tags: setting
comments: true
---

# jupyter 셀 너비 조정

* * *

```python
from IPython.core.display import display, HTML
display(HTML("<style>.container { width: 98% !important; }</style>"))
```
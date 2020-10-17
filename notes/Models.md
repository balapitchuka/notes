---
title: Models
tags: [Import-b418]
created: '2019-11-24T05:21:40.518Z'
modified: '2020-10-17T20:06:47.891Z'
---

## Models
Recommended ordering for models in django:
```python

* choices
* database fields
* custom manager attributes
* Meta
* def __str__()
* def save()
* def get_absolute_url()
* custom methods
```

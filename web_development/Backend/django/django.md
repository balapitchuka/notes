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

## Django Rest Framework

### APIView (User When need of full control over the logic):
 - Gives more control over the logic.
 - Perfect for implementing complex logic.


# Spark


## Resilient Distributed Dataset (RDD)
- RDD is a data abstraction over the distributed collection
- RDDs are immutable; therefore, changing the RDD is impossible

RDD Creation
- An RDD is created using various functions defined in the SparkContext class. 
- One important method for creating an RDD is parallelize()


Operations On RDD
- transformation
- action

### Transformation
- Transformation on an RDD returns another RDD
- We know that RDDs are immutable; therefore, changing the RDD is impossible. Hence transformations always return another RDD.
- Transformations are lazy.
- Transformation is lazy because whenever a transformation is applied to an RDD, that operation is not applied to the data at the same time. Instead, PySpark notes the operation request, but all the transformations are applied when the first action is called.


### Action
- Actions are eagerly evaluated.

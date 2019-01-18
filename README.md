# Predicting Churn - Apache Spark
*Predicting Churn from user's activity data*

## Dependencies
- Python 3.6.3
- PySpark 2.3.2
- Pandas 0.20.3

## Motivation
I am always eager to learn new frameworks and expand my capabilities, so when I heard about the possibility of a project utilized Apache Spark and Hadoop I was already very intrigued. Having learned the basics of Apache Spark's PySpark API, there is no better way of displaying machine learning prowess than in a big data context. This project revolves around a key business issue that many firms face; *How can we know which customers want to leave, and how can our marketing department target them?* 
Business applications are what excites me the most about Data Science. Proving that I can glean valuable insights from corporate-sized data sources would prove to me that i can say **Big Data** as more than just a buzzword.

## Repository
   
    .
    ├── 
    │   ├── Sparkify.ipynb            # initial development
    │   |
    │   └── market_cap_fill.csv    # CSV file to fill Null market capitalisation data
    │  
    └── ...
## Summary

## Acknowledgements
 - [PySpark Window Functions](https://databricks.com/blog/2015/07/15/introducing-window-functions-in-spark-sql.html)
 - Udacity DSND Apache Spark Lesson
 - [PySpark Documentation](https://spark.apache.org/docs/latest/api/python/index.html)
 - [Calculating Differences Between Rows](https://www.arundhaj.com/blog/calculate-difference-with-previous-row-in-pyspark.html)
 - [PySpark ML Package](http://spark.apache.org/docs/2.4.0/api/python/pyspark.ml.html)
 - [Converting rows to Vector type](https://stackoverflow.com/questions/46791302/pyspark-how-do-i-convert-rows-to-vectors)
 - [What is Apache Spark persistence](https://jaceklaskowski.gitbooks.io/mastering-apache-spark/spark-rdd-caching.html)
 - [PySpark ML vs PySpark MLLib](https://www.quora.com/Why-are-there-two-ML-implementations-in-Spark-ML-and-MLlib-and-what-are-their-different-features)
 - [ROC vs PR Metrics](https://www.kaggle.com/general/7517)
 - [Choosing Scalers](https://scikit-learn.org/stable/auto_examples/preprocessing/plot_all_scaling.html)
 - [Extending Transformer Class](https://stackoverflow.com/questions/32331848/create-a-custom-transformer-in-pyspark-ml)

Reqs:
Student must have a Github repository of their project. The repository must have a README.md file that communicates the libraries used, the motivation for the project, the files in the repository with a small description of each, a summary of the results of the analysis, and necessary acknowledgements. If the student submits a web app rather than a blog post, then the Project Definition, Analysis, and Conclusion should be included in the README file, or in their Jupyter Notebook. Students should not use another student's code to complete the project, but they may use other references on the web including StackOverflow and Kaggle to complete the project.

# Errors Encountered
```
'StructField' object has no attribute '_get_object_id'
Traceback (most recent call last):
  File "<stdin>", line 195, in custom_evaluation
  File "/usr/lib/spark/python/lib/pyspark.zip/pyspark/mllib/evaluation.py", line 204, in __init__
    StructField("label", DoubleType(), nullable=False)]))
  File "/usr/lib/spark/python/lib/pyspark.zip/pyspark/sql/context.py", line 307, in createDataFrame
    return self.sparkSession.createDataFrame(data, schema, samplingRatio, verifySchema)
  File "/usr/lib/spark/python/lib/py4j-0.10.7-src.zip/py4j/java_gateway.py", line 1248, in __call__
    args_command, temp_args = self._build_args(*args)
  File "/usr/lib/spark/python/lib/py4j-0.10.7-src.zip/py4j/java_gateway.py", line 1212, in _build_args
    (new_args, temp_args) = self._get_args(args)
  File "/usr/lib/spark/python/lib/py4j-0.10.7-src.zip/py4j/java_gateway.py", line 1199, in _get_args
    temp_arg = converter.convert(arg, self.gateway_client)
  File "/usr/lib/spark/python/lib/py4j-0.10.7-src.zip/py4j/java_collections.py", line 501, in convert
    java_list.add(element)
  File "/usr/lib/spark/python/lib/py4j-0.10.7-src.zip/py4j/java_gateway.py", line 1248, in __call__
    args_command, temp_args = self._build_args(*args)
  File "/usr/lib/spark/python/lib/py4j-0.10.7-src.zip/py4j/java_gateway.py", line 1218, in _build_args
    [get_command_part(arg, self.pool) for arg in new_args])
  File "/usr/lib/spark/python/lib/py4j-0.10.7-src.zip/py4j/protocol.py", line 298, in get_command_part
    command_part = REFERENCE_TYPE + parameter._get_object_id()
AttributeError: 'StructField' object has no attribute '_get_object_id'
```

- score of 1.0 for pr_auc, and roc_auc - double check
- didnt work with multi class metrics even though it did in local jupyter


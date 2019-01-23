# Predicting Churn - Apache Spark
*Predicting Churn from user click-level data with distributed computation*

### [Published Write Up on Medium](https://medium.com/@mati.kucz95/predicting-user-churn-apache-spark-8577d433ff8c)

## Dependencies
- Python 3.6.3
- PySpark 2.3.2
- Pandas 0.20.3
> - Matplotlib 3.0.2
> - seaborn 0.9.0

## Motivation
I am always eager to learn new frameworks and expand my capabilities, so when I heard about the possibility of a project utilized Apache Spark and Hadoop I was already very intrigued. Having learned the basics of Apache Spark's PySpark API, there is no better way of displaying machine learning prowess than in a big data context. This project revolves around a key business issue that many firms face; *How can we know which customers want to leave, and how can our marketing department target them?* 
Business applications are what excites me the most about Data Science. Proving that I can glean valuable insights from corporate-sized data sources would prove to me that I can say **Big Data** as more than just a buzzword.

## Repository Organization
   
    .
    ├── 
    │   ├── Sparkify.ipynb            # initial development & EDA on smaller subset of data
    │   ├── Sparkify-Viz.ipynb        # visualization of datafrom EDA and AWS
    │   ├── sparkify_full.ipynb       # AWS Implementation and final version
    │   └── sparkify_full.html        # final version of notebook in html format
    │  
    └── ...

## Summary
The final chosen model is a Random Forest classifier which was chosen due to it being the fastest model to train and generate predictions by half being twice as fast as the next fastest model. The classifier that predicted on a dataset of reduced dimensionality still managed exceptional performance. The final dataset was of reduced dimensionality through principal component analysis that explained >97% of the variance in the dataset.

The most interesting part of examining the features of the model is that it actually uses a much simpler version of the random forest classifier than the OOTB version. Instead of creating 32 decision trees that classify each instance, it only creates 10 during training, and lets the trees vote during prediction. The fact that this model did not make mistakes in validation or testing datasets suggests that it is a robust model.

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
The repository must have a README.md file that communicates the libraries used, the motivation for the project, the files in the repository with a small description of each, a summary of the results of the analysis, and necessary acknowledgement

## Errors & Exceptions Encountered
I encountered various errors when using AWS's EMR managed Hadoop framework that I could only attribute to errors in the backend and not with my code. What complicated manners was that the AWS hosted notebook would crash reasonably frequently.

The errors are listed below for future reference:
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

```
----------------------------------------
Exception happened during processing of request from ('127.0.0.1', 57960)
----------------------------------------
Traceback (most recent call last):
  File "/usr/lib64/python2.7/SocketServer.py", line 290, in _handle_request_noblock
    self.process_request(request, client_address)
  File "/usr/lib64/python2.7/SocketServer.py", line 318, in process_request
    self.finish_request(request, client_address)
  File "/usr/lib64/python2.7/SocketServer.py", line 331, in finish_request
    self.RequestHandlerClass(request, client_address, self)
  File "/usr/lib64/python2.7/SocketServer.py", line 652, in __init__
    self.handle()
  File "/usr/lib/spark/python/lib/pyspark.zip/pyspark/accumulators.py", line 266, in handle
    poll(authenticate_and_accum_updates)
  File "/usr/lib/spark/python/lib/pyspark.zip/pyspark/accumulators.py", line 241, in poll
    if func():
  File "/usr/lib/spark/python/lib/pyspark.zip/pyspark/accumulators.py", line 254, in authenticate_and_accum_updates
    received_token = self.rfile.read(len(auth_token))
TypeError: object of type 'NoneType' has no len()
```

```
Exception in thread cell_monitor-10:
Traceback (most recent call last):
  File "/opt/conda/lib/python3.6/threading.py", line 916, in _bootstrap_inner
    self.run()
  File "/opt/conda/lib/python3.6/threading.py", line 864, in run
    self._target(*self._args, **self._kwargs)
  File "/opt/conda/lib/python3.6/site-packages/awseditorssparkmonitoringwidget-1.0-py3.6.egg/awseditorssparkmonitoringwidget/cellmonitor.py", line 178, in cell_monitor
    job_binned_stages[job_id][stage_id] = all_stages[stage_id]
KeyError: 1148
```
- `BinaryClassificationEvaluator` always returned metric `areaUnderPR = 1.0` no matter the performance of the classifier
- aws notebook stopped working `Session '0' is not active`

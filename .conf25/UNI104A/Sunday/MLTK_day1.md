---
Title: Sunday MLTK focus
--- 

### Analytics workflow

1. Get Data - find historic data relevant to the problem at hand
2. Organize Data - make a workflow and set up new incoming data
3. Model & Respond - Build, Test, Optimize
<br> 
Machine Learning Use Cases

* Anomaly Detection
* Clustering
* Prediction
* Data Processing
<br>

_MLTK is getting rebranded as **Splunk AI Toolkit**_<br>

Training the model is much more resource intensive than using/applying the model. 
<br>
MLTK has a good diagram for which algorithm to choose. <br>
More models and python libraries available to control the algorithms and their behavior. 
<br>
The ONNX Models are trained in other environments and can be applied within Splunk environmnets. `MLTK 4.0.0`
<br>
`ai` command - can provide token and external LLM can be used to explain things like:

* what does a notable event look like?
* Do these user agents loook normal?
* can you summarize logs for me?

<br>

### Training Models

Train/Test split is used to assess the performance of a predictive model. Train on 70-80% and test on 20-30%. <br>
`sample` command from mltk automatically collects representative samples from the data. Event sampling is true random sampling. Use the sample command over event sampling for building the data set. <br>
Partitions are a good way to set aside different degrees of training quantity and testing quantity. <br>

<br>

`fit` pulls search results into memory, transforms the search results in memory. Prepares data: discards null, discards non-numeric with >100 distinct values, converts non-numeric into dummy binary variables, converts prepared data into a numeric matrix and runs the specified algorithm to build a model. 
<br> 
Applies the model to those search results and adds new (predicted) columns
<br>
Encodes the learned (trained) model. Saves it as a knowledge object.
<br>
Private model Knowledge Objects are a good way to run dev or building/testing of a model. 
<br>
Can bypass the nesting of private over app by using `app:model`.
<br>

### Scoring
`score` has a method called `describle` which will return a bunch of extra stuff. Skewness will tell you which tail is longer - how far one side stretches vs the other. Kurtosis will tell you if the bulk of data is to the left or to the right (left negative, right positive).
<br>
It would be cool to train models each week and then apply them ONLY IF the score improves....?
<br>





Data Science is the joining of domain expertise and data production.<br>
Can upload personal python models or ONNX format neural net algortithsm<br>
SPlunk app for data science and Deep Learning (way to build personal LLM). Turns your splunk environment into a Data Lake. Unlocks GPU support to run the algorithms. High barrier to entry w/ no ceiling.

### Splunk Specific

NLP (natural language parsing) - sentiment analysis around natural language. Tokenize, lemmenize, generalize natural language. Download the app.

<br>

`R^2` is used to assess the goodness of the fit. How well the model's predictions align wiht the actual data. Ideal score is 1, close to 0 means it is not a good model, can't be negative. 

<br>

Do not try to use Catagorical classification and regression against numerical values - does poorly.<br>
<br>

**Splunk conf Archive** app can be installed to find specific URL's on the conf archives site. 
<br>

### Clustering Algorithms

KMeans wokrs best when clusters a spherical and equally sized, 
<br>
GMeans determines number of clusters to create on its own. 
<br>
XMeans is extension of KMeans that tests whether the data in acluster would be better as two clusters. 
<br>

* can be used to identify servers that are collectively exhibiting strange behavior.

<br>

**We should try and cluster against role based endpoint data to predict Role**

<br>
Scoring can indicate the amount of overlap between clusters. +1 is good, means point is very far from any other cluster centers. 0 means there's probably overlap. -1 means it's very close to another cluster's center. 
<br>
Can ask an LLM to look at the data in each of the clusters and have it describe it to us. 
<br>

You can run robust scaler or inputer in the search bar before applying models in the experiment. You can also apply a `my_cleaning_model` to the search and then pass on the cleaned data. 
<br>

### Support Vector Machine

<br>

Finds the best boundary or Hyperplanes that separates different classes of data points as clearly as possible. 
 <br>
 Works best when you maximize distance between classes. Exaggerate differences to make bucketing the groups easier. 
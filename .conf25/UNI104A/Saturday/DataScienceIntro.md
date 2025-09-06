---
Title: Saturday Data Science
--- 

### Intro to Data Science

Data Science is the joining of domain expertise and data production.<br>
Can upload personal python models or ONNX format neural net algortithsm<br>
SPlunk app for data science and Deep Learning (way to build personal LLM). Turns your splunk environment into a Data Lake. Unlocks GPU support to run the algorithms. High barrier to entry w/ no ceiling.

### Splunk Specific

NLP (natural language parsing) - sentiment analysis around natural language. Tokenize, lemmenize, generalize natural language. Download the app.

<br>

ITSI uses states based forecast algorithm

<br>

### Data Exploration

Correlation coefficients are important, especially when comparing linear and non-linear data. 

### Commands (SPL)


`bin` command is used to group amounts of data into evenly spaced buckets

<br>

`makecontinuous` command is used to create an x-axis field continueous. where no data exists, adds empty bins, use chart or timechart to visualize the new, complete data. Good for replacing "sort" when trying to express gaps in data. Span will just show the next x value with an associated y, makecontinuous will fill in those spots with 0's. 

<br>

`fieldsummary` summary stats for all or a subset of fields in your search results - gives a "values" column. recommended to use "maxvals". is_exact expresses whether distinct_count is an estimation or an exact representation

<br>

`autoegress` **this one is good** - allows us to calculate changes over time, give's you delta. Clones field a and offsets the values by p number of events/rows. 

```
    | timechart sum(price) as sales
    | autoegress sales 
    | eval diff = sales - sales_p1
```

<br>

converting categorical fields into binary: using `| eval is_{action}=1` will give you 1 if that categorical field exists and 0 if not. `Fillnull` is used to fill in the 0's. Here action is then is broken out across various is_addtocart=1, is_purchase=0 for an `add to cart` action type.

<br>

using the rex sed mode can help you normalize the categorical data. Makes things easier to use - better way is with the NLP Text analytics command.

<br>

`cleantext` command tokenizes and normalizes text. Pass the field you want tokenized. Different options result in slower but better cleaning. Can remove stopwords (true/false), remove URLs, base word, tokenize and normalize text. 

<br>

### Grouping

Behavior based clustering is the best way to group datasets. 

<br>

`kmeans` divides the data into "l" clusters. Each data point belongs to the group who's mean it's closest to.

* range = how far each cluster can be from the mean. Gives a distortion field describing how far from the mean the data points are. Distortion is the sum of euclidean (squared) distances from all points and their centroid.
* reps = repeats of kmeans using random starting clusters (defualt 10)
* iters = number of iterations allowed, default 10,000
* t = conversion tolerance
* cnumfield = name of output field
* dt = distance metrice to use
    * cityblock can be used to compare x and y values
    * sqeuclidean is normal distance 

<br>

Use the range (k=x - y clusters) to find the point where distortion begins to even out. This is the optimal number of clusters to run.

<br>

`cluster` commmand options - breaks fields into terms, computes the vector between events

* different match options to compare fields to consider them a "match" to the cluster
* tolerance is set to .8 by default (or 80%)

<br>

### Correlations and Transactions

<br>

`associate` command options = only includes specified fields
* `supcnt` minimum number of times that reference key = reference value
* `improv` minimum entropy improvement for the target key outputted field 

<br>
Conditional entropy is the shannon entropy
<br>

`analyzefields` analyze all the numerical fields to see how well each might predict the value of a field you choose. 

<br>

`correlate` view co-occurrence between fields (not values) in a matrix format. How many times two fields values show up within the same dataset.

<br>

`score` command runs a variety of statistical functions and tests
* pearsonr : linear correlation
* spearsonr : measures a monotonic (single direction) relationship where direction of change is consistent but the rate is not. 

<br>

#### Transactions

Transaction command can be expensive to run and take awhile. Other better ways to capture transactional relationships. 
<br>

Make sure to use `maxspan` and `maxpause` as well as `maxevents`, `startswith`, `endswith` when using `transaction` command. 
<br>

**Flaregraph** is pretty awesome for trace viewing.
<br>

Example use case in PDF.

<br>

**Dollar Sign** for subsearch | return $order will prevent it from being "order=1, 2, 3, 4" to just being "1, 2, 3, 4"
<br>
 
### anomaly Detections

`anomalydetection` method determines the method used to target anamolies (Histogram, zscore, iqr, etc). Can also set pvalue and some other things. Native splunk method. Can provide fields to specifically look at. 


<br>

Can use `mark=true` to label specific values that you might transform. Transform will allow you to flag or bring up anomaly events. 

<br>

### Predict and Forecast


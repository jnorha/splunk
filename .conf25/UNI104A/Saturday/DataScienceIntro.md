---
Title: Saturday Data Science
--- 

### Intro to Data Science
<br>
Data Science is the joining of domain expertise and data production.<br>
Can upload personal python models or ONNX format neural net algortithsm<br>
SPlunk app for data science and Deep Learning (way to build personal LLM). Turns your splunk environment into a Data Lake. Unlocks GPU support to run the algorithms. High barrier to entry w/ no ceiling.

### Splunk Specific
<br>
NLP (natural language parsing) - sentiment analysis around natural language. Tokenize, lemmenize, generalize natural language. Download the app.
<br>
ITSI uses states based forecast algorithm
<br>

### Data Exploration
<br>
Correlation coefficients are important, especially when comparing linear and non-linear data. 

### Commands (SPL)
<br>
`bin` command is used to group amounts of data into evenly spaced buckets
<br>
`makecontinuous` command is used to create an x-axis field continueous. where no data exists, adds empty bins, use chart or timechart to visualize the new, complete data. Good for replacing "sort" when trying to express gaps in data. Span will just show the next x value with an associated y, makecontinuous will fill in those spots with 0's. 
<br>
`fieldsummary` summary stats for all or a subset of fields in your search results - gives a "values" column. recommended to use "maxvals". is_exact expresses whether distinct_count is an estimation or an exact representation
<br>
`autoegress` ** this one is good ** - allows us to calculate changes over time, give's you delta. Clones field a and offsets the values by p number of events/rows. 
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

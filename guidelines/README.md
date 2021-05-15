<div align="left"><img src="https://raw.githubusercontent.com/EconomicsObservatory/ECOvisualisations/main/guidelines/logos/eco-bg-dark.png" width="800"/></div>

# Economics Observatory Data Guidelines

[**Standard guidelines**](#-standard-guidelines)
| [**Format guidelines**](#-format-guidelines)

At the **Observatory**, we strive to follow current best practices to stay up to date with recent developments of the rapidly-changing world of data visualisation. We maintain a set of guidelines that we use internally for designing and maintaining our datasets - please feel free to raise an [Issue](https://github.com/EconomicsObservatory/ECOdataHUB/issues) if you have any suggestions, everyone and everything is welcome! 💙

## 🔳 Standard

We maintain a data repository updated daily that contains the data displayed on the site in a standardized, [TIDY](http://vita.had.co.nz/papers/tidy-data.pdf) format. That means that every **data point** is a *row (line)* and every **data feature** is a *column*. The *first column* is called the **index**, and it is the typcially the column, based on which each of the data points gets a unique identifier. [`pandas`](https://pandas.pydata.org/) automatically assigns this column to its index upon load, but the standard `CSV` format does not. Therefore, sometimes (especially for the case of time series data) the *index* column of datasets is a *date*. This makes `pandas` treat the *data series* as [*time series*](https://pandas.pydata.org/pandas-docs/stable/user_guide/timeseries.html).

|index |feature1  | feature2|
--- | --- | ---
|data1.index|data1.feature1|data1.feature2|
|data2.index|data2.feature1|data2.feature2|
...
|data42.index|data42.feature1|data42.feature2|
...

During the data transformation and normalization process, the *objective* is to **minimize** the **number of data columns**. This means that this format ...

|Country |2019  | 2020| 2021|
--- | --- | --- | ---
|Austria|42|13|69
|Belgium|75|12|77

... should be converted to this:

|Country |Year  | Value|
--- | --- | ---
|Austria|2019|42|
|Austria|2020|13|
|Austria|2021|69|
|Belgium|2019|75|
|Belgium|2020|12|
|Belgium|2021|77|

This operation is typically called a [`stack`](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.stack.html) in `pandas` and a [`pivot`](https://support.microsoft.com/en-us/office/create-a-pivottable-to-analyze-worksheet-data-a9a84538-bfe9-40a9-a8e9-f99134456576) in [Excel](https://www.microsoft.com/en-us/microsoft-365/excel)/[PowerBI](http://powerbi.com/).  
Then, the following hold true:

- Every row (line) contains a unique data point
- Each data point is `n`-dimensional (caution! see below), where `n` equals the number of *columns*, i.e. each data points has `n` *features*.
- The dataset has `m` elements, where `m` equals the number of *rows*
- Likewise, the dataset can be represented as an `n` by `m` matrix
- Columns headers are called *features*. Sometimes they are also called *headers*, *(data) attributes* or even *(data) properties*. The latter comes from the fact that when the data is not in a table format, it is often in a **standardized `JSON` format**, like this:
  
  ```json
  [
    {"index":data1.index,"feature1":data1.feature1,"feature2":data1.feature2},
    {"index":data2.index,"feature1":data2.feature1,"feature2":data2.feature2},
    ...,
    {"index":data42.index,"feature1":data42.feature1,"feature2":data42.feature2},
    ...
  ]
  ```
  - In `JSON/JavaScript` lingo, this would be called a `JavaScript` [Object](https://www.w3schools.com/js/js_objects.asp) [Array](https://www.w3schools.com/js/js_arrays.asp), where `index`, `feature1` and `feature2` are called *properties*.
  - In `python`, this would be called a [list](https://www.w3schools.com/python/python_lists.asp) of [dictionaries](https://www.w3schools.com/python/python_dictionaries.asp), where `index`, `feature1` and `feature2` are called *keys*.
  - In both cases, `data1.index, data1.feature1, ...` are called *values*.
  - Likewise, in `JSON/JavaScript` the dataset can be represented as *Array* of length `m`, with each element being an *Object* containing `n` *property-value* pairs.
  - Likewise, in `python` the dataset can be represented as *list* of length `m`, with each element being an *dictionary* containing `n` *key-value* pairs. 
- The type of the *features* can be **field** or **tag** ⬅ this is [**InfluxDB**](https://www.influxdata.com/products/influxdb/) [lingo](https://docs.influxdata.com/influxdb/cloud/query-data/flux/query-fields/). You might see them [referred to](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/concepts/fact-and-dimension-tables) as *fact* and *dimension* tables.
  - A **fact** is a *measurable* data value for the respective data point in each row. You might simply refer to this as a *(quantitative or continuous) value*.
  - A **dimension** is a *descriptive* tag for the respective data point in each row. You might refer to this as a *tag*, a *label* or a *nominal value*.
  - Sometimes the *fact* columns of the data table (*fact table*) is simply called *data*, and the *dimension* columns (*dimension table*) is called *metadata*.
  - Somewhat incorrectly and confusingly, *dimension* is also used colloquially to refer to a *feature* in general. This comes from the fact that the *size* of the data `=` _nr of columns_ `x` _nr of rows_. This could allude to the fact that the data is `n` dimensional, where `n` equals the number of *columns*, i.e. the number of *data features*.
  - To avoid confusion, we prefer to use the **column/feature** ➡ **field** and **tag** nomenclature. 

## 💠 Format guidelines

- *Time series* datasets have *dates* in the `yyyy-mm-dd` format as their index and are sorted in *increasing* order.
- *Data series* datasets have an *increasing numerical range index* starting from `0`.
- `*_mirror` type datasets are local mirrors of external datasets and typically retain the format of their respective original sources.
- Column names are typically self-explanatory, unless otherwise noted in the _Comments_ column.

<hr>

## Make sure you check out the 📐[Visualisation Guidelines ↗](https://github.com/EconomicsObservatory/ECOvisualisations/tree/main/guidelines) too!

Updated on 📆 2021-05-03 by [Dénes Csala](https://csaladen.es)

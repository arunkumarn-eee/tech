---
title: 'Pandas Made Simple: Analyze Real-World Data Like a Pro'
description: A practical guide with hands-on examples for everyday use.
authors:
  -
    name: Arun kumar N
    avatar: ../../assets/image/favicon.png
    description: Creator
# update_date : 2025-04-09
published_date : 2025-06-20
# prefer light image
banner_image : assets/blogs/python/Pandas_python_made_simple_dark.png
tags:
  - pandas
hide:
  - navigation
draft: false
---


![Pandas Python Made Simple](../../../assets/blogs/python/Pandas_python_made_simple_dark.png#only-dark)
![Pandas Python Made Simple](../../../assets/blogs/python/Pandas_python_made_simple_light.png#only-light)

Pandas for Data Analysis

???+ Abstract "Table of Contents"

    [TOC]


## Why Pandas ?


## Time line

![time line](./images/timeline_pandas.png#only-dark)
![time line](./images/timeline_pandas_light.png#only-light)

Pandas 

## Installation


=== "rye"
    ```bash

    $ rye init --virtual
    $ rye add pandas

    ```

=== "uv"
    ```bash

    $ uv init .
    $ uv pip install pandas

    ```

=== "pip"
    ```bash
    $ pip install pandas

    ```

=== "conda :simple-anaconda:"
    ```ps

    $ conda install pandas

    ```


### Dependencies 

```mermaid
---
config:
  sankey:
    showValues: false
---

sankey-beta

%% source,target,value
Numpy, required, 30
python-dateutil, required, 30
pytz, required, 30
tzdata, required, 30



Visualization, matplotlib,  10
Visualization, Jinja2,  10
Visualization, tabulate,  10
optional, Visualization, 30

Performance, numexpr,  10
Performance, bottleneck,  10
Performance, numba,  10
optional, Performance, 30

Computation, Scipy,  10
Computation, xarray,  10
optional, Computation, 20

Excel Files, xlrd, 10
Excel Files, xlsxwriter, 10
Excel Files, openpyxl, 10
Excel Files, pyxlsb, 10
Excel Files, python-calamine, 10
optional, Excel Files , 50

BeautifulSoup4, HTML Files, 10
html5lib, HTML Files, 10
lxml, HTML Files, 10
HTML Files, optional, 30

lxml, XML, 10
XML, optional, 10

SQLAlchemy, PostgresSQL, 10
psycopg2, PostgresSQL, 10
adbc-driver-postgresql, PostgresSQL, 10
PostgresSQL, DataBase, 30

SQLAlchemy,MySQL,10
pymysql,MySQL,10
MySQL, DataBase, 20

SQLAlchemy, SQLite,10
adbc-driver-sqlite, SQLite, 10
SQLite, DataBase, 20

DataBase, optional, 70

required, pandas , 120
pandas, optional, 120

```

### Required Dependencies

The list of packages gets installed along with Pandas for its operations.

```mermaid
kanban
required[Required Dependency]
  numpy[Numpy]@{ticket: Version, assigned: '1.224' }
  dateutil[python-dateutil]@{ticket: Version, assigned: '2.8.2' }
  pytz[pytz]@{ticket: Version, assigned: '2020.1' }
  tzdata[tzdatal]@{ticket: Version, assigned: '2022.7' }

```

### Optional Dependencies

It has many optional dependencies, to improvise the performance, visualization, accessing particular API's or methods.

#### Performance

While working with large files, it is advised to install performance dependencies for pandas using

```mermaid
kanban
  [Performance]
    [numexpr]
    [bottleneck]
    [numba]

```


=== "rye"
    ```bash
    $ rye add pandas[performance]
    ```

=== "uv"
    ```bash
    $ uv pip install pandas[performance]

    ```

=== "pip"
    ```bash
    $ pip install pandas[performance]
    ```

=== "conda :simple-anaconda:"
    ```ps
    $ conda install pandas[performance]
    ```

---

#### Visualization : Plotting & Formatting

For plotting graph using pandas api, optional dependency `matplotlib` can be installed along with pandas using pip-extra [`plot`] for visualization and for markdown and DataFrame styles using `output-formatting`.


```mermaid
kanban
  [Plot]
    [matplotlib]

  [Output-formatting]
    [Jinja2]
    [tabulate]
 
```

=== "rye"
    ```bash
    $ rye add pandas[plot, output-formatting]
    ```

=== "uv"
    ```bash
    $ uv pip install pandas[plot, output-formatting]
    ```

=== "pip"
    ```bash
    $ pip install pandas[plot, output-formatting]
    ```

=== "conda :simple-anaconda:"
    ```ps
    $ conda install pandas[plot, output-formatting]
    ```

---

#### Computation

For N-dimensional data and statistical functions

```mermaid
kanban
  [Computation]
    [Scipy]
    [xarray]  

```


=== "rye"
    ```bash
    $ rye add pandas[computation]
    ```

=== "uv"
    ```bash
    $ uv pip install pandas[computation]

    ```

=== "pip"
    ```bash
    $ pip install pandas[computation]
    ```

=== "conda :simple-anaconda:"
    ```ps
    $ conda install pandas[computation]
    ```

---

#### Excel files

To work with excel files, it necessary to install optional dependencies along with pandas.

```mermaid
kanban
  [Excel Files]
    [xlrd]@{ticket: reading Excel}
    [xlsxwriter]@{ticket: Writing Excel}
    [openpyxl]@{ticket: read/write xlsx files}
    [pyxlsb]@{ticket: reading xlsb files}
    [python-calamine]@{ticket: Reading for xls/xlsx/xlsb/ods files}
  
  [HTML Files]
    [BeautifulSoup4]@{ticket: requires lxml or html5lib}
    [html5lib]
    [lxml]
  
  [XML]
    [lxml]

```

=== "rye"
    ```bash
    $ rye add pandas[excel]
    ```

=== "uv"
    ```bash
    $ uv pip install pandas[excel]

    ```

=== "pip"
    ```bash
    $ pip install pandas[excel]
    ```

=== "conda :simple-anaconda:"
    ```ps
    $ conda install pandas[excel]
    ```

#### HTML & XML file

=== "rye"
    ```bash
    $ rye add pandas[html]
    ```

=== "uv"
    ```bash
    $ uv pip install pandas[html]

    ```

=== "pip"
    ```bash
    $ pip install pandas[html]
    ```

=== "conda :simple-anaconda:"
    ```ps
    $ conda install pandas[html]
    ```

---

#### SQL databases

To access data from database files, it necessary to install optional dependencies along with pandas.

```mermaid
kanban
  [PostgresSQL]
    [SQLAlchemy]@{assigned: 'postgresql'}
    [psycopg2]@{assigned: 'postgresql'}
    [adbc-driver-postgresql]@{assigned: 'postgresql'}

  [MySQL]
    [SQLAlchemy]@{assigned: 'mysql'}
    [pymysql]@{assigned: 'mysql'}
  
  [SQLite]
    [SQLAlchemy]@{assigned: 'sql-other'}
    [adbc-driver-sqlite]@{assigned: 'sql-other'}
```

=== "rye"
    ```bash
    $ rye add pandas[postgresql, mysql, sql-other]
    ```

=== "uv"
    ```bash
    $ uv pip install pandas[postgresql, mysql, sql-other]

    ```

=== "pip"
    ```bash
    $ pip install pandas[postgresql, mysql, sql-other]
    ```

=== "conda :simple-anaconda:"
    ```ps
    $ conda install pandas[postgresql, mysql, sql-other]
    ```

---



!!! info
    All optional dependencies can be installed with
    
    === "rye"
        ```bash
        $ rye add pandas[all]
        ```

    === "uv"
        ```bash
        $ uv pip install pandas[all]

        ```

    === "pip"
        ```bash
        $ pip install pandas[all]
        ```

    === "conda :simple-anaconda:"
        ```ps
        $ conda install pandas[all]
        ```
    
    ---
    
    - Pandas is part of major Python distributions like Anaconda, ActiveState Python, WinPython etc.
    - Install from GitHub repository. [Pandas : Click here](https://github.com/pandas-dev/pandas)
    - For detailed information on Pandas installation, check out the [official link](https://pandas.pydata.org/docs/getting_started/install.html)


---

## Data Structure


1. Series
2. DataFrame

### Creating Pandas DataStructure

Pandas data structure comprises of rows and columns. Column represents the series data and Rows are represented by Index.

- A single column data structure is known as **Series**.
- Multi-column data structure is known as **DataFrame**.

![df](./images/df.png)

Pandas DataFrame can be created using python objects, flat files, databases, API requests etc. In this article will go through python objects and CSV file with some examples. The complete list of supported sources can be [found here](https://pandas.pydata.org/pandas-docs/stable/user_guide/io.html){target="_blank"}. 

### Series

- Creating Series using python objects.
  - list.
  - tuple.
  - dictionary.

#### Using Python **List**

```python

import pandas as pd

even = [2, 4, 6, 8, 10, 12]

series_data = pd.Series(even)
print(series_data)

```

OUTPUT: ![output](./images/output_1.png)

From the output we can draw out.

- Index of the series data is same as the index of the list data.
- `dtype` indicates the data type of the series.

We can name the series or column.
```python
series_data.name = "even"
print(series_data.info)
```

OUTPUT: ![output](./images/output_2.png)

#### Using Python **Dictionary**

```python
import pandas as pd

student = {'name':"Kishore", 
            'age':20, 
            'place':"Bengaluru", 
            'email':"kishore@email.com",}
student_data = pd.Series(student)
print(student_data)
```
OUTPUT: ![output](./images/output_3.png)

- Index of the series data is same as the key of the dictionary data.
- `dtype` indicates the data type of the series.

### DataFrame

Similar to pandas Series, DataFrame can be created using python objects.

#### Using Python **List**

```python
import pandas as pd

students = [
    ['Kishore', 'Bengaluru'], # use list or tuple
    ['Vikram',  'Hyderabad'],
    ['Vinay',  'Chennai'],
    ['Adithya',  'Mumbai'],
    ['Kumar',  'Kochi'],
]

students_df = pd.DataFrame(students)
print(students_df)
```

OUTPUT: ![output](./images/output_4.png)

- `0,1,2,3,4` indicates the `index`
- `0` and `1` column indicates the Series. 
- More than one Series data makes it a DataFrame.


#### Using Python **Dictionary**

```python
import pandas as pd

students = {
    "name": ['Kishore', 'Vikram', 'Vinay', 'Adithya', 'Kumar'],
    "place": ['Bengaluru', 'Hyderabad', 'Chennai', 'Mumbai', 'Kochi']
}

students_df = pd.DataFrame(students)
print(students_df)
```

OUTPUT: ![output](./images/output_5.png)

- `0,1,2,3,4` indicates the `index`
- `name` and `place` column indicates the Series. 
- More than one Series data makes it a DataFrame.

## Reading the files

For this article, will use the `Major Commercial Crops of India` downloaded from the [RBI Database](https://data.rbi.org.in/#/dbie/home){target="_blank"}

To follow along with this article download the [crop data](./attachments/clean_data_crop.csv){target="_blank"}.

[CSV Crop Data :material-file-download:](./attachments/clean_data_crop.csv){.md-button .md-button--primary}


!!! tip "Launch in Binder |  No configuration or downloads required"
    No need to worry about configuring your system with libraries and data.

    You can run it online using binder. 
    
    [![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/skilldisk/Python-Pandas-for-Real-World-Data-Data-Wrangling-Made-Easy/main?urlpath=%2Fdoc%2Ftree%2Fjune_22.ipynb)

### CSV files

```python
import pandas as pd

crop_info = pd.read_csv('./data/clean_data_crop.csv')

print(crop_info)
```

OUTPUT: ![output](./images/output_6.png)


### Excel files

### JSON files

## Inspecting



## Extracting Subsets


## Summary Statics


## Data Cleaning




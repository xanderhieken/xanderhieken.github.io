---
title: "Spark Data Warehouse"
date: 2020-03-23
tags:
 - Python
 - Spark
 - NoSQL
 - Jupyter Notebook
 - SQL
 - Data Warehousing
excerpt: "How to Create a Data Warehouse in Spark"
header:
  overlay_image: "/assets/DataWarehouseBackground.jpg"
  overlay_filter: 0.3 # same as adding an opacity of 0.3 to a black background
  teaser: "/assets/DataWarehouseBackground.jpg"
  actions:
    - label: "Go to GitHub Repository"
      url: "https://github.com/xanderhieken/SparkDataWarehouse"
---
# Creating a Data Warehouse in Spark

**This notebook illustrates how to turn directories full of CSV files into a data warehouse that can be queried with Spark SQL**

First, we will configure Spark to run optimally on your system.

Then, we will take matching datasets from 2017 and 2018, read them into Spark, and join them to create a data warehouse of Spark SQL tables containing data from both years combined.

Finally, we will examine the tables and demonstrate how to run some Spark SQL queries on them.

## Prerequisites

If you haven't installed and configured Apache Spark in your environment, I would highly recommend following [this guide](https://spark.apache.org/docs/latest/index.html) to get started.
This notebook uses PySpark, which allows Spark to be run interactively in a Python interpreter.

### Installing Dependencies

The packages necessary to run this notebook are provided in requirements.txt which can be installed using the following command in the terminal:

*Make sure requirements.txt is in the terminal's current directory*

```py
pip install -r requirements.txt
```

## Running the Notebook

If you are downloading everything to run locally, there folders labeled "2017" and "2018" in this repository that need to be placed in the same directory as the notebook to maintain consistent filepaths.

The following line of code in the first cell is where you will need to enter the filepath where you want your new data warehouse to be stored:
*I would set this to an empty folder to keep everything tidy*

```py
warehouse_dir = 'PATH/TO/YOUR/DATA/WAREHOUSE'
```

**Spark's performance depends greatly on the configuration settings you choose and the resources available on your machine, so you may need to adjust the next few lines accordingly** 

*I ran everything on a 2018 Macbook Pro with a 6-core processor and 32 GB of RAM*

I like to allocate 25% of the driver memory to Spark's executors, but this is just a personal preference on my system.

You can adjust the "4g" (for 4 GB) to different amounts to see how it affects performance.

```py
.config("spark.executor.memory", "4g")
```

It is recommended to allocate no more than 75% of your system's RAM to the driver.

The data used in this notebook is only about 35 MB, so it should be small enough to run on anyone's system, so you can adjust the "16g" (for 16 GB) to different values to see how it affects performance.

```py
.config("spark.driver.memory", "16g")
```

If your system has up to 32 GB of RAM, the following line of code compresses memory pointers in the Java Virtual Machine from 8 bytes to 4 bytes each.

This will drastically increase Spark's performance because it uses **a lot** of pointers.

If your system has over 32 GB of RAM, you will need to delete this line before running the cell or else it won't run.

```py
.config("spark.driver.extraJavaOptions", "-XX:+UseCompressedOops")
```

### Data Format

All of the data in the 2017 and 2018 folders are in CSV format.

After running the code, the data warehouse will contain a bunch of folders full of Parquet files using Snappy compression. Snappy Parquet files can be read and manipulated in Spark **much** faster than CSV files, so all future reads and writes will be noticeably faster.

## Author

**Xander Hieken**


## Acknowledgments

* Bill Chambers & Matei Zaharia's book [Spark: The Definitive Guide](https://www.oreilly.com/library/view/spark-the-definitive/9781491912201/)

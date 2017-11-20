---
author: "Andrie de Vries"
linktitle: "plumber-on-azure"
title: Using the plumber package to expose services on the Azure DSVM
tags: 
 - "R"
 - "Azure"
date: "2017-09-12"
description: "The `plumber` package allows you to easily publish R scripts as web services. In this post I explain how to use this package on the Azure data science virtual machine."
featured: ""
featuredalt: ""
featuredpath: ""
type: "post"
---

The [`plumber`](https://www.rplumber.io/) package is an "An API Generator for R", written by [Jeff Allen](https://github.com/trestletech).  The package makes it possible to turn any R script into a web service, and you can then call this web service from any language that can make REST calls.

The [Azure Data Science Virtual Machine](https://azure.microsoft.com/en-us/services/virtual-machines/data-science-virtual-machines/) (DSVM) is a hosted virtual machine with pre-installed data science utilities.

Usually it is very easy to deploy your plumber APIs, but my first attempt at doing this on the Azure DSVM failed.

After some experimentation, I discovered that you must do:

* Assign a port that is not in use. The default is port 8000, but this is already used by Jupyter Hub.  Try port 8888, for example.
* Listen on all ports (`host = "0.0.0.0"`). The default is to listen only on localhost.
* Remember to open the port 8888 in the Azure portal.

This code works for me:

```r
library(plumber)
r <- plumb("plumber/test-plumber.R")
r$run(port = 8888, host = "0.0.0.0")
```

To enable this as a service on the Azure DSVM, use the instructions for [hosting](https://www.rplumber.io/docs/hosting.html) using [Docker](https://www.rplumber.io/docs/hosting.html#docker) or [pm2](https://www.rplumber.io/docs/hosting.html#pm2).

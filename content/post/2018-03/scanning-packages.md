---
author: "Andrie de Vries"
title: "Scanning a project folder for R packages to install"
type: "post"
draft: "false"
date: "2018-04-19"
categories: 
  - "R"
tags:
  - "packrat"
  - "scanning packages"
summary: "How to scan a project folder for R packages to install"
thumbnail: ""
---
  
Several tools attempt to address the package installation problem, including `packrat` and `checkpoint`.  Both these tools have internal methods to scan folders for packages that are used in the project, but these methods aren't exposed in a convenient way.

This little function uses a non-exported method from the `packrat` package to scan for required packages.  The function will also optionally install these packages, after first comparing to what's already on your system. 

```r
scan_and_install <- function(path, 
                             lib = .libPaths()[1], 
                             repos = getOption("repos"), 
                             install = FALSE)
  {
  stopifnot(require("packrat"))
  pkgs <- packrat:::appDependencies(path)
  to_install <- pkgs[!(pkgs %in% unname(installed.packages()[, "Package"]))]
  if (install && length(to_install)){
    install.packages(to_install, lib = lib, repos = repos)
  }
  to_install
}

```


To list the required packages in a project, try:

```r
scan_and_install("path/to/project/")
```

And to also install the missing packages, add the argument `install = TRUE`:

```r
scan_and_install("path/to/project/", install = TRUE)
```

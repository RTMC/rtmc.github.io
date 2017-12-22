---
layout: page
title: Guide for students
permalink: /guide_students/
lang: en
categories:
    - en
---

# Start using RTMC

This guide will walk you through the first steps of using the test my code -addin for R.

## Rstudio

To use RTMC, you'll need Rstudio IDE. You can find it
[here](https://www.rstudio.com/products/RStudio/).

Download the desktop version of the software for the operation system of your choice and install it.

## Installing the addin

After installing Rstudio, you'll have to manually install the addin.

To do this, first open *RStudio*. There type the following command on the console

```{r}
install.packages("devtools")
```

After installing *devtools*, you can install the programs needed for the addin.

First, install [tmc-r-tester](https://github.com/RTMC/tmc-r-tester) with the command

```{r}
devtools::install_github("rtmc/tmc-r-tester/tmcrtestrunner")
```

After that, install [tmc-rstudio](https://github.com/RTMC/tmc-rstudio) with the command

```{r}
devtools::install_github("rtmc/tmc-rstudio/tmcrstudioaddin")
```

Now you should have everything you need to use the addin.


## Using the addin

After you have installed the addin, it should be able to find it in the toolbar

![Addin in the toolbar](../../resources/addin_toolbar.png)

Clicking this text opens the addin. 

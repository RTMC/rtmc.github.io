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
devtools::install_github("rtmc/tmc-r-tester/tmcRtestrunner")
```

After that, install [tmc-rstudio](https://github.com/RTMC/tmc-rstudio) with the command

```{r}
devtools::install_github("rtmc/tmc-rstudio/tmcrstudioaddin")
```

Now you should have everything you need to use the addin.


## Using the addin

After you have installed the addin, it should have appeared in the toolbar under Addins

![Addin in the toolbar](../../resources/addin_toolbar.png)

Clicking this text opens the addin. 

You can now log in with your tmc username and password. You can also change the server if you wish to use a server other than https://tmc.mooc.fi.

After logging in you are able to download exercises in the "Exercises" tab. First select the organization responsible for your course, for example Helsingin Yliopisto. After this, select the course. Now you should see listed every exercise from the course that are downloadable. If you have already downloaded a given exercise, it will not be overwritten. Select as many as you wish, or everything with the "Download all exercises"-checkbox. Then press "Download exercises".

Finally you can move on to the "Test & Submit" tab. First you can open an exercise you have downloaded. After opening, you can do one of three things. You can run your code with the "Source" button, as RStudio blocks the console when an addin is in use. You can also run test locally with "Run tests", or submit your code to the server for evaluation. Only the last one will grant you points, if the automatic tests associated with the exercise pass on the server. If they do not pass, you can see what went wrong with any individual test with "Toggle details".

This concludes the basic usage of the addin. If you wish to manually inspect your exercises, you can find a directory "tmcr" under your home folder, and under that folder, "tmcr-projects". All your downloaded exercises are there.

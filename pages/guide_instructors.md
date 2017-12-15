---
layout: page
title: Guide for teachers
permalink: /guide_teachers/
lang: en
categories:
    - en
---

## Create tmc account

Follow the instructions in [this guide](http://testmycode-usermanual.github.io/usermanual/teachers.html) to create a test my code account which allows you to link the exercises to the course.

## Creating a course repository

To create a tmc-course for R, you will need to create a git repository. This will contain exercise folders that serve as the basis for students' code for the exercises. Also in this repository you can write the tests for each exercise to check if students' code runs correctly.

There are couple of ways to create a repository. If you know your way around git, feel free to do it however you prefer to.

One easy way to create a git repository is using GitHub, which is a repository hosting service.

First, sign up / log in to [GitHub](https://github.com).

After logging on, you'll see the GitHub front page and (somewhere there) a big green button saying *new repository*. Click it.

![New repository](../../resources/github_create_repo.png)

Fill in the needed fields. The repository needs a name at least.

![New repository](../../resources/creating_repo_2.png)

And here it is, an empty repository. Now you can begin adding exerises.

![New repository](../../resources/empty_repository.png)

## Structure of the repository

Your repository should be structured something like this:

- *ROOT*
    - `Week1`
        - `01_some_exercise`
            - `R`
                - `arithmetic.R`
            - `src`
                - `empty.txt`
            - `tests`
                - `testthat`
                    - `testArithmetic.R`
                    - `testArithmeticHidden.R`
        - `02_some_other-exercise`
            - `R`
                - `matrices.R`
            - `src`
                - `empty.txt`
            - `tests`
                - `testthat`
                    - `testMatrices.R`
    - `Week2`

The root of the repository has directories for each exercise as subdirectories. In each of these directories, you should include three separate directories:

1. `R`:
    - This is where the code that the students can edit goes. You can have the student write the whole file or simply parts of the file.
2. `src`:
    - This is a dummy directory that exists for a technical reason.
    - You should include an empty text file "empty.txt" in this folder
3. `test`:
    - `test`-folder has a subfolder, `testthat`, where the test-files go. In these files, you can include test that check whether the student has written correct code in the `R`-folder. *If the student file is called somename.R, the test file should be named testSomename.R*. That is, you should name the corresponding test file by prepending "test" to the name of the student file and capitalizing the first letter of the student file.
    - If you want to create a hiddent test file that the students can't see, append "Hidden" to the end of the file name. Say that you want to create a hidden test file for the student file `matrices.R`. This should be named `testMatricesHidden.R`.

## Adding your repository to TMC servers

After creating your repository with the skeleton presented above, you can add
it to TMC servers. To this end, follow the steps in item [1.2 in this material](http://testmycode-usermanual.github.io/usermanual/customcourse.html#creating_a_course)

## Writing tests

The tests should be written in the folder `tests/testthat`. Suppose you  have a *student source file* `vectors.R` where the student is instructed to create a vector containing all integers from 8 to 800 by interval of 8 (that is, the integers 8, 16, 24, ..., 792, 800).

To test this, create a test file `tests/testthat/testVectors.R`. Below is an example of how this file could look like:

```{r}

library('testthat')

points_for_all_tests("r7")

test("7b", "r7.1", {
  expected_v1 <- c(8, 16, 24, 32, 40, 48, 56, 64, 72, 80, 88, 96, 104, 112, 120, 128,
                   136, 144, 152, 160, 168, 176, 184, 192, 200, 208, 216, 224, 232,
                   240, 248, 256, 264, 272, 280, 288, 296, 304, 312, 320, 328, 336,
                   344, 352, 360, 368, 376, 384, 392, 400, 408, 416, 424, 432, 440,
                   448, 456, 464, 472, 480, 488, 496, 504, 512, 520, 528, 536, 544,
                   552, 560, 568, 576, 584, 592, 600, 608, 616, 624, 632, 640, 648,
                   656, 664, 672, 680, 688, 696, 704, 712, 720, 728, 736, 744, 752,
                   760, 768, 776, 784, 792, 800)

  expect_equal(v1, expected_v1)
})

test("7c", c("r7.2"), {
  expect_equal(pituus, 24)
})
```

There are a few important things to note in this test file:

* include the line `library('testthat')` at the beginning of your test file.
* Determine the points that the student from solving the exercise problems using the function `points_for_all_tests("r1")`. It doesn't really matter what your points are called, as long as they are unique. For example, you could use names *a1, a2, a3,...* or *ex1, ex2, ex3...* for the points.
* You can tests students code with the `test`-function. Test function works almost exactly like `test_that`-function from the [testthat-library](https://journal.r-project.org/archive/2011-1/RJournal_2011-1_Wickham.pdf), but it allows you to pass the points corresponding to the test as parameter. For example, in the following snippet, the corresponding points are given as a parameter `c("r7.2")`.
```{r}
test("7c", c("r7.2"), {
    expect_equal(pituus, 24)
})
```
* `expect_equal`-function allows you to check whether two variables have the same value. From [testthat-documentation](https://journal.r-project.org/archive/2011-1/RJournal_2011-1_Wickham.pdf) you can read more about these `expect_`-functions. If all `expect_`-functions inside a `test`-function passes, the the student is given the point given as a parameter in the function call.

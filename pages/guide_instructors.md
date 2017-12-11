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
        - `R`
            - `arithmetic.R`
        - `src`
            - `empty.txt`
        - `tests`
            - `testthat`
                - `testArithmetic.R`
                - `testArithmeticHidden.R`
    - `Week2`
        - `R`
            - `matrices.R`
        - `src`
            - `empty.txt`
        - `tests`
            - `testthat`
                - `testMatrices.R`

The root of the repository has directories for each week as subdirectories. In each of these weeks, you should include three separate directories:

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

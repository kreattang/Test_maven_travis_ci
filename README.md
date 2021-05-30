[![Build Status](https://www.travis-ci.com/kreattang/Test_maven_travis_ci.svg?branch=main)](https://www.travis-ci.com/kreattang/Test_maven_travis_ci)
[![codecov](https://codecov.io/gh/kreattang/Test_maven_travis_ci/branch/main/graph/badge.svg?token=WI3NQL4HK5)](https://codecov.io/gh/kreattang/Test_maven_travis_ci)

# Test_maven_travis_ci
This repository is a demo of how to use [Travis CI](https://docs.travis-ci.com/) in a Java project on GitHub.

# Usage
## 1. Build
* Sign in to your user Github account and fork this repo
* Add a _.travis.yml_ file to your repo to tell Travis CI what to do, commit the changes and push it to your repo
```
language: java

# We can specify a list of JDKs to be used for testing

jdk:
 - openjdk11
```
* Go to [Travis-ci.com](https://travis-ci.com/) and Sign in with GitHub account

![avatar](https://github.com/kreattang/TravisCI_Java/blob/main/img/20210529151710.png)

* Accept the Authorization of Travis C
* Click on your profile picture in the top right of your Travis Dashboard, click Settings 

![avator](https://github.com/kreattang/TravisCI_Java/blob/main/img/20210529153038.png)

* Select the repo you want to use with Travis CI. If repo cannot be found, click _Sync account_.


![avatar](https://github.com/kreattang/TravisCI_Java/blob/main/img/20210529153337.png)

* Click your repo and you will find it start build by Travis CI

![avatar](https://github.com/kreattang/TravisCI_Java/blob/main/img/20210529152709.png)

* If the build is passed, you will see as follows.

![avatar](https://github.com/kreattang/TravisCI_Java/blob/main/img/20210529154131.png)

* Fix the README.md badges(copy the markdown code from [Travis CI](https://travis-ci.com/) and replace the top line of _readme.md_)
> [Travis CI](https://travis-ci.com/) => select your repository => click the build status image => select _FORMAT_ as Markdown => Copy the code of _RESULT_ => paste in the top line of _readme.md_

![acatar](https://github.com/kreattang/TravisCI_Java/blob/main/img/20210529154809.png)

## 2. Test
This repo also integrates with Codecov to generate reports.
* Go to the [Codecov website](https://about.codecov.io/) and Sign in with GitHub account.

![avatar](https://github.com/kreattang/TravisCI_Java/blob/main/img/20210530091144.png)

* Accept the Authorization of Codecov and add your repository 
* Add the following code in the end of _.travis.yml_ file. This is to enable CodeCov's coverage.
If a build is successful, the code is submitted for coverage analysis
```
after_success:
  - bash <(curl -s https://codecov.io/bash)
```
* Fix the README.md badge.
> [Codecov](https://codecov.io/gh)  =>select your repository => Setting => Bedge => Copy the contect of Markdown => paste in readme.md

## 3.Deploy
* Travis CI can help you release to Github. You will need to provide a Github personal access token(Tutorial: https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token). 
* Now that we have a token go to the project you want to use it with on Travis CI. Then on your project page, go to More options => Settings.

![avatar](https://github.com/kreattang/TravisCI_Java/blob/main/img/20210530094300.png)

* In the _Environment Variables_ section, add variable named _GITHUB_TOKEN_ and use the generated token from Github in previous step.

![avatar](https://github.com/kreattang/TravisCI_Java/blob/main/img/env-var.png)

* Travis CI can automatically upload assets to git tags on your GitHub repo. So you need create a tag in a GitHub repo(Tutorial:  https://stackoverflow.com/questions/18216991/create-a-tag-in-a-github-repository)
* Set the deployment details in _.travis.yml_

```
deploy:
  provider: releases
  file_glob: true
  skip_cleanup: true
  api_key: $GITHUB_TOKEN
  file:
    - src/main/java/io/github/kreattang/travis_ci_tutorial_java/trityp.java
  on:
    tags: true
    branch: tag
    repo: kreattang/Test_maven_travis_ci

```


 * Travis CI can notify you about your build results through email, IRC, chat or custom webhooks.
 ```
 notifications:
  email:
    - one@example.com(replace by your e-mail)
 ```

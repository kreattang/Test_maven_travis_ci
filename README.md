[![Build Status](https://travis-ci.com/kreattang/Test_maven_travis_ci.svg?branch=main)](https://travis-ci.com/kreattang/Test_maven_travis_ci)
[![codecov](https://codecov.io/gh/kreattang/Test_maven_travis_ci/branch/main/graph/badge.svg?token=WI3NQL4HK5)](https://codecov.io/gh/kreattang/Test_maven_travis_ci)

# Test_maven_travis_ci
This repository is a demo of how to use [Travis CI](https://docs.travis-ci.com/) in a Java project on GitHub.

# Usage
1. Build
* Sign in to your user Github account and fork this repo
* Go to [Travis-ci.com](https://travis-ci.com/) and Sign in with GitHub account.
* Accept the Authorization of Travis CI. 
* Click on your profile picture in the top right of your Travis Dashboard, click Settings and then the green Activate button, and select the repositories you want to use with Travis CI.
* Add a _.travis.yml_ file to your repository to tell Travis CI what to do. 
```
language: java

# We can specify a list of JDKs to be used for testing

jdk:
 - openjdk11
```
* Fix the README.md badges(copy the markdown code from [Travis CI](https://travis-ci.com/) and replace the top line of readme.md)
> [Travis CI](https://travis-ci.com/) => select your repository => click the status image => select FORMAT as Markdown => Copy the context of RESULT => paste in readme.md

* You can also choose to replace _kreattang_ in the URL with your-github-username instead of this operation.

2. Test
* Go to the [Codecov website](https://about.codecov.io/) and Sign in with GitHub account.
* Accept the Authorization of Codecov and add your repository 
* Add the following code in the end of _.travis.yml_ file. This is to enable CodeCov's coverage.
If a build is successful, the code is submitted for coverage analysis
```
after_success:
  - bash <(curl -s https://codecov.io/bash)
```
* Fix the README.md badge.
> [Codecov](https://codecov.io/gh)  =>select your repository => Setting => Bedge => Copy the contect of Markdown => paste in readme.md

3.Deploy
* Travis CI can help you release to Github
* You will need to provide a personal access token
* Set the deployment provider details in _.travis.yml._
* Create a tag in a GitHub repository
* Push your change and Travis CI will build environment again.

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

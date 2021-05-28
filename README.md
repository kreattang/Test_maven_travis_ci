[![Build Status](https://travis-ci.com/kreattang/Test_maven_travis_ci.svg?branch=main)](https://travis-ci.com/kreattang/Test_maven_travis_ci)
[![codecov](https://codecov.io/gh/kreattang/Test_maven_travis_ci/branch/main/graph/badge.svg?token=WI3NQL4HK5)](https://codecov.io/gh/kreattang/Test_maven_travis_ci)

# Test_maven_travis_ci
This resepository is a demo of how to use [Travis CI]() in a Java project on GitHub.

# Usage
1. Building
* [Fork](https://github.com/kreattang/Test_maven_travis_ci/fork) this repository
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
Fix the README.md badges (replacing in the URL joaomlneto with your-github-username) and push the changes.
2. Testing
* Go to the [Codecov website](https://about.codecov.io/) and Sign in with GitHub account.
* Accept the Authorization of Codecov andd add your repository 
* add the following code in the end of _.travis.yml_ file. This is to enable CodeCov's coverage.
If a build is successful, the code is submitted for coverage analysis
```
after_success:
  - bash <(curl -s https://codecov.io/bash)
```

 3.Deploying
 * Travis CI can notify you about your build results through email, IRC, chat or custom webhooks.
 ```
 notifications:
  email:
    - one@example.com(replace by your e-mail)
 ```

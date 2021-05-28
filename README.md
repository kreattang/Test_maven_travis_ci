[![Build Status](https://travis-ci.com/kreattang/Test_maven_travis_ci.svg?branch=main)](https://travis-ci.com/kreattang/Test_maven_travis_ci)
[![codecov](https://codecov.io/gh/kreattang/Test_maven_travis_ci/branch/main/graph/badge.svg?token=WI3NQL4HK5)](https://codecov.io/gh/kreattang/Test_maven_travis_ci)

# Test_maven_travis_ci
Just to learn how to use travis-ci in a java project!

This is a working minimal example of how to use Travis CI (and Codecov) with Java on GitHub.


# How To Start

1. [Fork](https://github.com/joaomlneto/travis-ci-tutorial-java/fork) this Repository
2. Go to [Travis CI](http://travis-ci.com) and enable the repository
3. Fix the `README.md` badges (replacing in the URL `joaomlneto` with `your-github-username`) and push the changes. This should trigger a build in Travis CI!

## Optional: Code Coverage with CodeCov

This repository also integrates with Codecov to generate reports.

What's done for you:
- The [JaCoCo](https://www.jacoco.org) plugin is included in `pom.xml`
- On `.travis.yml`, `after_success` target executes the Codecov script.

If you want to use it:
- Go to the Codecov website and create an account and setup permissions.
- Add your repository
- Fix the `README.md` badge.


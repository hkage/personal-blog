Date: 2013-05-28
Title: Continious integration
Tagline: Integrate a github project in Travis and Coveralls
Slug: continious
Category: Blog
Tags: github, ci, coverage, python

A couple of weeks ago I revived one of my personal projects called
[Inhouse-Web](https://github.com/hkage/inhouse-web) and made a complete
(source) makeover. During this process I also wanted to use a continious
integration and code coverage tool. Hosting the source on
[github](https://github.com), it made sense to me to give
[Travis-CI](https://travis-ci.org) and [coveralls.io](https://coveralls.io) a
try. Both are free to use for non commercial projects and the setup looked very
easy.

# Travis

## Create a repository

The first thing you will obviously have to do is signing in with you github
account. On the [profile page](https://travis-ci.org/profile) you can turn on
(or off) the integration for your public repositories. With "Sync now" you can
refresh the list of repositories.

## Setup the project

First you need to create a `.tavis.yml` file to configure the continious
integration environment. Let's take a look at a simple configuration file for
a Python/Django project:

    #!sh
    language: python
    python:
      - 2.6
      - 2.7
    install:
      - pip install -q -r requirements.txt --use-mirrors

`language` will tell Travis to use the Python interpreter for the integration
tests.

`python` specifies the different Python version you want to use. Each entry will
cause Travis to add a new fork. In this case we would generate two works for
the Python versions 2.6 and 2.7.

`install` specifies the commands Travis has to execute before running tests for
each fork. As we are using a set of libraries, e.g. Django, we tell Travis to
install those libraries with pip.

You can also check the
[documentation for Python](http://about.travis-ci.org/docs/user/languages/python/)
which describes the several Python specific settings and commands.

# Coveralls

## Create a repository

Like Travis-CI you can login with your github account. After that you can
[add](https://coveralls.io/repos/new) one of your public repositories.

## Setup the project

## Commandline execution

    #!sh
    pip install coveralls

Create a `.coveralls.yml` file and add your private token to the file. Note that
the token must be secret and the file should *NOT* be added to your project's
repository.

    #!sh
    repo_token: <your token>

To push the current coverage result, you will have to regenerate the coverage
statics, e.g. with:

    #!sh
    coverage run manage.py test

After that you can push the result to your project page:

    #!sh
    coveralls

# Post work

## Integrate badges
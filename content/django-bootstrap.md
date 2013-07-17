Date: 2013-07-17
Title: Bootstrap for Django projects
Tagline: Using bootstrap as a CSS-Framework for Django projects
Slug: bootstrap
Category: Blog
Tags: django, bootstrap

### Integrate bootstrap

    #!sh
    mkdir -p static/less static/css

Now we can add bootstrap as an external git submodule. You have to add the
submodule from your project (git) root directory:

    #!sh
    cd <project root>
    git submodule add git://github.com/twitter/bootstrap.git <static dir>/bootstrap

### Modify base template

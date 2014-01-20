Heroku Buildpack for Meteorite
============================

Based on the official [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for Node.js apps.

The aim of this rewrite is to greatly speed up meteor app deployments. I find the standard meteorite buildpack to be too slow.

How it Works
------------

Here's an overview of what this buildpack does:

- Does all that good stuff that the nodejs buildpack does
- Installs Meteorite
- Caches Meteorite packages between builds
- Installs Meteor
- Caches Meteor install between builds
- Runs `meteor update` on cached meteor install.
- Provisions the mongolab:sandbox addon and sets the MONGO_URL = MONGOLAB_URI


Usage
-------

```
# Create a new Heroku app that uses this buildpack
heroku create --region eu --buildpack https://github.com/johnnypez/heroku-buildpack-mrt.git
```
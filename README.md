dokku-multi-dockerfile
===============

Dokku plugin to choose which Dockerfile is used depending on the app being deployed to.

## Install

```
dokku plugin:install https://github.com/artofrawr/dokku-multi-dockerfile
```

## Usage

```
$ ls
.dokku-multi-dockerfile
Dockerfile
Dockerfile.storybook
```

The file .dokku-multi-dockerfile determines which Dockerfile is used for which app:
```
app=Dockerfile
stories=Dockerfile.storybook
```

The part before `=` is used to identify the dokku application. For example, here:
```
$ git remote -v
first             dokku@dokku.me:app
first-storybook   dokku@dokku.me:stories
second            dokku@dokku.me:second-app
```

For the `app` and `second-app` applications `Dockerfile` would be used. For `stories` the `Dockerfile.storybook` would be used.

When you push the code to an application's remote, the folder gets detected for you:
```
$ git push first-storybook
Counting objects: 253, done.
Writing objects: 100% (253/253), 38.27 KiB | 0 bytes/s, done.
Total 253 (delta 117), reused 233 (delta 109)
=====> Multi Dockerfile Project detected
=====> Installing with Dockerfile.storybook
-----> Cleaning up...
       ...
```

It's that easy!

# How to deploy a react app to Heroku

## What is Heroku?

> Heroku is a cloud platform that lets companies build, deliver, monitor and scale apps — we’re the fastest way to go from idea to URL, bypassing all those infrastructure headaches.

## Why Heroku?

1. Heroku is a platform as service that allow us to host our application for **free** (ok, if you need a lot of bandwidth for example the basic plan will not meet your needs).
2. Very easy to setup (don’t need to know how to install and configure Apache, nginx, unicorn, passenger, MySQL, Postgres etc)
3. Heroku handles pretty much everything for you. (it can be a drawback, but I am considering the deploy of a non commercial project)

## Installation (Ubuntu 16+)

```bash
sudo snap install heroku --classic
```

- [installation for other platforms](https://devcenter.heroku.com/articles/getting-started-with-nodejs#set-up)

## Setup and Deploy

1. Login into CLI

```bash
heroku login
```

2. Deploy

```bash
heroku create [app-name]--buildpack https://github.com/mars/create-react-app-buildpack.git
```

3. Push changes

```bash
git push heroku master
```

## More information

- [Official documentation](https://devcenter.heroku.com/categories/reference)

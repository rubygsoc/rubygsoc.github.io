
## Creating posts

You can use the `initpost.sh` to create your new posts. Just follow the command:

```
./initpost.sh -c Post Title
```

The new file will be created at `_posts` with this format `date-title.md`.

## Front-matter

When you create a new post, you need to fill the post information in the front-matter, follow this example:

```
---
layout: post
title: "Falando sobre RSCSS"
image: '/assets/img/rscss/rscss.png'
main-class: 'css'
tags:
- css
- metodologia
- frontend
categoriesintroduction: 'Escrevendo CSS sem perder a sanidade. Com essa introdução, Rico St. Cruz o criador chama a atenção de todos sobre uma metodologia melhor para se escrever CSS.'
---
```

## Running the blog in local

In order to compile the assets and run Jekyll on local you need to follow those steps:

- Install [NodeJS](https://nodejs.org/) (remember to use the latest version)
- Run `sudo npm install`
- Run `sudo npm install -g gulp gulp-cli`
- Run `sudo gulp`

If you see following error:
> Error: watch /path_to_folder/rubygsoc.github.io/src/styl/ ENOSPC

you need to increase system limit on the number of files you can monitor ([Read more](https://github.com/guard/listen/wiki/Increasing-the-amount-of-inotify-watchers)):

```
sudo sysctl fs.inotify.max_user_watches=524288
```

## Adding a new main-class

`main-class` is used to categorize projects. If you need a new main-class

* add it in `themes` in `src/styl/_theme-colors.styl`:
```
themes = {
    post-bundler: #0e8ab3,
    post-jruby: #2DA0C3,
    ...
    post-newclass: #hexcolor
}
```
* create a category template for your new main-class: `category/newclass.html`

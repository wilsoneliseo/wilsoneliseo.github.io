---
layout: post
title: "Instalando Jekyll en Ubuntu"
date: 2018-10-07 23:21:44
tags: ['ubuntu']
published: true
comments: true
# Does not change and does not remove 'script' variable.
script: [post.js]
---

<!-- Write from here your post !!! -->

Después de seguir el [tutorial](https://jekyllrb.com/docs/installation/ubuntu/) de instalacion, de Jekyll, en la pagina
oficial que según consta hay que hacer:

``` bash
$ sudo apt-get install ruby ruby-dev build-essential

$ echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
$ echo 'export GEM_HOME=$HOME/gems' >> ~/.bashrc
$ echo 'export PATH=$HOME/gems/bin:$PATH' >> ~/.bashrc
$ source ~/.bashrc

$ gem install jekyll bundler
```    

Cree mi sito con

``` bash
$ jekyll new myblog
$ cd myblog
```    

pero al correr el servidor obtenía

``` bash
$ bundle exec jekyll serve
Could not find i18n-0.8.6 in any of the sources
Run `bundle install` to install missing gems.
```    

La solución fue la siguiente

``` bash
$ sudo apt-get install libxml2-dev
$ sudo apt-get install libxslt-dev
$ bundle install
$ gem install execjs
$ sudo apt-get install nodejs
```    

Después de esto ya podía correr correctamente mi sito: `bundle exec
jekyll serve`.

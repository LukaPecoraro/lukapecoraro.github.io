# Chirpy Starter [![Gem Version](https://img.shields.io/gem/v/jekyll-theme-chirpy)](https://rubygems.org/gems/jekyll-theme-chirpy) [![GitHub license](https://img.shields.io/github/license/cotes2020/chirpy-starter.svg?color=blue)][mit]

When installing the [**Chirpy**][chirpy] theme through [RubyGems.org][gem], Jekyll can only read files in the folders `/_data`, `/_layouts`, `/_includes`, `/_sass` and `/assets`, as well as a small part of options of the `/_config.yml` file from the theme's gem. If you have ever installed this theme gem, you can use the command `bundle info --path jekyll-theme-chirpy` to locate these files.

The Jekyll team claims that this is to leave the ball in the user’s court, but this also results in users not being able to enjoy the out-of-the-box experience when using feature-rich themes.

To fully use all the features of **Chirpy**, you need to copy the other critical files from the theme's gem to your Jekyll site. The following is a list of targets:

```shell
.
├── _config.yml
├── _plugins
├── _tabs
└── index.html
```

To save you time, and also in case you lose some files while copying, we extract those files/configurations of the latest version of the **Chirpy** theme and the [CD][CD] workflow to here, so that you can start writing in minutes.

## Prerequisites

Follow the instructions in the [Jekyll Docs](https://jekyllrb.com/docs/installation/) to complete the installation of the basic environment. [Git](https://git-scm.com/) also needs to be installed.

## Installation

Sign in to GitHub and [**use this template**][use-template] to generate a brand new repository and name it `USERNAME.github.io`, where `USERNAME` represents your GitHub username.

Then clone it to your local machine and run:

```
$ bundle
```

## Usage

Please see the [theme's docs](https://github.com/cotes2020/jekyll-theme-chirpy#documentation).


## Installation

If on windows use wsl.

```
sudo apt update
sudo apt install ruby-full build-essential zlib1g-dev git
```

```
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

```
gem install jekyll bundler
```
If you get an error here, instead run `gem install jekyll --version="~> 4.2.0"`

## Chirpy starter
Video tutorial: https://www.youtube.com/watch?v=F8iOU1ci19Q


Clone your repo and install dependencies.

```
git clone git@<YOUR-USER-NAME>/<YOUR-REPO-NAME>.git
cd repo-name
bundle 
```


## Jekyll commands
Serve your site

```
bundle exec jekyll s
```

To use live reload start with `bundle exec jekyll s --force-polling`

Build your site in production mode, output will be in `_site`

```
JEKYLL_ENV=production bundle exec jekyll b
```

## Building with docker

Create a Dockerfile with the following

```Dockerfile
FROM nginx:stable-alpine
COPY _site /usr/share/nginx/html
```
Build the site in production

```
JEKYLL_ENV=production bundle exec jekyll b
```
Then build your image with docker build .


## Creating a post

Create a file in `_posts` with the format

YEAR-MONTH-DAY-title.md

## Local linking of files 

```Markdown
... which is shown in the screenshot below:
![A screenshot](/assets/screenshot.webp)
```

```Markdown
... you can [download the PDF](/assets/diagram.pdf) here.
```

## Host on github pages
Settings, pages, source github actions, but works also just from branc main


## Setup custom domain


CloudFlare is an awesome reverse cache proxy and CDN that provides DNS, free HTTPS (TLS) support, best-in-class performance settings (gzip, SDCH, HTTP/2, sane `Cache-Control` and `E-Tag` headers, etc.), minification, etc.

1. Make sure you have registered a domain name.
2. Sign up for [CloudFlare](https://www.cloudflare.com/) and create an account for your domain.
3. In your domain registrar's admin panel, point the nameservers to CloudFlare's (refer to [this awesome list of links for instructions for various registrars](https://surge.sh/help/adding-a-custom-domain)).
4. From the CloudFlare settings for that domain, enable HTTPS/SSL and set up a [Page Rule to force HTTPS redirects](https://support.cloudflare.com/hc/en-us/articles/200168306-Is-there-a-tutorial-for-Page-Rules-). (If you want to get fancy, you can also enable automatic minification for text-based assets [HTML/CSS/JS/SVG/etc.], which is a pretty cool feature if you don't want already have a build step for minification.)
5. If you don't already have one, create a new repository on GitHub to store your site's contents (preferably in the form of static web pages and assets; though not necessary, for the A-Frame site we use a static-site generator called [Hexo](https://github.com/hexojs/hexo)).
6. From your domain registrar's settings, create a `CNAME` record to point `<domain>.<tld>` to `<user>.github.io`. (Refer to [the GitHub docs for more information](https://help.github.com/en/github/working-with-github-pages/managing-a-custom-domain-for-your-github-pages-site).)
7. In your Github repo, create a file at the root called `CNAME` containing the domain name (e.g., `aframe.io`).
8. Push to GitHub Pages (either by pushing to `gh-pages` or `master` of your repo; or you can use the `master` branch of a repo named `<org>.github.io` - example: https://github.com/aframevr/aframevr.github.io/ automatically gets published to https://aframevr.github.io/, which redirects to https://aframe.io/)
9. You're done! All content will now be served to your users from CloudFlare.
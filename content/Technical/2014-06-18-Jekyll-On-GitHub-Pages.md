Title: How to setup Jekyll Blog Hosted on GitHub Project Pages
Date: 2014-06-18 20:08:27
Tags: ruby, jekyll
Slug: Jekyll-On-GithHub-Pages
Author: Anna Lukasiak
Summary: 

This blog post documents the setup done to create [OpenJC Blog](http://openjerseycity.org/blog) and instructions on how to create and add a new post.

Instructions used to create the OpenJC Blog can be found on [Jekyll on Github Pages](https://help.github.com/articles/using-jekyll-with-pages#installing-jekyll) and [Jekyll Documentation](http://jekyllrb.com/).  They include configuration options, plug-ins and theming not included in this post.

Installing ruby
---------------
Jekyll requires the Ruby language. If you have a Mac, you've most likely already got Ruby. To confirm if you have the required 1.9.3 or 2.0.0 version, open up the Terminal application, and run the command:

	ruby --version

If you have older version, follow [these instructions](https://www.ruby-lang.org/en/downloads/) to install Ruby.

Installing Bundler
------------------
Bundler is a package manager that makes versioning Ruby software a lot easier if you're going to be building GitHub Pages sites locally.  You don't have to use it, but it's recommended and the instructions in this document assume that you are using Bundler.

	gem install bundler

Installing Jekyll
-----------------
Create a file in your site's repository called `Gemfile` and add the line `gem 'github-pages'` and run:

	bundle install

Creating new blog site
----------------------
To create a new bog site, run:

	jekyll new myproject

 `myproject` will be the repo name and a directory name where the blog will be located.  If you are using github project pages, it will also be a part of the url (https://username.github.io/project).  If you want to use GitHub User or Organization pages, follow [those instructions](http://jekyllrb.com/docs/github-pages/#user-and-organization-pages) instead.

Adding content
--------------
In the `_posts` directory, crate your content file in this format:  'YYYY-MM-DD-your-title.md'.

Add the section about markdown & metadata.

Editing config
--------------
Edit `about.md`.  

Publishing on GitHub
--------------------
Create a new repo called `myproject`.  Follow [those instructions](https://help.github.com/articles/creating-a-new-repository).

On a command line, inside "project" directory, run:

	git init

Next, create new branch called "gh-pages" by running those commands:
	
	git branch gh-pages
	git checkout gh-pages

To check the current branch:

	git branch

There is one more config file change that needs to be made to run the blog on GitHub Pages.  Add those two lines to `_config.yml`:

	url: https://username.github.io
	baseurl: project

If you are using custom domain names, then use this url line `url: "http://customomain.com"` instead.  In our case we are using 

	url: "http://openjerseycity.org/"
	baseurl: "/blog"

Finally, add and commit all changes to GitHub:

	 git add .
	 git commit -m"your comment goes here"
	 git push origin gh-pages

In your browser, view `https://username.github.io/project`.  In case of this project the url is [http://openjerseycity.org/blog/](http://openjerseycity.org/blog/).

Running Jekyll locally in GitHub Pages Environment
--------------------------------------------------
To run Jekyll in a way that matches the GitHub Pages build server, in the root of your repository (after switching to the gh-pages branch for project repositories), run Jekyll with Bundler: 

	bundle exec jekyll serve --baseurl ''

The site should be available at [http://localhost:4000](http://localhost:4000). For a full list of Jekyll commands, see the [Jekyll documentation](http://jekyllrb.com/docs/usage/).

Running Jekyll locally (the classic way)
----------------------------------------
Inside the "project" directory:

	jekyll build
	jekyll serve

In your browser, view [http://localhost:4000](http://localhost:4000).

The `_sites` directory is generated by Pelican and can be deleted and regenerated at any time.
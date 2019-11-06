---
layout: post
title: Installing Jekyll on Termux
---

Due to the error caused by ruby libraries that haven't been converted for termux, which will give you some installation error with the gem package manager, we're going to use a pre-packaged library that resides on github. Its called [Jekyll Now](Http://jekyll-now.com). It's just a repo on github that we can fork, then clone to our machine and then you just run 'bundle exec jekyll build' to build it and 'jekyll serve' to run it locally on 'http://127.0.0.1:400'. You can later make edits and push back to your repo on github.

Anyways, we use this method to avoid errors like 'Nokogori' or some other libraries that isn't yet supported by termux or requires some native building. However, we do get an error for this version of jekyll '3.8.6', if you check the error message, you'll see something like '/proc/...'. To solve this error, we need to make some changes manually in the jekyll library in our gem folder. So navigates to /usr/files/lib/ruby/gem/jekyll/utils

Note that when you fork the Jekyll-Now repo, you should change the repo name to 'your-username.github.io', this way, when you run 'https://your-username.github.io' it shows the content of your jekyll site online automatically. Sometimes changes can take upto 3min as reported by github.

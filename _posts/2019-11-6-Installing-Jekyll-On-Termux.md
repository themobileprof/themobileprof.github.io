---
layout: post
title: Installing Jekyll on Termux
---
I can help you. This is a very easy of installation ok and at the end of this article you would have a local installation of jekyll on termux. Aiit, let's get started.

Due to the errors on termux, caused by ruby libraries that haven't been converted for termux etc etc, which will give you some installation error with the gem package manager, we're going to use a pre-packaged library that resides on github. Its called [Jekyll Now](http://jekyll-now.com). It's just a repo on github that we can fork then clone to our machine. 

Now, fork the repo and rename it to `your-github-username.github.io`. Then you clone and run `gem install github-pages` to install jekyll gem and other gems used by githubpages like Sass locally and finally run `jekyll serve` to view locally on your device at _http://127.0.0.1:4000_. You can later make edits and push back to your repo on github.


![Jekyll Gem path on termux]({{ site.baseurl}}/images/screenshot_jekyll-utils.png "Jekyll gem path on termux")

But, when we run `jekyll serve`, we get an error `jekyll 3.8.6 permission denied @ rb_sysopen-/proc/version`. To solve this error, we need to make some changes manually in the jekyll library in our gem folder. So navigate to _data/data/files/usr/lib/ruby/ruby/gems/2.6.0/jekyll/lib/jekyll/utils_ (NB: you can also get this path with the command `where jekyll`). Then open the file with [Nvim Editor](http://{{ site.baseurl }}/posts/2019-11-10-How-to-install-and-configure-nvim-editor) or your text editor and add the following to the **proc_version method**

```ruby
def proc_version
   @proc_version ||= begin
   Pathutil.new(
      "/proc/version"
      ).read
   rescue Error::ENOENT, Errno::EACCES #update area
     nil
   end
end
```
After updating the code, save and go back to your local repo and run `jekyll serve` again. This time there's no error and we proceed to opening our site on the browser. You can make changes to the post and even add your own post. Then push to guthub and view your site remotely on `your-github-username.github.io` 

Now we have our Jekyll installed locally on termux and can view our site remotely from any browser and that's that. Cheers. 

----

Note that when you fork the Jekyll-Now repo, you should change the repo name to 'your-username.github.io', this way, when you run 'https://your-username.github.io' it shows the content of your jekyll site online automatically. Sometimes changes can take upto 3min as reported by github.

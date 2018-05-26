---
#layout: post
title:  "Install Jekyll on Ubuntu on Win10"
---

GitHub Pages uses [Jekyll][jekyll-site] as a static site generator.
You can set up a local version of your Jekyll GitHub Pages site to test changes to your site locally. GitHub highly recommend installing Jekyll to preview your site and help troubleshoot failed Jekyll builds, according to [help][help-page].

Steps
-----
    # sudo apt-get install ruby ruby-dev build-essential
    # echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
    # echo 'export GEM_HOME=$HOME/gems' >> ~/.bashrc
    # echo 'export PATH=$HOME/gems/bin:$PATH' >> ~/.bashrc
    # source ~/.bashrc
    # gem install jekyll bundler
    # cd ~/kgyang.github.io
    # add posts in _posts subdirectory
    # jekyll serve

Reference
---------
[Installation Guide][install-guide]

[Setting up your GitHub Pages site locally with Jekyll][setup-guide]


[jekyll-site]: https://jekyllrb.com
[help-page]: https://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/
[install-guide]: https://jekyllrb.com/docs/installation/#ubuntu
[setup-guide]: https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/

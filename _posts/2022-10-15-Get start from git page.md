---
title: Start with a GitPage
description: GitPage probably is the best approach to record the daily learning activities. This is a hands-on tutorial of creating your own FREE blog using GitPage.
date: 2022-10-15 23:30:09
categories:
- Tutorial
---

This tutorial is based on MacOS, while setup jekyll in Linux system should work in the similar way.  
GitPage probably is the best approach to create a FREE blog for recording daily learning activities.  
You only need two steps to setup a GitPage:  
[https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site)
[https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)

You can find many templates online, I will take an example of a jekyll theme that I like.  
```sh
git clone https://github.com/Simpleyyt/jekyll-theme-next.git
```

For using jekyll, here is a user manual in Chinese.  
[http://jekyllcn.com/docs/usage/](http://jekyllcn.com/docs/usage/)
English manual link:  
[https://jekyllrb.com/docs/](https://jekyllrb.com/docs/)

<!--create a ruby venv for jekyll to prevent all the version and dependencies issues-->
When install required packages for jekyll, the most challenging part is the version and dependencies. To avoid possible issues, I recommend using a ruby venv instead.
# Install Ruby venv
To install Ruby venv, excecute below commandlines in the terminal:  
1. Install GnuPG
```sh
$ brew install gnupg
```

2. Install GPG keys (either way from below)
```sh
$ gpg --keyserver hkp://pool.sks-keyservers.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
```
**or**  
```sh
gpg --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB
```

3. Install RVM
```sh
$ \curl -sSL https://get.rvm.io | bash
```

4. As the successful installation message showed, close and restart the terminal. Run below command to install the new venv. Be aware that jekyll only works on the Ruby version **2.5.0** and above.
```sh
rvm install 3.1.2
```

5. Check your version list by:
```sh
rvm list
```

6. Create RVM Using Default Ruby Version:
```sh
rvm alias create default 3.1.2
```

- Tips: Some users might encounter the error of "./project.h:119:10: fatal error: 'openssl/ssl.h' file not found", to resolve this issue, run below command to install openssl:
```sh
brew link --force openssl
```

# Start Ruby venv And Install Required Dependencies
1. After install the rvm, start the rvm by runing:
```sh
source /The/Path/To/Your/RVM
```

2. Install jekyll:
```sh
gem install jekyll
```

3. Install Bundler:
```sh
bundle install
```

4. Update Bundler:
```sh
bundle update
```

5. You can always check your token by:
```sh
echo $JEKYLL_GITHUB_TOKEN
```
If it is empty, setup git token in the path by replacing *yourtoken* in your git setup. Token can be found in Git->Settings->Developer Settings->Personal access tokens
```sh
export JEKYLL_GITHUB_TOKEN=yourtoken
```
I only setup it once, even if the next time I didn't run the commandline above and the JEKYLL_GITHUB_TOKEN back to empty, the server can still be established.  

6. If the rvm is using version 3.x.x, also run the commandline below:
```sh
bundle add webrick
```

# Excecute The Preview
To preview the changes on local, run the command:
```sh
bundle exec jekyll server
```
Then the messages in terminal will show the url of local host preview.  
- Tips: Sometimes the local preview might not be established due to the port(the example below uses port 4000) is occupied, run the command line below to locate the pid:
```sh
lsof -wni tcp:4000
```
After validate the redundant process, kill the process by *pid*:
```sh
kill -9 <pid>
```

For more information, please refer to the official article below:  
[https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/testing-your-github-pages-site-locally-with-jekyll)

# Post Blog Articles
To post your article, simply commit and push the changes like using git daily.
# Hexo source files

## Setup
Make sure *Node.js* is installed.
Install *Hexo*:

``` bash
$ npm install
```

Install *Git* deployer:

``` bash
$ npm install hexo-deployer-git --save
```

## Write new posts
Create a new post:

``` bash
$ hexo new "My New Post"
```

More info: [Writing](https://hexo.io/docs/writing.html)

## Deploy to remote sites
Generate and run on local host:

``` bash
$ hexo generate
$ hexo server
```
Then navigate to URL [localhost:4000](https://localhost:4000) in the browser.

Deploy to GitHub.io

``` bash
$ hexo deploy
```

More info: [Deployment](https://hexo.io/docs/deployment.html)


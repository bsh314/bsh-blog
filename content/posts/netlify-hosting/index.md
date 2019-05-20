+++
title = "Netlify, hosting for modern web projects"
description = "Build, deploy, and manage modern web projects using Netlify"
date = "2019-05-20"
tags = [ "netlify", "cloudflare", "hosting", "git", "continous delivery", "https" ]
categories = [ "hosting" ]
type = "post"
+++

![image alt text](/posts/netlify-hosting/header.jpg)

This guide shows how to host your static website for free with about one hour of effort. It’s how I host this blog.

There are a lot of other options awailable (E.g.: [GitHub Pages](https://pages.github.com/), [Forge](https://getforge.com/), [Google Firebase](https://firebase.google.com/docs/hosting?hl=es-419)), but from my experience [Netlify](https://www.netlify.com) is the most convenient out there.

In this guide I'll use [GitHub](https://github.com/) as code repository and [Netlify](https://www.netlify.com) as hosting provider. There will be examples for deployment of static pages created using [Angular](https://angular.io/), [React](https://reactjs.org/), [VueJs](https://vuejs.org/) and [Hugo](https://gohugo.io/).

# Result

Your static website will be atomatically compiled and deployed whenever you push changes to your Git repository. The site will have free [https certificate](https://www.websecurity.symantec.com/security-topics/what-is-ssl-tls-https) and [Cloudflare](https://www.cloudflare.com) protection. You can buy domain name as well, but that procedure will not be covered in this guide.

# Preconditions

You must be able to create project based on [Angular](https://angular.io/), [React](https://reactjs.org/), [VueJs](https://vuejs.org/) or [Hugo](https://gohugo.io/) and Git installed in your system so you can upload source code to repository. I'm assuming you are using Linux or OSX.

# Setting up GitHub

Create new repository with desired project name, in this guide, I'll use <static-example>. Copy URL of git repository by clicking "Clone or download", in advance I'll use \<git-clone-url\> to refer this value. Create static web application project in your local environment and execute those commands in terminal from it's directory.

{{< highlight bash >}}
git init
git remote add origin <git-clone-url>
git add .
git commit -m "INITIAL COMMIT"
git push origin master
{{< / highlight >}}

After this, you should have your project repository with source code on "master" branch. You can create multiple branches for different environments like "development" and "stagging". Netlify allows selection of the specific branch for each site.

# Prepare repository for Netlify integration

Create new `netlify.toml` file in the root directory of your project, it will contain netlify build and publishing configuration. Each static site builder requires different values. 

- Angular:
{{< highlight toml >}}
[build]
    command = "npm run build:prod"
    publish = "dist"
{{< / highlight >}}

- React:
{{< highlight toml >}}
[build]
    command = "yarn build"
    publish = "<project-name>/build/"
    base = "<project-name>/"
{{< / highlight >}}

- VueJs:
{{< highlight toml >}}
[build]
    command = "npm run build"
    publish = "dist"
{{< / highlight >}}

- Hugo:
{{< highlight toml >}}
[build]
    command = "hugo --gc --minify"
    publish = "public"
{{< / highlight >}}

*Netlify provides much more configuration options, read more about them [here](https://www.netlify.com/docs/netlify-toml-reference/)*

# Setting up Netlify

1. In your Netlify account "Sites" tab, create "New site from Git".
2. Chose Github from repository providers list so Netlify can access project repository information.
2. Chose project repository from the list of all repositories awaylable on your github account.
3. Our `netlify.toml` should provide build configuration for Netlify form automatically, if not, please check [Prepare repository for Netlify integration](/posts/netlify-hosting#prepare-repository-for-netlify-integration).
5. Chose `master` repository branch.

You can check Netlify project dashboard to see progress of deployment. By default Netlify provides subdomain url for your project.

# Getting custom domain name

The most common way to adquiere domain name is buing it from providers like [GoDaddy](https://www.godaddy.com) or [Google Domains](https://domains.google/), those can cost you around 10$ a year. There are some free providers as well, for example [Freenom](https://www.freenom.com). Add it as domain to your Netlify account by following domain provider instructions. [More about domain names on Netlify](https://www.netlify.com/docs/dns)

You also can change your netlify site name from site options, this will provide you custom sub-domain name, which is totally free and valid for this guide, but it will contain `<site-name>.netlify.com`.

# Setting up Cloudflare

Now you can add new site to CloudFlare with CNAME record to Netlify and enable enforced SSL from "Crypto" tab of the dashboard. There are a lot of other functions awaylable for free, but more advanced requires payment. Cloudflare provides basic stadistics about your site usage as well.

# Conclusion

At this moment, your project should be stored on GitHub, hosted by Netlify and managed by CloudfFlare. Any time you push changes to project repository, Netlify will compile entire project and deploy the latest version of the application.

All of it completely free!
---
title: Fix Gemfile error diffrent versions of rouge
date: 2021-12-26 16:42
category:
  - Jekyll
  - Development
  - Linux 
author: 
tags: 
  - ruby
  - bundle
  - gemfile
  - rouge
  - "Gem::LoadError"
  - jekyll
  - development
summary: 
---

When trying to check jekyll version I got the following  **Gem::LoadError**


You have already activated rouge 3.27.0, but your Gemfile requires rouge 3.26.0. Prepending `bundle exec` to your command may solve this. (Gem::LoadError)

You solve the issue by clearing bundle

```bash
   bundle clean --force
```
---
layout: post
title:  Rails and Ajax
date:   2019-05-24 20:00:56 +0800
categories: rails
tags: [rails]
---

The general flow to follow when adding Ajax to Rails is...
1. Add `remote: true` to a button that already has a tested and functional HTML-based response
2. Add to corresponding action (e.g. `create`) in the controller that handles the request
```
respond_to do |format|
  format.js
end
```
3. Create a `.js.erb` template that corrspondes to the action in view (e.g. `create.js.erb`)
4. In the ERB template, write JavaScript code to monipulate the DOM

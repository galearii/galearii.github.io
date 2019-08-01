---
layout: post
title:  Skipping Individual Controllers and Actions of Authorization
date:   2019-06-10 21:00:56 +0800
categories: rails
---

You can put the authorization method in the `before_action` filer in the application controller and skip this method individually in each of the controller that doesn't need authorization.

```ruby
# ApplicationController
before_action :authorize

protected
  def authorize
    unless User.find_by(id: session[:user_id])
      redirect_to login_url, notice: "Please log in"
    end
  end
```

```ruby
# StoreController (accessible to everyone)
skip_before_action :authorize
```

```ruby
# CartsController (user can create a cart without logging in)
skip_before_action :authorize, only: [:new, :create]
```

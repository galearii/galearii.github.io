---
layout: post
title:  Handling Errors in Rails
date:   2019-05-23 20:00:56 +0800
categories: rails
tags: [rails]
---

## Controller
You can set your `rescue_from` and the error at the top of the controller and assign it a (normally `private`) method that handles the error.

```ruby
class CartsController < ApplicationController
  rescue_from ActiveRecord::RecordNotFound, with: :invalid_cart

  private
    def invalid_cart
      logger.error "Attempt to access invalid cart #{params[:id]}"
      redirect_to store_index_url, notice: 'Invalid cart'
    end
end
```

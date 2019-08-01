---
layout: post
title:  Rails Cache
date:   2019-05-22 19:00:56 +0800
categories: rails
---

Read more on [Caching with Rails: An Overview](https://guides.rubyonrails.org/caching_with_rails.html)

```
<% cache @products do %>
  <% @products.each do |product| %>
    <% cache product do %>
      <li>
        <%= image_tag(product.image_url) %>
        <h2><%= product.title %></h2>
        <p>
          <%= sanitize(product.description) %>
        </p>
        <div class="price">
          <%= number_to_currency product.price %>
        </div>
      </li>
    <% end %>
  <% end %>
<% end %>
```

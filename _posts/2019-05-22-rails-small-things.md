---
layout: post
title:  Some small things in Rails
date:   2019-05-22 20:00:56 +0800
categories: rails
tags: [rails]
---

*Some small things worth remembering for a Rails noob*

----
`root 'store#index', as: 'store_index'`

The `as: 'store_index'` part makes Rails generate `store_index_path` and `store_index_url` helper methods.

---
In view, use `sanitize(html_content)` to safely output content with HTML tags.

---
In view, use `number_to_currency(a_number)` to automatically show a number as currency.

---
With a module shared among controllers (stored in app/controllers/concerns), if a method is defined as `private`, it prevents Rails from making it availalbe as an action on the controller.

---
“A great rule of thumb for where to put `belongs_to` declarations is this: if a table has any columns whose values consist of ID values for another table (this concept is known by database designers as foreign keys), the corresponding model should have a `belongs_to` for each.”

---
Models have direct access to the `errors` object, the same place where the `validates` method stores error messages. Errors can be associated with individual attributes or to the `:base` object.

```ruby
errors.add(:base, 'Line Items present')
```

---
In a model, `throw :abort` in a `before_destroy` hook makes sure the row isn't destroyed.

---
Use `link_to` to GET pages; use `button_to` to POST things.

`button_to` creates a form.

---
When adding non-standard Rails migration, always define `up` and `down` to make it possible to both `db:migrate` and `db:rollback`.

---
With partials, Rails `render`s a collection "automatically," provided the collection has a template file with the same name in a directory with the same name and a database table that has the same name.

Provided the following, Rails automatically finds a `_line_item.html.erb` partial in the views/line_items directory to render,
```
<%= render(@cart.line_items) %>
```

and Rails also makes individual `line_item` available to the template file (i.e. you don't need to manually `.each do` through the collection).
```
<tr>
  <td class="quantity"><%= line_item.quantity %></td>
  <td><%= line_item.product.title %></td>
  <td class="price"><%= number_to_currency(line_item.total_price) %></td>
  <td><%= button_to('Remove', line_item_path(id: line_item.id), method: :delete) %></td>
</tr>
```

---
In a Rails app, when logic becomes more complex than a line or two of code, you want to move that out of _controller_ and into _model_.

---
Specifying 'password:digest' will generate a password_digest field of string type, and configure your generated model and tests for use with Active Model has_secure_password (assuming the default ORM and test framework are being used).

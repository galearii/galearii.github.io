---
layout: post
title:  The /lib Directory
date:   2019-06-14 21:00:56 +0800
categories: rails
---

- The `lib` directory holds application code that doesn't fit naturally into a model, view, or controller.
- The `lib` directory is also a good place that holds code that's shared among models, views, and controllers.
- To have Rails autoload files, add `config.autoload_paths += %W(#{Rails.root}/lib)` to `config/application.rb`.
- Files in the `lib` directory can be further organized into subdirectories.
  - If the files contain classes or modules and the files are named using the lowercase form of the class or module name, then Rails will autoload the file.
    - Rails autoloads the `PdfStuff::Receipt` class defined in `lib/pdf_stuff/receipt.rb`
  - Use `require` for situations where Rails cannot autoload the files.
    - `require "easter"` loads in `lib/easter.rb`
    - `require "shipping/airmail"` loads in `lib/shipping/airmail.rb`

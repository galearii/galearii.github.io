---
layout: post
title:  Using React in Rails through Webpacker
date:   2019-05-30 20:00:56 +0800
categories: rails
---

From _Agile Web Development with Rails 6_:
> The core concept in React is _components_. A component is a view, backed by some sort of state. When the state changes, the view rerenders. The view can behave differently depending on the current state inside the component.

You can use the `javascript_pack_tag('component_name')` in individual view to load in the JavaScript code only when necessary.

Webpacker is configured with certain paths to locate files we ask to `import`:
1. `node_modules`: Where Yarn downloads third-party JavaScript libraries
2. app/javascript

Steps of creating a React component:
1. Create a new pack in javascript/packs that holds the code. Consider this the 'controller' that gathers and drives the resources to create your desired behavior on the page. This is also the 'pack' that you include on a page.
2. Implement the component. The code and files of the component goes into an individual folder in the app/javascript folder, with an index.jsx as the entry point.
3. Bring the pack to view through `javascript_pack_tag`

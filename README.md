# underscore-partials [![Build Status](https://api.travis-ci.org/khepin/underscore-partials.svg?branch=master)](https://travis-ci.org/khepin/underscore-partials)

> underscore-partials lets you use templates within templates for abstraction and reuse.

Example:
```html
<!-- star_rating.tmpl -->
<% for (var i = 0; i < rating; i++) { %>
    *
<% } %>

<!-- main.tmpl -->
<h1><%= product.name %></h1>
<div><%= _.template.partial('star_rating', {rating: product.rating}) %></div>
```

```javascript
var template = _.template(main.tmpl);
_.template.partial.declare('star_rating', star_rating.tmpl);
template({product: {name: "DVD Player", rating: 3}});
```

Will output
```html
<h1>DVD Player</h1>
<div>***</div>
```

# API

```javascript
// Declare a partial
_.template.partial.declare('partial_name', partialString);

// Declare a partial with specific template settings
_.template.partial.declare('partial_name', partialString, {
  interpolate: ...,
  evaluate: ...,
  escape: ...,
  data: ...
});

// Use a partial
_.template.partial('partial_name');
// or
_.template.partial('partial_name', partial_data);

// Check if a partial exists
_.template.partial.exists('partial_name');

// Remove a partial that was declared before
_.template.partial.remove('partial_name');

```

# Contributing

## Setup the dependencies

    npm install -g bower
    bower install

## Setup Grunt

    npm install -g grunt-cli
    npm install

## Run the test suite

    grunt test

# Licence

This software is released under the MIT open source licence.

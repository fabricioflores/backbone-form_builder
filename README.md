backbone-form_builder
=====================

`form_builder` makes creating Backbone forms super easy.

I've only tested it with CoffeeScript, but it should work with
javascript templates also.

Usage
-----

Require `form_builder` after backbone.

Using `skim`:

```skim
== form_for @current_user, autocomplete: 'off', (f) ->
  == f.text_field 'username', autocapitalize: 'off'
  == f.password_field 'password'

  == f.submit "Sign In"
```


Using `eco`:

```eco
<%- form_for @current_user, autocomplete: 'off', (f) -> %>
  <%- f.text_field 'username', autocapitalize: 'off' %>
  <%- f.password_field 'password' %>
  <%- f.submit "Sign In" %>
<% end %>
```

The `error` class is added to fields with validation errors.
You can display the errors with `errors_for`:

```skim
== form_for @current_user, (f) ->
  == f.errors_for 'username'
  == f.text_field 'username'
```

The available methods are:

* `f.input(type, attribute, options = {})`
* `f.text_field(attribute, options = {})`
* `f.password_field(attribute, options = {})`
* `f.label(attribute, body = attribute, options = {})`
* `f.select(attribute, choices = {}, options = {})`
* `f.submit(value, options = {})`

You can customize html attributes by passing options:

```skim
== form_for @current_user, autocomplete: 'off', (f) ->
  == f.text_field 'username', id: 'username'
```

The default `id` 

`select` takes a `choices` object to create a series of `<option>` tags:

```skim
== f.select "color", red: "Red", blue: "Blue"
```

Renders as:

```html
<select name="color">
  <option value="red">Red</option>
  <option value="blue">Blue</option>
</select>
```





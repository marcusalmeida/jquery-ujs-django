jquery-ujs for Django
========================================
ATTENTION: This is a copy (without rails code) from https://github.com/aliang/jquery-ujs-django.git. Thanks aliang for the it.

Works like the one for Rails. Django's CsrfMiddleware differs from Rails's CSRF protection in the following ways:

- The CSRF token is included in the HTML on a per form basis, instead of as a meta tag in the head element of your HTML
- The CSRF token is sent as a POST parameter instead of as an HTTP header

We modified the django-ujs.js file to reflect these changes. It's still called rails.js in the repo, though.

The additional POST parameter is named 'csrfmiddlewaretoken'. To get the token, it uses the selector "#csrf_token input" and reads the resulting element's value attribute. The easiest way to set this up is to put something like

    <form id="csrf_token" style="display:none">{% csrf_token %}</form>

in your template. I haven't updated the tests to reflect the new token placement.

[You can download the file here.](https://github.com/marcusalmeida/jquery-ujs-django/raw/master/src/django-ujs.js) After you have the hidden token element included in your HTML, load the JavaScript file in your page after jQuery has loaded.

Unobtrusive scripting adapter for jQuery
========================================

This unobtrusive scripting support file was developed for the Ruby on Rails framework, but is not strictly tied to any specific backend. You can drop this into any application to:

- force confirmation dialogs for various actions;
- make non-GET requests from hyperlinks;
- make forms or hyperlinks submit data asynchronously with Ajax;
- have submit buttons become automatically disabled on form submit to prevent double-clicking.

These features are achieved by adding certain ["data" attributes][data] to your HTML markup.

Full [documentation is on the wiki][wiki], including the [list of published Ajax events][events].

Requirements
------------

- [jQuery 1.4.3][jquery] or later;
- for Ruby on Rails only: `<%= csrf_meta_tag %>` in the HEAD of your HTML layout;
- HTML5 doctype (optional).

If you don't use HTML5, adding "data" attributes to your HTML4 or XHTML pages might make them fail [W3C markup validation][validator]. However, this shouldn't create any issues for web browsers or other user agents.

Installation
------------

[Download jQuery][jquery] and ["django-ujs.js"][adapter] and place them in your "javascripts" directory.


[data]: http://dev.w3.org/html5/spec/elements.html#embedding-custom-non-visible-data-with-the-data-attributes "Embedding custom non-visible data with the data-* attributes"
[wiki]: https://github.com/rails/jquery-ujs/wiki
[events]: https://github.com/rails/jquery-ujs/wiki/ajax
[jquery]: http://docs.jquery.com/Downloading_jQuery
[validator]: http://validator.w3.org/
[csrf]: https://docs.djangoproject.com/en/1.3/ref/contrib/csrf/l
[adapter]: https://github.com/marcusalmeida/jquery-ujs-django/raw/master/src/django-ujs.js

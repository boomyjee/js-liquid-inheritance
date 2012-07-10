# js-liquid-inheritance

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](./LICENSE)

`Liquid` plugin to support template inheritance

## Features
- Layout extending
- Block overwrite


## Example
```html
<!doctype html>
<html>
    <head>
        <title>Js Liquid `Block` & `Extend`</title>
        <meta charset="utf-8">
        <script src="./liquid.js"></script>
        <script src="../liquid-inheritance.js"></script>
    </head>
    <body>

    <script id="layout" type="text/html">
        {% block 'title' %} <h1>Layout</h1> {% endblock %}
        {% block 'subTitle' %} <h3>Welcome to `{{ name }}` demo</h3> {% endblock %}
    </script>   

    <div id="demo_page">
        {% extends "layout" %}
        {% block 'title' %} <h2>Demo page</h2>  {% endblock %} 
    </div>

    <script>
        Liquid.readTemplateFile = function(path) {return document.getElementById(path).innerHTML;}
        var content = document.getElementById('demo_page');
        var tpl = Liquid.parse(content.innerHTML)
        content.innerHTML = tpl.render({name: 'liquid'});
    </script>

    </body>
</html>
```
Result:  
```html
<div id="demo_page">
    <h1>Demo page</h1>  
    <h3>Welcome to `liquid` demo</h3> 
</div>
```

You can test this example executing `demo/index.html`.

### License

Plugin is [MIT licensed](./LICENSE).

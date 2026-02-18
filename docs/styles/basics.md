# Style basics

Styles are primarily used to style vector features in Origo but are also used to create layer legends. This means that all layers in Origo should have a style.

Styles are created using [OpenLayers styles](https://openlayers.org/en/latest/apidoc/module-ol_style_Style-Style.html). In OpenLayers styles are created as JavaScript functions but in Origo the creation is simplified and only json syntax is used. All styles must have a name which is used to reference the style from a layer. A simple GeoJson layer example can be seen to the right.

Styles can be compared to building blocks. The smallest building block is a style which can be a fill, stroke, circle, icon or text. These styling blocks can be put together for example to style a polygon layer with a fill, stroke and text style. By combining these blocks more complex styling can be made. Two levels of styling are available where each level is delimited by brackets. The outer level is used to separate styles with filters, see the example [thematic styling](examples.md#thematic-styling). The inner level is used to add layers of various styles, see the example [combining styles](examples.md#combining-styles). The two levels of brackets must always be provided even if only one fill style is used.

For more advanced styling it is possible to use a custom style function. This function has to be included in the /src/style/stylefunctions.js. You will still need an usual style/icon for display in the legend. [Example](examples.md#custom-style-function)

#### Example defining a layer style

```json
{
  "name": "mylayer",
  "title": "My layer",
  "source": "data/layer.geojson",
  "style": "mask",
  "type": "GEOJSON",
  "visible": true
}
```

```json
{
  "styles": {
    "mask": [
      [
        {
          "stroke": {
            "color": "rgba(0,0,0,1.0)"
          },
          "fill": {
            "color": "rgba(0,0,0,0.5)"
          }
        }
      ]
    ]
  }
}
```

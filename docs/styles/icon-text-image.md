# Icon, Text & Image

### Icon

An icon style can be defined with the OpenLayers options for an [Icon](https://openlayers.org/en/latest/apidoc/module-ol_style_Icon-Icon.html). Size and src are required.

Icon rotation can be set with `"rotation"`, either by using a fixed value or by specifying an attribute holding rotation values. In the latter case, the attribute name should be enclosed in double curly braces. Rotation values should always be in degrees.

#### Icon example

```json
{
  "icon": {
    "size": [32, 32],
    "src": "data/png/my_icon.png"
  }
}
```

### Text

A text style can be defined with the OpenLayers options for a [Text](https://openlayers.org/en/latest/apidoc/module-ol_style_Text-Text.html). The fill option sets the font color and the stroke option is used to create halo effects.

Arbitrary text can be provided as text value. For cluster layers the reserved word "size" can be used to show number of features of the cluster.

#### Text example with static text

```json
{
  "text": {
    "font": "Bold 12px Arial",
    "textAlign": "center",
    "offsetX": 10,
    "offsetY": -10,
    "text": "My label text",
    "fill": {
      "color": "rgba(0,0,0,1.0)"
    },
    "stroke": {
      "color": "rgba(255,255,255,0.7)",
      "width": 2
    }
  }
}
```

#### Example with text from attribute

```json
{
  "text": {
    "font": "14px Arial",
    "textAlign": "center",
    "offsetX": 10,
    "offsetY": -10,
    "text": "{{name}}",
    "fill": {
      "color": "rgba(0,0,0,1.0)"
    },
    "stroke": {
      "color": "rgba(255,255,255,0.7)",
      "width": 2
    }
  }
}
```

### Image

The image style is not used to style features. It is only used for legend purposes, for example to symbolize a raster layer in the legend. Only the src property is set.

#### Image

```json
{
  "image": {
    "src": "img/png/gra.png"
  }
}
```

### Legend graphics

Map server legend graphics (WMS only) can be used in the legend. Please note that this will not change the layer style.

#### Legend graphics

```json
{
  "icon": {
    "src": "URL for GetLegendGraphic request (or any other static image asset)"
  },
  "extendedLegend": true
}
```

### Label

The label shown for the style in the layermanager/legend when clicking the layer name. If omitted, none is shown.

#### Label

```json
{
  "label": "Label for the layer"
  }
}
```

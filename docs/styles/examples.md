# Style examples

To get started some common use cases are provided.

### Opacity

Colors are defined with rgba values. Opacity is set with the alpha channel, the a part of rgba. In this example the fill is semi-transparent.

#### Opacity

```json
{
  "styles": {
    "simple": [
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

### Combining styles

Different styles can be combined to create complex styles. In this example the features will be styled with two circle styles, one inner circle and one outer circle. The inner circle has the radius 4 and the outer circle the radius 16. Styles are combined by adding styles within the same brackets and are seperated by curly brackets.

#### Combining styles

```json
{
  "styles": {
    "doubleCircle": [
      [
        {
          "circle": {
            "radius": 16,
            "stroke": {
              "color": "rgba(0,0,0,1)",
              "width": 5
            },
            "fill": {
              "color": "rgba(255,255,255,0.9)"
            }
          }
        },
        {
          "circle": {
            "radius": 4,
            "stroke": {
              "color": "rgba(0,0,0,0)",
              "width": 1
            },
            "fill": {
              "color": "rgba(37,129,196,1)"
            }
          }
        }
      ]
    ]
  }
}
```

### Thematic styling

By applying filters thematic styling can be made. In this example features with the attribute type equal to vegetation will be green and features with the attribute type equal to water will be blue. The style settings for each type are grouped by brackets. You are also able to add a label to each filter.

#### Thematic styling

```json
{
  "styles": {
    "thematic": [
      [
        {
          "fill": {
            "color": "rgba(0,255,0,0.5)"
          },
          "stroke": {
            "color": "rgba(0,255,0,1)",
            "width": 2
          },
          "filter": "[type] == 'vegetation'",
          "label": "Vegetation"
        }
      ],
      [
        {
          "fill": {
            "color": "rgba(0,0,255,0.5)"
          },
          "stroke": {
            "color": "rgba(0,0,255,1)",
            "width": 2
          },
          "filter": "[type] == 'water'",
          "label": "Water"
        }
      ]
    ]
  }
}
```

### Center point

Geometry calculations can be used to style features. In this example the center point within a polygon is styled with an icon. This is done by adding a geometry property with the value "centerPoint" for the icon style.

#### Center point of polygon

```json
{
  "styles": {
    "center": [
      [
        {
          "stroke": {
            "color": "rgba(103,60,31,1.0)",
            "width": 1
          },
          "fill": {
            "color": "rgba(103,60,31,0.1)"
          }
        },
        {
          "icon": {
            "size": [23, 36],
            "src": "img/png/droppe.png"
          },
          "geometry": "centerPoint"
        }
      ]
    ]
  }
}
```

### Cluster style

When creating a style for a cluster layer it is usually desired to show the number of features in each cluster. This can be done be by using the reserved word "size" in which case the number of features will be used as text value. Other text properties are provided as usual.

#### Cluster style with size as text

```json
{
  "styles": {
    "cluster": [
      [
        {
          "circle": {
            "radius": 16,
            "fill": {
              "color": "rgba(103,60,31,0.5)"
            },
            "stroke": {
              "color": "rgba(103,60,31,0.9)",
              "width": 4
            }
          }
        },
        {
          "text": {
            "font": "Bold 12px Arial",
            "textAlign": "center",
            "text": "size",
            "fill": {
              "color": "rgba(255,255,255,1.0)"
            },
            "stroke": {
              "color": "rgba(103,60,31,0.9",
              "width": 2
            }
          }
        }
      ]
    ]
  }
}
```

### Custom style function

For more advanced styling you can use a custom style function and for instance style features depending on multiple attribute values or use more complex filters and styling techniques.

#### Style function included in src/style/stylefunctions.js with a .png-icon for presentation in the legend.

```json
{
  "styles": {
    "basemap": [
      [
        {
          "custom": "basemapStyle",
          "icon": {
            "src": "img/png/basemap.png",
            "size": [20, 20]
          }
        }
      ]
    ]
  }
}
```

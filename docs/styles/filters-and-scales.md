# Filters & Scales

### Alternative WMS style

Option to pick an alternative layer style for WMS layers. Requires alternative style to be published on map server.

#### Alternative WMS style

```json
{
  "icon": {
    "src": "..."
  },
  "wmsStyle": "Name of alternative WMS style"
}
```

### Filter

Features can be filtered by attributes, enabling [thematic styling](examples.md#thematic-styling). Filters can be defined using relational and logical operators. Regular expressions can be used if enclosed in forward slashes.

#### Filter

```json
"style_example": [
  [
    {
      "icon": {
      "src": "..."
      },
      "filter": "[attributename] == 'Value'", // basic string comparison
      "label": "Label shown in legend"
    }
  ],
  [
    {
      "icon": {
      "src": "..."
      },
      "filter": "[attributename] === '/^(?!.*stad$).*/'",  // using regular expression enclosed in slashes like this /regex/
      "label": "Label shown in legend"
    }
  ],
  [
    {
      "icon": {
      "src": "..."
      },
      "filter": "[attributename] > 'Value' AND [attributename] !== 'Other value'", // using relational and logical operator
      "label": "Label shown in legend"
    }
  ]
]


```

### minScale and maxScale

To use different styles at different zoom levels.

#### minScale and maxScale

```json
"areas": [
  [
    {
      "maxScale": 12500,
      "minScale": 100000,
      "fill": {
        "color": "rgba(66,89,179,0.4)"
      },
      "stroke": {
        "color": "rgba(60,43,0,0.8)",
        "width": 1.5
      },
      "label": "Style for small scale"
    }
  ],
  [
    {
      "minScale": 12499,
      "fill": {
        "color": "rgba(66,89,179,0.2)"
      },
      "stroke": {
        "color": "rgba(60,43,0,0.8)",
        "width": 1.5
      },
      "label": "Style for big scale"
    }
  ]
]
```

### header

The icon shown in the legend. If true, this symbol will overwrite the default list icon used when having a thematic style. Default is false.

#### header

```json
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
	"label": "Vegetation",
	"header": true
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
```

### hidden

Makes a style hidden in the legend. Default is false. In this example the "Style for small scale" will not be displayed in the layers legend.

#### hidden

```json
"areas": [
  [
    {
      "maxScale": 12500,
      "minScale": 100000,
      "fill": {
        "color": "rgba(66,89,179,0.4)"
      },
      "stroke": {
        "color": "rgba(60,43,0,0.8)",
        "width": 1.5
      },
      "label": "Style for small scale",
      "hidden": true
    }
  ],
  [
    {
      "minScale": 12499,
      "fill": {
        "color": "rgba(66,89,179,0.2)"
      },
      "stroke": {
        "color": "rgba(60,43,0,0.8)",
        "width": 1.5
      },
      "label": "Style for big scale"
    }
  ]
]
```

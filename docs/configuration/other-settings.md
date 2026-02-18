# Other settings

### attributeAlias
Key-value pairs to swap an attribute name for an alias. Used with the default featureinfo template.

#### Example attributeAlias

```json
"attributeAlias": {
  "name": "Namn",
  "strl": "Storlek"
}
```

### clusterOptions
Can also be set on layer or source level.

Property | Type | Description
---|---|---
`clusterDistance` | number | The distance in pixels within which features will be clustered. Default is 60.
`clusterMaxZoom` | number | The zoom level where the features no longer will be clustered. Default is the last zoom level.

#### Example clusterOptions

```json
{
  "clusterOptions": {
    "clusterDistance" : 40,
    "clusterMaxZoom" : 2
  }
}
```

### tileGridOptions

Property | Type | Description
---|---|---
`alignBottomLeft` | boolean | Whether to align grid to top or bottom left corner. Default is true.
`extent` | array | Extent for the tilegrid. Used to calculate the tiles position. If omitted maps extent is used.
`minZoom` | number | Minimum zoom level. Defaults to 0.
`resolutions` | array | Resolutions for the tilegrid. If omitted maps resolutions are used.
`tileSize` | number or array | Size of tiles in the tileGrid. Default is [256,256]
`origin` | array | If origin is set it is used instead of top/bottom left coordinate of the extent. Optional

#### Example tileGridOptions

```json
"tileGridOptions": {
  "alignBottomLeft": false,
  "tileSize": 512
}
```

### layerParams
Set of parameters to add to a layer configuration. If a setting is present in both layerParam and the layer itself, the layer setting will win.

#### Example layerParams

```json
"layerParams": {
  "default": {
    "group": "root",
    "visible": true
  }
},
"layers": [
  {
    "name": "origo-cities",
    "title": "Origokommuner",
    "source": "data/origo-cities-3857.geojson",
    "style": "origo-logo",
    "type": "GEOJSON",
    "attributes": [
      {
        "name": "name"
      }
    ],
    "layerParam": "default"
  }
```


### palette
Array of colors used in the stylewindow when for instance styling features in the draw tool. Will replace the default colors.

#### Example palette

```json
"palette": ["rgb(0,0,0)", "rgb(255,255,255)", "rgb(0,255,255)", "rgb(255,0,255)", "rgb(166,206,227)", "rgb(31,120,180)", "rgb(178,223,138)", "rgb(51,160,44)", "rgb(251,154,153)", "rgb(227,26,28)", "rgb(253,191,111)"]
```

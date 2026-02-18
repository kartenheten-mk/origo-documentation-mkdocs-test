# Measure control

Adds a measure control. Measure length, area, buffer or elevation (requires access to external elevation data web service) in the map.

Property | Description
---|---
`name` | the name of the control (measure)
`options` | options for the control

Option | Description
---|---
`measureTools` | Array of tools to use. Valid are 'length', 'area', 'elevation' and 'buffer'. Default is ["length", "area"].
`default` | What tool to use as default. Default is 'length'.
`elevationServiceURL` | URL to elevation data web service, with variable parameters enclosed in curly braces. Applicable variables are `{easting}` and `{northing}`. Required if using elevation tool.
`elevationTargetProjection` | Projection code for coordinates to be sent to an elevation web service, if other than the current map projection.
`elevationAttribute` | "Path" to the elevation data attribute in the web service response. Required if using elevation tool.
`showSegmentLengths` | True or false if individual segment lengths should be shown. Default is false.
`showSegmentLabelButtonActive` | True or false if the label for segment lengths should be active or not from start. Default is true.
`snap` | Enables snapping. Defaults to false.
`snapIsActive` | Sets the initial state of the snap.
`snapLayers` | Array of layers that snap is enabled for. If undefined, snap will be enabled for all layers.
`snapRadius` | Distance from point where snap is triggered.
`useHectare` | True or false if hectare should be used for area between 10 000 and 1 000 000 square meters. Default is true and hectare is used, false and square meters is used.
`highlightColor` | Second (outer) color of the measure lines. Valid input is an rgba string, see below for example. Defaults to a light blue.
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.
`queryable` | if set to true, the features in the measure layer is clickable and will show its length/area. Defaults to false.

#### Example measure control

```json
{
  "name": "measure",
  "options": {
    "measureTools": ["length", "area"],
    "default": "length",
    "highlightColor": "rgba(133, 193, 233, 0.8)"
  }
}
```

#### Example measure control with elevation data tool

```json
{
  "name": "measure",
  "options": {
    "measureTools": ["length", "area", "elevation"],
    "default": "length",
    "elevationServiceURL": "https://maps.googleapis.com/maps/api/elevation/json?locations={northing},{easting}&key=MY_API_KEY",
    "elevationProjection": "EPSG:4326",
    "elevationAttribute": "results[0].elevation"
  }
}
```

#### Example measure control with snap enabled

```json
{
  "name": "measure",
  "options": {
    "snap": true,
    "snapIsActive": true,
    "snapLayers": [
      "origo-cities"
    ],
    "snapRadius": 15
  }
}
```

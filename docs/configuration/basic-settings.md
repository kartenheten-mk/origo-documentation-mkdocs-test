# Basic settings

Basic settings for the application include map options such as projection and extent. Note that all OpenLayers map and view settings of string, number or boolean type (or arrays/objects thereof) can be set in the config file, on the first level. Please see the OpenLayers [map](https://openlayers.org/en/latest/apidoc/module-ol_Map-Map.html#Map) or [view](https://openlayers.org/en/latest/apidoc/module-ol_View-View.html#View) documentation for more information about available settings.

## Page settings

With the pageSettings object you can define a footer and control the visibility of the map grid.

#### Example page settings definition

```json
{
"pageSettings": {
  "footer": {
    "img": "img/png/logo.png",
    "url" : "https://github.com/origo-map/origo",
    "text": "Origo"
  },
  "mapGrid": {
    "visible": true
  },
  "mapInteractions": {
    "embedded": false
  }
}
}
```

### footer

Name | Type | Description
---|---|---
`img` | string | URL or file path to an image.
`text` | string | Text to be displayed.
`url` | string | Sets the URL for a link.

### mapGrid

Name | Type | Description
---|---|---
`visible` | boolean | Sets the visibility of the map grid. Default is false.

### mapInteractions

Name | Type | Description
---|---|---
`embedded` | boolean | Sets if special map interactions for embedded maps should be used or not. Default is true.

## Map projection
The map projection is defined with the mandatory property projectionCode. If the projection is EPSG:3857 (Web mercator) or EPSG:4326 (WGS84) then the proj4Defs is optional, otherwise it is mandatory. An optional projection extent can also be set. Projections are handled with the proj4js library. The Proj4js definitions can be found on [epsg.io](http://epsg.io/).

#### Example projection definition

```json
{
"projectionCode": "EPSG:3010",
"proj4Defs": [
      {
          "code": "EPSG:3010",
          "alias": "urn:ogc:def:crs:EPSG::3010",
          "projection": "+proj=tmerc +lat_0=0 +lon_0=16.5 +k=1 +x_0=150000 +y_0=0 +ellps=GRS80 +towgs84=0,0,0,0,0,0,0 +units=m +no_defs"
      }
],
"projectionExtent": [
  -1678505.1838360203,
  4665380,
  2431912.7361639794,
  8775797.92
]
}
```

### proj4Defs

Name | Type | Description
---|---|---
`proj4Defs` | array | The proj4 definitions for projections used in the map. Several projections can be definied but the projection set as projectionCode will be the map projection. Each projection is defined as an object. Visit [epsg.io](http://epsg.io/) to find proj4 definitions. EPSG:3857 (Web mercator) and EPSG:4326 (WGS84) doesn't need to be defined.

Name | Type | Description
---|---|---
`code` | string | The EPSG-name.
`alias` | string | An optional EPSG alias.
`projection` | string | The Proj4js definition for the projection.

### projectionCode

Name | Type | Description
---|---|---
`projectionCode` | string | The EPSG-name for the projection that will be used when the map is created. Visit [epsg.io](http://epsg.io/) to find the EPSG-code.

### projectionExtent

Name | Type | Description
---|---|---
`projectionExtent` | array | Extent that will be set for the projection.

## extent

Name | Type | Description
---|---|---
`extent` | array | Constraining extent for map layers.

## center

Name | Type | Description
---|---|---
`center` | array | The intial center coordinates for the map.

## zoom

Name | Type | Description
---|---|---
`zoom` | number | Initial zoom level for the map.

## resolutions

Name | Type | Description
---|---|---
`resolutions` | array | The resolutions used to define available zoom levels for the map. The resolutions should be valid for the base maps.

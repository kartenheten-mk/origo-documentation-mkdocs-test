# External url control

Adds a button that will send the center coordinates in an url template and opens the url in a new browser tab. When configuring more than one link, the button expands and displays a button for each url.

Property | Description
---|---
`name` | the name of the control (externalurl)
`options` | options for the control

Option | Description
---|---
`icon` | optional, defaults to `#ic_baseline_link_24px`. Other icons are possible.
`tooltipText` | the tooltip text for the button
`direction` | option to control the subbutton display orientation. Optional, defaults to "vertical". "horizontal" is possible.
`links` | options for the links. Configured as a list. Available options are listed below.
`target` | default behaviour is to open url in new window (_blank). It's possible to specify other targets as _top, _self and _parent. Optional.
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.

Links option | Description
---|---
`name` | the name of the link. Optional.
`tooltipText` | the tooltip text for the button. Optional.
`method` | the method/format that the coordinates will be send in. Valid values are “LatLon”, “XY” and "none". Required. Method "none" can be used when sending coordinates is not needed.
`projection` | the projection of the external web map services. The projection must be defined in proj4Defs, except EPSG:4326, EPSG:4269, EPSG:3857, EPSG:3785, EPSG:900913, EPSG:102113 or GOOGLE, which are included by default. Default is EPSG:3857.
`url` | url to the external endpoint. Coordinates can be defined within curly brackets. If method is set as “LatLon” then {{LAT}} and {{LON}} must be available in the url. If method is set as “XY” then {{X}} and {{Y}} must be available. Required.
`buttonImage` | path to the button image. If not specified, a default image is displayed. Optional.

#### Example external url control

```json
{
  "name": "externalurl",
  "options": {
       "tooltipText": "Kartlänkar",
       "links": [
           {
            "tooltipText": "OpenStreetMap",
            "method": "LatLon",
            "projection": "EPSG:3857",
            "url": "https://www.openstreetmap.org/#map=17/{{LAT}}/{{LON}}",
            "buttonImage": "img/png/osm.png"
           },
           {
            "tooltipText": "Google street view",
            "method": "LatLon",
            "url": "https://www.google.com/maps/@?api=1&map_action=pano&viewpoint={{LAT}},{{LON}}&heading=-45&pitch=10&fov=80",
            "buttonImage": "img/png/google_street_view.png"
          }
         ]
    }
}
```

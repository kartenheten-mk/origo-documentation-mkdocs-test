# featureinfoOptions

Property | Type | Description
---|---|---
`clusterFeatureinfoLevel` | number | Zoom level where cluster layers will be identifiable. Default is 1.
`pinning` | boolean | Option to enable/disable pinning. If enabled a pin will be placed where clicked in places with no identifiable features. Default is true.
`hitTolerance` | number | Option to set the hit tolerance in pixels. Features within this tolerance from a click will be considered. This makes it easier to click features on touch devices. Default is 0.
`infowindow` | string | Option to show featureinfo in overlay, sidebar or infowindow. Default is overlay.
`infowindowOptions` | object | Options for infowindow. Currently only useful when using infowindow as infowindow. See options below. Optional.
`selectionStyles` | object | Option to set custom selection style. Optional.
`multiSelectionStyles` | object | Option to set custom selection style for `selected` features, features `inActiveLayer` and `highlighted` features when using infowindow as infowindow. Optional.
`toggleSelectOnClick` | boolean | Option to enable/disable selection toggling. Used with the multiselection plugin and defaults to false.
`changePointerOnHover` | boolean | When set to true, the mouse pointer changes when hovering over a clickable object. Optional. Defaults to false.
`imageFeatureInfoMode` | string | Option to set the map level featureinfo mode for image type (WMS, AGS_MAP/TILE etc) layers. The default is `pixel` which will produce feature info if the pixel targeted of a feature of a visible layer isn't totally transparent. Alternatives are `visible` which works on wholly transparent styles too and `always` which will produce feature info even for layers that are not visible. This option is available at the layer level as well and where present there will override the map level option. Optional.
`autoplay` | number | Option to let a carousel attribute images to rotate, set a number in milliseconds. Optional. Defaults to false.

## infowindowOptions

Name | Type | Description
---|---|---
`title` | string | Infowindow header text. Default is "Träffar".
`listLayout` | boolean | Option to show layers as a list. Default is false.
`export` | object | Defines settings for the export. Two different export options are possible, server side and client side. Server side export requires a server endpoint and can be configured either as a simple export or layer specific export. All three export types can be used together. Currently only attributes can be sent with server side export.
`groupAggregations`| array of groupAggregation objects | If specified an aggregation of features in each layer is displayed for a selection. E.g. sum of all area. Multiple aggregations can be configured.

## export properties

Name | Type | Description
---|---|---
`toasterMessages` | object  | Status message to the user. Defines messages for "success" and "fail". Default message is "Success!" and "Sorry, something went wrong, please contact your administrator." Currently only fail message is shown.
`layerSpecificExport` | array | Sends requests using selected objects per layer to one or more server endpoints. Each layer is defined as an object with the layer name and an array of exportUrls with settings for the exports. See exportUrls properties below for export modes.
`simpleExport`| object | Sends all attributes from selected objects per layer to a server endpoint. Defines layers and service url for the export.
`clientExport`| object | Configuration for exporting layers without the need of a server.

## layerSpecificExport properties

Name | Type | Description
---|---|---
`layer` | string | Defines a layer that can export selected objects.
`exportUrls` | array | Defines settings for one or more exports. The settings (except `url`) can also be defined at this level, directly under `layerSpecificExport`, as default values used by all `exportUrls`. Each export is defined as an object.

## exportUrls properties

Name | Type | Required | Description
---|---|---|---
`url` | string | Yes | Url to a service.
`button` | object | Yes | Configuration for using a text button or a round button. See below.
`urlParameters` | object | No | Adds URL parameters to the request as key-value pairs. Each property is added as a URL parameter, with the key as parameter name and the value as the parameter value. Fill parameter values with values from selected objects' attributes by setting a property value to an object with an attribute property: `{ "attribute": "objekt_id", "separator": ";"}`. The separator character can be customized but uses semicolon by default. Set a property value to `null` to add the parameter without the equals sign or value.
`requestMethod` | string | No | The type of request to send. Can be one of `"POST_JSON" | "OPEN" | "GET"`. Defaults to `POST_JSON`. <br><ul><li>`POST_JSON` sends the attributes of selected features per layer as a JSON body in a POST request.</li><li>`OPEN` opens the url in a new browser tab/window.</li><li>`GET` Makes a GET request. Also set `"displayExportResponse": true` to display the response.</li></ul>
`attributesToSendToExport` | array | Conditional | Attributes to send to the export service. Required when using `POST_JSON` mode.
`exportedFileName` | string | Conditional | File name and file extension for the export. The file extension must match the file extension from the service. Required when using `POST_JSON` mode and recieving non-JSON responses.
`displayExportResponse` | boolean | No | Defaults to false. If true, when using `GET` mode, the request's response will be displayed in the infowindow. Supports images and text (`text/plain | application/json`) Non-image content must come from the same domain or be otherwise allowed by CORS restrictions.

## simpleExport properties

Name | Type | Description
---|---|---
`url` | string | Url to a service. Exports all attributes from the layer source. Can be used with excel creator in Origo server. Required.
`layers` | array of string | List of layer names that are allowed to export selected objects. Required.
`button` | object | Configuration for using a text button or a round button. Required.

## clientExport properties

Name | Type | Description
---|---|---
`layers` | array of string | List of layer names that are allowed to export selected objects. Optional, if omitted export is allowed for all layers.
`format` | string | Fileformat to export to. Can be one of `'geojson' | 'gpx' | 'kml'` Required.
`button` | object | Configuration for using a text button or a round button. Required.

## button properties

Name | Type | Description
---|---|---
`roundButton` | boolean | If true, a round export button is displayed instead of a textbutton. Default is false.
`roundButtonIcon` | string | Icon for the round button. Path to an image or an icon from a library that are available as SVG sprites in Origo. Required if roundButton is true.
`roundButtonTooltipText` | string | Tooltip text for the round button. Required if roundButton is true.
`buttonText` | string | Text to display on export button. Optional. Default is 'Export'.

## groupAggregation object

Name | Type | Required | Description
---|---|---
`layer` | string | No | Name of layer to apply to. If omitted or empty applies to all layers that has the configured `attribute`.
`function` | string | Yes | Name of aggregation function. Currently only supported function is `"sum"`, which calculates the sum.
`scalefactor` | Number | No | If `unit` is specified the result is multiplied with this scale factor. Defaults to 1.
`decimals` | integer | No | Number of decimals in result. Defaults to 2.
`attribute` | string | Yes | Name of the attribute to aggregate or name of function to apply. A function is prepended with `@`. See table below for supported functions. If the attribute is not present or the function can not be applied for a layer no aggregation is displayed for that layer.
`label`| string | No | Text to put before result. Defaults to _function name_(attribute): _result_ _unit_, e.g. sum(@area): 55.01 km^2^
`unit`| string | No | If specified it is printed after the result. Defaults to nothing unless a function that specifies its own unit is used.
`useHectare` | boolean | No | If _true_ areas can be displayed in hectares for functions that calcultes areas. defaults to _true_.

## groupAggregation attribute functions
groupAggregation attribute functions are functions that are applied to each feature and the result is aggregated.

Name | Description
---|---
`@length` | Calculates the length of the feature. The result is automatically scaled to meters or kilometers unless `unit` is specified in which case result is in meters before scalefactor is applied.
`@area` | Calculates the area of the feature. The result is automatically scaled to m^2^, ha or km^2^ unless `unit` is specified in which case result is in square meters before scalefactor is applied. If `useHectare` is false result is not displayed as ha.


#### Example featureinfoOptions with overlay as infowindow

```json
{
  "featureinfoOptions": {
    "clusterFeatureinfoLevel": 3,
    "infowindow": "overlay",
    "pinning": false,
    "hitTolerance": 3,
    "selectionStyles": {
      "Point": [{
        "circle": {
          "radius": 5,
          "stroke": {
            "color": [0, 153, 255, 1],
            "width": 0
          },
          "fill": {
            "color": [0, 153, 255, 1]
          }
        }
      }],
      "LineString": [{
        "stroke": {
          "color": [255, 255, 255, 1],
          "width": 5
        }
      },
      {
        "stroke": {
          "color": [0, 153, 255, 1],
          "width": 3
        }
      }],
      "Polygon": [{
        "stroke": {
          "color": [255, 255, 255, 1],
            "width": 5
          }
        },
        {
          "stroke": {
            "color": [0, 153, 255, 1],
            "width": 3
          }
        }
      ]
    }
  }
}
```
#### Example featureinfoOptions with infowindow as infowindow

```json
{
  "featureinfoOptions": {
    "clusterFeatureinfoLevel": 3,
    "pinning": false,
    "hitTolerance": 3,
    "infowindow": "infowindow",
    "infowindowOptions": {
      "title": "Testtitel",
      "export": {
        "toasterMessages": {
          "success": "OK!",
          "fail": "Sorry!"
        },
        "simpleExport": {
          "url": "url_to_service",
          "layers": ["layer_1","layer_2"],
          "button": {
            "roundButton": false,
            "buttonText": "Send to excel"
          }
        },
        "layerSpecificExport": [
          {
            "layer": "layer_3",
            "attributesToSendToExport": [ "attribute_1", "attribute_2" ],
            "exportUrls": [
              {
                "url": "url_to_service",
                "exportedFileName": "filename_1.xlsx",
                "button": {
                  "roundButton": true,
                  "roundButtonIcon": "#fa-download",
                  "roundButtonTooltipText": "Send to excel"
                }
              },
              {
                "url": "url_to_service",
                "exportedFileName": "filename_2.docx",
                "button": {
                  "roundButton": true,
                  "roundButtonIcon": "img/png/image.png",
                  "roundButtonTooltipText": "Send to word"
                }
              }
            ]
          },
          {
            "layer": "layer_4",
            "exportUrls": [
              // Define an export button to make a GET request and display
              // the response (image or text) in the infowindow e g:
              // https://my.api.se/sendSomething?param1=value1&featureid=1;3;12&silent
              {
                "button": { "buttonText": "Send IDs" },
                "url": "https://my.api.se/sendSomething",
                "requestMethod": "GET",
                "urlParameters": {
                  "param1": "value1",
                  "featureid": { "attribute": "id", "separator": ";" },
                  "silent": null
                },
                "displayExportResponse": true
              },
              // Define an export button to open a new browser tab/window
              // with attributes from selected features as URL parameters e g:
              // https://my.otherapp.se?param1=value1&lat=59.1653;59.16659&lon=18.13751;18.13135&v2
              {
                "button": { "buttonText": "Open external page" },
                "url": "https://my.otherapp.se",
                "requestMethod": "OPEN",
                "urlParameters": {
                  "param1": "value1",
                  "lat": { "attribute": "y" },
                  "lon": { "attribute": "x" },
                  "v2": null
                }
              }
            ]
          }
        ]
      }
    },
    "multiSelectionStyles": {
      "selected": [
        {
        "zIndex": 1,
        "fill": {
          "color": [128, 128, 128, 0.13]
        },
        "stroke": {
          "color": [0, 0, 0, 0.13],
          "width": 3
        },
        "circle": {
          "radius": 14,
          "stroke": {
          "color": [0, 0, 0, 0.13],
          "width": 3
          },
          "fill": {
          "color": [128, 128, 128, 0.13]
          }
        }
        }
      ],
      "inActiveLayer": [
        {
          "zIndex": 3,
          "fill": {
          "color": [128, 128, 192, 0.4]
          },
          "stroke": {
          "color": [255, 255, 255, 1],
          "width": 4
          },
          "circle": {
          "radius": 14,
          "stroke": {
            "color": [255, 255, 255, 1],
            "width": 3
          },
          "fill": {
            "color": [255, 255, 255, 0.01]
          }
          }
        },
        {
          "zIndex": 4,
          "stroke": {
          "color": [220, 24, 24, 1],
          "width": 2
          },
          "circle": {
          "radius": 14,
          "stroke": {
            "color": [220, 24, 24, 1],
            "width": 2
          },
          "fill": {
            "color": [128, 128, 192, 0.4]
          }
          }
        }
      ],
      "highlighted": [
        {
          "zIndex": 5,
          "fill": {
          "color": [255, 255, 255, 0.6]
          },
          "stroke": {
          "color": [255, 255, 255, 1],
          "width": 6
          },
          "circle": {
          "radius": 14,
          "stroke": {
            "color": [255, 255, 255, 1],
            "width": 6
          },
          "fill": {
            "color": [255, 255, 255, 0.01]
          }
          }
        },
        {
          "zIndex": 6,
          "stroke": {
          "color": [48, 48, 255, 1],
          "width": 3
          },
          "circle": {
          "radius": 14,
          "stroke": {
            "color": [48, 48, 255, 1],
            "width": 3
          },
          "fill": {
            "color": [255, 255, 255, 0.6]
          }
          }
        }
      ]
    }
  }
}
```

#### Example featureinfoOptions with aggregations
```json
"featureinfoOptions": {
    "infowindow": "infowindow",
    "infowindowOptions": {
      "groupAggregations": [
        {
          "layer": "linjelager",
          "function": "sum",
          "scalefactor": 0.01,
          "decimals": 1,
          "attribute": "@length",
          "label": "Total length",
          "unit": "hektometer"
        },
        {
          // No layer specified, apply to all (multi) polygon layers
          "function": "sum",
          "attribute": "@area",
          "label": "<b>Total area:</b> ",
        },
        {
          // No layer specified, applies to all layers that happens to have an attribute called "inten"
          "function": "sum",
          "attribute": "inten", // ordinary attribute
          "decimals": 0
        }
      ]
    }
  },
```

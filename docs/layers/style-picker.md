# Style Picker

## stylePicker
The stylePicker is available for vector layers and WMS layers. It is defined in one way for vector layers and a slightly different way for WMS layers due to the different nature of styles of image type layers like WMS layers compared to the client side styles of vector layers.
#### vector layers
A stylePicker refers to defined styles and allows a style title to be set. (It usually makes sens for the `style` property of the layer to refer to one of the styles in the stylePicker.)
```json
"stylePicker": [
  {"title": "Sommarstil", "style": "bokbuss_sommar"},
  {"title": "Sval ton", "style": "bokbuss_bla"}
]
///
"styles": {
  "bokbuss_sommar": [
    [
      {
        "stroke": {
          "color": "rgba(211,84,0,1.0)"
        },
        "fill": {
          "color": "rgba(241,196,15,0.9)"
        }
      }
    ]
  ]
}
```
#### WMS layers
if a stylePicker is defined for a WMS layer then it refers to styles available to the layer on the WMS server.

A `style` layer property is overriden and any `hasThemeLegend` and `legendParams` are incorporated in the stylePicker on a per layer basis (rather than as properties of the layer).

There can only be one `defaultWMSServerStyle` as well as `initialStyle` where the later specifies which style the map should load with. If there's no `initialStyle` specified then the first style in the array will be it.
```json
      "stylePicker": [
        { "title": "Ljus", "style": "Bakgrund_bke_fk_lj_0484" },
        { "title": "Mörk", "style": "Bakgrund_bkm_fk_mo_0484",
          "initialStyle": true,
          "hasThemeLegend": true,
            "legendParams": {
              "legend_options": "dpi:600"
            }
        },
        { "title": "Standard", "defaultWMSServerStyle": true,
          "legendParams": {
            "scale": 100
          }
        }
      ]
```

## Automatic default (legend) style for WMS layers
A WMS layer can have a style property defined for its legend graphic or for an alternate layer style defined on the WMS server. If a style property is not defined then Origo will attempt to create one for the legend graphic using getLegendGraphic and optionally two additional layer properties can then be defined, `legendParams` and `hasThemeLegend`.

`hasThemeLegend` is used to manually indicate if the layer has theme symbology and that the legend should be behind a theme style icon (extendedLegend).

Example `legendParams` object with Geoserver vendor parameter
```json
      "legendParams" : {
        "scale" : 5000,
        "legend_options" : "dpi:300"
      }
```

## text/html infoFormat for WMS-layers
WMS servers can usually serve getFeatureInfo requests with a text/html reply. Sometimes they provide customizability of these replies. Then the html returned can have an infinite amount of variation. Origo has basic support for Geoserver WMS layers configured with `infoFormat: text/html`:

 if the layer also has the `htmlSeparator` property set to an html tag, like `htmlSeparator: 'ul'` Origo will try to separate the features from the html reply via the configured tag and present the infoclick hits with a selection that can be traversed via clicking the features in the infowindow or cycling the carousel of the overlay like usual. If no such tag is present for a layer a point will show where the infoclick happened and all feature hits will be presented in one overlay/infowindow (representing the reply from the WMS server as it is).

 Because of :milky_way: amount of variation of featureInfo html responses Origo may not be able to separate features with a supplied tag, to this end it is possible to supply Origo with a handler function for the featureInfo html reply. This can be done via the api: `origo.api().getFeatureinfo().addTextHtmlHandler(function)` as well as via a plugin that would define a function and `viewer.getFeatureinfo().addTextHtmlHandler(function)`.

 It is advisable to check the default function in src/getfeatureinfo.js to see the form of what is to be returned depending on whether a `htmlSeparator` prop is provided.

 Note that the `source` of the [WMS](wms.md) layer must have the `type` prop with the `geoserver` value for the `text/html` value of the `infoFormat` property to have the proper effect.

# Print

Adds a print control to the mapmenu.  **NOTE** - requires mapmenu control.

Property | Description
---|---
`name` | the name of the control (print)
`options` | options for the control

Option | Description
---|---
`placement` | option where the button is displayed. Optional, defaults to ["menu"]. ["screen"] or both are possible.
`leftFooterText` | a small left-aligned text on the bottom left. Optional.
`showCreated` | shows the current date as a small right-aligned text on the bottom right. Optional. Default is false.
`createdPrefix` | text displayed before the current date on the bottom right. Requires `showCreated: true`. Optional.
`logo` | a object for configure placing the logo on the printed map. Optional.
`cls` | a css class for styling e.g. the placing of the image. Optional, defaults to "padding-bottom-small".
`src` | the path to logo image relative to the maps base url. Optional, defaults to "css/png/logo_print.png".
`style` | a style object for setting e.g. the height of the image. Optional, defaults to "{"height": "3rem"}".
`northArrow` | a object for configure the north arrow on the printed map. Optional.
`cls` | a css class for styling e.g. the placing of the image. Optional, defaults to "padding-right-small printmap-north-arrow".
`src` | the path to logo image relative to the maps base url. Optional, defaults to "css/png/north_arrow_print.png".
`visible` | option to set if the north arrow should be visible on load. Default is true.
`style` | a style object for setting e.g. the height of the image. Optional, defaults to "{"height": "5rem"}".
`showScale` | option to set if the scale should be visible on load. Optional, default is true.
`scales` | Array of scales to use. Optional, if not specified the scales are calculated from the map resolutions.
`supressResolutionsRecalculation` | option to set if the resolutions array should not be recalculated when entering the print preview (and restored when exited). Recalculating alleviates a problem with large scales and 300DPI. The option defaults to false.
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.
`suppressNewDPIMethod` | option to set if the new DPI calculation when changing resolution in the print preview should not be used. The option defaults to false.
`mapInteractionsActive` | option to set whether map interactions should be enabled by default (true) or not. Default is false.


#### Example Print control

```json
{
  "name": "print",
  "options": {
      "placement": ["screen","menu"],
      "leftFooterText": "OBS: Kartan är inte rättsligt gällande.",
      "showCreated": true,
      "createdPrefix": "Skapad ",
      "logo": {
        "cls": "padding-bottom-small",
        "src": "css/png/logo_print.png",
        "style": {
            "height": "3rem"
          }
        },
        "northArrow": {
          "cls": "padding-right-small printmap-north-arrow",
          "src": "css/png/north_arrow_print.png",
          "visible": true,
          "style": {
            "height": "5rem"
          }
        },
        "showScale": true,
        "scales": [
          "1:100000",
          "1:50000",
          "1:15000",
          "1:10000",
          "1:5000",
          "1:1000",
          "1:500"
        ]
  }
}
```

# Controls

A control is an optional module with a DOM element in a fixed position on the
screen. They can involve user input (buttons), or be informational only. The controls to be included in the maps are set in the map configuration. The order of the controls matter. For instance, adding legend before mapmenu will make it render below when overlapping. Similarily the order of the controls in the mapmenu is set by the order in the config.

#### Example setting controls to be included

```json
{
"controls": [
  {
    "name": "geoposition",
    "options": {
        "zoomLevel": 15
    }
  },
  {
    "name": "mapmenu"
  },
  {
    "name": "sharemap"
  },
  {
    "name": "print",
    "options": {
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
          "visible": false,
          "style": {
            "height": "5rem"
          }
        }
    }
  },
  {
    "name": "legend",
    "options": {
        "expanded": false
    }
  },
  {
    "name": "search",
    "options": {
        "url": "http://localhost:3000/adressok",
        "searchAttribute": "NAMN",
        "northing": "N",
        "easting": "E",
        "title": "Adress"
    }
  }
],
}
```

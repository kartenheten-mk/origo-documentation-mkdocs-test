# Position

Control to show coordinates of the mouse cursor or map center and navigate to coordinate. The control supports multiple coordinate systems that can be toggled by clicking
the coordinate system label. By clicking the hair cross the functionality toggles between displaying mouse position or map center. In map center mode
it is possible to navigate to a coordinate by entering a new value in the coordinate display box.

Property | Description
---|---
`name` | The name of the control. Required. For position contol name is "position".
`options` | A _positionControlOptions_ object

__positionControlOptions__

Option | Description
---|---
`title` | alias name of the current map projection to be displayed. Optional. If specified it is the first in the toggle loop.
`projections` | Array of _positionControlProjectionConfiguration_ objects that defines which projections are possible to toggle between. The projection must be defined in proj4Defs, except EPSG:4326 and EPS:3857 which are included by default. Alternatively `projections` can be an object with projection codes as properties and display name as value.
`noPositionText` | when empty last mouse position is rendered else text of choise renders. If this option is not defined, no coordinates when no mouse position.
`hideWhenEmbedded` | if set to true, the control is not added when the map is embedded. Defaults to false.

__positionControlProjectionConfiguration__

Option | Description
---|---
`projectionCode` | String with the EPSG code e.g. "EPSG:4326". Required.
`projectionLabel`| String with text to display in the control for this projection. Required.
`dms` | Bool. If true coordinates are displayed in Degree minute second format. Optional, defaults to false.
`precision` | Number of decimals in the coordinate. If `dms` is true, it sets the number of decimals of _seconds_. Optional, defaults to 0 for all coordinate systems except EPSG:4326, for which it defaults to 5 if not using _dms_.

#### Example position control
```json
{
      "name": "position",
      "options": {
        "projections": [
          {
            "projectionCode": "EPSG:4326",
            "projectionLabel": "Wgs84"
          },
          {
            "projectionCode": "EPSG:4326",
            "projectionLabel": "Wgs84 DMS",
            "dms": true,
            "precision": 2
          }
        ]
      }
    }
```

#### Example position control using simplified configuration format

```json
{
  "name": "position",
  "options": {
    "title": "Sweref99 16.30",
    "projections": {
      "EPSG:4326": "WGS84",
      "EPSG:3006": "Sweref99 TM"
    },
    "noPositionText": ""
  }
}
```

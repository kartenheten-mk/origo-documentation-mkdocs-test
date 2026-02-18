# Groups

Name | Type | Description
---|---|---
`groups` | array | Define groups to organise layers. The group names are used in the legend control. Each group is defined as an object. A group can contain subgroups, defined as groups within a group.

Name | Type | Description
---|---|---
`name` | string | Name of the group that identifies the group. Each name must be unique.
`title` | string | A title for the group. The title is visible for the user in the legend control.
`description` | string | description of the group. Shown on the properties page. Optional.
`abstract` | string | short description of the group. Shown on the properties page unless showAbstractInLegend is true. Optional.
`showAbstractInLegend` | boolean | if abstract should be placed in the legend instead of on the properties page. Default is false.
`expanded` | boolean | Whether the group should be expanded not. Used by the legend control. Default is false.
`autoExpand` | boolean | For subgroups. Whether the subgroup should be expanded/collapsed when toggling the subgroups checkbox. Used by the legend control. Default is true.
`groups` | array | Array of group objects defining subgroups. Optional.
`exclusive` | boolean | Setting to true will prevent activating more than one layer in the group. Defaults to false.
`toggleAll` | boolean | For subgroups. Set to false to disable the option to show/hide all layers in the subgroup at once. Will have no effect if exclusive is set to true. Default is true.
`draggable` | boolean | Set to true to be able to rearrange layers and subgroups in the group and affect the drawing order. Default is false.
`removable` | boolean | Set to true to be able to remove the group from the legend. Default is false.
`opacityControl` | boolean | Set to true to show opacity slider on the properties page. Default is false.
`zoomToExtent` | boolean | Set to true to be able to zoom to specified extent. `extent` must also be set. Default is false.
`extent` | array | array of extent to zoom to with zoomToExtent.

#### Example groups

```json
{
"groups": [
    {
      "name": "GROUP",
      "title": "GROUP",
      "abstract": "This is parents group",
      "groups": [
        {
          "name": "group",
          "title": "group",
          "abstract": "This is childrens group",
          "exclusive": true
        }
      ]
    }
]
}
```

# Related Layers
A related layer is a layer that is a child in a _1-to-many_ relationship. Origo supports related layers for WFS layers by
defining a _private-foreign key relation_ between layers. The layers do not have to be in the same database or be servered from
the same WFS server. The relation is only stored in the child object, which makes it suitable for adding attributes
to a table that is considered read only.
A layer can have several child layers and a child layer can have child layers of its own.

Entries in the child layer can be added, deleted and edited through the parent's edit form and does not have a geometry of its own. Child objects may have a geometry,
but there is not support to edit or add new geometries other that edit the child layer directly.

Attributes from child layers can be aggregated and displayed in the featureInfo window of the parent.

## Related layers Configuration
All configuration regarding the relation is performed on the parent layer. The child layer must be configured as an ordinary wfs layer and most likely configured with
`'isTable': true`. The child layer can use `'strategy': 'bbox'` even if it is a table. In that case related objects are fetched when the parent is edited or featureInfo
is displayed

Relations are configured on the parent layer using the `"relatedLayers"` property containing an array of objects with the following properties.

Property | Description | Required | Default value
---|---|---|---
`layerName` | Name of the child layer as already configured as a layer | Yes |
`PK`| Name of the field that holds the private key in the parent object. | No | featureid (omit for featureid as that can not be explicitly set)
`stripPK` | If PK is featureid, remove layer name part from featureid when joining. Useful to keep only the fid part as FK in the database. | No | true
`FK` | Name of field in child that holds the foreign key. When a new entry is created this field will be updated with the value of PK of the parent. | Yes |
`FKIsString` | Has to be `true` if the FK field datatype in database is string. | No | false
`childTitle`| The title (string) that will be displayed above all child elements in the parent's attributes editor | No | Child layer's `title`
`featureTitle`| Name of the attribute that holds the text that will be displayed in the parent's attribute form for each feature | No | featureid
`maxChildren`| Number of children that can be added. | No | Unlimited
`cascadingDelete`| How to handle if parent is deleted. Can be one of `'cascade'` : delete recursively, both in database and in local layer. `'db'`: Assume database has cascading delete and only recursively delete locally. `'none'`:  Do nothing. Child remains both locally and in db, orphaned | No | `'none'`
`disableAdd` | `true` if the add button in the parent's edit form should be disabled for this layer| No | false
`disableDelete` | `true` if the delete button in the parent's edit form should be disabled for this layer | No | false
`disableEdit` | `true` if the edit button in the parent's edit form should be disabled for this layer | No | false
`promoteAttribs`| An array of [promoteAttrib objects](#promoteattrib-object) that defines how attributes are aggregated and available to the parent in featureInfo | No | None


### promoteAttrib object

Each entry creates an attribute on the parent by first extract an expression from each child and then aggregate the
result from all children. Currently the only supported aggregation function is _string.join()_

Property | Description | Required | Default value
---|---|---|---
`parentName` | Name of the attribute to create in the parent | Yes |
`html` | Template string that extracts values from each child object. Attribute names enclosed in `{{}}` are replaced with its value. Does not have to be html, but can contain html tags | Yes
`separator` | String to use as separator when aggregating extracted strings | No | Empty string

#### Example related tables configuration
Basic example to set up a parent which has a related child layer. The parent itself is not editable, but the child layer has two attributes that can be edited. Also
the attributes from the child layer is aggregated and displayed in the featureInfo window of the parent.

```json
{
  "layers": [
    {
      // This is the child layer
      "name": "sf:person",
      "source": "local_wfs",
      "type": "WFS",
      "isTable": true,
      "attributes": [
        {
          "name": "name",
          "type": "text"
        },
        {
          "name": "org",
          "type": "text"
        }
      ]
    },
    {
      // This is the parent layer
      "name": "sf:property",
      "queryable": true,
      "group": "root",
      "source": "local_wfs",
      "type": "WFS",
      "geometryName": "the_geom",
      "geometryType": "Point",
      "visible": true,
      "editable": true,
      "allowedEditOperations": [
        "updateAttributes"
      ],
      "attributes": [
        {
          "name": "adress",
          "type": "text",
          "readonly": true
        },
        {
          // This is the temporary attribute created by related table configuration
          "name": "responsible",
        }
      ],
      "relatedLayers": [
        {
          "layerName": "person",
          "FK": "parent_fid",
          "featureTitle": "name",
          "promoteAttribs": [
            {
              "parentName": "responsible",
              "html": "<p><b>{{name}},</b>{{org}}</p>"
            }
          ]
        }
      ]
    }
  ]
}
```

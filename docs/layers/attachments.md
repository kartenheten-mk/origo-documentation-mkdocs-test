# Attachments
While attributes are taken from each feature itself in a layer, an attachment is a file that
is stored somewhere else but can be treated as an attribute. An attachment is typically an
image or document that relates to a special feature and for practical reasons can not be stored in an attribute.
Attachments can be viewed, added and removed by the user in the editor form and viewed in featureInfo as links or emedded as images.

Attachments are configured on each layer. It can be configured
for both raster and vector layers, but can only be edited on vector layers.
In order to use attachments, an attachment server is needed. The attachment server must implement the arcgis server
rest api for attachments.

- _attachment Infos_ https://developers.arcgis.com/rest/services-reference/enterprise/attachment-infos-feature-service-.htm
- _attachment_ https://developers.arcgis.com/rest/services-reference/enterprise/attachment-feature-service-.htm
- _add attachment_ https://developers.arcgis.com/rest/services-reference/enterprise/add-attachment.htm
- _delete attachment_ https://developers.arcgis.com/rest/services-reference/enterprise/delete-attachments.htm


Optionally the server can extend the AGS interface by adding the concept
of attachment groups in order to group attachments in different groups. Groups can be used to have
different rules and display them differently. AGS server can be used out-of-the-box for AGS layers, but the extented
format must be implemented as a server side component.

The extensions to the AGS format are:

- The response from _attachments infos_ must include a "group" property for each attachmentInfo object
- The request to _addAttachment_ must include a "group" parameter

A reference implementation of the extended
format is available here: https://github.com/ornskoldsvikskommun/attachmentServer-reference It
should not be used for production environments as it lacks security, performance and
flexibilty.

## Attachment configuration
Attachments are configured on each layer using the `"attachments"` property containing an object with the following properties.

Property | Description | Required | Default value
---|---|---|---
`url` | The base adress for the attachment server. | Yes
`formTitle` | Title of section in editor form | No | 'Bilagor'
`format` | The format to use. 'origo' or 'arcgis'. 'origo' extenteds the AGS format by using groups | No | 'origo'
`foreignKey` | Name of the attribute in the parent feature that contains the private key. | No | Uses id of feature
`stripLayerNameFromId` | Removes layer name from featureid when _foreignKey_ is not specified. Useful when using geoserver wfs services to get only database FID as private key. | No | _true_
`layerId` | The layer id in the attachment server. | No | _Layer name_
`groups` | Array of [group objects](#group-object) defining an attachment group. A group has its own title and each group is treated as a separate attribute. At least one group has to be specified. If format is "arcgis" exactly one group must be specified | Yes |


### Group object

Property | Description | Required | Default value
---|---|---|---
`name` | Name of the group on the attachment server. Ignored for format 'arcgis' | Yes |
`title` | Title displayed in the editor. Ignored for format 'arcgis' | No | `name`
`linkAttribute` | Name of an attribute to create on a feature containing all links as a semicolon separated list. Can be used to create links in featureInfo using the _img_ or _url_ property. | No |
`fileNameAttribute` | Name of an attribute to create on a feature containing all filename as a semicolon separated list. Order is same as linkAttribute list. Can be used in combination with _linkAttribute_ to set link text using the _linktext_ property | No
`allowedFiles` | Comma separated list of valid file extensions and mime types that are allowed to upload. Format is accordning to the accept attribute of https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/file | No | *

#### Example attachment configuration
```json
"attachments": {
        "formTitle" : "Attachments",
        "layerId": "entity_blob",
        "url": "http://gis.kommun.org/attachmentserver/",
        "groups": [
          {
            "name": "proto",
            "title": "Protocols",
            "allowedFiles": ".pdf"
          },
          {
            "name": "public",
            "title": "Public Image",
            "allowedFiles": ".jpg,.png",
            "linkAttribute": "pictureLinks",
            "fileNameAttribute": "pictureTexts"

          }
        ]
      }
```

#### Example display attachments in featureinfo configuration
```json
"attributes": [
    {
        "title": "Images",
        "linktext": "pictureTexts",
        "url": "pictureLinks",
        "splitter": ";"
     }
]
```

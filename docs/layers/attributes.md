# Attributes

By default all available attributes for a queryable layer are listed in a featureinfo popup. The content can be customized in several ways, for example to make url:s or embed images. There are two basic approaches to do this. The first is to use a named handlebars template. This is what is used by default but requires a precompiled template. The second approach is to define how each attribute should be presented in the layer configuration. Each attribute is defined within curly brackets with options according the table below.

## Information window

Attribute options | Description
---|---
`name` | the name of the attribute. The value of the attribute will be shown. Optional.
`title` | static label for the attribute. Optional.
`url` | absolute url ('//example.com/nonsense.html') or attribute containing an url. Creates a link automatically and can be combined with name as value. Optional.
`urlPrefix` | a general prefix to be used together with url, img, audio or video. Optional.
`urlSuffix` | a general suffix to be used together with url, img, audio or video. Optional.
`target` | default behaviour is to open url in new window (_blank). It's possible to specify other targets as _top, _self and _parent or to open link in an iframe in a modal window which should than be set to modal for normal size or modal-full. Optional.
`targetTitle` | used along with target to define title in modal titlebar and link tooltip. Can be set to "static text" or "{{attribute value}}". Default is url.
`img` | attribute containing url or base64 data to an image. The image will be embedded. Optional.
`audio` | attribute containing url or base64 data to an audio file. The audio will be embedded. Optional.
`video` | attribute containing url or base64 data to an video file. The video will be embedded. Optional.
`carousel` | attribute containing url to several images combined with splitter option. Set `autoplay` in `featureinfoOptions` to have the carousel rotate the images. Optional.
`splitter` | set a splitter for example , or ; which is used to split the attribute if it is made up of delimited list of compounded attributes of the same type. To be used together with `url`, `img`, `audio`, `video`, `carousel` and `linktext`. Optional.
`cls` | css class name for custom styling. Optional.
`html` | Custom html. Attributes can be referenced by placing the attribute name within double curly brackets.  It also possible in a similar way to apply a function by prepending the function name with `@`. See table below for supported functions. The `html` option can't be combined with any of the other options, except for `cls`. Optional.
`linktext` | Name of attribute that holds the text that should be used on links when using `url` in combination with `splitter`. Optional.
`prefix` | adds the text entered in front of the attribute value. Optional.
`suffix` | adds the text entered after the attribute value. Optional.
`formatDatetime` | makes it possible to format an attribute that contains a datetime value that follows ISO 8601 or Unix TimeStamp. FormatDatetime value should be a object specifying which locale to be used for the formatting and an options object with choosen formats, for example `{"locale": "sv-SE", "options": { "dateStyle": "full", "timeStyle": "long" }}` if you want swedish formatting with ful date and long time reprsentation or `{"locale": "en-US", "options": { "weekday": "long", "year": "numeric", "month": "long", "day": "numeric" }}` if you want american english, weekday and month as word and year and day as numbers. More formatting options can be found here: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl/DateTimeFormat The default value is `{"locale": "default", "options": { dateStyle: 'full', timeStyle: 'long' }}`. Optional.

**Html Attribute Functions**

An html attribute function is either used with no arguments (all defaults) or all arguments specifed enclosed by parenthesis and separated by comma. Arguments are specified as constant values without any form of quotation marks.

Function name | Description | Arguments | Example
---|---|---|---
`@center` | Prints out the center coordinate of the geometry | coordinatesystem: _string_ (defaults to map coordsys), axis rotation: `default` \|\| `reverse` (defaults to `default`) | `{{@center(EPSG:4326,reverse)}}`
`@area` | Prints out the area of the geometry. Area is automatically scaled to a suitable unit (m2, ha, km2) | decimals: _integer_ (defaults to 2) | `{{@area}} {{@area(1)}}`
`@length` | Prints out the length of the geometry. Length is automatically scaled to a suitable unit (m,km) | decimals: _integer_ (defaults to 2) | `{{@length(1)}}`


#### Example defining layer attributes

```json
{
  "name": "mygeojson",
  "title": "My geojson with custom attributes",
  "source": "data/mylayer.geojson",
  "style": "mask",
  "type": "GEOJSON",
  "attributes": [
    {
      "name":"NAME",
      "title": "Name: ",
      "url": "PAGEID",
      "urlPrefix":"http://my.link.com/",
      "urlSuffix":".html"
    },
    {
      "html": "<p>For more information contact {{CONTACT}} at {{PHONE}}</p>",
      "cls": "o-custom-class-name"
    }
  ]
}
```


## Editor attributes

When editing a layer, additional attributes are supported to control the behaviour of the edit attributes tool.

Attribute option | Description
---|---
`type` | The attribute type. Determines which edit control is used. See [Editor attribute types](#editor-attribute-types)  (required)
`allowBatchEdit` | _bool_ true if allowed to update a selection of features with the same value (optional)
`config`| _object_ Additional configuration. The config object depends on the _type_.
`constraint` | _string_  \<event\>:\<attribute name\>:\<value\> or \<event\>:\<attribute name\>:[\<value1\>,\<value2\>, ...], where \<event\> is the event that the \<attribute name\> input emits, most likely `change`. Attribute is only editable when \<attribute name\> has value \<value\> (optional)
`list` | _array of strings_ or _array of list object_. List of possible values for searchList. (optional)
`maxLength` | _int_ Maximum number of characters (optional)
`options` | _array of strings_ List of allowed values. Required for type `dropdown` (optional)
`readonly` | _bool_ True if attribute should be displayed but not allowed to edit (optional)
`required` | _bool_ True if the attribut must have a value (optional)
`defaultValue` | _string_ or _object_. When type is string that string is used as default value on feature creation. When it is an object a _defaultValue_ object defines behaviour (optional)


### Editor attribute types

type | format | required | readonly | maxLength | constraint | Description
---|---|---|---|---|---|---
`text`      | string | supported | supported | supported || Text input
`textarea`  | string | supported | supported | supported || Text input with resizable box
`dropdown`  | string || supported || supported | Dropdown based on options values
`checkbox`  | boolean or configured values || supported ||| Checkbox, defaults not checked.
`checkboxgroup`  | array with configured values || supported ||| A group of checkboxes where multiple choices can be selected and also freetext choices can be added, defaults to not checked.
`image`     | base64 || supported ||| Uploads image
`audio`     | base64 or url || supported ||| Uploads audio or sets url to audio
`video`     | base64 or url || supported ||| Uploads video or sets url to video
`color`     | hexadecimal || supported ||| Activates a color-picker
`time`      | hh:mm:ss | supported | supported ||| Defaults to current time. Use defaultTime:false to not.
`date`      | YYYY-MM-DD | supported | supported ||| Defaults to current date. Use defaultDate:false to not.
`datetime`  | YYYY-MM-DD hh:mm:ss | supported | supported ||| Defaults to current date. Use defaultDatetime:false to not.
`email`     | string | supported | supported ||| Email address
`url`       | string | supported | supported ||| Homepage address
`integer`   | integer | supported | supported ||| Whole number
`decimal`   | decimal | supported | supported ||| Decimal number
`searchList`   | string | supported ||supported. Defaults to 50|| Dropdown based on options values with search capabilities.
`hidden` | string ||||| Not visible to the user.

**searchList List object**

Defines the possible values in a _searchList_

Property | Description | Required | Default value
---|---|---|---
`value` | _string_ text to display. If `useBackingValue` is set it is used as the value while `label` is used for display | When _location_ is not specified |
`src`| _url_ to an image that will be displayed next to _value_. Url is relative to app or absolute | No |
`location`| _url_ to a HTML page that contains links to images. All a-tags hrefs that matches _extension_ will be used as list items. Filename will appear as text and the image itself as a thumbnail next to the text. If _location_ is specified it must be only item in list | No |
`extension` | Filename extension without dot to filter links when using _location_ | When _location_ is specified |
`label`| Text to display and search instead of value when `useBackingValue` is set | When `useBackingValue` is _true_ |

**searchList Config object**
An object that defines additional configuration for searchList. The searchList can be configured to get its list from static configuration
or a remote server. If using a remote server it can either get all available options in one request or
query the server for each keypress. It can also be configured to use _value_ and _label_ similar to an HTML select drop down. In that
case _value_ is stored in the database but _label_ is displayed in the searchList.

__Requirerments on the backend server__
If the `url` option is used an additional HTTP server endpoint is needed, not included in the origo project.
The server must respond with a list of _searchList list objects_ as described above with the exception that `location` is not supported. There is no support for authentication other than what the browser
automatically provides, e.g. sending cookies or authentication headers if server is located on same site as application.


If the `dynamic` option is used the server must accept a GET parameter named "input" or the configured `queryParameter` name. The parameter gets the value of the searchList text box and the server should return
a list of matching search items. The exact algorithm is up to the server, but origo will assume the list is filtered and sorted so the list will be displayed as is as suggestions, but will be truncated to `maxItems`. If the server's algorithm is not based on substrings of the value, the highlighting may not work as expected.

If the `useBackingValue` is specified in combination with `dynamic` the server must besides return both _value_ and _label_ for each list item also support reverse looking up in order to display correct label for the current value
when opening the attribute editor. The reverse lookup is performed by sending the current value as GET parameter "value". The surver must
then respond with a list with exactly one _searchList list objects_ with both _value_ and _label_ that corresponds to the current value.


Property | Description | Required | Default value
---|---|---|---
`url`| Url (GET) that responds with a JSON _array of List object_ (_location_ not supported) or _array of string_. If specified, _list_ property is ignored. | No  |
`dynamic` | _true_ if the server specified in `url` should be queried for each keypress. | No | false
`queryParameter` | Name of query parameter to use to send user input to `url` when `dynamic` is _true_| No | "input"
`allowOnlyFromList` | _true_ if the user only can input values from the list, which makes it work like a searchable drop down. | No | _false_
`disallowDropDown` | _true_ to allow the user to click the down arrow (or enter) when input is empty and get all possible suggestions even if minChar has not been reached. | No | _false_
`minChars` | Number of character that must be written before suggestions are displayed. | No | 2
`maxItems`| Number of suggestion items to display | No | 10
`typeMoreText` | The text to show to the user if the input has less then _minChar_ characters. | No | "Skriv fler tecken"
`noHitsText` | The text to show to the user if there are no suggestions to show. | No | "Inga träffar"
`useBackingValue` | If set to _true_ the list items must have both `value` and `label`. `value` is stored in the database and `label`is displayed in the searchList. If used in combination with `dynamic=true`, the server must also support reverse lookup as described in the requirements on the backend server. | No | _false_,
`valueQueryParameter`| When using `useBackingValue` in combination with `dynamic` the GET parameter name that is used for reverse lookup can be set using this parameter | No | "value"

**defaultValue object**

The defaultValue object controls how an attribute's default value is handled. Default values are always set when creating new features, and can optionally be set when updating attributes.
Default values can be overridden in the attribute editor unless attribute is configured as readonly or hidden.

Property | Description | Required | Default value
---|---|---|---
`type` | Source of default value. One of `sessionStorage`, `localStorage`, `timestamp`. If `timestamp` is specified it overrules default values for input types `time`, `date` and `datetime` | Yes |
`key`| key in sessionStorage or localStorgage | When `type` is `localStorage` or `sessionStorage` |
`updateOnEdit`| `true` if default value should be applied when editing as well as creating a new feature. | No | `false`
`timeStampFormat`| One of `time` = "HH:mm:ss", `date`= "yyyy-MM-dd", `datetime` = "yyyy-MM-dd HH:mm:ss", `timestamp` = "yyyy-MM-ddTHH:mm:ss | No | `timestamp`
`useUTC` | `true`if time should be in UTC, otherwise local time | No | `false`

**checkbox Config object**

An object that defines additional configuration for checkbox. The entire object is optional and all
properties are set to default if omitted.

Property | Description | Required | Default value
---|---|---|---
 `uncheckedValue` | Value that corresponds to the unchecked state | No | 0 (false)
 `checkedValue` | Value that corresponds to the checked state | No | 1 (true)

**checkboxgroup additional attributes**

Attribute option | Description | Note | Default value
---|---|---|---
`options` | An array of objects further explained in next section | This shares the name with `dropdown` but not the syntax. Required for type `checkboxgroup` | Defaults to `[]`.
`separator` | The separator to be used to differentiate the values. | This effects the way the value is saved so changes in config will need updating the data values correspondingly. | Defaults to `;`.
`freetextOptionPrefix` | The prefix text in the value to be uesd to differentiate that this is a freetext value. | This effects the way the value is saved so changes in config will need updating the data values correspondingly. | Defaults to `freetext_option:`.
`freetextOptionValueSeparator`| The sign used to differentiate the unique freetext option and it's value. | This effects the way the value is saved so changes in config will need updating the data values correspondingly. | Defaults to `=`.

**checkboxgroup options array syntax**

For the checkboxgroup attribute type an array can be supplied used to set up multiple choice type checkbox questions.
The array should at least contain one object with the key `text` and a string value.

Property | Description | Required | Default value
---|---|---|---
`text` | The text for the choice and will also be the value unless another is specified | Yes |
`value` | Optional the object can have the key `value` which holds an alternative value for the option. | No | Defaults to the `text` if not supplied.
`type` | By adding to the object the type `textbox`, a textbox is attached to the option, the text box is enabled only if the option is checked. This can be used as an "other"/"miscellaneous" free text option. | No |

#### Example editor attributes

```json

{
  "name": "art",
  "title": "Art: ",
  "type": "text",
  "maxLength": 64,
  "readonly": true,
},
{
  "name": "isTrue",
  "title": "Is this true?: ",
  "type": "checkbox",
  "config": {
      "checkedValue": "true",
      "uncheckedValue": "false"
  }
},
{
  "name": "multiChoice",
  "title": "Please select all that applies: ",
  "type": "checkboxgroup",
  "options":  [
      { "text": "choice 1" },
      { "text": "choice 2", "value": 2 },
      { "text": "choice 3" },
      { "text": "choice other", "type": "textbox" }
  ]
},
{
  "name": "category",
  "title": "category: ",
  "type": "dropdown",
  "options": [
      "category_1",
      "category_2",
      "category_3"
  ]
},
{
  "name": "subcategory",
  "title": "subcategory: ",
  "type": "dropdown",
  "constraint": "change:category:category_1",
  "options": [
      "subcategory_1",
      "subcategory_2",
      "subcategory_3"
  ]
},
{
  "name": "choice",
  "title": "choice: ",
  "type": "dropdown",
  "options": [
      "choice 1",
      "choice 2",
      "choice 3"
  ]
},
{
  "name": "subchoice",
  "title": "subchoice: ",
  "type": "dropdown",
  "constraint": "change:choice:[choice 1,choice 3]",
  "options": [
      "subchoice 1",
      "subchoice 2",
      "subchoice 3"
  ]
},
{
  "name": "sprak",
  "title": "Språk: ",
  "type": "searchList",
  "list": [
      {
        "value": "Java"
      },
      ...
  ],
  "config": {
    "minChars": 2,
    "maxItems": 15
  }
},
{
  "name": "icons",
  "title": "Ikoner: ",
  "type": "searchList",
  "list": [
    {
      "src": "img/kompass.svg",
      "value": "Riktning"
    },
    ...
  ],
  "config": {
    "minChars": 0,
    "maxItems": 5
  }
},
{
  "name": "icon-lib",
  "title": "Bibliotek: ",
  "type": "searchList",
  "list": [
    {
      "location": "img/png",
      "extension": "png"
    },
    ...
  ],
  "config": {
    "minChars": 0,
    "maxItems": 5
  }
}

```

#### Example Default Values. Readonly user, hidden timestamp.
```json
"attributes": [
        {
          "name": "user",
          "title": "Edited by",
          "type": "text",
          "readonly": true,
          "defaultValue": {
            "type": "sessionStorage",
            "key": "loggedInUser",
            "updateOnEdit": true
          }
        },
        {
          "name": "lastUpdate",
          "type": "hidden",
          "defaultValue": {
            "type": "timestamp",
            "updateOnEdit": true,
            "useUTC":  true
          }
        }
 ]
```

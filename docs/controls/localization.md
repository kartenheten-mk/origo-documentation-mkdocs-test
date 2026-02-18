# Localization control

Provides localization for an instance of Origo and potentially any employed plugins, text strings and numbers that are part of the UI are the target.
Locales can be added during runtime (and saved in local storage).

Can be controlled per user via a map menu language locales selector.

Property | Description
---|---
`localeId` | the name of the locale to be used by default, for instance 'sv-SE' (must exist as a translation file in `loc/` and be imported by the control). Can be overridden by user selection and local storage.
`fallbackLocaleId` | the name of the locale to be used if a translation cannot be looked up in the default locale.
`showLocMenu` | whether to show the language locales selector in the map menu. Else it must be changed via a query param (`?loc=sv-SE`) added to the current URL which is then re-loaded, however this will only have an effect if there is not already a memorized locale selection in local storage.

#### Example localization control

```json
{
  "name": "localization",
  "options": {
    "showLocMenu": true,
    "localeId": "en-US",
    "fallbackLocaleId": "sv-SE"
  }
}

```
For additional use of this control see the [api](../api/index.md#using-origo-api) documentation.

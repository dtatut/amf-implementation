# OpenTimelineIO (OTIO) support

OTIO allows private extensions to be added for any object that supports the metadata element (e.g. Clip_1)

The mechanism requires the definition of a custom element, in this case

amf

In the custom element other custom elements can be define. See example below

### Clip metadata example:

```json
"metadata":
{
  "amf":
  {
    "uuid": "afe122be-59d3-4360-ad69-33c10108fa7a", 
    "url": "./example.amf" 
  }
}
```

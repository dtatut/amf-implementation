# Final Cut Pro X XML (FCPXML) support

FCPXML allows private extensions to be added for any object that supports the metadata element (e.g. Clip_1)

The mechanism requires the definition of a custom key, in this case

org.ampas.aces.amf

In the metadata/md element a single value or an array of values can be stored. See example below

### Clip metadata example:

```xml
<metadata>
  <md key="org.ampas.aces.amf" type="string" editable="1" displayName="ACES Metadata File reference by UUID" source="custom">
    <array>
      <string>urn:uuid:d9f152a2-54cc-11ea-a2e3-2e728ce88125</string>
      <string>file:///Volumes/Media/Clip.amf</string>
    </array>
  </md>
</metadata>
```

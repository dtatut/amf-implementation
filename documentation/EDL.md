# Edit Decision List (EDL) support


define	AMF_UUID

define	AMF_NAME

AMF_UUID shall be used to convey the AMF UUID from the fileInfo/uuid element

AMF_NAME shall be used to convey the AMF file name located in the same folder as the .edl source file

if both are defined, what is the rule/priority?

	a) UUID first, then NAME
	b) NAME first, then UUID

### EDL event example:

~~~
...
010   Clip1   V     C          05:40:12:18 05:40:14:09 01:00:29:16 01:00:31:07
* AMF_URL ./example.amf
* AMF_UUID afe122be-59d3-4360-ad69-33c10108fa7a
...
~~~

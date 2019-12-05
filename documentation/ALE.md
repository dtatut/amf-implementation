# Avid Log Exchange (ALE) support

define	AMF_UUID
define	AMF_NAME

AMF_UUID shall be used to convey the AMF UUID from the fileInfo/uuid element

if both are defined, what is the rule/priority?
	a) UUID first, then NAME
	b) NAME first, then UUID

### ALE example:

~~~
...
Column
Name	Tracks	Start	End	Auxiliary TC1	Auxiliary TC2	Camroll	Labroll	Scene	Take	ASC_SOP	ASC_SAT	AMF_UUID	AMD_NAME

Data
clip_001.mxf	V	00:00:00;00	00:11:59;01	00:00:00;00	00:00:00;00	unknown	unknown	unknown	unknown	(1.0000 1.0000 1.0000) (0.0000 0.0000 0.0000) (1.0000 1.0000 1.0000)	1.0000	afe122be-59d3-4360-ad69-33c10108fa7a	clip_001.amf
clip_002.mxf	V	00:01:00;00	00:02:59;01	00:00:00;00	00:00:00;00	unknown	unknown	unknown	unknown	(1.0000 1.0000 1.0000) (0.0000 0.0000 0.0000) (1.0000 1.0000 1.0000)	1.0000	afe122be-59d3-4360-ad69-33c10108fa7a	clip_002.amf
...
~~~

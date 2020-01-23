# Avid Log Exchange (ALE) support

The Avid Log Exchange (ALE) format supports custom metadata elements through the definition of dedicated columns in the ALE table. In order to support AMF linkage through ALE, the following columns are defined:

1. AMF_UUID

2. AMF_NAME

These two columns enable the linkage of AMF files, independently for every clip listed in the ALE file. Both AMF_UUID and AMF_NAME are defined as optional. The linkage rules are described below.

## AMF_UUID

The AMF_UUID column shall be used to convey the AMF UUID from the amfInfo/uuid element. The format of the column entries must use the canonical textual representation, the 16 octets of a UUID are represented as 32 hexadecimal (base-16) digits, displayed in 5 groups separated by hyphens, in the form 8-4-4-4-12 for a total of 36 characters (32 alphanumeric characters and 4 hyphens):

~~~
afe122be-59d3-4360-ad69-33c10108fa7a
~~~

The AMF_UUID column is optional

## AMF_NAME

AMF_NAME shall be used to convey the AMF file name located in the same folder as the .ale source file:

~~~
clip_001.amf
~~~

The AMF_NAME is optional. When present, it should indicate the file name of the AMF document related to the clip. The AMF file must reside locally in the same folder as the ALE file. No sub-folder structure is permitted.

While AMF file can have any name, it is recommended to use the same base name as the clip file that the AMF document relates to. Moreover to ensure portability across file systems and operating systems it is recommended to use characters from the set a-z, A-Z, 0-9, - (dash), _ (underscore) and ".".

The AMF file name should use no more than 1024 characters.

## Linkage Rules

Since both AMF_UUID and AMF_NAME are optional, there are four possible combinations that can occur:

1. AMF_UUID and AMF_NAME are both absent

In this case, no AMF file can be associated with the clip and is treated like a regular ALE file

2. AMF_UUID is present and AMF_NAME is absent

In this case the host product must look for the corresponding AMF files into a database, using the UUID as a key to match the AMF file and the corresponding clip. Please note that the word "database" does not imply any specific implementation. This feature many not be supported by the host product

3. AMF_UUID is absent and AMF_NAME is present

In this case, the AMF_NAME column contains file names for AMF files that should be located at the same level in the file system (i.e. same folder) as the ALE file, or in a subfolder. The linkage is based on the file name and the UUID of the AMF files (if present) is ignored

4. AMF_UUID and AMF_NAME are both present

In this case, the host product can select between the methods described in 2) and 3). However, it is recommended to rely on the UUID in priority. The host product can provide and option to select the matching rule (UUID or file name). It is desirable to also provide a matching rule that checks both the UUID and file name.

### ALE example:

~~~
...
Column
Name	Tracks	Start	End	Auxiliary TC1	Auxiliary TC2	Camroll	Labroll	Scene	Take	ASC_SOP	ASC_SAT	AMF_UUID	AMF_NAME

Data
clip_001.mxf	V	00:00:00;00	00:11:59;01	00:00:00;00	00:00:00;00	unknown	unknown	unknown	unknown	(1.0000 1.0000 1.0000) (0.0000 0.0000 0.0000) (1.0000 1.0000 1.0000)	1.0000	afe122be-59d3-4360-ad69-33c10108fa7a	clip_001.amf
clip_002.mxf	V	00:01:00;00	00:02:59;01	00:00:00;00	00:00:00;00	unknown	unknown	unknown	unknown	(1.0000 1.0000 1.0000) (0.0000 0.0000 0.0000) (1.0000 1.0000 1.0000)	1.0000	afe122be-59d3-4360-ad69-33c10108fa7a	clip_002.amf
...
~~~

## Remarks

1. Since the ALE file can reference a large number of clips, it is recommended that the host product presents the issues encountered during the linkage and validation process as a log.

2. ALE files can carry inline ASC parameters. When using AMF with EDLs, the inline ASC parameters should be absent to avoid confusion, or ignored if present. If the inline parameters are present they should be identical to the ASC parameters provided by the AMF file for compatibility with systems not supporting AMF. However this is not a recommended practice.

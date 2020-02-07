# OpenTimelineIO Test Vector #1 - Minimal

## Goal

Test minimal support for AMF in OpenTimelineIO (OTIO) files

## Procedure

1. Load the .otio file into the product
2. Verifiy that the tool correctly reports the presence of the AMF files for each entry in the OTIO file
3. Set the ACES pipeline according to AMF elements

## Success criteria

1. The product shall configure it's internal ACES pipeline to the work with the ACES version specified in the acesPipeline/pipelineInfo/acesVersion element.

2. The RRT shall be selected based on the version specified in the acesPipeline/outputTransform/rrt/transformId element

3. The ODT shall be selected based on the version specified in the acesPipeline/outputTransform/odt/transformId element

## Remarks

Several situations may occur where the host product cannot succeed while performing the procedure described above. Some common situations are described below with the recommended behavior:

1. ACES version is not supported

The host product should display an error message. The user should be given the choice to proceed with different settings or cancel the operation. The exact behavior should be documented by the manufacturer

2. RRT/ODT output transform ID is invalid or not supported

The host product should display an error message. The user should be given the choice to proceed with different settings or cancel the operation The exact behavior shouldbe documented by the manufacturer

## Notes

It is desirable that the host product offers an option to disable/bypass the error/warning messages that could occur when checking the support for the specified ACES version and/or the transform versions. Typically the "patch" number is not impacting the algorithm implemented by a specific transform and can be ignored during checks.

Moreover the host product should offer a fallback mechanism to avoid workflow disruption. For instance, if ACES v1.0.3 is not supported/implemented but ACES v1.0.0 is, then the host product should use ACES v1.0.0 as a substitute.

## Test Material

1. [OTIOV1_minimal.otio](OTIOV1_minimal.otio)

Minimal valid file

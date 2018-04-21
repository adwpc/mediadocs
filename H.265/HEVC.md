# H.265/HEVC

ISO/IEC 14496-15, 8.3.3.1.2 Syntax

```
aligned(8) class HEVCDecoderConfigurationRecord {
	unsigned int(8) configurationVersion = 1;
	unsigned int(2) general_profile_space;
	unsigned int(1) general_tier_flag;
	unsigned int(5) general_profile_idc;
	unsigned int(32) general_profile_compatibility_flags;
	unsigned int(48) general_constraint_indicator_flags;
	unsigned int(8) general_level_idc;
	bit(4) reserved = ‘1111’b;
	unsigned int(12) min_spatial_segmentation_idc;
	bit(6) reserved = ‘111111’b;
	unsigned int(2) parallelismType;
	bit(6) reserved = ‘111111’b;
	unsigned int(2) chromaFormat;
	bit(5) reserved = ‘11111’b;
	unsigned int(3) bitDepthLumaMinus8;
	bit(5) reserved = ‘11111’b;
	unsigned int(3) bitDepthChromaMinus8;
	bit(16) avgFrameRate;
	bit(2) constantFrameRate;
	bit(3) numTemporalLayers;
	bit(1) temporalIdNested;
	unsigned int(2) lengthSizeMinusOne; 
	unsigned int(8) numOfArrays;
	for (j=0; j < numOfArrays; j++) {
		bit(1) array_completeness;
		unsigned int(1) reserved = 0;
		unsigned int(6) NAL_unit_type;
		unsigned int(16) numNalus;
		for (i=0; i< numNalus; i++) {
			unsigned int(16) nalUnitLength;
			bit(8*nalUnitLength) nalUnit;
		}
	}
}
```

ITU-T H.265(ISO/IEC 23008-2), A.3 Profiles

|idc|Profile|
|---|---|
|  1|Main|
|  2|Main 10|
|  3|Main Still Picture|

ITU-T H.265(ISO/IEC 23008-2), A.4 Tiers and levels

|flag|Tier|
|---|---|
|  0|Main|
|  1|High|

|idc|Level|
|---|---|
| 30|1|
| 60|2|
| 63|2.1|
| 90|3|
| 93|3.1|
|120|4|
|123|4.1|
|150|5|
|153|5.1|
|156|5.2|
|180|6|
|183|6.1|
|186|6.2|
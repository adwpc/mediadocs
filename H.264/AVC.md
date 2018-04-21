# H.264/AVC

ISO/IEC 14496-15, 5.3.3.1.2 Syntax

```
aligned(8) class AVCDecoderConfigurationRecord {
	unsigned int(8) configurationVersion = 1;
	unsigned int(8) AVCProfileIndication;
	unsigned int(8) profile_compatibility;
	unsigned int(8) AVCLevelIndication; 
	bit(6) reserved = '111111'b;
	unsigned int(2) lengthSizeMinusOne; 
	bit(3) reserved = '111'b;
	unsigned int(5) numOfSequenceParameterSets;
	for (i = 0; i < numOfSequenceParameterSets; i++) {
		unsigned int(16) sequenceParameterSetLength ;
		bit(8*sequenceParameterSetLength) sequenceParameterSetNALUnit;
	}
	unsigned int(8) numOfPictureParameterSets;
	for (i = 0; i < numOfPictureParameterSets; i++) {
		unsigned int(16) pictureParameterSetLength;
		bit(8*pictureParameterSetLength) pictureParameterSetNALUnit;
	}
	if (profile_idc == 100 || profile_idc == 110 ||
	    profile_idc == 122 || profile_idc == 144)
	{
		bit(6) reserved = '111111'b;
		unsigned int(2) chroma_format;
		bit(5) reserved = '11111'b;
		unsigned int(3) bit_depth_luma_minus8;
		bit(5) reserved = '11111'b;
		unsigned int(3) bit_depth_chroma_minus8;
		unsigned int(8) numOfSequenceParameterSetExt;
		for (i = 0; i < numOfSequenceParameterSetExt; i++) {
			unsigned int(16) sequenceParameterSetExtLength;
			bit(8*sequenceParameterSetExtLength) sequenceParameterSetExtNALUnit;
		}
	}
}
```

ITU-T H.264(ISO/IEC 14496-10), A.2 Profiles

|idc|Profile|
|---|---|
| 66|Baseline|
| 77|Main|
| 88|Extended|
|100|High|
|110|High 10|
|122|High 4:2:2|
|144|(High 4:4:4; removed)|
|244|High 4:4:4 Predictive|

ITU-T H.264(ISO/IEC 14496-10), A.3 Levels

Defined level_idc: 10, 9[^1], 11, 12, 13, 20, 21, 22, 30, 31, 32, 40, 41, 42, 50, 51, 52

[^1]: `level_idc==9` represents "Leve 1b" **unless** Baseline(Constrained Baseline), Main, or Extended profiles.

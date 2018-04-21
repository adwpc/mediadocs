# AAC
ISO/IEC 14496-3, 1.6.2.1 AudioSpecificConfig

```
AudioSpecificConfig() {
	audioObjectType = GetAudioObjectType();
	samplingFrequencyIndex; // 4 bslbf
	if (samplingFrequencyIndex == 0xf) {
		samplingFrequency; // 24 uimsbf
	}
	channelConfiguration; // 4 bslbf
	sbrPresentFlag = -1;
	psPresentFlag = -1;
	if (audioObjectType == 5 || audioObjectType == 29) {
		// ...
	}
	else {
		extensionAudioObjectType = 0;
	}
	switch (audioObjectType) {
	case 1: case 2: case 3: case 4: //...
		GASpecificConfig();
		break:
	case ...:
		//...
	}
	if (extensionAudioObjectType != 5 && bits_to_decode() >= 16) {
		//...
	}
```

```
GetAudioObjectType() {
	audioObjectType; // 5 uimsbf
	if (audioObjectType == 31) {
		audioObjectType = 32 + audioObjectTypeExt; // 6 uimsbf
	}
	return audioObjectType;
}
```

ISO/IEC 14496-3, 1.5.1.1 Audio object type definition

|ID|Type|
|---|---|
|0|Null|
|1|AAC main|
|2|AAC LC|
|3|AAC SSR|
|4|AAC LTP|
|5|SSR|
|...|...|

ISO/IEC 14496-3, 1.6.3.4 samplingFrequencyIndex

|index|value|
|---|---|
|0x0|96000|
|0x1|88200|
|0x2|64000|
|0x3|48000|
|0x4|44100|
|0x5|32000|
|0x6|24000|
|0x7|22050|
|0x8|16000|
|0x9|12000|
|0xa|11025|
|0xb|8000|
|0xc|7350|
|0xd|reserved|
|0xe|reserved|
|0xf|escape value|
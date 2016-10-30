# Inputs

WeTranscode supports different types of uploads of the origins. 
please see below



## Create input URL

> Example Request

```java
weTranscode.apiKey = "sk_test_jCDpqFHg7nMDaIF7OQrkRMxE";

Map<String, Object> params = new HashMap<String, Object>();
params.put("type", "URL");
param.put("url","http://www.johnOrigins.com/best_movie.mp4");
params.put("user", "John");
params.put("pass", "John_password");
Subscription.create(params);
```

> The above command returns HTTP Response:

```http
HTTP/1.1 201 OK
Content-Type: application/json

{
  "jobId": "57f0f41b010000fc0697de25",
  "status": "success",
  "statusString": "uploaded finished with no errors",
  "accountId": "f9b3c20c-9209-401e-a151-3afef52b6523",
  "inputType": "URL",
  "fileName": "SampleVideo_1280x720_1mb_233125586.mp4",
  "analyzeProgress": 100,
  "sourceThumbnail": "https://etranscoder.s3.amazonaws.com/jobs/57fde25/sources/0000fc0697.jpg",
  "mediaInfo": {
	"general": {
	  "completeName": "/opt/ecomedia/sources/57f0f41b010000fc0697de25_0.mp4",
	  "format": "MPEG-4",
	  "formatProfile": "Base Media / Version 2",
	  "codecId": "mp42 (isom/iso2/avc1/mp41/mp42)",
	  "fileSize": "245KiB",
	  "duration": 5504,
	  "overallBitRate": "364kb/s"
	},
	"video": {
	  "id": "1",
	  "format": "AVC",
	  "formatProfile": "Baseline@L1.3",
	  "duration": 5334,
	  "bitRate": "308kb/s",
	  "width": "428",
	  "height": "240",
	  "frameRate": "24.000FPS"
	},
	"audios": [
	  {
		"id": "2",
		"format": "AAC",
		"codecId": "40",
		"duration": 5504,
		"bitRate": "61.6kb/s",
		"samplingRate": "44.1kHz",
		"audioChannels": "2 channels"
	  }
	]
  }
}
```

This allows you to create an input URL where your origin is located

### HTTP Request
`POST http://www.wetranscode.com/upload/remote/`

### Query Parameters

Parameter | type | Default | Description
--------- | ---- | ------- | -----------
Type | String | URL | For URL input, this must be URL or FTP
URL | String | N/A  | Valid HTTP URL to your file (Allowed protocols: http(s),(s)ftp)
UserName | String | N/A | the user name 
Password | String |N/A |Auth Password

<aside class="success">
Pay attention that the URL should be a path of a specific file and not a folder that contains few files
</aside>



## Create S3 input
> Example Request

```java
weTranscode.apiKey = "sk_test_jCDpqFHg7nMDaIF7OQrkRMxE";

Map<String, Object> params = new HashMap<String, Object>();
params.put("type", "S3");
param.put("accessKey","132415sgsgs35gsdg");
params.put("secretKey", "132415sgsgs35gsdg");
params.put("bucket", "Mygreatmovies");
params.put("region", "eu-west-1");
params.put("objectKey", "pathOnBucket/to/your/file.mp4");
Subscription.create(params);
```
> The above command returns HTTP Response:

```http

HTTP/1.1 201 OK
Content-Type: application/json

{
  "jobId": "57f0f41b010000fc0697de25",
  "status": "success",
  "statusString": "uploaded finished with no errors",
  "accountId": "f9b3c20c-9209-401e-a151-3afef52b6523",
  "inputType": "S3",
  "fileName": "SampleVideo_1280x720_1mb_233125586.mp4",
  "analyzeProgress": 100,
  "sourceThumbnail": "https://etranscoder.s3.amazonaws.com/jobs/57fde25/sources/0000fc0697.jpg",
  "mediaInfo": {
	"general": {
	  "completeName": "/opt/ecomedia/sources/57f0f41b010000fc0697de25_0.mp4",
	  "format": "MPEG-4",
	  "formatProfile": "Base Media / Version 2",
	  "codecId": "mp42 (isom/iso2/avc1/mp41/mp42)",
	  "fileSize": "245KiB",
	  "duration": 5504,
	  "overallBitRate": "364kb/s"
	},
	"video": {
	  "id": "1",
	  "format": "AVC",
	  "formatProfile": "Baseline@L1.3",
	  "duration": 5334,
	  "bitRate": "308kb/s",
	  "width": "428",
	  "height": "240",
	  "frameRate": "24.000FPS"
	},
	"audios": [
	  {
		"id": "2",
		"format": "AAC",
		"codecId": "40",
		"duration": 5504,
		"bitRate": "61.6kb/s",
		"samplingRate": "44.1kHz",
		"audioChannels": "2 channels"
	  }
	]
  }
}
```

### HTTP Request
`POST http://www.wetranscode.com/upload/remote/`

### Query Parameters

Parameter | type  | Description
--------- | ---- | -----------
Type | String |  For S3 input, this must be S3
accessKey | String |  Your AWS AccessKey
secretKey | String |  your AWS secretKey 
bucket | String | your bucket name
region | string | your region e.g eu-west-1
objectKey | string | Path to your input file


## Create GCS input

> Example Request

```java
weTranscode.apiKey = "sk_test_jCDpqFHg7nMDaIF7OQrkRMxE";

Map<String, Object> params = new HashMap<String, Object>();
params.put("type", "GCS");
param.put("accessKey","132415sgsgs35gsdg");
params.put("secretKey", "132415sgsgs35gsdg");
params.put("bucket", "Mygreatmovies");
params.put("objectKey", "pathOnBucket/to/your/file.mp4");
Subscription.create(params);
```
> The above command returns HTTP Response:

```http

HTTP/1.1 201 OK
Content-Type: application/json

{
  "jobId": "57f0f41b010000fc0697de25",
  "status": "success",
  "statusString": "uploaded finished with no errors",
  "accountId": "f9b3c20c-9209-401e-a151-3afef52b6523",
  "inputType": "GCS",
  "fileName": "SampleVideo_1280x720_1mb_233125586.mp4",
  "analyzeProgress": 100,
  "sourceThumbnail": "https://etranscoder.s3.amazonaws.com/jobs/57fde25/sources/0000fc0697.jpg",
  "mediaInfo": {
	"general": {
	  "completeName": "/opt/ecomedia/sources/57f0f41b010000fc0697de25_0.mp4",
	  "format": "MPEG-4",
	  "formatProfile": "Base Media / Version 2",
	  "codecId": "mp42 (isom/iso2/avc1/mp41/mp42)",
	  "fileSize": "245KiB",
	  "duration": 5504,
	  "overallBitRate": "364kb/s"
	},
	"video": {
	  "id": "1",
	  "format": "AVC",
	  "formatProfile": "Baseline@L1.3",
	  "duration": 5334,
	  "bitRate": "308kb/s",
	  "width": "428",
	  "height": "240",
	  "frameRate": "24.000FPS"
	},
	"audios": [
	  {
		"id": "2",
		"format": "AAC",
		"codecId": "40",
		"duration": 5504,
		"bitRate": "61.6kb/s",
		"samplingRate": "44.1kHz",
		"audioChannels": "2 channels"
	  }
	]
  }
}
```

### HTTP Request
`POST http://www.wetranscode.com/upload/remote/`

### Query Parameters

Parameter | type  | Description
--------- | ---- | -----------
Type | String |  For GCS input, this must be GCS
accessKey | String |  Your GCS AccessKey
secretKey | String |  your GCS secretKey 
bucket | String | your bucket name
objectKey | string | Path to your input file



## Create Azure input

> Example Request

```java
weTranscode.apiKey = "sk_test_jCDpqFHg7nMDaIF7OQrkRMxE";

Map<String, Object> params = new HashMap<String, Object>();
params.put("type", "azure");
param.put("accountName","132415sgsgs35gsdg");
params.put("accountKey", "132415sgsgs35gsdg");
params.put("url", "Mygreatmovies");
params.put("container", "pathOnBucket/to/your/file.mp4");
Subscription.create(params);
```
> The above command returns HTTP Response:

```http

HTTP/1.1 201 OK
Content-Type: application/json

{
  "jobId": "57f0f41b010000fc0697de25",
  "status": "success",
  "statusString": "uploaded finished with no errors",
  "accountId": "f9b3c20c-9209-401e-a151-3afef52b6523",
  "inputType": "Azure",
  "fileName": "SampleVideo_1280x720_1mb_233125586.mp4",
  "analyzeProgress": 100,
  "sourceThumbnail": "https://etranscoder.s3.amazonaws.com/jobs/57fde25/sources/0000fc0697.jpg",
  "mediaInfo": {
	"general": {
	  "completeName": "/opt/ecomedia/sources/57f0f41b010000fc0697de25_0.mp4",
	  "format": "MPEG-4",
	  "formatProfile": "Base Media / Version 2",
	  "codecId": "mp42 (isom/iso2/avc1/mp41/mp42)",
	  "fileSize": "245KiB",
	  "duration": 5504,
	  "overallBitRate": "364kb/s"
	},
	"video": {
	  "id": "1",
	  "format": "AVC",
	  "formatProfile": "Baseline@L1.3",
	  "duration": 5334,
	  "bitRate": "308kb/s",
	  "width": "428",
	  "height": "240",
	  "frameRate": "24.000FPS"
	},
	"audios": [
	  {
		"id": "2",
		"format": "AAC",
		"codecId": "40",
		"duration": 5504,
		"bitRate": "61.6kb/s",
		"samplingRate": "44.1kHz",
		"audioChannels": "2 channels"
	  }
	]
  }
}
```

### HTTP Request
`POST http://www.wetranscode.com/upload/remote/`

### Query Parameters

Parameter | type  | Description
--------- | ---- | -----------
Type | String |  For S3 input, this must be S3
accountName | String |  Your Azure accountName
accountKey | String |  your Azure accountKey 
url | String | https://yourAccountName.blob.core.windows.net/yourContainerName/videoObjectInContainer.mkv
container | string | Path to your input file e.g. yourAzureStorageContainer

## Create Aspera Input

> Example Request

```java
weTranscode.apiKey = "sk_test_jCDpqFHg7nMDaIF7OQrkRMxE";

Map<String, Object> params = new HashMap<String, Object>();
params.put("type", "aspera");
param.put("url","fasp://urlof/your/asperasource/video.mp4");
params.put("minBandwidth", "minimal_download_bandwidth");
params.put("maxBandwidth", "maximal_download_bandwidth");
Subscription.create(params);
```
> The above command returns JSON structured like this:

```http

HTTP/1.1 201 OK
Content-Type: application/json

{
  "jobId": "57f0f41b010000fc0697de25",
  "status": "success",
  "statusString": "uploaded finished with no errors",
  "accountId": "f9b3c20c-9209-401e-a151-3afef52b6523",
  "inputType": "Aspera",
  "fileName": "SampleVideo_1280x720_1mb_233125586.mp4",
  "analyzeProgress": 100,
  "sourceThumbnail": "https://etranscoder.s3.amazonaws.com/jobs/57fde25/sources/0000fc0697.jpg",
  "mediaInfo": {
	"general": {
	  "completeName": "/opt/ecomedia/sources/57f0f41b010000fc0697de25_0.mp4",
	  "format": "MPEG-4",
	  "formatProfile": "Base Media / Version 2",
	  "codecId": "mp42 (isom/iso2/avc1/mp41/mp42)",
	  "fileSize": "245KiB",
	  "duration": 5504,
	  "overallBitRate": "364kb/s"
	},
	"video": {
	  "id": "1",
	  "format": "AVC",
	  "formatProfile": "Baseline@L1.3",
	  "duration": 5334,
	  "bitRate": "308kb/s",
	  "width": "428",
	  "height": "240",
	  "frameRate": "24.000FPS"
	},
	"audios": [
	  {
		"id": "2",
		"format": "AAC",
		"codecId": "40",
		"duration": 5504,
		"bitRate": "61.6kb/s",
		"samplingRate": "44.1kHz",
		"audioChannels": "2 channels"
	  }
	]
  }
}
```

### HTTP Request
`POST http://www.wetranscode.com/upload/remote/`

### Query Parameters

Parameter | type  | Description
--------- | ---- | -----------
Type | String |  For Aspera input, this must be aspera
url | String | The URL Path to your Video file e.g. fasp://urlof/your/asperasource/video.mp4
minBandwidth | String |  Minimal download bandwidth. Examples: 100k, 100m, 100g
maxBandwidth | String | Maximal download bandwidth. Examples: 100k, 100m, 100g

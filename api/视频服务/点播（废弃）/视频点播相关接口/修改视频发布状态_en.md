## 1. API Description


This API (SetVodPlayStatus) is used to pause or resume  playing a video.

 
Domain: vod.api.qcloud.com



## 2. Input Parameters
 
<table class="t"><tbody><tr>
<th><b>Parameter Name</b></th>
<th><b>Required</b></th>
<th><b>Type</b></th>
<th><b>Description</b></th>
<tr>
<td> fileId
<td> Yes
<td> String
<td> Video ID
<tr>
<td> playStatus
<td> Yes
<td> Int
<td> Video playing status. 0 means Paused, and 1 means Resumed
</tbody></table>

 

## 3. Output Parameters
 
<table class="t"><tbody><tr>
<th><b>Parameter Name</b></th>
<th><b>Type</b></th>
<th><b>Description</b></th>
<tr>
<td> code
<td> Int
<td> Error code. 0:  Succeeded, other values:  Failed
<tr>
<td> message
<td> String
<td> Error message
</tbody></table>

 

## 4. Example
 
Input
<pre>
  https://domain/v2/index.php?ActionSetVodPlayStatus
  &fileId=2721945854681023354
  &playStatus=1
  &<a href="https://cloud.tencent.com/doc/api/229/6976">Common request parameters</a>
</pre>
Output
```

{
    "code" : 0,
    "message" : "",
}

```




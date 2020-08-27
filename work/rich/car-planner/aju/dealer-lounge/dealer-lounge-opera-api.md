# OPERA API


## Request

```perl

{
  "info": {
      "sid":"insuOnGins"
      ,"aid":"counselState"
      ,"timeStamp":"1512301234564",
      "reqDateTime":"20200419145601"
  },
  "data":
   {
     "srchYear":"2020",
     "srchMonth":"06",
     "udid":"DA0000",
     "tmSeqnoArray": [
        77312,77313
     ]
   }
}

```


## Response

```perl
{
  "info": {
      "sid":"gBizOpera",
      "aid":"counselState",
      "rtnCode":"S000",
      "rtnMsg":"성공",
      "timeStamp":"1512301234564",
      "rtnDateTime":"20200419145601"
   },
  "data":{
    "statusArray": [
      {
       "tmSeqno":"77312",
      "statusCode":"02"
      },
      {
      "tmSeqno":"77313",
      "statusCode":"06"
      }
    ]
  }
}
```

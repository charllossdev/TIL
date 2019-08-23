# Egovframework Annotation

Egovframework API

* [egovframework:rte:ptl:annotation-based_controller](https://www.egovframe.go.kr/wiki/doku.php?id=egovframework:rte:ptl:annotation-based_controller)
* [egovframework:rte:fdl:ioc_container:annotation-based_configuration](https://www.egovframe.go.kr/wiki/doku.php?id=egovframework:rte:fdl:ioc_container:annotation-based_configuration)


## jqGrid Ajax Controller Setting

* @RequestMapping
    * value: Location
    * produces: Ajax Return Object Type(Json Object), Character Setting
* @ResponseBody
    * Ajax ResponseBody Return

```java
@RequestMapping(value 		= "/dpBnnrList.do",
					produces 	= "application/json; charset=utf8")
	@ResponseBody
	public String dpBnnrList() {

		Map<String, Object> resMap = new HashMap<String, Object>();

		try {
			List<EgovMap> bnList = dpService.selectBnServiceList();

			System.out.println(bnList);

			resMap.put("rows", bnList);
		} catch (Exception e) {

		}

		return JsonUtil.HashMapToJson((HashMap<String, Object>) resMap);
	}
```

## Dynamic URL Location Setting

* @RequestMapping
    * Dynamic Url Location Set Parameter Map
* @PathVariable
    * URL Set Map
    * Set Key, Get Key as @RequestMapping Keys

```java
//view에서 올라온 url을 / 기준으로 구별해주는 기능
@RequestMapping("/{step}/{gisu}.do")
public String pageAllInit(@PathVariable Map<String, String> pathMap) throws Exception {
    System.out.println(pathMap);

    return pathMap.get("step") + "/" + pathMap.get("gisu");
}
```

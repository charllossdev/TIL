# PG Inicis
Api Doc: https://manual.inicis.com/mobile/

Import 연동 시도해보기: https://www.iamport.kr/getstarted
## Test User

```Java
// 상점 ID
private final static String TEST_P_MID 		   	= "INIpayTest";

// 이니시스 Test Hash Key
private final static String TEST_PG_HASH_KEY	= "ItEQKi3rY7uvDS8l";
private final static String TEST_PG_IV 			  = "HYb3yQ4f65QL89==";
```


## Api Source


```java
package com.richncar.groom.api.external.inicis;

import java.math.BigInteger;
import java.net.InetAddress;
import java.net.URLEncoder;
import java.nio.charset.Charset;
import java.security.MessageDigest;
import java.text.SimpleDateFormat;
import java.util.HashMap;
import java.util.Map;
import org.json.simple.JSONObject;
import org.json.simple.parser.JSONParser;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.http.HttpEntity;
import org.springframework.http.HttpHeaders;
import org.springframework.http.client.HttpComponentsClientHttpRequestFactory;
import org.springframework.http.converter.StringHttpMessageConverter;
import org.springframework.util.LinkedMultiValueMap;
import org.springframework.util.MultiValueMap;
import org.springframework.web.client.RestTemplate;

import com.richncar.groom.web.trial.model.PgPayment;

public class Inicis {
	private static final Logger logger = LoggerFactory.getLogger(Inicis.class);
	private final SimpleDateFormat dateFormat = new SimpleDateFormat("yyyyMMddHHmmss");

	// 상점 ID // 실상점 ID richncoin0 //테스트 상점 ID INIpayTest
	private final static String P_MID 				= "richncoin0";
	private final static String TEST_P_MID 			= "INIpayTest";

	// 이니시스 Hash Key
	private final static String PG_HASH_KEY 		= "CmiX6SJFxQzLrBT4";
	private final static String PG_IV 				= "6eKjCNuaYyi861==";

	// 이니시스 Test Hash Key
	private final static String TEST_PG_HASH_KEY	= "ItEQKi3rY7uvDS8l";
	private final static String TEST_PG_IV 			= "HYb3yQ4f65QL89==";

	private final int TIME_OUT_INT_VALUE 			= 120 * 1000;
	private final String INICIS_PAYMENT_CANCLE_URL 	= "https://iniapi.inicis.com/api/v1/refund";

	/**
	 * 전문통신 - 이니시스 결제 승인 전문
	 * @author charllossDev
	 * @param  PG params
	 * @return Map<String, Object>  
	 */
	public Map<String, Object> apiPgPaymentCallRequest(Map<String, Object> param) throws Exception {

		String charSet = "EUC-KR";
		Map<String, Object> resultMap = null;
		MultiValueMap<String,String> paramMap = new LinkedMultiValueMap<String, String>();
		paramMap.add("P_MID", TEST_P_MID);
		paramMap.add("P_TID", param.get("P_TID").toString());
		logger.debug("apiPgPaymentCallRequest: " + param.toString());

		try {
			resultMap = getPgReturnMap(this.restApiCall(charSet, param.get("P_REQ_URL").toString(), paramMap));
			logger.debug("apiPgPaymentCallRequest Data: " + resultMap.toString());
		} catch (Exception e) {
			logger.error("apiPgPaymentCallRequest Error: " + e.toString());
		}

		return resultMap;
	}

	/**
	 * 전문통신 - 이니시스 결제 취소 전문
	 * @author charllossDev
	 * @param  PgPayment
	 * @return JSONObject  
	 */
	public JSONObject apiPgPaymentCancleRequest(PgPayment pgPayment) throws Exception {

		String paymethod 	= null;
    	String charSet		= "UTF-8";
    	String type 		= "Refund";

    	String mid 			= TEST_P_MID;
    	String timestamp 	= dateFormat.format(pgPayment.getpAuthDt());
    	String tid 			= pgPayment.getpTid();
    	String clientIp 	= InetAddress.getLocalHost().getHostAddress();//local.getHostAdress();
    	String msg 			= "결제 취소";

    	if ("CARD".equals(pgPayment.getpType())) {
    		paymethod = "Card";
    	}

    	String plainText = TEST_PG_HASH_KEY + type + paymethod + timestamp + clientIp + mid + tid;
    	String hashData = getSHA512(plainText);

    	JSONObject resultJson = null;

    	StringBuilder paramBuilder = new StringBuilder();
    	paramBuilder.append(String.format("%s=%s", URLEncoder.encode("type", charSet),URLEncoder.encode(type, charSet)));
    	paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("paymethod", 	charSet),URLEncoder.encode(paymethod, 	charSet)));
    	paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("timestamp",	charSet),URLEncoder.encode(timestamp, 	charSet)));
    	paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("clientIp",  	charSet),URLEncoder.encode(clientIp,  	charSet)));
    	paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("mid", 		charSet),URLEncoder.encode(mid, 		charSet)));
    	paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("tid", 		charSet),URLEncoder.encode(tid, 		charSet)));
    	paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("msg",		charSet),URLEncoder.encode(msg, 		charSet)));
    	paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("hashData", 	charSet),URLEncoder.encode(hashData, 	charSet)));

    	HttpHeaders headers = new HttpHeaders();
		headers.add("Content-Type", "application/x-www-form-urlencoded; charset=" + charSet);

		try {
			resultJson = (JSONObject)new JSONParser().parse(this.restApiCall(headers, INICIS_PAYMENT_CANCLE_URL, paramBuilder.toString()));
			logger.debug("apiPgPaymentCancleRequest Data : " + resultJson.toString());
		} catch (Exception e) {
			logger.error("apiPgPaymentCancleRequest Error : " + e.toString());
		}

    	return resultJson;
	}

	private String restApiCall(String charSet, String url, Object param) throws Exception {
		RestTemplate restCallApiTemplate = getRestTemplate();
		restCallApiTemplate.getMessageConverters()
		.add(0, new StringHttpMessageConverter(Charset.forName(charSet)));

		return restCallApiTemplate.postForObject(url, param, String.class);
	}

	private String restApiCall(HttpHeaders headers, String url, String param) throws Exception {

		RestTemplate restCallApiTemplate = new RestTemplate();
		HttpEntity<String> request = new HttpEntity<>(param, headers);

		return restCallApiTemplate.postForObject(url, request, String.class);
	}

    private static Map<String, Object> getPgReturnMap(String result) {
    	Map<String, Object> resultMap = new HashMap<String, Object>();
    	String[] resultArr = result.split("&");

    	for (String s : resultArr) {

    		String[] sArr = s.split("=");

    		if (sArr.length == 2) {
    			resultMap.put(sArr[0], sArr[1]);
    		}
		}

    	return resultMap;
    }

	public static String getSHA512(String input){

	    String toReturn = null;
		try {
		    MessageDigest digest = MessageDigest.getInstance("SHA-512");
		    digest.reset();
		    digest.update(input.getBytes("utf8"));

	        //for (byte b : digest.digest()) sb.append(Integer.toHexString(0xff & b));

		    toReturn = String.format("%0128x", new BigInteger(1, digest.digest()));
		} catch (Exception e) {
		    e.printStackTrace();
		}

		return toReturn;
    }

	private RestTemplate getRestTemplate() {
	    HttpComponentsClientHttpRequestFactory factory

	         = new HttpComponentsClientHttpRequestFactory();
	    factory.setConnectTimeout(TIME_OUT_INT_VALUE);
	    factory.setReadTimeout(TIME_OUT_INT_VALUE);
	    RestTemplate restTemplate = new RestTemplate(factory);
	    return restTemplate;
	}
}
package com.richncar.groom.api.external.inicis;

import java.math.BigInteger;
import java.net.InetAddress;
import java.net.URLEncoder;
import java.nio.charset.Charset;
import java.security.MessageDigest;
import java.text.SimpleDateFormat;
import java.util.HashMap;
import java.util.Map;
import org.json.simple.JSONObject;
import org.json.simple.parser.JSONParser;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.http.HttpEntity;
import org.springframework.http.HttpHeaders;
import org.springframework.http.client.HttpComponentsClientHttpRequestFactory;
import org.springframework.http.converter.StringHttpMessageConverter;
import org.springframework.util.LinkedMultiValueMap;
import org.springframework.util.MultiValueMap;
import org.springframework.web.client.RestTemplate;

import com.richncar.groom.web.trial.model.PgPayment;

public class Inicis {
	private static final Logger logger = LoggerFactory.getLogger(Inicis.class);
	private final SimpleDateFormat dateFormat = new SimpleDateFormat("yyyyMMddHHmmss");

	// 상점 ID // 실상점 ID richncoin0 //테스트 상점 ID INIpayTest
	private final static String P_MID 				= "richncoin0";
	private final static String TEST_P_MID 			= "INIpayTest";

	// 이니시스 Hash Key
	private final static String PG_HASH_KEY 		= "CmiX6SJFxQzLrBT4";
	private final static String PG_IV 				= "6eKjCNuaYyi861==";

	// 이니시스 Test Hash Key
	private final static String TEST_PG_HASH_KEY	= "ItEQKi3rY7uvDS8l";
	private final static String TEST_PG_IV 			= "HYb3yQ4f65QL89==";

	private final int TIME_OUT_INT_VALUE 			= 120 * 1000;
	private final String INICIS_PAYMENT_CANCLE_URL 	= "https://iniapi.inicis.com/api/v1/refund";

	/**
	 * 전문통신 - 이니시스 결제 승인 전문
	 * @author charllossDev
	 * @param  PG params
	 * @return Map<String, Object>  
	 */
	public Map<String, Object> apiPgPaymentCallRequest(Map<String, Object> param) throws Exception {

		String charSet = "EUC-KR";
		Map<String, Object> resultMap = null;
		MultiValueMap<String,String> paramMap = new LinkedMultiValueMap<String, String>();
		paramMap.add("P_MID", TEST_P_MID);
		paramMap.add("P_TID", param.get("P_TID").toString());
		logger.debug("apiPgPaymentCallRequest: " + param.toString());

		try {
			resultMap = getPgReturnMap(this.restApiCall(charSet, param.get("P_REQ_URL").toString(), paramMap));
			logger.debug("apiPgPaymentCallRequest Data: " + resultMap.toString());
		} catch (Exception e) {
			logger.error("apiPgPaymentCallRequest Error: " + e.toString());
		}

		return resultMap;
	}

	/**
	 * 전문통신 - 이니시스 결제 취소 전문
	 * @author charllossDev
	 * @param  PgPayment
	 * @return JSONObject  
	 */
	public JSONObject apiPgPaymentCancleRequest(PgPayment pgPayment) throws Exception {

		String paymethod 	= null;
    	String charSet		= "UTF-8";
    	String type 		= "Refund";

    	String mid 			= TEST_P_MID;
    	String timestamp 	= dateFormat.format(pgPayment.getpAuthDt());
    	String tid 			= pgPayment.getpTid();
    	String clientIp 	= InetAddress.getLocalHost().getHostAddress();//local.getHostAdress();
    	String msg 			= "결제 취소";

    	if ("CARD".equals(pgPayment.getpType())) {
    		paymethod = "Card";
    	}

    	String plainText = TEST_PG_HASH_KEY + type + paymethod + timestamp + clientIp + mid + tid;
    	String hashData = getSHA512(plainText);

    	JSONObject resultJson = null;

    	StringBuilder paramBuilder = new StringBuilder();
    	paramBuilder.append(String.format("%s=%s", URLEncoder.encode("type", charSet),URLEncoder.encode(type, charSet)));
    	paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("paymethod", 	charSet),URLEncoder.encode(paymethod, 	charSet)));
    	paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("timestamp",	charSet),URLEncoder.encode(timestamp, 	charSet)));
    	paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("clientIp",  	charSet),URLEncoder.encode(clientIp,  	charSet)));
    	paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("mid", 		charSet),URLEncoder.encode(mid, 		charSet)));
    	paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("tid", 		charSet),URLEncoder.encode(tid, 		charSet)));
    	paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("msg",		charSet),URLEncoder.encode(msg, 		charSet)));
    	paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("hashData", 	charSet),URLEncoder.encode(hashData, 	charSet)));

    	HttpHeaders headers = new HttpHeaders();
		headers.add("Content-Type", "application/x-www-form-urlencoded; charset=" + charSet);

		try {
			resultJson = (JSONObject)new JSONParser().parse(this.restApiCall(headers, INICIS_PAYMENT_CANCLE_URL, paramBuilder.toString()));
			logger.debug("apiPgPaymentCancleRequest Data : " + resultJson.toString());
		} catch (Exception e) {
			logger.error("apiPgPaymentCancleRequest Error : " + e.toString());
		}

    	return resultJson;
	}

	private String restApiCall(String charSet, String url, Object param) throws Exception {
		RestTemplate restCallApiTemplate = getRestTemplate();
		restCallApiTemplate.getMessageConverters()
		.add(0, new StringHttpMessageConverter(Charset.forName(charSet)));

		return restCallApiTemplate.postForObject(url, param, String.class);
	}

	private String restApiCall(HttpHeaders headers, String url, String param) throws Exception {

		RestTemplate restCallApiTemplate = new RestTemplate();
		HttpEntity<String> request = new HttpEntity<>(param, headers);

		return restCallApiTemplate.postForObject(url, request, String.class);
	}

    private static Map<String, Object> getPgReturnMap(String result) {
    	Map<String, Object> resultMap = new HashMap<String, Object>();
    	String[] resultArr = result.split("&");

    	for (String s : resultArr) {

    		String[] sArr = s.split("=");

    		if (sArr.length == 2) {
    			resultMap.put(sArr[0], sArr[1]);
    		}
		}

    	return resultMap;
    }

	public static String getSHA512(String input){

	    String toReturn = null;
		try {
		    MessageDigest digest = MessageDigest.getInstance("SHA-512");
		    digest.reset();
		    digest.update(input.getBytes("utf8"));

	        //for (byte b : digest.digest()) sb.append(Integer.toHexString(0xff & b));

		    toReturn = String.format("%0128x", new BigInteger(1, digest.digest()));
		} catch (Exception e) {
		    e.printStackTrace();
		}

		return toReturn;
    }

	private RestTemplate getRestTemplate() {
	    HttpComponentsClientHttpRequestFactory factory

	         = new HttpComponentsClientHttpRequestFactory();
	    factory.setConnectTimeout(TIME_OUT_INT_VALUE);
	    factory.setReadTimeout(TIME_OUT_INT_VALUE);
	    RestTemplate restTemplate = new RestTemplate(factory);
	    return restTemplate;
	}
}
```


## Service Code

```java
@Override
	public Map<String, Object> apiPgPaymentOrderCall(Map<String, Object> param) throws Exception {

		boolean result = false;
		Inicis inicis = new Inicis();
		Map<String, Object> resultMap = new HashMap<String, Object>();
		Map<String, Object> pgResultMap = inicis.apiPgPaymentCallRequest(param);

		if (pgResultMap != null) {
			// 최종 결제 승인
			if (PG_API_SUCCESS.equals(pgResultMap.get("P_STATUS"))) {
				try {
					PgPayment pgPayment = PgPayment.setPgPayment(pgResultMap);
					pgPayment.setUid(Integer.parseInt(param.get("memberUid").toString()));
					pgPaymentDao.insert(pgPayment);

					MgTrialCar mgTrialCar = new MgTrialCar();
					mgTrialCar.setpTid(pgResultMap.get("P_TID").toString());
					mgTrialCar.setTelmsgno(pgResultMap.get("P_NOTI").toString());
					mgTrialCar.setProctype(pgResultMap.get("P_STATUS").toString());
					mgTrialCar.setModDate(new Date());
					mgTrialCarDao.updateMgTriaclCar(mgTrialCar);

					result = true;
				}catch (Exception e) {
					logger.error("TrialServiceImpl insertPgPaymentOrder insert error : "+e.getMessage() + "  " + e.toString());
					TransactionAspectSupport.currentTransactionStatus().setRollbackOnly();

					// 결제 취소
					if (true) {//this.apiPgPaymentOrderCancle(pgPayment)) {
						logger.error("###PG_INICIS CANCLE OK###");
					}
				}
				resultMap.put("MSG", "결제가 완료되었습니다.");
			} else {
				resultMap.put("MSG", "결제 과정에서 장애가 발생했습니다.<br>다시 시도해주세요.");
			}
		} else {
			resultMap.put("MSG", "결제 과정에서 네트워크 장애가 발생했습니다.<br>다시 시도해주세요.");
		}
		resultMap.put("SUCCESS", result);
		return resultMap;
	}

```

## Front Code

```js
<form  name="payForm" 	id="payForm" 		method="post" action='https://mobile.inicis.com/smart/payment/' accept-charset='euc-kr'>
<input type='hidden' 	name='P_NEXT_URL' 	 value="<c:out value='${P_NEXT_URL}'/>" />
<input type='hidden' 	name='P_GOODS' 		   value="<c:out value='${P_GOODS}'/>"/>
<input type='hidden' 	name='P_INI_PAYMENT' value="<c:out value='${P_INI_PAYMENT}'/>"/>
<input type='hidden' 	name='P_MID' 		     value="<c:out value='${P_MID}'/>"/>
<input type='hidden' 	name='P_OID' 		     value="<c:out value='${P_OID}'/>"/>
<input type='hidden' 	name='P_AMT' 		     value="<c:out value='${P_AMT}'/>"/>
<input type='hidden' 	name='P_UNAME' 		   value="<c:out value='${P_UNAME}'/>"/>
<input type='hidden' 	name='P_MNAME' 		   value="<c:out val ue='${P_MNAME}'/>"/>
<input type='hidden' 	name='P_NOTI' 		   value="<c:out value='${P_NOTI}'/>"/>
<input type='hidden' 	name='P_EMAIL' 		   value="<c:out value='${P_EMAIL}'/>"/>
</form>
<script type="text/javascript">

$(function() {

	$("#payForm").submit();
});


</script>
```

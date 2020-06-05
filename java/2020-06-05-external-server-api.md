# External Server API Connection 
외부 서버와 연동화여, API 통신 공통 모듈

## Param 생성

```java
String charSet		= "UTF-8";

StringBuilder paramBuilder = new StringBuilder();
paramBuilder.append(String.format("%s=%s", URLEncoder.encode("type", charSet),URLEncoder.encode(type, charSet)));
paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("paymethod", 	charSet),URLEncoder.encode(paymethod, 	charSet)));
paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("timestamp",	charSet),URLEncoder.encode(timestamp, 	charSet)));
paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("clientIp",  	charSet),URLEncoder.encode(clientIp,  	charSet)));
paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("mid", 		charSet),URLEncoder.encode(mid, 		charSet)));
paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("tid", 		charSet),URLEncoder.encode(tid, 		charSet)));
paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("msg",		charSet),URLEncoder.encode(msg, 		charSet)));
paramBuilder.append("&").append(String.format("%s=%s", URLEncoder.encode("hashData", 	charSet),URLEncoder.encode(hashData, 	charSet)));

```

## Target 설정
외부 서버 URL, 연결 옵션, 언어셋 설정

```java
HttpsURLConnection connect = null;
int TIME_OUT_INT_VALUE = 3000; // 3 second
URL pgResultUrl = new URL("https://iniapi.inicis.com/api/v1/refund"); // 연결 URL

connect = (HttpsURLConnection)pgResultUrl.openConnection();

connect.setConnectTimeout(TIME_OUT_INT_VALUE);
connect.setReadTimeout(TIME_OUT_INT_VALUE);  
connect.setRequestMethod("POST");

connect.setRequestProperty("Content-Type", "application/x-www-form-urlencoded;charset=utf-8");
connect.setRequestProperty("User-Agent","java-client");
connect.setRequestProperty("Cache-Control", "no-cache");
connect.setRequestProperty("Connection", "keep-alive");
connect.setRequestProperty("Content-Type", "application/x-www-form-urlencoded");
connect.setRequestProperty("charset", charSet);

connect.setDoInput(true);
connect.setDoOutput(true);
connect.setUseCaches(false);

```

## 외부 서버 호출

연결 실패 시, RETRY 로직 구현 고민중

```java
String responseParam = connectionExternalApi(connect, paramBuilder, charSet);

public String connectionExternalApi(HttpURLConnection connect, StringBuilder param, String charSet) {
	
	String				result = null;
	BufferedReader		reader = null;
	DataOutputStream	writer = null;

	try {
		
		writer = new DataOutputStream(connect.getOutputStream());
		writer.writeBytes(param.toString());
		writer.flush();
		
		if (connectState(connect.getResponseCode())) {

			String inputLine;
			StringBuffer response = new StringBuffer();

			reader = new BufferedReader(new InputStreamReader(connect.getInputStream(), charSet));

			while((inputLine = reader.readLine()) != null) {
				response.append(inputLine);
			}

			result = response.toString();
			logger.debug("###API CONNECTION### IP = " + connect.getURL().getPath());
			logger.debug("###API CONNECTION### RESULT = " + result);
		}	
		
	} catch (Exception e) {
		logger.debug("###API CONNECTION ERROR###:" +e.getMessage());
	} finally {
		if(writer != null ) try {writer.close();} 		catch(Exception ignore){}
		if(reader != null ) try {reader.close();} 		catch(Exception ignore){}
		if(connect!= null ) try {connect.disconnect();} catch(Exception ignore){}
	}

	return result;
}

private boolean connectState(int responseCode) {
	
	boolean result = false;
	int responseState = responseCode/100;
	
	if (responseState == 1) {
		logger.debug("###API HTTP STATE### INFO=" + responseCode);
	} else if (responseState == 2) {
		result = true;
		logger.debug("###API HTTP STATE### SUCCES=" + responseCode); 
	} else if (responseState == 3) {
		logger.debug("###API HTTP STATE### REDIRECT=" + responseCode);
	} else if (responseState == 4) {
		logger.debug("###API HTTP STATE### CLIENT ERROR=" + responseCode);
	} else if (responseState == 5) {
		logger.debug("###API HTTP STATE### SERVER ERROR=" + responseCode);
	} else {
		logger.debug("###API HTTP STATE### =" + responseCode);
	}
	
	return result;
}
```


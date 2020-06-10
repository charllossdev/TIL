# Java Rest API & JSON Paser

# Post Request
```java
Data actionAPI(JSONArray commandlist) {
    HttpURLConnection conn = null;
    JSONObject responseJson = null;
    
    try {
        //URL 설정
        URL url = new URL(this.HOST_URL + "/action");

        conn = (HttpURLConnection) url.openConnection();
        //Request 형식 설정
        conn.setRequestMethod("POST");
        conn.setRequestProperty("X-Auth-Token", this.token);
        conn.setRequestProperty("Content-Type", "application/json");

        //request에 JSON data 준비
        conn.setDoOutput(true);
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(conn.getOutputStream()));
        //commands라는 JSONArray를 담을 JSONObject 생성
        JSONObject commands = new JSONObject();
        commands.put("commands", commandlist);
        //request에 쓰기
        bw.write(commands.toString());
        bw.flush();
        bw.close();
        
        //보내고 결과값 받기
        int responseCode = conn.getResponseCode();
        if (responseCode == 400) {
            System.out.println("400:: 해당 명령을 실행할 수 없음 (실행할 수 없는 상태일 때, 엘리베이터 수와 Command 수가 일치하지 않을 때, 엘리베이터 정원을 초과하여 태울 때)");
        } else if (responseCode == 401) {
            System.out.println("401:: X-Auth-Token Header가 잘못됨");
        } else if (responseCode == 500) {
            System.out.println("500:: 서버 에러, 문의 필요");
        } else { // 성공 후 응답 JSON 데이터받기
            BufferedReader br = new BufferedReader(new InputStreamReader(conn.getInputStream()));
            StringBuilder sb = new StringBuilder();
            String line = "";
            while ((line = br.readLine()) != null) {
                sb.append(line);
            }
            
            responseJson = new JSONObject(sb.toString());
            
        }
    } catch (MalformedURLException e) {
        e.printStackTrace();
    } catch (IOException e) {
        e.printStackTrace();
    } catch (JSONException e) {
        System.out.println("not JSON Format response");
        e.printStackTrace();
    }
    return parser.JSONtoData(responseJson);
}
```

# Get Request
```java
Data onCallsAPI() {
    HttpURLConnection conn = null;
    JSONObject responseJson = null;
    
    try {
        
        URL url = new URL(this.HOST_URL + "/oncalls");
        conn = (HttpURLConnection) url.openConnection();
        conn.setRequestMethod("GET");
        conn.setRequestProperty("X-Auth-Token", this.token);
        conn.setDoOutput(true);
        
        int responseCode = conn.getResponseCode();
        if (responseCode == 400) {
            System.out.println("400:: 해당 명령을 실행할 수 없음 (실행할 수 없는 상태일 때, 엘리베이터 수와 Command 수가 일치하지 않을 때, 엘리베이터 정원을 초과하여 태울 때)");
        } else if (responseCode == 401) {
            System.out.println("401:: X-Auth-Token Header가 잘못됨");
        } else if (responseCode == 500) {
            System.out.println("500:: 서버 에러, 문의 필요");
        } else { // 성공
            BufferedReader br = new BufferedReader(new InputStreamReader(conn.getInputStream()));
            StringBuilder sb = new StringBuilder();
            String line = "";
            while ((line = br.readLine()) != null) {
                sb.append(line);
            }
            
            responseJson = new JSONObject(sb.toString());    
        }
    } catch (MalformedURLException e) {
        e.printStackTrace();
    } catch (IOException e) {
        e.printStackTrace();
    } catch (JSONException e) {
        System.out.println("not JSON Format response");
        e.printStackTrace();
    }
    Data data = parser.JSONtoData(responseJson);
    data.calls = parser.JSONtoCalls(responseJson);
    return data;
}
```

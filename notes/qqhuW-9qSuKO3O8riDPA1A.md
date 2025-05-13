---
tags: edu,
---

# 問題與解法
1. 問題描述:**2025/01/07使用許先生的chatweb打包失敗跳出錯誤訊息**
```bash=
Unable to find image 'chatweb:latest' locally
docker: Error response from daemon: pull access denied for chatweb, repository does not exist or may require 'docker login': denied: requested access to the resource is denied.
See 'docker run --help'.
```
**並且執行 `docker load < chatweb.tar` 正常，執行 `docker images` 也有該映像存在**。
* 解法:經測試看起來像是tag夾帶未知字符導致再linux環境無法辨識，重新tag即可。先執行 `docker load < chatweb.tar`然後再執行`docker images` 取得IMAGE_ID ,最後重新tag `docker tag IMAGE_ID chatweb:latest`,接著執行docker run的相關指令即可。

2.問題描述:**2025/01/10使用許先生的puhui.tar從.net 7 升級成 .net 8 出現健康度問題 回傳500還503有點忘了。對外的口是在docker run時決定的所以GCP端口與防火牆應該沒事。docker logs 查看事有正常啟動。**
* 解法：查看https://learn.microsoft.com/zh-tw/aspnet/core/migration/70-80?view=aspnetcore-9.0&tabs=visual-studio .net 7 升級成 .net 8的技術文件 發現若使用默認阜號升級後將從80改為8080，使用docker logs確認確實啟動的阜號為8080，修改.sh中的docker run內部端口即正常啟動，當日下午開會與許先生敲定puhui.tar專案綁定阜號80，之後部署使用原來的.sh檔即可。
(https://learn.microsoft.com/zh-tw/dotnet/core/compatibility/containers/8.0/aspnet-port)

3. 問題描述:**React專案出現 Company.js:172  Warning: Each child in a list should have a unique "key" prop.**
* 解法：由 map 生成的每個子項目，需要添加 key 屬性的元素，修改 `<tr key={member.id || index}> {/* 確保使用唯一的 key */} `或是 ` <tr key={member.id}> {/* 確保使用唯一的 key */}`

4. 問題描述: **CORS 相關的error 會長這樣 "Cross-Origin Request Blocked: The Same Origin Policy disallows reading the remote resource at $somesite"**
5. 問題描述:**react-bootstrap 的 Accordion.Header對component 尤其是動態的支援是無效的(會無法渲染套件)，其在Header主要以放靜態資訊為主，body應該可以正常渲染套件。**
* 解法:其實可以，支援是有效的，是我的import檔案不同卻取相同名子。

6. 問題描述: **如果docker部屬正常，但是結束後持續重啟**
*解法:很高的機率是配製檔.config/.jason 出現格式錯誤(多或少逗點之類的)，如果有配置檔檢查指令，優先檢查其格式

7. 問題描述:使用java restTemplate 呼叫API失敗
* 解法:
    1.call API 時使用 MappingJackson2HttpMessageConverter() 轉成jason
    2.查看response如果 status是數字代表不是使用HttpStatus，如果是字串，如:success 或 error，才是
    3.API呼叫方法
    ```
    HttpHeaders headers = new HttpHeaders();
    headers.setContentType(MediaType.APPLICATION_JSON);
    HttpEntity<request物件型態> entity = new HttpEntity<>(request物件,headers);
    ResponseEntity<res泛型結構物件<res物件DTO>> response = restTemplate.exchange(
        		url,
        		HttpMethod.POST,
        		entity,
        		new ParameterizedTypeReference<res泛型結構物件<res物件DTO>>() {});
    ```
    如果沒有res泛型結構物件，下面以回傳格式為byte[]舉例
    ```
    ResponseEntity<byte[]> response = restTemplate.exchange(
        		url,
        		HttpMethod.POST,
        		entity,
        		byte[].class);
    ```
    4.要確認是不是在request時格式錯誤或是jason轉譯失敗，可使用下面方法測試
    ```
    ObjectMapper mapper = new ObjectMapper();
        try {
			System.out.println("JSON payload: {}"+ mapper.writeValueAsString(request物件));
		} catch (JsonProcessingException e) {
			e.printStackTrace();
		}
    ```
    5.下面為兩個restTemplate範例
    ```
    @Bean
    public RestTemplate restTemplate(RestTemplateBuilder builder) {
        return builder
            .messageConverters(new MappingJackson2HttpMessageConverter())
            .additionalInterceptors((request, body, execution) -> {
            	System.out.println("Request URI: {}"+ request.getURI());
            	System.out.println("Request Body: {}"+ new String(body, StandardCharsets.UTF_8));
                return execution.execute(request, body);
            })
            .build();
    }
    ```
    ```
    @Bean("restTemplateDebug")
    public RestTemplate restTemplateDebug() {
        // 用 Buffering 包起來，允許 response body 被讀多次（攔截器可用）
        RestTemplate restTemplate = new RestTemplate(
            new BufferingClientHttpRequestFactory(new SimpleClientHttpRequestFactory())
        );

        // 加入攔截器
        restTemplate.getInterceptors().add((request, body, execution) -> {
        	System.out.println("➡️ Request URI: {}"+ request.getURI());
        	System.out.println("➡️ Request Headers: {}"+ request.getHeaders());
        	System.out.println("➡️ Request Body: {}"+ new String(body, StandardCharsets.UTF_8));

            ClientHttpResponse response = execution.execute(request, body);

            // 讀取 response body（一次性）
            byte[] responseBody = response.getBody().readAllBytes();
            String responseBodyStr = new String(responseBody, StandardCharsets.UTF_8);

            System.out.println("⬅️ Response Status: {}"+ response.getStatusCode());
            System.out.println("⬅️ Response Headers: {}"+ response.getHeaders());
            System.out.println("⬅️ Response Body: {}"+ responseBodyStr);

            // 包成新的 response 傳回（回填 body）
            return new ClientHttpResponse() {
                @Override public HttpStatusCode getStatusCode() throws IOException { return response.getStatusCode(); }
                @Override public String getStatusText() throws IOException { return response.getStatusText(); }
                @Override public void close() { response.close(); }
                @Override public InputStream getBody() { return new ByteArrayInputStream(responseBody); }
                @Override public HttpHeaders getHeaders() { return response.getHeaders(); }
            };
        });

        return restTemplate;
    }
    ```
    6.如果有多的restTemplate 可以命名Bean並在呼叫時使用Qualifier
    ```
    @Autowired
	@Qualifier("Bean名稱")
	private RestTemplate restTemplate;
    ```
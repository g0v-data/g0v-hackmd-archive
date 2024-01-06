Paper code:

```java=
private Map<String, Object> prefs = new HashMap<String, Object>();
private Map<String, Object> lang = new HashMap<String, Object>();
driver.manage().window().maximize();
driver.get(input.getUrl());

lang.put("en-US", "zh-TW");
prefs.put("translate", "{'enabled' : true}");
prefs.put("translate_whitelists", lang);
options.setExperimentalOption("prefs", prefs);
options.addArguments("-lang=en-US-zh-TW");

WebDriver driver = new ChromeDriver(options);
```
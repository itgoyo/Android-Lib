# Android-Lib
开发中常用的lib

### xUtils

接口请求数据格式

```
http://111.222.111.56:8080/serviceProxy/edu_plat/servlet/?json={"SERVICE_CODE":"xxx.edu.xxx.service.UserLogin","CONSUMER_ID":"itgoyo","input":"itgoyo@163.com","password":"abc123456"}
```

```
//JsonObject 是com.google.gson的包

HttpUtils httpUtils = new HttpUtils();
       RequestParams requestParams = new RequestParams();
       JsonObject jsonObject = new JsonObject();
       jsonObject.addProperty("SERVICE_CODE","xxx.UploadCrashLog");
       jsonObject.addProperty("CONSUMER_ID",app.getToken());
       jsonObject.addProperty("log_url",logurl);
       jsonObject.addProperty("os_type","1");

       requestParams.addBodyParameter("json",jsonObject.toString());
       httpUtils.send(HttpRequest.HttpMethod.POST, BASE_URL, requestParams, new RequestCallBack<String>() {
           @Override
           public void onSuccess(ResponseInfo<String> responseInfo) {

               logFile.delete();

           }

           @Override
           public void onFailure(HttpException e, String s) {
               //失败重新上传
//                upLoadLog();
           }
       });
```

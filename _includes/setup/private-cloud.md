
## 私有云配置

私有云的配置一般都会给出 api server 和 rtm router server 的地址，因此需要在初始化的时候，单独指定这两个地址即可。


```swift
let app: LeanCloudApp = LeanCloudApp(appId: "uay57kigwe0b6f5n0e1d4z4xhydsml3dor24bzwvzr57wdap", appKey: "kfgz7jjfsk55r5a8a3y4ttd3je1ko11bkibcikonk32oozww")
app.api = "https://api.aaabbbccc.com"
app.rtmRouter = "http://rtmrouter.aaabbbccc.com"
let sdk = RxAVClient.initialize(app: app)
```

```typescript
let app = new LeanCloudApp({
    appId: `uay57kigwe0b6f5n0e1d4z4xhydsml3dor24bzwvzr57wdap`,
    appKey: `kfgz7jjfsk55r5a8a3y4ttd3je1ko11bkibcikonk32oozww`,
    server: {
        api: 'https://api.aaabbbccc.com',
        realtimeRouter: "http://rtmrouter.aaabbbccc.com",
    }
});

RxAVClient.init({
    log: true,
}).add(app);
```
```java
LeanCloudApp app = new LeanCloudApp("315XFAYyIGPbd98vHPCBnLre-9Nh9j0Va","Y04sM6TzhMSBmCMkwfI3FpHc", LeanCloudApp.AVRegion.Public_East_CN);
LeanCloud.addApp(app,"test");
```
## 客户端多应用（多个数据仓库）配置
一般情况下，一个客户端只会访问一个 LeanCloud app，但是有一些特殊的需求，单个客户端配置了访问多个 LeanCloud app 的需求，因此在 RxLeanCloud SDK 都支持了这种设置，而这一点是官方 SDK 没有的。


```swift
let app: LeanCloudApp = LeanCloudApp(appId: "uay57kigwe0b6f5n0e1d4z4xhydsml3dor24bzwvzr57wdap", appKey: "kfgz7jjfsk55r5a8a3y4ttd3je1ko11bkibcikonk32oozww")
let sdk = AVClient.initialize(app: app)

let qcloudApp = LeanCloudApp(appId: "67L3JTrHzTJy688HoJyYbp0J-9Nh9j0Va", appKey: "8MCnFUHUOJcN6l23T09nHojs", region: .Public_East_CN)
// 增加一个 app，
_ = sdk.add(app: qcloudApp)
// 也可以增加一个 replace 参数表示这个 app 是默认的 app 代码：
// sdk.add(app: qcloudApp,replace: true)
// 打开全局的访问日志
_ = sdk.toggleLog(enable: true)
```
```typescript
import { RxAVClient, LeanCloudApp } from 'rx-lean-js-core';

let app = new LeanCloudApp({
    appId: `uay57kigwe0b6f5n0e1d4z4xhydsml3dor24bzwvzr57wdap`,
    appKey: `kfgz7jjfsk55r5a8a3y4ttd3je1ko11bkibcikonk32oozww`,
});
let app2 = new LeanCloudApp({
    appId: `1kz3x4fkhvo0ihk967hxdnlfk4etk754at9ciqspjmwidu1t`,
    appKey: `14t4wqop50t4rnq9e99j2b9cyg51o1232ppzzc1ia2u5e05e`,
    shortname: `dev`
});
let qcloudApp3 = new LeanCloudApp({
    appId: `cfpwdlo41ujzbozw8iazd8ascbpoirt2q01c4adsrlntpvxr`,
    appKey: `lmar9d608v4qi8rvc53zqir106h0j6nnyms7brs9m082lnl7`,
});

export function init() {
    RxAVClient.init({
        log: true,
    }).add(app).add(app2).add(qcloudApp3, true);
}
```

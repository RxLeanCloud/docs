
## <a name="private-cloud"></a>私有云配置 {#private-cloud} 

私有云的配置一般都会给出 api server 和 rtm router server 的地址，因此需要在初始化的时候，单独指定这两个地址即可。


<pre><code class="swift">
let app: AVApp = AVApp(appId: "uay57kigwe0b6f5n0e1d4z4xhydsml3dor24bzwvzr57wdap", appKey: "kfgz7jjfsk55r5a8a3y4ttd3je1ko11bkibcikonk32oozww")
app.api = "https://api.aaabbbccc.com"
app.rtmRouter = "http://rtmrouter.aaabbbccc.com"
let sdk = AVClient.initialize(app: app)
</code></pre>

<pre><code class="ts">
let app = new RxAVApp({
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
</code></pre>
# rx-lean-js-core for TypeScript & JavaScript 安装指南


##  在 angular(2+,4+,5+) 中使用

首先，安装 angular 定制版本的依赖：

```bash
npm install rx-lean-angular --save
``` 

在 `app.module.ts` 放置如下代码：


```typescript
import { LeanCloudApp, RxAVClient } from 'rx-lean-js-core';
import { ngRxLeanCloud } from 'rx-lean-angular';

let app = new LeanCloudApp({
  appId: 'your-app-id',
  appKey: 'your-app-key'
});

RxAVClient.init({
  plugins: {
    websocket: ngRxLeanCloud.ngWebSocketClient,//指定 websocket lib 由浏览器内核提供
    storage: ngRxLeanCloud.ngStorage// 指定本地存储有 localstorage 来提供
  },
  log: true//请求日志，包括 websocket 和 http 
}).add(app);
```


## 在 ionic(2+,3+) 中使用

首先，安装 ionic 定制版本的依赖：

```bash
npm install rx-lean-ionic --save
``` 
在

```typescript
import { LeanCloudApp, RxAVClient } from 'rx-lean-js-core';
import { IonLeanCloud } from 'rx-lean-ionic';

let app = new LeanCloudApp({
  appId: 'your-app-id',
  appKey: 'your-app-key'
});

RxAVClient.init({
  plugins: {
    websocket: IonLeanCloud.ionWebSocketClient,//指定 websocket lib 由浏览器内核提供
    storage: IonLeanCloud.ionStorage// 指定本地存储有 ionic 的默认的 storage 来提供，ionic 还提供了 sqlite 的解决方案
  },
  log: true//请求日志，包括 websocket 和 http 
}).add(app);
```

## 在 nodejs 中使用

```bash
npm install rx-lean-js-core ws --save
``` 

无需再次安装 @type 的描述文件，VSCode/SublimeText/Atom 都会自动检测源码中的注释，智能提示都会显示出来。

为了在 node 中使用实时通信，需要单独声明一个如下的文件，放在你的代码根目录下即可：


```typescript
//import WebSocket from 'ws';
var WebSocket = require('ws');
import { IWebSocketClient } from '../../src/RxLeanCloud';

export class NodeJSWebSocketClient implements IWebSocketClient {
    newInstance(): IWebSocketClient {
        return new NodeJSWebSocketClient();
    }
    onopen: (event: { target: NodeJSWebSocketClient }) => void;
    onerror: (err: Error) => void;
    onclose: (event: { wasClean: boolean; code: number; reason: string; target: NodeJSWebSocketClient }) => void;
    onmessage: (event: { data: any; type: string; target: NodeJSWebSocketClient }) => void;
    readyState: number;
    wsc: any;
    open(url: string, protocols?: string | string[]) {
        this.wsc = new WebSocket(url, protocols);
        this.readyState = 0;

        this.wsc.onmessage = (event: { data: any; type: string; target: any }): void => {
            this.onmessage({ data: event.data, type: event.type, target: this });
        };
        this.wsc.onclose = (event: { wasClean: boolean; code: number; reason: string; target: any }): void => {
            this.readyState = 3;
            this.onclose({ wasClean: event.wasClean, code: event.code, reason: event.reason, target: this });
        };

        this.wsc.onerror = (err: Error): void => {
            this.onerror(err);
        };

        this.wsc.onopen = (event: { target: any }): void => {
            this.readyState = 1;
            this.onopen({ target: this });
        };
    }

    close(code?: number, data?: any): void {
        this.readyState = 2;
        this.wsc.close(code, data);
    }
    send(data: ArrayBuffer | string | Blob) {
        this.wsc.send(data);
    }
}
```

然后初始化：


```typescript
import { RxAVClient, LeanCloudApp } from 'rx-lean-js-core';
import { NodeJSWebSocketClient } from './NodeJSWebSocketClient';
let app = new LeanCloudApp({
    appId: `your-app-id`,
    appKey: `your-app-key`,
});

export function init() {
    RxAVClient.init({
        pluginVersion: 1,
        log: true,
        plugins: {
            websocket: new NodeJSWebSocketClient(),
        }
    }).add(app);
}
```
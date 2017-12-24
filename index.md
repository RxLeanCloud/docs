---
title: SDK | RxLeanCloud
permalink: index.html
layout: docs

---

<div class="container padding-top-40 padding-bottom-50" data-nav-waypoint>
  <div class="copy-block">
      <h3 class="h3 h3--blue margin-bottom-10"></h3>
      <p class="margin-top-10">不同的平台，不同的语言，用 Rx 风格代码封装起来，优雅的链式表达将粘连的业务逻辑逐层解耦，让所有不同终归一统。希望阅读这里的文档能让你有兴趣去维护这里的源码。</p>
  </div>
  <div class="docs-platforms">
    <div class="docs-platform">
          <header class="docs-platform__header">
              <span class="docs-platform__name">ReactiveX</span>
              <img class="icon" src="{{ site.baseurl }}/assets/images/Rx_Logo_S.png"/>
          </header>
          <ul class="docs-platform__links">
              <li class="docs-platform__links"><a href="https://mcxiaoke.gitbooks.io/rxdocs/content/Intro.html">ReactiveX 文档(中文)</a></li>
          </ul>
          <footer class="docs-platform__footer">
              <a href="http://reactivex.io/" class="btn btn--outline">ReactiveX 官方文档</a>
          </footer>
      </div>
      <div class="docs-platform">
          <header class="docs-platform__header">
              <span class="docs-platform__name">安装与初始化</span>
              <svg class="icon"><use xlink:href="{{ site.baseurl }}/assets/symbols.svg#code"></use></svg>
          </header>
          <ul class="docs-platform__links">
              <li class="docs-platform__links"><a href="setup/guide/#setup">安装</a></li>
              <li class="docs-platform__links"><a href="setup/guide/#private-cloud">私有云配置</a></li>
              <li class="docs-platform__links"><a href="setup/guide/#multi-apps">多 App 配置</a></li>
          </ul>
          <footer class="docs-platform__footer">
              <a href="setup/guide" class="btn btn--outline">完整文档</a>
          </footer>
      </div>
      <div class="docs-platform">
          <header class="docs-platform__header">
              <span class="docs-platform__name">RxAVObject</span>
              <img src="https://png.icons8.com/ios/50/000000/stack-filled.png">
          </header>
          <ul class="docs-platform__links">
              <li class="docs-platform__links"><a href="objects/guide/#basic">基础用法</a></li>
              <li class="docs-platform__links"><a href="objects/guide/#type-security">类型安全</a></li>
              <li class="docs-platform__links"><a href="objects/guide/#subclass">子类化</a></li>
          </ul>
          <footer class="docs-platform__footer">
              <a href="objects/guide" class="btn btn--outline">完整文档</a>
          </footer>
      </div>
      <!-- <div class="docs-platform">
          <header class="docs-platform__header">
              <span class="docs-platform__name">RxAVUser</span>
          </header>
          <ul class="docs-platform__links">
              <li class="docs-platform__links"><a href="#">用户管理开发指南</a></li>
          </ul>
          <footer class="docs-platform__footer">
          </footer>
      </div> -->
      <!-- <div class="docs-platform">
          <header class="docs-platform__header">
              <span class="docs-platform__name">RxAVQuery</span>
          </header>
          <ul class="docs-platform__links">
              <li class="docs-platform__links"><a href="#">数据查询开发指南</a></li>
          </ul>
          <footer class="docs-platform__footer">
          </footer>
      </div> -->
      <div class="docs-platform">
          <header class="docs-platform__header">
              <span class="docs-platform__name">RxAVCloudFunction</span>
              <img src="https://png.icons8.com/nolan/96/000000/barcode.png">
          </header>
          <ul class="docs-platform__links">
              <li class="docs-platform__links"><a href="cloud-functions/guide/#use-rpc-another-way">远程调用</a></li>
          </ul>
          <footer class="docs-platform__footer">
              <a href="cloud-functions/guide" class="btn btn--outline">完整文档</a>
          </footer>
      </div>
      <!-- <div class="docs-platform">
          <header class="docs-platform__header">
              <span class="docs-platform__name">RxAVFile</span>
          </header>
          <ul class="docs-platform__links">
              <li class="docs-platform__links"><a href="#">文件存储开发指南</a></li>
          </ul>
          <footer class="docs-platform__footer">
          </footer>
      </div> -->
      <div class="docs-platform">
          <header class="docs-platform__header">
              <span class="docs-platform__name">RxAVSMS</span>
              <img src="https://png.icons8.com/nolan/96/000000/sms.png">
          </header>
          <ul class="docs-platform__links">
              <li class="docs-platform__links"><a href="sms/guide/">短信服务开发指南</a></li>
          </ul>
          <footer class="docs-platform__footer">
              <a href="sms/guide" class="btn btn--outline">完整文档</a>
          </footer>
      </div>
      <!-- <div class="docs-platform">
          <header class="docs-platform__header">
              <span class="docs-platform__name">RxAVACL</span>
          </header>
          <ul class="docs-platform__links">
              <li class="docs-platform__links"><a href="#">权限管理开发指南</a></li>
          </ul>
          <footer class="docs-platform__footer">
          </footer>
      </div> -->
      <!-- <div class="docs-platform">
          <header class="docs-platform__header">
              <span class="docs-platform__name">RxAVIMConversation</span>
          </header>
          <ul class="docs-platform__links">
              <li class="docs-platform__links"><a href="#">聊天对话开发指南</a></li>
          </ul>
          <footer class="docs-platform__footer">
          </footer>
      </div> -->
      <!-- <div class="docs-platform">
          <header class="docs-platform__header">
              <span class="docs-platform__name">RxAVIMMessage</span>
          </header>
          <ul class="docs-platform__links">
              <li class="docs-platform__links"><a href="#">聊天自定义消息开发指南</a></li>
          </ul>
          <footer class="docs-platform__footer">
          </footer>
      </div> -->
      <div class="docs-platform">
          <header class="docs-platform__header">
              <span class="docs-platform__name">SDK 开发技巧</span>
              <img src="https://png.icons8.com/ultraviolet/96/000000/biotech.png">
          </header>
          <ul class="docs-platform__links">
              <li class="docs-platform__links"><a href="sdk/development/#sdk-architecture">基础规范</a></li>
          </ul>
          <footer class="docs-platform__footer">
              <a href="sdk/development" class="btn btn--outline">完整文档</a>
          </footer>
      </div>
  </div><!-- .docs-platforms -->
</div><!-- end .container -->

# Interview Points

系统性的梳理一下面试可能会考察到的基本知识点

## 前端部分

### 样式/CSS/LESS/CSS Module/设计系统 

### html/webview/跨端/浏览器

### JS/TS/ES/内核

### 设计模式

### 前端框架 San/Vue/React

### 编译工具 Webpack/Vite/Rollup

### 周边常用库
Terser
babel
postcss

### e2e测试/单测

### 模块化


## 网络部分

### 协议 http/https/tcp/udp/socket

### cookie/session/token

### 缓存
强缓存/协商缓存/service worker缓存/CDN缓存/DNS/CDN/BOS

强缓存：浏览器端通过header中的信息判端当前资源在有效缓存时间内，无需再次发请求的缓存，一般包含：
- expires，值为一个具体的GMT时间表示资源的绝对过期时间，在此之前无需请求可以直接使用缓存。缺点是当服务器端时间与浏览器端时间差异较大时会导致缓存混乱。源自http 1.0的规范
- cache-control，来源自http 1.1的规范具有以下有效值：
    - max-age，值是一个相对时间，单位是秒，表示当从此刻起，再过多长时间资源缓存过期。在此之前无需请求直接使用缓存。
    - no-store，禁止缓存，每次访问资源都重新请求全新的当前资源
    - public，公共缓存，表示该资源可以被网络请求的整个链路中，所有其他方比如cdn等缓存
    - private，私有缓存，表示该资源只可以被浏览器缓存，不可以被cdn之类的其他房缓存
    - no-cache，表示不直接使用缓存，带上其他协商缓存使用的header信息再次发送请求确认

协商缓存：浏览器发送请求，其header中包含如 etag/if-non-match 或 lastModified/if-modified-since信息，服务端通过比较：
- etag是否一致、if-non-match
- lastModified是否仍然有效
- if-modified-since

## Nodejs

### koa、express

### 文件系统/mvc

## 服务器/部署

### nginx/https/openssl/负责均衡

### 服务器基本操作/运维

## 计算机知识

### 多线程/多进程

### 函数式编程/oop

### 

## [算法]({{site.url}}/interview/program)


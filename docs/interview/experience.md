1. 实现一个发布订阅 class EventListener，具备emit、on以及返回一个取消订阅的函数
```
const events = new EventListener();

const offSum = event.on('receive', (a, b) => {
  console.log('sum', a + b)
});

const offDiff = event.on('receive', (a, b) => {
  console.log('diff', a - b)
});

events.emit('receive', 1, 3);

offSum();

events.emit('receive', 6, 2);

// 4
// -1
// 8

```

2. 讲一下css盒模型
3. 讲一下跨域，有哪些跨域解决办法？cors的响应头里，如果要设置允许携带cookie，前后端分别需要做什么操作
5. 自我介绍一下
6. 讲一些移动端常见的适配有哪些？
7. 移动端1px效果如何实现，有哪些问题？是什么原因造成的？怎么解决？rem方案是怎么运作的？屏幕分辨率是如何影响的？
8. 常见的安全问题有哪些？讲一下xss？如何在业务无任何的感知下防止xss？讲一下csp？知道csrf吗讲一下？
9. 移动端端能力是如何实现的？scheme和端能力注入？na与h5之间在两种模式下的通信详细细节？两种方式有什么区别？两者为何需要搭配使用？
10. 按照碰到了什么问题，怎么解决的，获得了什么样的成长的方式讲一下最近比较复杂的项目？
11. 为什么没用开源库？调研了哪些开源库？fabric.js
12. 怎么做canvas的性能优化的？分别都用到了哪些手段？







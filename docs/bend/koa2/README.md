# KOA2 资源及参考资料

## Koa v2.7.0 中文文档 [阅读](https://www.bookstack.cn/read/koa-docs-Zh-CN-v2.7.0/Readme.md)

## 把koa2扩展成一个完备服务端api开发框架 [阅读](https://ethluz.github.io/blog/use-koa2-for-restfulapi-server/)

基于 koa2 项目代码的分层和扩展

## koa2 使用 koa-body 代替 koa-bodyparser 和 koa-multer [阅读](http://www.ptbird.cn/koa-body.html)

注意评论中对微信支付的处理
```
但是不支持xml格式的解析对吗？我正准备使用tenpay来做微信支付，商户号还没拿到，看到koa-body的文档说是不支持。。
不行的话，只有回退到bodyparser+multer了。。


tangchiNovember 25th, 2018 at 10:22 pm回复
tenpay不是提供了一个koa的中间件吗，集成了接受微信支付通知的解析呀，而且所有主动请求微信的返回数据都是自动解析的。


ThyiadDecember 28th, 2018 at 06:07 pm回复
那个前提是要你能把参数当成text处理，放在body里传递过去，默认应该会是空的，我最后手动改了一下代码，让koa-body把xml格式的请求当成text处理，这样就没问题了
```
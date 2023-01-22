```java
  default <A> A getAttribute(String name) {
	return (A) getAttributes().get(name);
  }
  
  String s = this.getAttribute("key");
  
  Object obj = this.getAttribute("key");
  
  Long num = this.getAttribute("key");
```

想得到什么类型就得到什么类型 ，不需要进行类型转换

#### -

spring security 会过滤掉options请求 

### HTTP请求方法

GET

POST

DELETE

PUT: 不打补丁 直接更换

PATCH: 打补丁

HEAD：没听说过

OPTIONS：springsecurity里面使用到了 过滤掉这种请求

CONNECT：没听说过

TRACE：没用过 看MDN文档上讲可以追踪链路 感觉挺牛逼的


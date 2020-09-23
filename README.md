## 微服务架构实战04 服务网关zuul
用于提供微服务路由和实现网关功能，运行于8040端口
### 配置文件如下
```
spring:
  application:
    name: microservice-gateway-zuul
eureka:
  client:
    service-url:
      defaultZone: http://eureka1:8761/eureka/ ,http://eureka2:8762/eureka/
  instance:
    prefer-ip-address: true
```
### 连接配置项
```
hystrix:
  command:
    default:
      execution:
        isolation:
          thread:
            timeoutInMilliseconds: 60000         #用于解决上传大文件时超时问题
        timeout:
          enabled: false
ribbon:
  ConnectTimeout: 3000
  ReadTimeout: 60000                             #设置超时时间，用于解决上传大文件超时问题
```
实战05中会实现使用zuul上传大文件，此配置项用于解决上传大文件时超时的问题  

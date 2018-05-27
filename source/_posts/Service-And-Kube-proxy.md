---
title: Service And Kube-proxy
date: 2018-05-27 23:07:15
tags: service
---
## Introduction
本文探究kubernetes架构中，服务发现的具体工作原理，涉及到service定义、服务发现与coredns，kube-proxy工作原理等。

## Service
kubernetes架构中，Service是对一组提供相同功能pod的抽象。Service通过标签选取服务后端。Service有四种类型：
  * ClusterIP: 默认类型，为服务自动分配一个虚拟ip，该ip仅集群内部可见
  * NodePort: 在ClusterIP的基础上，为Service在每台机器上绑定一个端口，外部请求可以通过NodeIP:NodePort访问服务
  * LoadBalancer: 在NodePort的基础上，通过云服务厂商创建一个外部的负载均衡器
  * ExternalName: 把服务通过CNAME的方式转发到制定的域名。
  <br/>

### 创建Service
  * 一般，在创建服务时，需要指定selector，该selector会和特定label关联，通过和pod的label对比，选择相应的pod作为该服务的endpoints；
  * 如果不指定selector，可以自己定义endpoint，需要创建一个和Service同名的Endpoints资源，在endpoint中配置指定的ip和端口；
  * 还有一种情况不需要指定selectors，就是通过DNS CNAME方式把服务转发到指定的域名；
  <br/>

### headless 服务

## Service Discovery

## DNS in kubernetes
## Kube-proxy
## CoreDNS

## Conclusion

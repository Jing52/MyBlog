---
title: 学习笔记-EDAS介绍
date: 2018-10-27 21:22:44
tags: 
	- EDAS
	- Java
	- 分布式
categories: 分布式
---
### HSF：
HSF为EDAS应用开发提供了一套分布式服务框架的解决方案，从应用层面提供统一的服务发布/调用支持，让开发者很容易的开发分布式的应用，不用考虑分布领域中的各种技术细节（远程通讯、性能消耗、调用的透明化、同步/异步调用方式的实现等等问题）

<!-- more -->


### 容器：
　　Ali-tomcat:

　　　　与Apache Tomcat完全兼容的WebApp容器

　　　　引入Pandora容器的类隔离机制解决EDAS依赖包与应用包冲突的问题

　　Pandora: 

　　　　能够隔离EADS与应用之间的jar包依赖，保证两者互不受影响

### 配置中心：

　　Address-Server：地址中心，寻址Config-Server和Diamond-Server

　　Diamond-Server：动态配置变更推送

　　优势特性：

*   高效性

　　　　　　基于推拉结合的方式，实现配置动态变更实时推送

*   可靠性

　　　　　　通过客户端、服务端多级容灾，实现系统的高可用

*   易扩展

　　　　　　配置数据在集群单节点上全量分布，实现节点无状态

#### 　Config-Server:　　
　　　用于HSF服务数据的发布订阅　　　

　　　优势特性：

##### 　　  1、无Master

　　　　　　ConfigServer基于无Master架构不存在单点问题

##### 　　　2、自动聚合

　　　　　　ConfigServer支持数据的自动聚合

##### 　　　3、实时

　　　　　　服务端在订阅关系变化时，会主动推送配置数据到客户端


Lattice
Copyright 2013-2014 ticeng.com. All rights reserved.
Support: http://www.ticeng.com
License: http://www.ticeng.com/license
Author: hongquanli<hongquanli@qq.com>
Revision: 1.0
Date: 2013-12-31

商品管理
商品管理
商品分类
商品参数
商品属性
规格管理
品牌管理
到货通知

订单管理
订单管理
收款管理
退款管理
发货管理
退货管理
发货点管理
快递单模板

会员管理
会员管理
会员等级
会员注册项
评论管理
咨询管理

内容管理
导航管理
文章管理
文章分类
标签管理
友情链接
广告位
广告管理
模板管理
缓存管理
静态化管理
索引管理

营销管理
促销管理
优惠券管理
SEO设置
Sitemap管理

统计报表
访问统计
统计设置
销售统计
销售排行
消费排行
预存款

系统设置
系统设置
地区管理
支付方式
配送方式
物流公司
支付插件
存储插件
管理员
角色管理
发送消息
消息列表
草稿箱
日志管理


attachments 附件
articles 文章静态化目录
products 产品静态化目录
resources 网站资源文件
topics 主题活动
default 默认页
favicon.ico 网站图标
sitemap.xml 站点地图
robots.txt 搜索引擎收录
changelog.txt 更新日志
readme.txt 网站自述
license.html 许可协义
META-INF
WEB-INF




使用Request里的Attribute值最简单的方法就是直接${AttributeName}或者安全一点：${AttributeName!"default Value"}

1.取Application范围的对象
xml 代码
   1. <#if Application.myApplicationAttribute?exists>  
   2.      ${Application.myApplicationAttribute}   
   3. </#if>  
或者 ：  ${Application.myApplicationAttribute!"default value"}   

2.取session范围的对象
xml 代码
   1. <#if Session.mySessionAttribute?exists>  
   2.      ${Session.mySessionAttribute}   
   3. </#if>  
或者 ：   ${Session.mySessionAttribute!"default value"}   

3.取request范围的对象
xml 代码
   1. <#if Request.myRequestAttribute?exists>  
   2.       ${Request.myRequestAttribute}   
   3. </#if>  
或者 ：   ${Request.myRequestAttribute!"default value"}   

4.取request parameter范围的对象
xml 代码
   1. <#if Parameters.myParameter?exists>  
   2.      ${Parameters.myParameter}   
   3. </#if>  
或者 ： ${Parameters.myParameter!"default value"}   

5.取context parameter范围的对象
xml 代码
   1. ${stack.findValue('#myContextParam')}  
 
 request 对象直接对应 HttpServletResponse
例如 获取 当前网页地址:  ${request.requestURL}
客户端IP地址:  ${request.getRemoteAddr()} 或者  ${request.remoteAddr}
提交方式:  ${request.method}
等等
 
 
 Request： 用于获取Request对象中的attribute对象。
例如：${Request["myRequestAttribute"]} 这样是直接在页面输出属性值。相当于request.getAtrribute("myRequestAttribute");
         如果要对这个值进行判断就必须使用如下格式：<#if Request["myRequestAttribute"]="edit">
或者 ： ${Request["myRequestAttribute"]!"default value"}   
 
Session：用于获取Session 对象中的attribute对象。
用法参照Request的用法。
 
Application：用于获取 Application(ServletContext)对象中的attribute对象。
用法参照Request的用法。
 
RequestParameters：用 于获取Request对象的parameter参数（浏览器端发送的请求数据）
例如：${RequestParameters["myRequestAttribute"]}等同于 request.getParameter("myRequestAttribute");
 
Parameters：属性获取，依次从 RequestParameters、Request、Session、Application对象中获取对应属性\参数，一旦获取，则不再向下查找。
例如：${Parameters["myRequestAttribute"]}
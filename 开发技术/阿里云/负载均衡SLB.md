---
title: 阿里云 · 负载均衡（SLB）
description: 阿里云ACP考试范围
published: true
date: 2023-03-13T05:57:51.736Z
tags: 阿里云, 负载均衡
editor: markdown
dateCreated: 2023-03-13T05:34:55.568Z
---

1. 阿里云负载均衡SLB只能是阿里云的ECS服务器
2. 负载均衡（SLB）系统会用10或100开头的IP地址频繁访问后端ECS实例，是在进行健康检查
3. 健康检查检查出云服务器ECS实例ecs_inst 1处于不健康状态，则会将ecs_inst 1移出伸缩组且会重新创建一个新的ECS实例来代替ecs_inst 1， 同时将其加入负载均衡SLB后端并给其分发请求
4. 公网SLB与ECS之前的流量费用不仅有实例收费,流量计费,当有按带宽收费等
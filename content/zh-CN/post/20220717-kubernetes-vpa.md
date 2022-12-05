+++
author = "abstractmj"
title = "Introduction to Kubernetes Vertical Pod Autoscaler"
date = "2022-07-17"
description = "尝试分析Kubernetes VPA原理及使用场景"
tags = [
    "kubernetes",
    "vpa",
    "autoscaler",
]
+++

## 导语

某个有状态（只有master工作）的服务要想使用HPA，需要比较大的改造成本，最后发现还是VPA比较适合这个服务。虽然日常工作中HPA，VPA等词语说的很溜，但是真正要在生产环境中应用自动扩缩绒，必须对其工作原理，适用场景，参数配置有一定的了解，否则极容易给系统带来不稳定因素。

<!--more-->

## VPA简介

VPA可以根据实际资源利用率，自动调节Pod的request和limit资源，同时在自动调节过程中，也能够保持用户设置的初始limits和requests资源的比例；

## 1 安装

### 1.1 安装metric server

根据腾讯云文档安装metric server,[在TKE上安装metrics-server](https://cloud.tencent.com/document/product/457/50074)

通过kubectl top pod或者kubectl top node能够获取到metrics数据即可

### 1.2 使用helm charts安装vertical pod autoscaleer

使用[https://artifacthub.io/packages/helm/cowboysysop/vertical-pod-autoscaler/1.4.2](https://artifacthub.io/packages/helm/cowboysysop/vertical-pod-autoscaler/1.4.2) charts包安装vertical pod autoscaler

## 参考文献

# Week8 工作日志

本周在小组会上做了research报告，然后实现了一个pbft的4节点共识简单版本

## 报告

报告主要是对我的上一个课题做了个总结，在制作ppt的过程中我又一次回顾了整个科研的过程，这对我既是一种肯定也是一种激励，希望在以后的科研道路上我能有更深入的思考和更严谨的结果。

## PBFT simple implementation 

我通过localhost的4个不同端口初始化四个节点来进行简单共识，人工模拟client，通过curl发送一个post请求，里面包含一个json，包括clientid，时间戳，请求类型，完成一次reply。


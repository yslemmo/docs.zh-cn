---
title: "invalidIUnknown MDA | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MDAs (managed debugging assistants), invalid IUnknown pointer"
  - "InvalidIUnknown MDA"
  - "invalid IUnknown pointers"
  - "IUnknown pointers"
  - "managed debugging assistants (MDAs), invalid IUnknown pointer"
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# invalidIUnknown MDA
当将无效的`IUnknown` 指针从本地代码传递到托管代码时，`invalidIUnknown`托管调试助手 \(MDA\) 将被激活。  当查询 `IUnknown` 接口时，`IUnknown` 将无法成功返回。  
  
## 症状  
 参数封送处理期间，封送处理某个 COM 接口指针时，发生意外错误。  
  
## 原因  
 将 COM 接口上一个不正确的 `QueryInterface` 实现传递给了 CLR。  
  
## 解决方法  
 更正 `QueryInterface` 实现。  
  
## 对运行时的影响  
 此 MDA 对 CLR 无任何影响。  
  
## 输出  
 错误说明。  
  
## 配置  
  
```  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## 请参阅  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [互操作封送处理](../../../docs/framework/interop/interop-marshaling.md)
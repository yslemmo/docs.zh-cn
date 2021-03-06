---
title: ".NET Framework 正则表达式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET Framework 正则表达式"
  - ".NET Framework 正则表达式, 关于"
  - "字符 [.NET Framework], 正则表达式"
  - "分析带有正则表达式的文本"
  - "分析带有正则表达式的文本, 概述"
  - "正则表达式的模式匹配"
  - "正则表达式的模式匹配, 关于模式匹配"
  - "正则表达式 [.NET Framework]"
  - "正则表达式 [.NET Framework], 关于正则表达式"
  - "用正则表达式搜索"
  - "用正则表达式搜索, 关于正则表达式"
  - "字符串 [.NET Framework], 正则表达式"
  - "子字符串"
ms.assetid: 521b3f6d-f869-42e1-93e5-158c54a6895d
caps.latest.revision: 24
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 24
---
# .NET Framework 正则表达式
正则表达式提供了功能强大、灵活而又高效的方法来处理文本。  正则表达式的全面模式匹配表示法使你可以快速分析大量文本以找到特定的字符模式；验证文本以确保它匹配预定义的模式（如电子邮件地址）；提取、编辑、替换或删除文本子字符串；将提取的字符串添加到集合以生成报告。  对于处理字符串或分析大文本块的许多应用程序而言，正则表达式是不可缺少的工具。  
  
## 正则表达式的工作方式  
 使用正则表达式处理文本的中心构件是正则表达式引擎，该引擎在 .NET Framework 中由 <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> 对象表示。  使用正则表达式处理文本至少要求向该正则表达式引擎提供以下两方面的信息：  
  
-   要在文本中标识的正则表达式模式。  
  
     在 .NET Framework 中，正则表达式模式用特殊的语法或语言定义，该语法或语言与 Perl 5 正则表达式兼容，并添加了一些其他功能，例如从右到左匹配。  有关详细信息，请参阅[正则表达式语言 \- 快速参考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)。  
  
-   要为正则表达式模式分析的文本。  
  
 <xref:System.Text.RegularExpressions.Regex> 类的方法使你可以执行以下操作：  
  
-   通过调用 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=fullName> 方法确定输入文本中是否具有正则表达式模式。  有关使用 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> 方法验证文本的示例，请参阅[如何：确认字符串是有效的电子邮件格式](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md)。  
  
-   通过调用 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=fullName> 或 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=fullName> 方法检索匹配正则表达式模式的一个或所有文本匹配项。  第一个方法返回提供有关匹配文本的信息的 <xref:System.Text.RegularExpressions.Match?displayProperty=fullName> 对象。  第二个方法返回 <xref:System.Text.RegularExpressions.MatchCollection> 对象，该对象对于在分析的文本中找到的每个匹配项包含一个 <xref:System.Text.RegularExpressions.Match?displayProperty=fullName> 对象。  
  
-   通过调用 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=fullName> 方法替换匹配正则表达式模式的文本。  有关使用 <xref:System.Text.RegularExpressions.Regex.Replace%2A> 方法更改日期格式和删除字符串中的无效字符的示例，请参阅[如何：从字符串中剥离无效字符](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md)和[示例：更改日期格式](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md)。  
  
 有关正则表达式对象模型的概述，请参阅[正则表达式对象模型](../../../docs/standard/base-types/the-regular-expression-object-model.md)。  
  
 有关正则表达式语言的详细信息，请参阅[正则表达式语言 \- 快速参考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)，或下载和打印以下小册子中的一个:  
  
 [Word \(.docx\) 格式的快速参考](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)   
 [PDF \(.pdf\) 格式的快速参考](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## 正则表达式示例  
 <xref:System.String> 类包括许多字符串搜索和替换方法，当你要在较大字符串中定位文本字符串时，可以使用这些方法。  当你希望在较大字符串中定位若干子字符串之一时，或者当你希望在字符串中标识模式时，正则表达式最有用，如以下示例所示。  
  
### 示例 1：替换子字符串  
 假设一个邮件列表包含一些姓名，这些姓名有时包括称谓（Mr.、Mrs.、Miss 或 Ms.）以及姓氏和名字。  如果你从列表中生成信封标签时不希望包括称谓，则可以使用正则表达式移除称谓，如以下示例所示。  
  
 [!code-csharp[Conceptual.Regex#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 正则表达式模式 `(Mr\.? |Mrs\.? |Miss |Ms\.? )` 可匹配任何“Mr”、“Mr.”  、“Mrs”、“Mrs.”  、“Miss”、“Ms”或“Ms.”  .  对 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=fullName> 方法的调用会将匹配的字符串替换为 <xref:System.String.Empty?displayProperty=fullName>；换句话说，它从原始字符串中将其移除。  
  
### 示例 2：标识重复的单词  
 意外地重复单词是编写器常犯的错误。  可以使用正则表达式标识重复的单词，如以下示例所示。  
  
 [!code-csharp[Conceptual.Regex#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 正则表达式模式 `\b(\w+?)\s\1\b` 的解释如下:  
  
|||  
|-|-|  
|`\b`|在单词边界处开始。|  
|\(\\w\+?\)|匹配一个或多个单词字符，但字符要尽可能的少。  它们一起构成可称为 `\1` 的组。|  
|`\s`|与空白字符匹配。|  
|`\1`|与等于名为 `\1` 的组的子字符串匹配。|  
|`\b`|与字边界匹配。|  
  
 通过将正则表达式选项设置为 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=fullName>，调用 <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName> 方法。  因此，匹配操作不区分大小写，此示例将子字符串“This this”标识为重复。  
  
 请注意，输入字符串包括子字符串“this?  This”。  但是，由于插入标点符号，该子字符串不被标识为重复。  
  
### 示例 3：动态生成区分区域性的正则表达式  
 下面的示例演示如何将正则表达式的功能与 .NET Framework 的全球化功能所提供的灵活性结合在一起。  它使用 <xref:System.Globalization.NumberFormatInfo> 对象确定系统的当前区域性设置中货币值的格式。  然后使用该信息动态构造从文本提取货币值的正则表达式。  对于每个匹配，它提取仅包含数字字符串的子组，将其转换为 <xref:System.Decimal> 值，然后计算累计值。  
  
 [!code-csharp[Conceptual.Regex#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 在当前区域性设置为“英语 \- 美国”\(en\-US\) 的计算机上，该示例动态生成正则表达式 `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`。  此正则表达式模式可以按以下方式解释：  
  
|||  
|-|-|  
|`\$`|在输入字符串中查找美元符号 \($\) 的一个匹配项。  正则表达式模式字符串包含一个反斜杠来指示按字面解释美元符号而非将其作为正则表达式定位点。  （单独的 $ 符号将指示正则表达式引擎应尝试在字符串的末尾开始匹配。） 为了确保当前区域性设置的货币符号不被错误解释为正则表达式符号，该示例调用 <xref:System.Text.RegularExpressions.Regex.Escape%2A> 方法使该字符转义。|  
|`\s*`|查找空白字符的零个或多个匹配项。|  
|`[-+]?`|查找正号或负号的零个或一个匹配项。|  
|`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|括起此表达式的外部括号将表达式定义为捕获组或子表达式。  如果找到匹配项，则有关匹配字符串的此部分的信息可以从第二个 <xref:System.Text.RegularExpressions.Group> 对象中检索（该对象位于 <xref:System.Text.RegularExpressions.GroupCollection> 属性所返回的 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=fullName> 对象中）。  （集合中的第一个元素表示整个匹配。）|  
|`[0-9]{0,3}`|查找十进制数字 0 到 9 的零到三个匹配项。|  
|`(,[0-9]{3})*`|查找后跟三个十进制数字的组分隔符的零个或多个匹配项。|  
|`\.`|查找小数分隔符的一个匹配项。|  
|`[0-9]+`|查找一个或多个十进制数字。|  
|`(\.[0-9]+)?`|查找后跟至少一个十进制数字的小数分隔符的零个或一个匹配项。|  
  
 如果在输入字符串中找到所有这些子模式，则匹配成功，并将包含有关匹配的信息的 <xref:System.Text.RegularExpressions.Match> 对象添加到 <xref:System.Text.RegularExpressions.MatchCollection> 对象。  
  
## 相关主题  
  
|标题|说明|  
|--------|--------|  
|[正则表达式语言 \- 快速参考](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|提供有关可用来定义正则表达式的字符集、运算符和构造的信息。|  
|[正则表达式对象模型](../../../docs/standard/base-types/the-regular-expression-object-model.md)|提供演示如何使用正则表达式类的信息和代码示例。|  
|[正则表达式行为的详细信息](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|提供有关 .NET Framework 正则表达式的功能和行为的信息。|  
|[正则表达式示例](../../../docs/standard/base-types/regular-expression-examples.md)|提供演示正则表达式的典型用法的代码示例。|  
  
## 引用  
 <xref:System.Text.RegularExpressions?displayProperty=fullName>   
 <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName>  
 [正则表达式 \- 快速参考（以 Word 格式下载）](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [正则表达式 \- 快速参考（以 PDF 格式下载）](http://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
---
ms.openlocfilehash: d33d75b4c2d9bc18844f66f1fcca1e2efc6f1eee
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497867"
---
### <a name="xslt-style-sheet-exception-message-changed"></a>Le message de l’exception relative aux feuilles de style XSLT a été changé

#### <a name="details"></a>Détails

Dans le .NET Framework 4,5, le texte du message d’erreur lorsqu’un fichier XSLT est trop complexe est &quot; la feuille de style est trop complexe. &quot; Dans les versions précédentes, le message d’erreur était &quot; erreur de compilation XSLT. &quot; Le code d’application qui dépend du texte du message d’erreur ne fonctionnera plus. Toutefois, comme les types d’exception restent les mêmes, cette modification ne devrait pas avoir d’impact réel.

#### <a name="suggestion"></a>Suggestion

Mettez à jour le code d’application qui dépend du message d’exception de cette condition d’erreur pour qu’il attende le nouveau message ou (encore mieux) mettez à jour le code pour qu’il dépende uniquement du type d’exception (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>), qui n’a pas changé.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime|

#### <a name="affected-apis"></a>API affectées

- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>
- <xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.String)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`
- `M:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)`

-->

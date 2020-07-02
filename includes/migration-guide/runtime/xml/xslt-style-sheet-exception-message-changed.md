---
ms.openlocfilehash: 5c27e8acdf30533036546ba4cca9e06877bde362
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620524"
---
### <a name="xslt-style-sheet-exception-message-changed"></a>Le message de l’exception relative aux feuilles de style XSLT a été changé

#### <a name="details"></a>Détails

Dans le .NET Framework 4,5, le texte du message d’erreur lorsqu’un fichier XSLT est trop complexe est &quot; la feuille de style est trop complexe. &quot; Dans les versions précédentes, le message d’erreur était &quot; erreur de compilation XSLT. &quot; Le code d’application qui dépend du texte du message d’erreur ne fonctionnera plus. Toutefois, comme les types d’exception restent les mêmes, cette modification ne devrait pas avoir d’impact réel.

#### <a name="suggestion"></a>Suggestion

Mettez à jour le code d’application qui dépend du message d’exception de cette condition d’erreur pour qu’il attende le nouveau message ou (encore mieux) mettez à jour le code pour qu’il dépende uniquement du type d’exception (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>), qui n’a pas changé.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4,5|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|

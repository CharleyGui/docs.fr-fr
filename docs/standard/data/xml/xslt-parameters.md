---
title: Paramètres XSLT
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: fe60aaa0-ae43-4b1c-9be1-426af66ba757
ms.openlocfilehash: cc412042e69a43bbecec9dbe68618e2d307ca793
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709697"
---
# <a name="xslt-parameters"></a>Paramètres XSLT
Des paramètres XSLT sont ajoutés à l'objet <xref:System.Xml.Xsl.XsltArgumentList> en utilisant la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>. Un nom qualifié et un URI d'espace de noms sont associés à l'objet de paramètre à ce stade.  
  
### <a name="to-use-an-xslt-parameter"></a>Pour utiliser un paramètre XSLT  
  
1. Créez un objet <xref:System.Xml.Xsl.XsltArgumentList> et ajoutez le paramètre à l'aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A>.  
  
2. Appelez le paramètre à partir de la feuille de style.  
  
3. Transmettez l'objet <xref:System.Xml.Xsl.XsltArgumentList> à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="parameter-types"></a>Types de paramètres  
 L'objet de paramètre doit correspondre à un type W3C. Le tableau suivant illustre les types W3C correspondants, les classes Microsoft .NET Framework équivalentes (type) et précise si le type W3C est un type XPath ou XSLT.  
  
|Type W3C|Équivalent de classe .NET (type)|Type XPath ou XSLT|  
|--------------|------------------------------------|------------------------|  
|`String`|<xref:System.String?displayProperty=nameWithType>|XPath|  
|`Boolean`|<xref:System.Boolean?displayProperty=nameWithType>|XPath|  
|`Number`|<xref:System.Double?displayProperty=nameWithType>|XPath|  
|`Result Tree Fragment`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XSLT|  
|`Node*`|<xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>|XPath|  
|`Node Set`|<xref:System.Xml.XPath.XPathNodeIterator><br /><br /> **XPathNavigator []**|XPath|  
  
 *Cela équivaut à une collection de nœuds contenant un seul nœud.  
  
 Si l'objet de paramètre n'est pas l'une des classes ci-dessus, il est converti selon les règles suivantes. Les types CLR numériques sont convertis en objet <xref:System.Double>. Le type <xref:System.DateTime> est converti en <xref:System.String>. Les types <xref:System.Xml.XPath.IXPathNavigable> sont convertis en <xref:System.Xml.XPath.XPathNavigator>. **XPathNavigator[]** est converti en objet <xref:System.Xml.XPath.XPathNodeIterator>.  
  
 Tous les autres types provoquent une erreur.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddParam%2A> pour créer un paramètre destiné à contenir une date de remise calculée. La date de la remise correspond à 20 jours à partir de la date de la commande.  
  
 [!code-csharp[XSLT_Param#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XSLT_Param/CS/xsltparam.cs#1)]
 [!code-vb[XSLT_Param#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XSLT_Param/VB/xsltparam.vb#1)]  
  
### <a name="input"></a>Entrée  
  
##### <a name="orderxml"></a>order.xml  
 [!code-xml[XSLT_Param#2](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/order.xml#2)]  
  
##### <a name="discountxsl"></a>discount.xsl  
 [!code-xml[XSLT_Param#3](../../../../samples/snippets/xml/VS_Snippets_Data/XSLT_Param/XML/discount.xsl#3)]  
  
### <a name="output"></a>Output  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<order>  
  <total>36.9</total>  
     15% discount if paid by: 2/4/2004 12:00:00 AM  
</order>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Transformations XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)

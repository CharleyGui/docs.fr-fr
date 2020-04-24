---
title: Mise en correspondance de nœuds avec XPathNavigator
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: f0988c3a112fefc351175de02c790dc25fe6e94a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710685"
---
# <a name="matching-nodes-using-xpathnavigator"></a>Mise en correspondance de nœuds avec XPathNavigator
La classe <xref:System.Xml.XPath.XPathNavigator> fournit la méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> permettant de déterminer si un nœud correspond à une expression XPath. La méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> prend une expression XPath comme entrée et retourne un objet <xref:System.Boolean> indiquant si le nœud actuel correspond à l’expression XPath donnée ou à l’objet <xref:System.Xml.XPath.XPathExpression> compilé donné.  
  
## <a name="matching-nodes"></a>Mise en correspondance de nœuds  
 La méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> retourne `true` si le nœud actuel correspond à l’expression XPath spécifiée. Par exemple, dans le code suivant, la méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> retournera `true` si le nœud actuel est l'élément `b` et si l'élément `b` a un attribut `c`.  
  
> [!NOTE]
> La méthode <xref:System.Xml.XPath.XPathNavigator.Matches%2A> ne modifie pas l'état de l'objet <xref:System.Xml.XPath.XPathNavigator>.  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [Traitement des données XML à l'aide du modèle de données XPath](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [Sélection de données XML à l'aide de XPathNavigator](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [Évaluation d’expressions XPath à l’aide de XPathNavigator](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [Types de nœuds reconnus avec les requêtes XPath](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Requêtes et espaces de noms XPath](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Expressions XPath compilées](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)

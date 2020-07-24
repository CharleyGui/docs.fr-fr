---
title: Comparaison de XPath et LINQ to XML
description: En savoir plus sur les similitudes et les différences de fonctionnalités entre XPath et LINQ to XML en C#. Vous pouvez utiliser les deux pour interroger une arborescence XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e2f34903b20a53dea6e5ff4858d4fadaebd9c37a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104012"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>Comparaison de XPath et LINQ to XML
XPath et LINQ to XML offrent certaines fonctionnalités similaires. Tous deux peuvent être utilisés pour interroger une arborescence XML et retourner des résultats tels qu'une collection d'élément, une collection d'attributs, une collection de nœuds ou la valeur d'un élément ou attribut. Il existe toutefois certaines différences.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>Différences entre XPath et LINQ to XML  
 XPath n'autorise pas la projection de nouveaux types. Il peut uniquement retourner des collections de nœuds de l’arborescence, tandis que LINQ to XML peut exécuter une requête et projeter un graphique d’objet ou une arborescence XML dans une nouvelle forme. Les requêtes LINQ to XML englobent beaucoup plus de fonctionnalités et sont beaucoup plus puissantes que les expressions XPath.  
  
 Les expressions XPath existent de manière isolée dans une chaîne. Le compilateur C# ne peut pas contribuer à l’analyse de l’expression XPath au moment de la compilation. En revanche, c’est lui qui analyse et compile les requêtes LINQ to XML. Le compilateur est capable d'intercepter de nombreuses erreurs de requête.  
  
 Les résultats XPath ne sont pas fortement typés. Dans certaines circonstances, le résultat de l'évaluation d'une expression XPath est un objet et il incombe au développeur de déterminer le type correct et de convertir le résultat si nécessaire. En revanche, les projections à partir d’une requête LINQ to XML sont fortement typées.  
  
## <a name="result-ordering"></a>Ordonnancement des résultats  
 La Recommandation XPath 1.0 stipule qu'une collection qui est le résultat de l'évaluation d'une expression XPath n'est pas ordonnée.  
  
 Toutefois, lors de l’itération d’une collection retournée par une méthode d’axe XPath LINQ to XML, les nœuds de la collection sont retournés dans l’ordre du document. Cela est valable même lors de l'accès à des axes XPath où les prédicats sont exprimés dans l'ordre inverse du document, par exemple `preceding` et `preceding-sibling`.  
  
 Par contraste, la plupart des axes LINQ to XML retournent les collections dans l’ordre du document, mais deux d’entre eux, <xref:System.Xml.Linq.XNode.Ancestors%2A> et <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, retournent les collections dans l’ordre inverse du document. Le tableau suivant énumère les axes et indique l’ordre de collection pour chacun d’eux :  
  
|Axe LINQ to XML|Classement|  
|----------------------|--------------|  
|XContainer.DescendantNodes|Ordre du document|  
|XContainer.Descendants|Ordre du document|  
|XContainer.Elements|Ordre du document|  
|XContainer.Nodes|Ordre du document|  
|XContainer.NodesAfterSelf|Ordre du document|  
|XContainer.NodesBeforeSelf|Ordre du document|  
|XElement.AncestorsAndSelf|Ordre inverse du document|  
|XElement.Attributes|Ordre du document|  
|XElement.DescendantNodesAndSelf|Ordre du document|  
|XElement.DescendantsAndSelf|Ordre du document|  
|XNode.Ancestors|Ordre inverse du document|  
|XNode.ElementsAfterSelf|Ordre du document|  
|XNode.ElementsBeforeSelf|Ordre du document|  
|XNode.NodesAfterSelf|Ordre du document|  
|XNode.NodesBeforeSelf|Ordre du document|  
  
## <a name="positional-predicates"></a>Prédicats de position  
 Dans une expression XPath, les prédicats de position sont exprimés dans l'ordre du document pour de nombreux axes, mais dans l'ordre inverse du document pour les axes inversés, qui sont `preceding`, `preceding-sibling`, `ancestor` et `ancestor-or-self`. Par exemple, l'expression XPath `preceding-sibling::*[1]` retourne le frère qui précède. C'est le cas même si le jeu de résultats final est présenté dans l'ordre du document.  
  
 Par contraste, tous les prédicats de position dans LINQ to XML sont toujours exprimés dans l'ordre de l'axe. Par exemple, `anElement.ElementsBeforeSelf().ElementAt(0)` retourne le premier élément enfant du parent de l'élément interrogé, mais pas l'enfant qui précède. Autre exemple : `anElement.Ancestors().ElementAt(0)` retourne l'élément parent.  
  
 Si vous souhaitez rechercher l’élément qui précède dans LINQ to XML, vous devez écrire l’expression suivante :  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a>Différences en matière de performances  
 Les requêtes XPath qui utilisent la fonctionnalité XPath dans LINQ to XML présentent des performances inférieures à celles des requêtes LINQ to XML.  
  
## <a name="comparison-of-composition"></a>Comparaison de la composition  
 La composition d’une requête LINQ to XML est quelque peu parallèle à celle d’une expression XPath, bien que sa syntaxe soit très différente.  
  
 Par exemple, si vous avez un élément dans une variable nommée `customers` et que vous souhaitez trouver un élément petit-enfant `CompanyName` sous tous les éléments enfants nommés `Customer`, vous devez écrire une expression XPath comme suit :  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 La requête LINQ to XML équivalente est :  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 Il existe des parallèles similaires pour chacun des axes XPath.  
  
|Axe XPath|Axe LINQ to XML|  
|----------------|----------------------|  
|enfant (l'axe par défaut)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Parent (..)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|axe des attributs (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|axe des ancêtres|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|axe ancestor-or-self|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|axe des descendants (//)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|descendant-or-self|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|frère suivant|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|frère précédent|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> ou<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|suivant|Aucun équivalent direct.|  
|précédent|Aucun équivalent direct.|  
  
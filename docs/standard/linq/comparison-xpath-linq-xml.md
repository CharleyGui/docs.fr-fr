---
title: Comparaison entre XPath et LINQ to XML-LINQ to XML
description: Les requêtes XPath et LINQ to XML peuvent interroger des arborescences XML. Cet article compare les deux options et recherche LINQ to XML les requêtes sont, sur l’ensemble, le plus puissant, polyvalent, plus rapide, plus sûr et plus pratique.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: b98651ffd7e0df0057164f40bedbc43d654d8c81
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553399"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>Comparaison de XPath et LINQ to XML

XPath et LINQ to XML sont similaires d’une certaine manière. Tous deux peuvent être utilisés pour interroger une arborescence XML et retourner des résultats tels qu'une collection d'élément, une collection d'attributs, une collection de nœuds ou la valeur d'un élément ou attribut. Toutefois, il existe des différences significatives entre les deux options.

## <a name="differences-between-xpath-and-linq-to-xml"></a>Différences entre XPath et LINQ to XML

XPath n’autorise pas la projection de nouveaux types. Il peut uniquement retourner des collections de nœuds de l’arborescence, tandis que LINQ to XML peut exécuter une requête et projeter un graphique d’objet ou une arborescence XML dans une nouvelle forme. LINQ to XML requêtes peuvent faire bien plus que des expressions XPath.

Les expressions XPath existent de manière isolée dans une chaîne. Le compilateur C# ne peut pas aider à analyser l’expression XPath au moment de la compilation. En revanche, c’est lui qui analyse et compile les requêtes LINQ to XML. Le compilateur peut intercepter de nombreuses erreurs de requête.

Les résultats XPath ne sont pas fortement typés. Dans plusieurs cas, le résultat de l’évaluation d’une expression XPath est un objet, et c’est au développeur de déterminer le type approprié et de convertir le résultat si nécessaire. En revanche, les projections à partir d’une requête LINQ to XML sont fortement typées.

## <a name="result-ordering"></a>Classement des résultats

La recommandation XPath 1,0 stipule qu’une collection qui est le résultat de l’évaluation d’une expression XPath n’est pas ordonnée.

Toutefois, lors de l’itération d’une collection retournée par une méthode d’axe XPath LINQ to XML, les nœuds de la collection sont retournés dans l’ordre du document. Cela est valable même lors de l'accès à des axes XPath où les prédicats sont exprimés dans l'ordre inverse du document, par exemple `preceding` et `preceding-sibling`.

En revanche, la plupart des LINQ to XML axes retournent les collections dans l’ordre du document. Toutefois, deux d’entre eux, <xref:System.Xml.Linq.XNode.Ancestors%2A> et <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> , retournent des collections dans l’ordre inverse du document. Le tableau suivant énumère les axes et indique l’ordre de collection pour chacun d’eux :

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

## <a name="positional-predicates"></a>Prédicats positionnels

Dans une expression XPath, les prédicats positionnels sont exprimés en termes d’ordre des documents pour de nombreux axes, mais sont exprimés dans l’ordre inverse des documents pour les axes inversés. Les axes inversé sont les suivants : `preceding` , `preceding-sibling` , `ancestor` et `ancestor-or-self` . Par exemple, l'expression XPath `preceding-sibling::*[1]` retourne le frère qui précède. C'est le cas même si le jeu de résultats final est présenté dans l'ordre du document.

Par contraste, tous les prédicats de position dans LINQ to XML sont toujours exprimés dans l'ordre de l'axe. Par exemple, `anElement.ElementsBeforeSelf().ElementAt(0)` retourne le premier élément enfant du parent de l'élément interrogé, mais pas l'enfant qui précède. Autre exemple : `anElement.Ancestors().ElementAt(0)` retourne l'élément parent.

Si vous souhaitez rechercher l’élément qui précède dans LINQ to XML, vous devez écrire l’expression suivante :

```csharp
ElementsBeforeSelf().Last()
```

```vb
ElementsBeforeSelf().Last()
```

## <a name="performance-differences"></a>Différences de performances

Les requêtes XPath qui utilisent la fonctionnalité XPath dans LINQ to XML seront plus lentes que les requêtes LINQ to XML.

## <a name="comparison-of-composition"></a>Comparaison de la composition

La composition d’une requête LINQ to XML est semblable à la composition d’une expression XPath, mais la syntaxe est très différente.

Par exemple, si vous avez un élément dans une variable nommée `customers` et que vous souhaitez trouver un élément petit-enfant nommé `CompanyName` sous tous les éléments enfants nommés `Customer` , vous devez écrire l’expression XPath suivante :

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
|axe des attributs (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|
|axe des ancêtres|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|
|axe ancestor-or-self|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|
|axe des descendants (//)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|
|descendant-or-self|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|
|frère suivant|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|
|frère précédent|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> or<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|
|suivant|Aucun équivalent direct.|
|précédent|Aucun équivalent direct.|

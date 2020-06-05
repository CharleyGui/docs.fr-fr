---
title: Vue d'ensemble des axes LINQ to XML
ms.date: 07/20/2015
ms.assetid: 9161f151-cfa8-4408-94ba-08a9ba3a486d
ms.openlocfilehash: 447490e784aa531b6603ddcd32d01eabea8f7299
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368996"
---
# <a name="linq-to-xml-axes-overview-visual-basic"></a>Vue d’ensemble des axes LINQ to XML (Visual Basic)
Après avoir créé une arborescence XML ou chargé un document XML dans une arborescence XML, vous pouvez l'interroger pour rechercher des éléments et des attributs et récupérer leurs valeurs. Vous pouvez récupérer des collections via les *méthodes d’axe*, également appelées *axes*. Certains des axes sont des méthodes dans les classes <xref:System.Xml.Linq.XElement> et <xref:System.Xml.Linq.XDocument> qui retournent des collections <xref:System.Collections.Generic.IEnumerable%601>. Certains axes sont des méthodes d'extension dans la classe <xref:System.Xml.Linq.Extensions>. Les axes qui sont implémentés en tant que méthodes d’extension opèrent sur des collections et retournent des collections.  
  
 Comme décrit dans [Vue d’ensemble de la classe XElement](xelement-class-overview.md), un objet <xref:System.Xml.Linq.XElement> représente un nœud à un seul d’élément. Le contenu de l'élément peut être complexe (parfois appelé contenu structuré) ou il peut s'agir d'un simple élément. Un élément simple peut être vide ou peut contenir une valeur. Si le nœud contient du contenu structuré, vous pouvez utiliser les différentes méthodes d'axe pour récupérer des énumérations d'éléments descendants. Les méthodes d'axe les plus couramment utilisées sont <xref:System.Xml.Linq.XContainer.Elements%2A> et <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
 Outre les méthodes d’axe, qui retournent des collections, il existe deux autres méthodes que vous utilisez fréquemment dans les requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. La méthode <xref:System.Xml.Linq.XContainer.Element%2A> retourne un seul objet <xref:System.Xml.Linq.XElement>. La méthode <xref:System.Xml.Linq.XElement.Attribute%2A> retourne un seul objet <xref:System.Xml.Linq.XAttribute>.  
  
 Dans de nombreux cas, les requêtes LINQ offrent la manière la plus puissante d’examiner une arborescence, d’en extraire des données et de la transformer. Les requêtes LINQ opèrent sur des objets qui implémentent <xref:System.Collections.Generic.IEnumerable%601> , et les [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] axes retournent <xref:System.Collections.Generic.IEnumerable%601> des <xref:System.Xml.Linq.XElement> collections et <xref:System.Collections.Generic.IEnumerable%601> des <xref:System.Xml.Linq.XAttribute> Collections. Vous avez besoin de ces collections pour effectuer vos requêtes.  
  
 Outre les méthodes d’axe qui récupèrent des collections d’éléments et d’attributs, il existe des méthodes d’axe qui vous permettent d’itérer au sein de l’arborescence en détail. Par exemple, au lieu de travailler au niveau des éléments et des attributs, vous pouvez travailler avec les nœuds de l'arborescence. Les nœuds représentent un niveau de granularité plus élevé que les éléments et les attributs. Lorsque vous travaillez avec des nœuds, vous pouvez examiner les commentaires XML, les nœuds de texte, les instructions de traitement, et bien plus encore. Cette fonctionnalité est importante, par exemple pour quelqu'un qui écrit un traitement de texte et qui souhaite enregistrer des documents au format XML. Toutefois, la plupart des programmeurs XML sont principalement concernés par les éléments, les attributs et leurs valeurs.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Méthodes pour récupérer une collection d'éléments  
 Voici un récapitulatif des méthodes de la classe <xref:System.Xml.Linq.XElement> (ou de ses classes de base) que vous appelez sur un objet <xref:System.Xml.Linq.XElement> pour retourner une collection d'éléments.  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> des ancêtres de cet élément. Une surcharge retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> des ancêtres qui ont l'objet <xref:System.Xml.Linq.XName> spécifié.|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> des descendants de cet élément. Une surcharge retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> des descendants qui ont l'objet <xref:System.Xml.Linq.XName> spécifié.|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> des éléments enfants de cet élément. Une surcharge retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> des éléments enfants qui ont l'objet <xref:System.Xml.Linq.XName> spécifié.|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> des éléments enfants placés après cet élément. Une surcharge retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> des éléments après cet élément qui ont l'objet <xref:System.Xml.Linq.XName> spécifié.|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> des éléments enfants placés avant cet élément. Une surcharge retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> des éléments avant cet élément qui ont l'objet <xref:System.Xml.Linq.XName> spécifié.|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> de cet élément et de ces ancêtres. Une surcharge retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> des éléments qui ont l'objet <xref:System.Xml.Linq.XName> spécifié.|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> de cet élément et de ces descendants. Une surcharge retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> des éléments qui ont l'objet <xref:System.Xml.Linq.XName> spécifié.|  
  
## <a name="method-for-retrieving-a-single-element"></a>Méthode pour récupérer un seul élément  
 La méthode suivante récupère un seul enfant à partir d'un objet <xref:System.Xml.Linq.XElement>.  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Retourne le premier objet <xref:System.Xml.Linq.XElement> enfant qui a l'objet <xref:System.Xml.Linq.XName> spécifié.|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Méthode pour récupérer une collection d’attributs  
 La méthode suivante récupère des attributs à partir d'un objet <xref:System.Xml.Linq.XElement>.  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Retourne un objet <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XAttribute> de tous les attributs.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Méthode pour récupérer un seul attribut  
 La méthode suivante récupère un seul attribut à partir d'un objet <xref:System.Xml.Linq.XElement>.  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Retourne l'objet <xref:System.Xml.Linq.XAttribute> qui a l'objet <xref:System.Xml.Linq.XName> spécifié.|  
  
## <a name="see-also"></a>Voir aussi

- [Axes LINQ to XML (Visual Basic)](linq-to-xml-axes.md)

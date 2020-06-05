---
title: LINQ to XML pour les utilisateurs XPath
ms.date: 07/20/2015
ms.assetid: 0e64911c-a7cc-4c20-b927-ca99078b5656
ms.openlocfilehash: 7942d33831644875f390e9128965fe1c36433808
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368788"
---
# <a name="linq-to-xml-for-xpath-users-visual-basic"></a>LINQ to XML pour les utilisateurs XPath (Visual Basic)

Cet ensemble de rubriques illustre un certain nombre d'expressions XPath et leurs équivalents [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Tous les exemples utilisent la fonctionnalité XPath dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] accessible par la méthode d'extension dans <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>. L'exemple exécute à la fois l'expression XPath et l'expression [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Chaque exemple compare ensuite les résultats des deux requêtes et confirme que l'expression XPath est fonctionnellement équivalente à la requête [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Étant donné que les deux types de requêtes retournent des nœuds de la même arborescence XML, la comparaison des résultats de requêtes est effectuée à l'aide de l'identité référentielle.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Comparaison de XPath et LINQ to XML](../../../../csharp/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|Fournit une vue d'ensemble des similitudes et différences entre XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].|  
|[Comment : Rechercher un élément enfant (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-child-element-xpath-linq-to-xml.md)|Compare l’axe des éléments enfants XPath à la [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> méthode.<br /><br /> L'expression XPath associée est : `"DeliveryNotes"`.|  
|[Comment : Rechercher une liste d’éléments enfants (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|Compare l’axe des éléments enfants XPath à l' [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> axe.<br /><br /> L'expression XPath associée est : `"./*"`|  
|[Comment : Rechercher l’élément racine (XPath-LINQ to XML) (Visual Basic)](how-to-find-the-root-element-xpath-linq-to-xml.md)|Compare comment obtenir l'élément racine avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"/PurchaseOrders"`|  
|[Comment : Rechercher des éléments descendants (XPath-LINQ to XML) (Visual Basic)](how-to-find-descendant-elements-xpath-linq-to-xml.md)|Compare comment obtenir les éléments descendants avec un nom particulier avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"//Name"`|  
|[Comment : filtrer sur un attribut (XPath-LINQ to XML) (Visual Basic)](how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Compare comment obtenir les éléments descendants avec un nom spécifié, et avec un attribut avec une valeur spécifiée avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"./Address[@Type='Shipping']"`|  
|[Comment : Rechercher des éléments connexes (XPath-LINQ to XML) (Visual Basic)](how-to-find-related-elements-xpath-linq-to-xml.md)|Compare comment obtenir un élément en sélectionnant un attribut auquel il est fait référence par la valeur d'un autre élément avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"./Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Comment : Rechercher des éléments dans un espace de noms (XPath-LINQ to XML) (Visual Basic)](how-to-find-elements-in-a-namespace.md)|Compare l’utilisation de la <xref:System.Xml.XmlNamespaceManager> classe XPath à la [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XName.Namespace%2A> propriété de la <xref:System.Xml.Linq.XName> classe pour utiliser des espaces de noms XML.<br /><br /> L'expression XPath associée est : `"./aw:*"`|  
|[Comment : Rechercher les frères précédents (XPath-LINQ to XML) (Visual Basic)](how-to-find-preceding-siblings-xpath-linq-to-xml.md)|Compare l'axe `preceding-sibling` XPath à l'axe [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] enfant <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>.<br /><br /> L'expression XPath associée est : `"preceding-sibling::*"`|  
|[Comment : Rechercher des descendants d’un élément enfant (XPath-LINQ to XML) (Visual Basic)](how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|Compare comment obtenir les éléments descendants d'un élément enfant avec un nom particulier avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"./Paragraph//Text/text()"`|  
|[Comment : Rechercher une Union de deux chemins d’accès d’emplacement (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-union-of-two-location-paths-xpath.md)|Compare l'utilisation de l'opérateur d'union <code>&#124;</code> dans XPath avec l'opérateur de requête standard <xref:System.Linq.Enumerable.Concat%2A> dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : <code>"//Category&#124;//Price"</code>|  
|[Comment : Rechercher des nœuds frères (XPath-LINQ to XML) (Visual Basic)](how-to-find-sibling-nodes-xpath-linq-to-xml.md)|Compare comment rechercher tous les frères d'un nœud qui ont un nom spécifique avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. <br /><br /> L'expression XPath associée est : `"../Book"`|  
|[Comment : Rechercher un attribut du parent (XPath-LINQ to XML) (Visual Basic)](how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Compare comment naviguer jusqu'à l'élément parent et rechercher un attribut associé à l'aide de XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"../@id"`|  
|[Comment : Rechercher des attributs de frères avec un nom spécifique (XPath-LINQ to XML) (Visual Basic)](how-to-find-attributes-of-siblings-with-a-specific-name.md)|Compare comment rechercher des attributs spécifiques des frères du nœud de contexte avec XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"../Book/@id"`|  
|[Comment : Rechercher des éléments avec un attribut spécifique (XPath-LINQ to XML) (Visual Basic)](how-to-find-elements-with-a-specific-attribute.md)|Compare comment rechercher tous les éléments contenant un attribut spécifique à l'aide de XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. <br /><br /> L'expression XPath associée est : `"./*[@Select]"`|  
|[Comment : Rechercher des éléments enfants en fonction de leur position (XPath-LINQ to XML) (Visual Basic)](how-to-find-child-elements-based-on-position.md)|Compare comment rechercher un élément en fonction de sa position relative à l'aide de XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"Test[position() >= 2 and position() <= 4]"`|  
|[Comment : Rechercher le frère précédent (XPath-LINQ to XML) (Visual Basic)](how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|Compare comment faire rechercher le frère précédent d'un nœud à l'aide de XPath et [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].<br /><br /> L'expression XPath associée est : `"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XPath?displayProperty=nameWithType>
- [Interrogation d’arborescences XML (Visual Basic)](querying-xml-trees.md)
- [Traitement des données XML à l'aide du modèle de données XPath](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)

---
title: Axes LINQ to XML
ms.date: 07/20/2015
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
ms.openlocfilehash: 757c765062b1d1ca1cddb0c559fa46ef6a0fe796
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368983"
---
# <a name="linq-to-xml-axes-visual-basic"></a>Axes LINQ to XML (Visual Basic)
Après avoir créé une arborescence XML ou chargé un document XML dans une arborescence XML, vous pouvez l'interroger pour rechercher des éléments et des attributs et récupérer leurs valeurs.  
  
 Pour pouvoir écrire des requêtes, vous devez comprendre ce que sont les axes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Il existe deux sortes de méthodes d’axe : tout d’abord, il y a les méthodes que vous appelez sur un seul objet <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> ou <xref:System.Xml.Linq.XNode>. Ces méthodes opèrent sur un seul objet et renvoient une collection d’objets <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute> ou <xref:System.Xml.Linq.XNode>. En second lieu, il y a des méthodes d'extension qui opèrent sur des collections et retournent des collections. Les méthodes d'extension énumèrent la collection source, appellent la méthode d'axe appropriée sur chaque élément dans la collection et concatènent les résultats.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Vue d’ensemble des axes LINQ to XML (Visual Basic)](linq-to-xml-axes-overview.md)|Définit les axes et explique comment les utiliser dans le contexte des requêtes [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].|  
|[Comment : récupérer une collection d’éléments (LINQ to XML) (Visual Basic)](how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Présente la méthode <xref:System.Xml.Linq.XContainer.Elements%2A>. Cette méthode récupère une collection d’éléments enfants d’un élément.|  
|[Comment : récupérer la valeur d’un élément (LINQ to XML) (Visual Basic)](how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Montre comment obtenir les valeurs d'éléments.|  
|[Comment : filtrer sur des noms d’éléments (LINQ to XML) (Visual Basic)](how-to-filter-on-element-names-linq-to-xml.md)|Montre comment filtrer les noms d'éléments lors de l'utilisation des axes.|  
|[Comment : chaîner des appels de méthode d’axe (LINQ to XML) (Visual Basic)](how-to-chain-axis-method-calls-linq-to-xml.md)|Montre comment chaîner les appels aux méthodes d'axe.|  
|[Comment : récupérer un seul élément enfant (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-child-element-linq-to-xml.md)|Montre comment récupérer un seul élément enfant d’un élément, étant donné le nom d’étiquette de l’élément enfant.|  
|[Comment : récupérer une collection d’attributs (LINQ to XML) (Visual Basic)](how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Présente la méthode <xref:System.Xml.Linq.XElement.Attributes%2A>. Cette méthode récupère les attributs d'un élément.|  
|[Comment : récupérer un seul attribut (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-attribute-linq-to-xml.md)|Montre comment récupérer un seul attribut d'un élément, étant donné le nom de l'attribut.|  
|[Comment : récupérer la valeur d’un attribut (LINQ to XML) (Visual Basic)](how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Montre comment obtenir les valeurs d'attributs.|  
|[Comment : récupérer la valeur superficielle d’un élément (Visual Basic)](how-to-retrieve-the-shallow-value-of-an-element.md)|Indique comment récupérer la valeur superficielle d'un élément.|  
|[Axes intégrés au langage en Visual Basic (LINQ to XML)](language-integrated-axes.md)|Résume les axes intégrés Visual Basic.|  
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation (LINQ to XML) (Visual Basic)](programming-guide-linq-to-xml.md)

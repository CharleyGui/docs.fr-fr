---
title: LINQ to XML Annotations2
ms.date: 07/20/2015
ms.assetid: c3e8b3ff-fceb-4428-b0ca-1ed6f128aac8
ms.openlocfilehash: 917129a06483ce2001e178d744440504533d28d6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84369009"
---
# <a name="linq-to-xml-annotations"></a>Annotations LINQ to XML
Les annotations dans [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] vous permettent d’associer n’importe quel objet arbitraire de n’importe quel type arbitraire à n’importe quel composant XML dans une arborescence XML.  
  
 Pour ajouter une annotation à un composant XML, tel qu'un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute>, vous appelez la méthode <xref:System.Xml.Linq.XObject.AddAnnotation%2A>. Vous pouvez récupérer des annotations par type.  
  
 Notez que les annotations ne font pas partie du jeu d'informations XML ; elles ne sont pas sérialisées ou désérialisées.  
  
## <a name="methods"></a>Méthodes  
 Vous pouvez utiliser les méthodes suivantes lorsque vous travaillez avec des annotations :  
  
|Méthode|Description|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XObject.AddAnnotation%2A>|Ajoute un objet à la liste d'annotation de <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotation%2A>|Obtient le premier objet annotation du type spécifié de <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.Annotations%2A>|Obtient une collection d’annotations du type spécifié pour un objet <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObject.RemoveAnnotations%2A>|Supprime les annotations du type spécifié d’un objet <xref:System.Xml.Linq.XObject>.|  
  
## <a name="see-also"></a>Voir aussi

- [Visual Basic (Advanced LINQ to XML Programming)](advanced-linq-to-xml-programming.md)

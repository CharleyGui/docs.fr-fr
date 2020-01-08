---
title: Comment récupérer un seul élément enfant (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: ce37db9e-76fa-46eb-b4cc-e8f32d22ad90
ms.openlocfilehash: 0e10cf230a73e6419f2d9c663766f9a24a0930af
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347474"
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-c"></a>Comment récupérer un seul élément enfant (LINQ to XML) (C#)
Cette rubrique explique comment récupérer un seul élément enfant, étant donné le nom de l'élément enfant. Lorsque vous connaissez le nom de l’élément enfant et qu’il n’y a qu’un seul élément qui possède ce nom, il peut être plus commode de récupérer un seul élément plutôt qu’une collection.  
  
 La méthode <xref:System.Xml.Linq.XContainer.Element%2A> retourne le premier objet <xref:System.Xml.Linq.XElement> enfant avec l'objet <xref:System.Xml.Linq.XName> spécifié.  
  
 Si vous souhaitez récupérer un seul élément enfant en Visual Basic, une approche courante consiste à utiliser la propriété XML, puis à récupérer le premier élément à l'aide de la notation d'indexeur de tableau.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre l'utilisation de la méthode <xref:System.Xml.Linq.XContainer.Element%2A>. Cet exemple prend l'arborescence XML nommée `po` et recherche le premier élément nommé `Comment`.  
  
 L'exemple Visual Basic illustre l'utilisation de la notation d'indexeur de tableau pour récupérer un seul élément.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
XElement e = po.Element("DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre le même code pour du XML qui est dans un espace de noms. Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique dans un espace de noms](./sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```csharp  
XElement po = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
XElement e = po.Element(aw + "DeliveryNotes");  
Console.WriteLine(e);  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Axes LINQ to XML (C#)](./linq-to-xml-axes-overview.md)

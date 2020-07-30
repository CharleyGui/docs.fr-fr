---
title: Comment écrire des requêtes avec un filtrage complexe (C#)
description: Découvrez comment écrire des requêtes de LINQ to XML avec des filtres complexes. Consultez des exemples de code et affichez des ressources supplémentaires.
ms.date: 07/20/2015
ms.assetid: 4065d901-cf89-4e47-8bf9-abb65acfb003
ms.openlocfilehash: 5d2c1aafc210b35d4d6b1f1b2d74b11966d90c80
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303424"
---
# <a name="how-to-write-queries-with-complex-filtering-c"></a>Comment écrire des requêtes avec un filtrage complexe (C#)
Il peut arriver que vous souhaitiez écrire des requêtes LINQ to XML à l'aide de filtres complexes. Par exemple, il se peut que vous deviez rechercher tous les éléments qui ont un élément enfant avec un nom et une valeur spécifiques. Cette rubrique fournit un exemple d'écriture de requête avec un filtrage complexe.  
  
## <a name="example"></a>Exemple  
 Cet exemple montre comment rechercher tous les éléments `PurchaseOrder` qui ont un élément `Address` enfant ayant un attribut `Type` égal à « Shipping » et un élément `State` enfant égal à « NY ». Il utilise une sous-requête dans la clause `Where` et l'opérateur `Any` retourne `true` si la collection possède des éléments. Pour plus d’informations sur la syntaxe de requête basée sur une méthode, consultez [Syntaxe de requête et syntaxe de méthode dans LINQ](./query-syntax-and-method-syntax-in-linq.md).  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
 Pour plus d’informations sur l’opérateur `Any`, consultez [Opérations de quantificateur (C#)](./quantifier-operations.md).  
  
```csharp  
XElement root = XElement.Load("PurchaseOrders.xml");  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements("PurchaseOrder")  
    where
        (from add in el.Elements("Address")  
        where  
            (string)add.Attribute("Type") == "Shipping" &&  
            (string)add.Element("State") == "NY"  
        select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute("PurchaseOrderNumber"));  
```  
  
 Ce code génère la sortie suivante :  
  
```output  
99505  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms. Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur dans un espace de noms](./sample-xml-file-multiple-purchase-orders-in-a-namespace.md).  
  
```csharp  
XElement root = XElement.Load("PurchaseOrdersInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> purchaseOrders =  
    from el in root.Elements(aw + "PurchaseOrder")  
    where  
        (from add in el.Elements(aw + "Address")  
         where  
             (string)add.Attribute(aw + "Type") == "Shipping" &&  
             (string)add.Element(aw + "State") == "NY"  
         select add)  
        .Any()  
    select el;  
foreach (XElement el in purchaseOrders)  
    Console.WriteLine((string)el.Attribute(aw + "PurchaseOrderNumber"));  
```  
  
 Ce code génère la sortie suivante :  
  
```output  
99505  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Opérations de projection (C#)](./projection-operations.md)
- [Opérations de quantificateur (C#)](./quantifier-operations.md)

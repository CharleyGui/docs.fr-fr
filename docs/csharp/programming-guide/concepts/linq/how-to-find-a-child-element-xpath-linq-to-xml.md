---
title: Comment rechercher un élément enfant (XPath-LINQ to XML) (C#)
description: Découvrez comment rechercher un élément enfant en comparant l’axe des éléments enfants XPath à la méthode d’élément LINQ to XML.
ms.date: 07/20/2015
ms.assetid: 4fa6182d-6196-4ed1-9c9e-82949ff89c71
ms.openlocfilehash: 57d1a4e636e3443512020129a76cc2de7bb3f244
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301734"
---
# <a name="how-to-find-a-child-element-xpath-linq-to-xml-c"></a>Comment rechercher un élément enfant (XPath-LINQ to XML) (C#)
Cette rubrique compare l’axe des éléments enfants XPath à la [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> méthode.  
  
 L'expression XPath est `DeliveryNotes`.  
  
## <a name="example"></a>Exemple  
 Cet exemple recherche l'élément enfant `DeliveryNotes`.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```csharp  
XDocument cpo = XDocument.Load("PurchaseOrders.xml");  
XElement po = cpo.Root.Element("PurchaseOrder");  
  
// LINQ to XML query  
XElement el1 = po.Element("DeliveryNotes");  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("DeliveryNotes");  
// same as "child::DeliveryNotes"  
// same as "./DeliveryNotes"  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
Results are identical  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
---
title: Comment filtrer sur un attribut (XPath-LINQ to XML) (C#)
description: Apprenez à filtrer les éléments descendants avec un nom et une valeur d’attribut spécifiés pour XPath-LINQ to XML.
ms.date: 07/20/2015
ms.assetid: 208d6256-1bd7-4237-b2c9-909f26dfd0e2
ms.openlocfilehash: 80c43b8485314c6a711b574b5d6c23b56533833d
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302891"
---
# <a name="how-to-filter-on-an-attribute-xpath-linq-to-xml-c"></a>Comment filtrer sur un attribut (XPath-LINQ to XML) (C#)
Cette rubrique montre comment obtenir les éléments descendants avec un nom spécifié et avec un attribut avec une valeur spécifiée.  
  
 L’expression XPath est la suivante :  
  
 `.//Address[@Type='Shipping']`  
  
## <a name="example"></a>Exemple  
 Cet exemple recherche tous les éléments descendants avec le nom `Address` et avec un attribut `Type` avec une valeur de « Shipping ».  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
// XPath expression  
IEnumerable<XElement> list2 = po.XPathSelectElements(".//Address[@Type='Shipping']");  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
Results are identical  
<Address Type="Shipping">  
  <Name>Ellen Adams</Name>  
  <Street>123 Maple Street</Street>  
  <City>Mill Valley</City>  
  <State>CA</State>  
  <Zip>10999</Zip>  
  <Country>USA</Country>  
</Address>  
<Address Type="Shipping">  
  <Name>Cristian Osorio</Name>  
  <Street>456 Main Street</Street>  
  <City>Buffalo</City>  
  <State>NY</State>  
  <Zip>98112</Zip>  
  <Country>USA</Country>  
</Address>  
<Address Type="Shipping">  
  <Name>Jessica Arnold</Name>  
  <Street>4055 Madison Ave</Street>  
  <City>Seattle</City>  
  <State>WA</State>  
  <Zip>98112</Zip>  
  <Country>USA</Country>  
</Address>  
```  

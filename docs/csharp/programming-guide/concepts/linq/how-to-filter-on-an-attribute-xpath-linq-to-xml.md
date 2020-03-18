---
title: Comment filtrer sur un attribut (XPath-LINQ à XML) (C)
ms.date: 07/20/2015
ms.assetid: 208d6256-1bd7-4237-b2c9-909f26dfd0e2
ms.openlocfilehash: ab2cd439f4dd1454de4fa565658ef5dac14b8c22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141275"
---
# <a name="how-to-filter-on-an-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="771f5-102">Comment filtrer sur un attribut (XPath-LINQ à XML) (C)</span><span class="sxs-lookup"><span data-stu-id="771f5-102">How to filter on an attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="771f5-103">Cette rubrique montre comment obtenir les éléments descendants avec un nom spécifié et avec un attribut avec une valeur spécifiée.</span><span class="sxs-lookup"><span data-stu-id="771f5-103">This topic shows how to get the descendant elements with a specified name, and with an attribute with a specified value.</span></span>  
  
 <span data-ttu-id="771f5-104">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="771f5-104">The XPath expression is:</span></span>  
  
 `.//Address[@Type='Shipping']`  
  
## <a name="example"></a><span data-ttu-id="771f5-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="771f5-105">Example</span></span>  
 <span data-ttu-id="771f5-106">Cet exemple recherche tous les éléments descendants avec le nom `Address` et avec un attribut `Type` avec une valeur de « Shipping ».</span><span class="sxs-lookup"><span data-stu-id="771f5-106">This example finds all descendants elements with the name of `Address`, and with a `Type` attribute with a value of "Shipping".</span></span>  
  
 <span data-ttu-id="771f5-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Plusieurs commandes fournisseur (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="771f5-107">This example uses the following XML document: [Sample XML File: Multiple Purchase Orders (LINQ to XML)](./sample-xml-file-multiple-purchase-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="771f5-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="771f5-108">This example produces the following output:</span></span>  
  
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

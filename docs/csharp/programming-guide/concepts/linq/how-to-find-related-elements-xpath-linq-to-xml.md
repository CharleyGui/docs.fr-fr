---
title: 'Procédure : Rechercher des éléments connexes (XPath-LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 41b386ee-562d-4841-bd6b-e44a7eb69f26
ms.openlocfilehash: 2aa3f6c6c2c2ac327ff2dffc206cdd294e12d7a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253644"
---
# <a name="how-to-find-related-elements-xpath-linq-to-xml-c"></a><span data-ttu-id="6cdd4-102">Procédure : Rechercher des éléments connexes (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="6cdd4-102">How to: Find Related Elements (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="6cdd4-103">Cette rubrique montre comment obtenir un élément en sélectionnant un attribut auquel il est fait référence par la valeur d'un autre élément.</span><span class="sxs-lookup"><span data-stu-id="6cdd4-103">This topic shows how to get an element selecting on an attribute that is referred to by the value of another element.</span></span>  
  
 <span data-ttu-id="6cdd4-104">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="6cdd4-104">The XPath expression is:</span></span>  
  
 `.//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]`  
  
## <a name="example"></a><span data-ttu-id="6cdd4-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="6cdd4-105">Example</span></span>  
 <span data-ttu-id="6cdd4-106">Cet exemple recherche le douzième élément `Order`, puis recherche le client associé à cette commande.</span><span class="sxs-lookup"><span data-stu-id="6cdd4-106">This example finds the 12th `Order` element, and then finds the customer for that order.</span></span>  
  
 <span data-ttu-id="6cdd4-107">Notez que l’indexation dans une liste en .NET est en base « zéro ».</span><span class="sxs-lookup"><span data-stu-id="6cdd4-107">Note that indexing into a list in .NET is 'zero' based.</span></span> <span data-ttu-id="6cdd4-108">L'indexation dans une collection de nœuds dans un prédicat XPath est basée sur « un ».</span><span class="sxs-lookup"><span data-stu-id="6cdd4-108">Indexing into a collection of nodes in an XPath predicate is 'one' based.</span></span> <span data-ttu-id="6cdd4-109">Cet exemple reflète cette différence.</span><span class="sxs-lookup"><span data-stu-id="6cdd4-109">This example reflects this difference.</span></span>  
  
 <span data-ttu-id="6cdd4-110">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="6cdd4-110">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XDocument co = XDocument.Load("CustomersOrders.xml");  
  
// LINQ to XML query  
XElement customer1 =  
    (from el in co.Descendants("Customer")  
     where (string)el.Attribute("CustomerID") ==  
          (string)(co  
              .Element("Root")  
              .Element("Orders")  
              .Elements("Order")  
              .ToList()[11]  
              .Element("CustomerID"))  
    select el)  
    .First();  
  
// An alternate way to write the query that avoids creation  
// of a System.Collections.Generic.List:  
XElement customer2 =  
    (from el in co.Descendants("Customer")  
     where (string)el.Attribute("CustomerID") ==  
          (string)(co  
              .Element("Root")  
              .Element("Orders")  
              .Elements("Order")  
              .Skip(11).First()  
              .Element("CustomerID"))  
    select el)  
    .First();  
  
// XPath expression  
XElement customer3 = co.XPathSelectElement(  
  ".//Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]");  
  
if (customer1 == customer2 && customer1 == customer3)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(customer1);  
```  
  
 <span data-ttu-id="6cdd4-111">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="6cdd4-111">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Customer CustomerID="HUNGC">  
  <CompanyName>Hungry Coyote Import Store</CompanyName>  
  <ContactName>Yoshi Latimer</ContactName>  
  <ContactTitle>Sales Representative</ContactTitle>  
  <Phone>(503) 555-6874</Phone>  
  <Fax>(503) 555-2376</Fax>  
  <FullAddress>  
    <Address>City Center Plaza 516 Main St.</Address>  
    <City>Elgin</City>  
    <Region>OR</Region>  
    <PostalCode>97827</PostalCode>  
    <Country>USA</Country>  
  </FullAddress>  
</Customer>  
```  
 
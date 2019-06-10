---
title: 'Procédure : Rechercher un élément avec un attribut spécifique (C#)'
ms.date: 07/20/2015
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 7ec6240bf399058ca94cc52c66e6029f924fcd29
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485558"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a><span data-ttu-id="42d27-102">Procédure : Rechercher un élément avec un attribut spécifique (C#)</span><span class="sxs-lookup"><span data-stu-id="42d27-102">How to: Find an Element with a Specific Attribute (C#)</span></span>
<span data-ttu-id="42d27-103">Cette rubrique montre comment rechercher un élément qui possède un attribut qui a une valeur spécifique.</span><span class="sxs-lookup"><span data-stu-id="42d27-103">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42d27-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="42d27-104">Example</span></span>  
 <span data-ttu-id="42d27-105">L'exemple montre comment rechercher l'élément `Address` qui possède un attribut `Type` avec la valeur « Billing ».</span><span class="sxs-lookup"><span data-stu-id="42d27-105">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="42d27-106">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Commande fournisseur standard (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="42d27-106">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="42d27-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="42d27-107">This code produces the following output:</span></span>  
  
```xml  
<Address Type="Billing">  
  <Name>Tai Yee</Name>  
  <Street>8 Oak Avenue</Street>  
  <City>Old Town</City>  
  <State>PA</State>  
  <Zip>95819</Zip>  
  <Country>USA</Country>  
</Address>  
```  
  
## <a name="example"></a><span data-ttu-id="42d27-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="42d27-108">Example</span></span>  
 <span data-ttu-id="42d27-109">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="42d27-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="42d27-110">Pour plus d’informations, consultez [Utilisation des espaces de noms XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="42d27-110">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="42d27-111">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Commande fournisseur standard dans un espace de noms](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="42d27-111">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrderInNamespace.xml");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> address =  
    from el in root.Elements(aw + "Address")  
    where (string)el.Attribute(aw + "Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="42d27-112">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="42d27-112">This code produces the following output:</span></span>  
  
```xml  
<aw:Address aw:Type="Billing" xmlns:aw="http://www.adventure-works.com">  
  <aw:Name>Tai Yee</aw:Name>  
  <aw:Street>8 Oak Avenue</aw:Street>  
  <aw:City>Old Town</aw:City>  
  <aw:State>PA</aw:State>  
  <aw:Zip>95819</aw:Zip>  
  <aw:Country>USA</aw:Country>  
</aw:Address>  
```  
  
## <a name="see-also"></a><span data-ttu-id="42d27-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="42d27-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="42d27-114">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="42d27-114">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="42d27-115">Opérations de projection (C#)</span><span class="sxs-lookup"><span data-stu-id="42d27-115">Projection Operations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)

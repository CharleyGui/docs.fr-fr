---
title: Comment rechercher un élément avec un attribut spécifique (C#)
description: Découvrez comment rechercher un élément qui possède un attribut avec une valeur spécifique. Consultez des exemples de code et des ressources supplémentaires.
ms.date: 07/20/2015
ms.assetid: b92591aa-3cfb-490e-99f6-da8de335e362
ms.openlocfilehash: 44875ca2104e7a8f83e83da983af49ef85c89f0a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303281"
---
# <a name="how-to-find-an-element-with-a-specific-attribute-c"></a><span data-ttu-id="cc3bb-104">Comment rechercher un élément avec un attribut spécifique (C#)</span><span class="sxs-lookup"><span data-stu-id="cc3bb-104">How to find an element with a specific attribute (C#)</span></span>
<span data-ttu-id="cc3bb-105">Cette rubrique montre comment rechercher un élément qui possède un attribut qui a une valeur spécifique.</span><span class="sxs-lookup"><span data-stu-id="cc3bb-105">This topic shows how to find an element that has an attribute that has a specific value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc3bb-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="cc3bb-106">Example</span></span>  
 <span data-ttu-id="cc3bb-107">L'exemple montre comment rechercher l'élément `Address` qui possède un attribut `Type` avec la valeur « Billing ».</span><span class="sxs-lookup"><span data-stu-id="cc3bb-107">The example shows how to find the `Address` element that has a `Type` attribute with a value of "Billing".</span></span>  
  
 <span data-ttu-id="cc3bb-108">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="cc3bb-108">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> address =  
    from el in root.Elements("Address")  
    where (string)el.Attribute("Type") == "Billing"  
    select el;  
foreach (XElement el in address)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="cc3bb-109">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="cc3bb-109">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="cc3bb-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="cc3bb-110">Example</span></span>  
 <span data-ttu-id="cc3bb-111">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cc3bb-111">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="cc3bb-112">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="cc3bb-112">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="cc3bb-113">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique dans un espace de noms](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="cc3bb-113">This example uses the following XML document: [Sample XML File: Typical Purchase Order in a Namespace](./sample-xml-file-typical-purchase-order-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="cc3bb-114">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="cc3bb-114">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cc3bb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc3bb-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [<span data-ttu-id="cc3bb-116">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="cc3bb-116">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="cc3bb-117">Opérations de projection (C#)</span><span class="sxs-lookup"><span data-stu-id="cc3bb-117">Projection Operations (C#)</span></span>](./projection-operations.md)

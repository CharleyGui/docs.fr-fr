---
title: Comment calculer des valeurs intermédiaires (C#)
description: Cet exemple de LINQ to XML en C# montre comment calculer des valeurs intermédiaires qui peuvent être utilisées dans le tri, le filtrage et la sélection.
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: fc648f20550de13735a1f6da6b2f811fd0d39004
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103611"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="eb21d-103">Comment calculer des valeurs intermédiaires (C#)</span><span class="sxs-lookup"><span data-stu-id="eb21d-103">How to calculate intermediate values (C#)</span></span>
<span data-ttu-id="eb21d-104">Cet exemple montre comment calculer des valeurs intermédiaires qui peuvent être utilisées dans le tri, le filtrage et la sélection.</span><span class="sxs-lookup"><span data-stu-id="eb21d-104">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb21d-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="eb21d-105">Example</span></span>  
 <span data-ttu-id="eb21d-106">L'exemple suivant utilise la clause `Let`.</span><span class="sxs-lookup"><span data-stu-id="eb21d-106">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="eb21d-107">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="eb21d-107">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> extensions =  
    from el in root.Elements("Data")  
    let extension = (decimal)el.Element("Quantity") * (decimal)el.Element("Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="eb21d-108">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="eb21d-108">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="eb21d-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="eb21d-109">Example</span></span>  
 <span data-ttu-id="eb21d-110">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="eb21d-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="eb21d-111">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="eb21d-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="eb21d-112">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques dans un espace de noms](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="eb21d-112">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<decimal> extensions =  
    from el in root.Elements(ad + "Data")  
    let extension = (decimal)el.Element(ad + "Quantity") * (decimal)el.Element(ad + "Price")  
    where extension >= 25  
    orderby extension  
    select extension;  
foreach (decimal ex in extensions)  
    Console.WriteLine(ex);  
```  
  
 <span data-ttu-id="eb21d-113">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="eb21d-113">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  

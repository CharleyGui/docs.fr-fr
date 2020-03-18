---
title: Comment calculer les valeurs intermédiaires (C)
ms.date: 07/20/2015
ms.assetid: 7fd3001f-f8f9-4bce-879f-d4c7af8a04fe
ms.openlocfilehash: 3ead3bfb02f7c9192db96996c1f1e01a86a4191a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141448"
---
# <a name="how-to-calculate-intermediate-values-c"></a><span data-ttu-id="55651-102">Comment calculer les valeurs intermédiaires (C)</span><span class="sxs-lookup"><span data-stu-id="55651-102">How to calculate intermediate values (C#)</span></span>
<span data-ttu-id="55651-103">Cet exemple montre comment calculer des valeurs intermédiaires qui peuvent être utilisées dans le tri, le filtrage et la sélection.</span><span class="sxs-lookup"><span data-stu-id="55651-103">This example shows how to calculate intermediate values that can be used in sorting, filtering, and selecting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55651-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="55651-104">Example</span></span>  
 <span data-ttu-id="55651-105">L'exemple suivant utilise la clause `Let`.</span><span class="sxs-lookup"><span data-stu-id="55651-105">The following example uses the `Let` clause.</span></span>  
  
 <span data-ttu-id="55651-106">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="55651-106">This example uses the following XML document: [Sample XML File: Numerical Data (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="55651-107">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="55651-107">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  
  
## <a name="example"></a><span data-ttu-id="55651-108"> Exemple</span><span class="sxs-lookup"><span data-stu-id="55651-108">Example</span></span>  
 <span data-ttu-id="55651-109">L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="55651-109">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="55651-110">Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="55651-110">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="55651-111">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques dans un espace de noms](./sample-xml-file-numerical-data-in-a-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="55651-111">This example uses the following XML document: [Sample XML File: Numerical Data in a Namespace](./sample-xml-file-numerical-data-in-a-namespace.md).</span></span>  
  
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
  
 <span data-ttu-id="55651-112">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="55651-112">This code produces the following output:</span></span>  
  
```output  
55.92  
73.50  
89.99  
198.00  
435.00  
```  

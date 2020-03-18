---
title: Comment trouver des éléments avec un attribut spécifique (XPath-LINQ à XML) (C)
ms.date: 07/20/2015
ms.assetid: daed00dd-923a-43be-8a90-eee406f6f574
ms.openlocfilehash: e79cad3ad6fb0bf88e388b552f8e39327acfb4ad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141042"
---
# <a name="how-to-find-elements-with-a-specific-attribute-xpath-linq-to-xml-c"></a><span data-ttu-id="10a7f-102">Comment trouver des éléments avec un attribut spécifique (XPath-LINQ à XML) (C)</span><span class="sxs-lookup"><span data-stu-id="10a7f-102">How to find elements with a specific attribute (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="10a7f-103">Parfois, vous souhaitez rechercher tous les éléments qui ont un attribut spécifique.</span><span class="sxs-lookup"><span data-stu-id="10a7f-103">Sometimes you want to find all elements that have a specific attribute.</span></span> <span data-ttu-id="10a7f-104">Vous ne vous souciez pas du contenu de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="10a7f-104">You are not concerned about the contents of the attribute.</span></span> <span data-ttu-id="10a7f-105">Au lieu de cela, vous souhaitez sélectionner les éléments en fonction de l'existence de l'attribut.</span><span class="sxs-lookup"><span data-stu-id="10a7f-105">Instead, you want to select based on the existence of the attribute.</span></span>  
  
 <span data-ttu-id="10a7f-106">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="10a7f-106">The XPath expression is:</span></span>  
  
 `./*[@Select]`  
  
## <a name="example"></a><span data-ttu-id="10a7f-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="10a7f-107">Example</span></span>  
 <span data-ttu-id="10a7f-108">Le code suivant sélectionne simplement les éléments qui ont l'attribut `Select`.</span><span class="sxs-lookup"><span data-stu-id="10a7f-108">The following code selects just the elements that have the `Select` attribute.</span></span>  
  
```csharp  
XElement doc = XElement.Parse(  
@"<Root>  
    <Child1>1</Child1>  
    <Child2 Select='true'>2</Child2>  
    <Child3>3</Child3>  
    <Child4 Select='true'>4</Child4>  
    <Child5>5</Child5>  
</Root>");  
  
// LINQ to XML query  
IEnumerable<XElement> list1 =  
    from el in doc.Elements()  
    where el.Attribute("Select") != null  
    select el;  
  
// XPath expression  
IEnumerable<XElement> list2 =  
    ((IEnumerable)doc.XPathEvaluate("./*[@Select]")).Cast<XElement>();  
  
if (list1.Count() == list2.Count() &&  
        list1.Intersect(list2).Count() == list1.Count())  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <span data-ttu-id="10a7f-109">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="10a7f-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
<Child2 Select="true">2</Child2>  
<Child4 Select="true">4</Child4>  
```  
  
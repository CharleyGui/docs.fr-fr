---
title: Comment rechercher des descendants d’un élément enfant (XPath-LINQ to XML) (C#)
description: Découvrez comment rechercher des éléments descendants d’un élément enfant avec un nom particulier à l’aide d’une expression XPath.
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: b8e110abc2e0df99c3fdf6d2846c7cbbc4736c1a
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303255"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="8cfb2-103">Comment rechercher des descendants d’un élément enfant (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="8cfb2-103">How to find descendants of a child element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="8cfb2-104">Cette rubrique montre comment obtenir les éléments descendants d'un élément enfant avec un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="8cfb2-104">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="8cfb2-105">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="8cfb2-105">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="8cfb2-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="8cfb2-106">Example</span></span>  
 <span data-ttu-id="8cfb2-107">Cet exemple simule les problèmes d'extraction de texte à partir d'une représentation XML d'un document de traitement de texte.</span><span class="sxs-lookup"><span data-stu-id="8cfb2-107">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="8cfb2-108">Il sélectionne tout d'abord tous les éléments `Paragraph`, puis il sélectionne tous les éléments descendants `Text` de chaque élément `Paragraph`.</span><span class="sxs-lookup"><span data-stu-id="8cfb2-108">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="8cfb2-109">Il ne sélectionne pas `Text`les éléments descendants de`Comment` l'élément.</span><span class="sxs-lookup"><span data-stu-id="8cfb2-109">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root>  
  <Paragraph>  
    <Text>This is the start of</Text>  
  </Paragraph>  
  <Comment>  
    <Text>This comment is not part of the paragraph text.</Text>  
  </Comment>  
  <Paragraph>  
    <Annotation Emphasis='true'>  
      <Text> a sentence.</Text>  
    </Annotation>  
  </Paragraph>  
  <Paragraph>  
    <Text>  This is a second sentence.</Text>  
  </Paragraph>  
</Root>");  
  
// LINQ to XML query  
string str1 =  
    root  
    .Elements("Paragraph")  
    .Descendants("Text")  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
// XPath expression  
string str2 =  
    ((IEnumerable)root.XPathEvaluate("./Paragraph//Text/text()"))  
    .Cast<XText>()  
    .Select(s => s.Value)  
    .Aggregate(  
        new StringBuilder(),  
        (s, i) => s.Append(i),  
        s => s.ToString()  
    );  
  
if (str1 == str2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(str2);  
```  
  
 <span data-ttu-id="8cfb2-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="8cfb2-110">This example produces the following output:</span></span>  
  
```output  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
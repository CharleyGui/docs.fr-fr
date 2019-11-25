---
title: Comment rechercher des descendants d’un élément enfant (XPath-LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: fb3e20ce21c1f6d2a71f2f71b8acec7cecf0f3ed
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141095"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="d8c3e-102">Comment rechercher des descendants d’un élément enfant (XPath-LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d8c3e-102">How to find descendants of a child element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="d8c3e-103">Cette rubrique montre comment obtenir les éléments descendants d'un élément enfant avec un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="d8c3e-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="d8c3e-104">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="d8c3e-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="d8c3e-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8c3e-105">Example</span></span>  
 <span data-ttu-id="d8c3e-106">Cet exemple simule les problèmes d'extraction de texte à partir d'une représentation XML d'un document de traitement de texte.</span><span class="sxs-lookup"><span data-stu-id="d8c3e-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="d8c3e-107">Il sélectionne tout d'abord tous les éléments `Paragraph`, puis il sélectionne tous les éléments descendants `Text` de chaque élément `Paragraph`.</span><span class="sxs-lookup"><span data-stu-id="d8c3e-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="d8c3e-108">Il ne sélectionne pas `Text`les éléments descendants de`Comment` l'élément.</span><span class="sxs-lookup"><span data-stu-id="d8c3e-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
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
  
 <span data-ttu-id="d8c3e-109">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d8c3e-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
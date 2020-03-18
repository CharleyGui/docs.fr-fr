---
title: Comment trouver les descendants d’un élément enfant (XPath-LINQ à XML) (C)
ms.date: 07/20/2015
ms.assetid: 505b7512-bb8b-4f85-abbf-491f039c961e
ms.openlocfilehash: fb3e20ce21c1f6d2a71f2f71b8acec7cecf0f3ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141095"
---
# <a name="how-to-find-descendants-of-a-child-element-xpath-linq-to-xml-c"></a><span data-ttu-id="0b33c-102">Comment trouver les descendants d’un élément enfant (XPath-LINQ à XML) (C)</span><span class="sxs-lookup"><span data-stu-id="0b33c-102">How to find descendants of a child element (XPath-LINQ to XML) (C#)</span></span>
<span data-ttu-id="0b33c-103">Cette rubrique montre comment obtenir les éléments descendants d'un élément enfant avec un nom particulier.</span><span class="sxs-lookup"><span data-stu-id="0b33c-103">This topic shows how to get the descendant elements of a child element with a particular name.</span></span>  
  
 <span data-ttu-id="0b33c-104">L’expression XPath est la suivante :</span><span class="sxs-lookup"><span data-stu-id="0b33c-104">The XPath expression is:</span></span>  
  
 `./Paragraph//Text/text()`  
  
## <a name="example"></a><span data-ttu-id="0b33c-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="0b33c-105">Example</span></span>  
 <span data-ttu-id="0b33c-106">Cet exemple simule les problèmes d'extraction de texte à partir d'une représentation XML d'un document de traitement de texte.</span><span class="sxs-lookup"><span data-stu-id="0b33c-106">This example simulates the problems of extracting text from an XML representation of a word processing document.</span></span> <span data-ttu-id="0b33c-107">Il sélectionne tout d'abord tous les éléments `Paragraph`, puis il sélectionne tous les éléments descendants `Text` de chaque élément `Paragraph`.</span><span class="sxs-lookup"><span data-stu-id="0b33c-107">It first selects all `Paragraph` elements, and then it selects all `Text` descendant elements of each `Paragraph` element.</span></span> <span data-ttu-id="0b33c-108">Il ne sélectionne pas `Text`les éléments descendants de`Comment` l'élément.</span><span class="sxs-lookup"><span data-stu-id="0b33c-108">This doesn't select the descendant `Text` elements of the `Comment` element.</span></span>  
  
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
  
 <span data-ttu-id="0b33c-109">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0b33c-109">This example produces the following output:</span></span>  
  
```output  
Results are identical  
This is the start of a sentence.  This is a second sentence.  
```  
  
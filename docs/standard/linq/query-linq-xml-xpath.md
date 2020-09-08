---
title: Comment interroger des LINQ to XML à l’aide de XPath-LINQ to XML
description: Découvrez les méthodes d’extension qui vous permettent d’interroger une arborescence XML à l’aide de XPath.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: 8189bcdd38f9242a5890837633bbec4e7f2fc601
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553712"
---
# <a name="how-to-query-linq-to-xml-using-xpath-linq-to-xml"></a><span data-ttu-id="f450a-103">Comment interroger des LINQ to XML à l’aide de XPath (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f450a-103">How to query LINQ to XML using XPath (LINQ to XML)</span></span>

<span data-ttu-id="f450a-104">Cet article présente les méthodes d’extension qui vous permettent d’interroger une arborescence XML à l’aide de XPath.</span><span class="sxs-lookup"><span data-stu-id="f450a-104">This article introduces the extension methods that enable you to query an XML tree by using XPath.</span></span> <span data-ttu-id="f450a-105">Pour plus d'informations sur l'utilisation de ces méthodes d'extension, consultez <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f450a-105">For detailed information about using these extension methods, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="f450a-106">À moins que vous n’ayez une raison très spécifique d’interroger à l’aide de XPath, par exemple l’utilisation intensive de code hérité, l’utilisation de XPath avec LINQ to XML n’est pas recommandée.</span><span class="sxs-lookup"><span data-stu-id="f450a-106">Unless you have a very specific reason for querying using XPath, such as extensive use of legacy code, using XPath with LINQ to XML isn't recommended.</span></span> <span data-ttu-id="f450a-107">Les requêtes XPath ne sont pas exécutées aussi bien que les requêtes LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="f450a-107">XPath queries won't perform as well as LINQ to XML queries.</span></span>

## <a name="example"></a><span data-ttu-id="f450a-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="f450a-108">Example</span></span>

<span data-ttu-id="f450a-109">L'exemple suivant crée une petite arborescence XML et utilise <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> pour sélectionner un ensemble d'éléments.</span><span class="sxs-lookup"><span data-stu-id="f450a-109">The following example creates a small XML tree and uses <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> to select a set of elements.</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("Child1", 1),
    new XElement("Child1", 2),
    new XElement("Child1", 3),
    new XElement("Child2", 4),
    new XElement("Child2", 5),
    new XElement("Child2", 6)
);
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");
foreach (XElement el in list)
    Console.WriteLine(el);
```

```vb
Dim root As XElement = _
    <Root>
        <Child1>1</Child1>
        <Child1>2</Child1>
        <Child1>3</Child1>
        <Child2>4</Child2>
        <Child2>5</Child2>
        <Child2>6</Child2>
    </Root>

Dim list As IEnumerable(Of XElement) = root.XPathSelectElements("./Child2")
For Each el As XElement In list
    Console.WriteLine(el)
Next
```

<span data-ttu-id="f450a-110">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f450a-110">This example produces the following output:</span></span>

```xml
<Child2>4</Child2>
<Child2>5</Child2>
<Child2>6</Child2>
```

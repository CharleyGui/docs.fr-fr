---
title: Comment analyser une chaîne (C)
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: 79821eb9e5cd7187ac3c2a93f85eaae45c5c48ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345809"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="53de5-102">Comment analyser une chaîne (C)</span><span class="sxs-lookup"><span data-stu-id="53de5-102">How to parse a string (C#)</span></span>

<span data-ttu-id="53de5-103">Cette rubrique montre comment analyser une chaîne pour créer une arborescence XML en C#.</span><span class="sxs-lookup"><span data-stu-id="53de5-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>

## <a name="example"></a><span data-ttu-id="53de5-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="53de5-104">Example</span></span>

<span data-ttu-id="53de5-105">Le code Cmd suivant montre comment analyser une chaîne XML :</span><span class="sxs-lookup"><span data-stu-id="53de5-105">The following C# code shows how to parse an XML string:</span></span>

```csharp
XElement contacts = XElement.Parse(
    @"<Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type=""home"">206-555-0144</Phone>
            <Phone Type=""work"">425-555-0145</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>10</NetWorth>
        </Contact>
        <Contact>
            <Name>Gretchen Rivas</Name>
            <Phone Type=""mobile"">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>");
Console.WriteLine(contacts);
```

<span data-ttu-id="53de5-106">Le `Contacts` nœud `Contact` de racine a deux nœuds.</span><span class="sxs-lookup"><span data-stu-id="53de5-106">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="53de5-107">Pour accéder à certaines données spécifiques dans votre XML analysé, utilisez la méthode [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) qui, dans ce cas, renvoie les éléments de l’enfant du nœud de racine. `Contacts`</span><span class="sxs-lookup"><span data-stu-id="53de5-107">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="53de5-108">L’exemple suivant imprime le premier `Contact` nœud à la console :</span><span class="sxs-lookup"><span data-stu-id="53de5-108">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a><span data-ttu-id="53de5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53de5-109">See also</span></span>

- [<span data-ttu-id="53de5-110">Comment trouver un élément avec un attribut spécifique (C)</span><span class="sxs-lookup"><span data-stu-id="53de5-110">How to find an element with a specific attribute (C#)</span></span>](how-to-find-an-element-with-a-specific-attribute.md)

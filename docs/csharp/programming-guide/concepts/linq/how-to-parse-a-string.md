---
title: Comment analyser une chaîne (C#)
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: 79821eb9e5cd7187ac3c2a93f85eaae45c5c48ac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345809"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="d8d95-102">Comment analyser une chaîne (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d95-102">How to parse a string (C#)</span></span>

<span data-ttu-id="d8d95-103">Cette rubrique montre comment analyser une chaîne pour créer une arborescence XML en C#.</span><span class="sxs-lookup"><span data-stu-id="d8d95-103">This topic shows how to parse a string to create an XML tree in C#.</span></span>

## <a name="example"></a><span data-ttu-id="d8d95-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8d95-104">Example</span></span>

<span data-ttu-id="d8d95-105">Le code C# suivant montre comment analyser une chaîne XML :</span><span class="sxs-lookup"><span data-stu-id="d8d95-105">The following C# code shows how to parse an XML string:</span></span>

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

<span data-ttu-id="d8d95-106">Le nœud de `Contacts` racine a deux nœuds `Contact`.</span><span class="sxs-lookup"><span data-stu-id="d8d95-106">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="d8d95-107">Pour accéder à des données spécifiques dans votre code XML analysé, utilisez la méthode [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) , qui, dans ce cas, retourne les éléments enfants du nœud de `Contacts` racine.</span><span class="sxs-lookup"><span data-stu-id="d8d95-107">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="d8d95-108">L’exemple suivant imprime le premier nœud `Contact` sur la console :</span><span class="sxs-lookup"><span data-stu-id="d8d95-108">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a><span data-ttu-id="d8d95-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8d95-109">See also</span></span>

- [<span data-ttu-id="d8d95-110">Comment rechercher un élément avec un attribut spécifique (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d95-110">How to find an element with a specific attribute (C#)</span></span>](how-to-find-an-element-with-a-specific-attribute.md)

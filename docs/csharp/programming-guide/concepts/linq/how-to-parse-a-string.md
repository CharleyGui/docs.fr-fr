---
title: Comment analyser une chaîne (C#)
description: Découvrez comment analyser une chaîne pour créer une arborescence XML en C#. Découvrez comment accéder à des données spécifiques dans votre code XML analysé.
ms.date: 07/20/2015
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: a4664e090b6a44c52c519e61b66ccdc5d59a71f1
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104812"
---
# <a name="how-to-parse-a-string-c"></a><span data-ttu-id="68ec3-104">Comment analyser une chaîne (C#)</span><span class="sxs-lookup"><span data-stu-id="68ec3-104">How to parse a string (C#)</span></span>

<span data-ttu-id="68ec3-105">Cette rubrique montre comment analyser une chaîne pour créer une arborescence XML en C#.</span><span class="sxs-lookup"><span data-stu-id="68ec3-105">This topic shows how to parse a string to create an XML tree in C#.</span></span>

## <a name="example"></a><span data-ttu-id="68ec3-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="68ec3-106">Example</span></span>

<span data-ttu-id="68ec3-107">Le code C# suivant montre comment analyser une chaîne XML :</span><span class="sxs-lookup"><span data-stu-id="68ec3-107">The following C# code shows how to parse an XML string:</span></span>

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

<span data-ttu-id="68ec3-108">Le `Contacts` nœud racine a deux `Contact` nœuds.</span><span class="sxs-lookup"><span data-stu-id="68ec3-108">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="68ec3-109">Pour accéder à des données spécifiques dans votre code XML analysé, utilisez la méthode [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) , qui, dans ce cas, retourne les éléments enfants du `Contacts` nœud racine.</span><span class="sxs-lookup"><span data-stu-id="68ec3-109">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="68ec3-110">L’exemple suivant imprime le premier `Contact` nœud sur la console :</span><span class="sxs-lookup"><span data-stu-id="68ec3-110">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

## <a name="see-also"></a><span data-ttu-id="68ec3-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68ec3-111">See also</span></span>

- [<span data-ttu-id="68ec3-112">Comment rechercher un élément avec un attribut spécifique (C#)</span><span class="sxs-lookup"><span data-stu-id="68ec3-112">How to find an element with a specific attribute (C#)</span></span>](how-to-find-an-element-with-a-specific-attribute.md)

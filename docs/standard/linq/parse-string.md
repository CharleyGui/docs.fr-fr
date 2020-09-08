---
title: Comment analyser un LINQ to XML de chaîne
description: Vous pouvez analyser une chaîne avec XElement. Parse pour créer une arborescence XML en C# et en Visual Basic, et vous pouvez créer une arborescence XML avec des littéraux XML dans Visual Basic.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 81e5686c-9658-42d8-a7e3-b11be0a2c98b
ms.openlocfilehash: f4bd22acbf3b11d801c791cc591d882810450fd4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552489"
---
# <a name="how-to-parse-a-string-linq-to-xml"></a><span data-ttu-id="82faa-103">Comment analyser une chaîne (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="82faa-103">How to parse a string (LINQ to XML)</span></span>

<span data-ttu-id="82faa-104">Cet article montre comment analyser une chaîne pour créer une arborescence XML en C# et dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="82faa-104">This article shows how to parse a string to create an XML tree in C# and in Visual Basic.</span></span>

## <a name="example"></a><span data-ttu-id="82faa-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="82faa-105">Example</span></span>

<span data-ttu-id="82faa-106">Le code C# suivant montre comment analyser une chaîne XML :</span><span class="sxs-lookup"><span data-stu-id="82faa-106">The following C# code shows how to parse an XML string:</span></span>

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

<span data-ttu-id="82faa-107">Vous pouvez analyser une chaîne dans Visual Basic de la même manière.</span><span class="sxs-lookup"><span data-stu-id="82faa-107">You can parse a string in Visual Basic in a similar manner.</span></span> <span data-ttu-id="82faa-108">Toutefois, il est plus efficace d’utiliser des littéraux XML, comme indiqué dans le code suivant, parce que les littéraux XML ne sont pas affectés par les mêmes pénalités de performances que l’analyse de code XML à partir d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="82faa-108">However, it's more efficient to use XML literals, as shown in following code, because XML literals don't suffer from the same performance penalties as parsing XML from a string.</span></span>

<span data-ttu-id="82faa-109">En utilisant des littéraux XML, vous pouvez simplement copier et coller votre code XML dans votre programme Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="82faa-109">By using XML literals, you can just copy and paste your XML into your Visual Basic program.</span></span>

> [!NOTE]
> <span data-ttu-id="82faa-110">L'analyse de texte ou le chargement d'un document XML à partir d'un fichier texte est moins efficace que la construction fonctionnelle.</span><span class="sxs-lookup"><span data-stu-id="82faa-110">Parsing text or loading an XML document from a text file is less efficient than functional construction.</span></span> <span data-ttu-id="82faa-111">Si vous initialisez une arborescence XML à partir du code, il faut moins de temps processeur pour utiliser la construction fonctionnelle que pour analyser le texte.</span><span class="sxs-lookup"><span data-stu-id="82faa-111">If you're initializing an XML tree from code, it takes less processor time to use functional construction than to parse text.</span></span>

```vb
Dim contacts as XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone Type="home">206-555-0144</Phone>
            <Phone Type="work">425-555-0145</Phone>
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
            <Phone Type="mobile">206-555-0163</Phone>
            <Address>
            <Street1>123 Main St</Street1>
            <City>Mercer Island</City>
            <State>WA</State>
            <Postal>68042</Postal>
            </Address>
            <NetWorth>11</NetWorth>
        </Contact>
    </Contacts>
```

<span data-ttu-id="82faa-112">Le `Contacts` nœud racine a deux `Contact` nœuds.</span><span class="sxs-lookup"><span data-stu-id="82faa-112">The root `Contacts` node has two `Contact` nodes.</span></span> <span data-ttu-id="82faa-113">Pour accéder à des données spécifiques dans votre code XML analysé, utilisez la méthode [XElement. Elements ()](xref:System.Xml.Linq.XContainer.Elements) , qui, dans ce cas, retourne les éléments enfants du `Contacts` nœud racine.</span><span class="sxs-lookup"><span data-stu-id="82faa-113">To access some specific data in your parsed XML, use the [XElement.Elements()](xref:System.Xml.Linq.XContainer.Elements) method, which in this case returns the child elements of the root `Contacts` node.</span></span> <span data-ttu-id="82faa-114">L’exemple suivant imprime le premier `Contact` nœud sur la console :</span><span class="sxs-lookup"><span data-stu-id="82faa-114">The following example prints the first `Contact` node to the console:</span></span>

```csharp
List<XElement> contactNodes = contacts.Elements("Contact").ToList();
Console.WriteLine(contactNodes[0]);
```

```vb
Dim contactNodes As List(Of XElement) = contacts.Elements("Contact").ToList()
Console.WriteLine(contactNodes(0))
```

## <a name="see-also"></a><span data-ttu-id="82faa-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82faa-115">See also</span></span>

- [<span data-ttu-id="82faa-116">Guide pratique pour rechercher un élément avec un attribut spécifique</span><span class="sxs-lookup"><span data-stu-id="82faa-116">How to find an element with a specific attribute</span></span>](find-element-specific-attribute.md)

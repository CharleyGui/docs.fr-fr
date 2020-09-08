---
title: Portée des espaces de noms par défaut-LINQ to XML
description: Les espaces de noms par défaut tels qu’ils sont représentés dans l’arborescence XML ne sont pas dans la portée des requêtes. Voici des méthodes correctes et incorrectes pour les interroger.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: fe826236-830f-457a-9027-7ad62c909fae
ms.openlocfilehash: 105309a70e5fbf48c4e595d4064b11fe0378f81e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553827"
---
# <a name="scope-of-default-namespaces-linq-to-xml"></a><span data-ttu-id="047a8-104">Portée des espaces de noms par défaut (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="047a8-104">Scope of default namespaces (LINQ to XML)</span></span>

<span data-ttu-id="047a8-105">Les espaces de noms par défaut tels qu’ils sont représentés dans l’arborescence XML ne sont pas dans la portée des requêtes.</span><span class="sxs-lookup"><span data-stu-id="047a8-105">Default namespaces as represented in the XML tree aren't in scope for queries.</span></span> <span data-ttu-id="047a8-106">Si vous avez du code XML qui se trouve dans un espace de noms par défaut, vous devez combiner un espace de noms avec le nom local pour faire en sorte qu’un nom qualifié soit utilisé dans la requête.</span><span class="sxs-lookup"><span data-stu-id="047a8-106">If you have XML that's in a default namespace, you must combine a namespace with the local name to make a qualified name to be used in the query.</span></span>

<span data-ttu-id="047a8-107">Une erreur courante lors de l’interrogation d’une arborescence XML avec un espace de noms par défaut consiste à écrire la requête comme si le XML ne se trouve pas dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="047a8-107">A common mistake in querying an XML tree that has a default namespace is to write the query as if the XML weren't in a namespace.</span></span> <span data-ttu-id="047a8-108">Le premier exemple montre une requête incorrecte standard d’un espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="047a8-108">The first example shows a typical improper query of a default namespace.</span></span> <span data-ttu-id="047a8-109">Le deuxième affiche une requête appropriée.</span><span class="sxs-lookup"><span data-stu-id="047a8-109">The second shows a proper query.</span></span>

## <a name="example-improper-query-of-xml-in-a-namespace"></a><span data-ttu-id="047a8-110">Exemple : requête incorrecte de code XML dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="047a8-110">Example: Improper query of XML in a namespace</span></span>

<span data-ttu-id="047a8-111">Cet exemple illustre la création de code XML dans un espace de noms et une requête incorrecte qui retourne un jeu de résultats vide.</span><span class="sxs-lookup"><span data-stu-id="047a8-111">This example shows the creation of XML in a namespace, and an improper query that returns an empty result set.</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
IEnumerable<XElement> c1 =
    from el in root.Elements("Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="047a8-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="047a8-112">This example produces the following output:</span></span>

```output
Result set follows:
End of result set
```

## <a name="example--proper-query-of-xml-in-a-namespace"></a><span data-ttu-id="047a8-113">Exemple : interrogation correcte du code XML dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="047a8-113">Example:  Proper query of XML in a namespace</span></span>

<span data-ttu-id="047a8-114">Cet exemple illustre la création de code XML dans un espace de noms et une requête appropriée.</span><span class="sxs-lookup"><span data-stu-id="047a8-114">This example shows the creation of XML in a namespace, and a proper query.</span></span>

<span data-ttu-id="047a8-115">En C#, l’approche correcte consiste à déclarer et à initialiser un <xref:System.Xml.Linq.XNamespace> objet et à l’utiliser lors de la spécification d' <xref:System.Xml.Linq.XName> objets.</span><span class="sxs-lookup"><span data-stu-id="047a8-115">In C#, the correct approach is to declare and initialize an <xref:System.Xml.Linq.XNamespace> object, and to use it when specifying <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="047a8-116">Dans ce cas, l'argument de la méthode <xref:System.Xml.Linq.XContainer.Elements%2A> est un objet <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="047a8-116">In this case, the argument to the <xref:System.Xml.Linq.XContainer.Elements%2A> method is an <xref:System.Xml.Linq.XName> object.</span></span>

<span data-ttu-id="047a8-117">L'approche correcte lors de l'utilisation de Visual Basic consiste à déclarer et à initialiser un espace de noms global par défaut.</span><span class="sxs-lookup"><span data-stu-id="047a8-117">The correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="047a8-118">Cela place toutes les propriétés XML dans l'espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="047a8-118">This places all XML properties in the default namespace.</span></span>

<span data-ttu-id="047a8-119">Voici le code :</span><span class="sxs-lookup"><span data-stu-id="047a8-119">Here is the code:</span></span>

```csharp
XElement root = XElement.Parse(
@"<Root xmlns='http://www.adventure-works.com'>
    <Child>1</Child>
    <Child>2</Child>
    <Child>3</Child>
    <AnotherChild>4</AnotherChild>
    <AnotherChild>5</AnotherChild>
    <AnotherChild>6</AnotherChild>
</Root>");
XNamespace aw = "http://www.adventure-works.com";
IEnumerable<XElement> c1 =
    from el in root.Elements(aw + "Child")
    select el;
Console.WriteLine("Result set follows:");
foreach (XElement el in c1)
    Console.WriteLine((int)el);
Console.WriteLine("End of result set");
```

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root xmlns='http://www.adventure-works.com'>
                <Child>1</Child>
                <Child>2</Child>
                <Child>3</Child>
                <AnotherChild>4</AnotherChild>
                <AnotherChild>5</AnotherChild>
                <AnotherChild>6</AnotherChild>
            </Root>
        Dim c1 As IEnumerable(Of XElement) = _
                From el In root.<Child> _
                Select el
        Console.WriteLine("Result set follows:")
        For Each el As XElement In c1
            Console.WriteLine(el.Value)
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="047a8-120">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="047a8-120">This example produces the following output:</span></span>

```output
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="047a8-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="047a8-121">See also</span></span>

- [<span data-ttu-id="047a8-122">Vue d’ensemble des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="047a8-122">Namespaces overview</span></span>](namespaces-overview.md)

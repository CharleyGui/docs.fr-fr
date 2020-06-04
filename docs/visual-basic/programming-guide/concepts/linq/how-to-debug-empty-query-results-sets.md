---
title: 'Procédure : déboguer des ensembles de résultats de requête vides'
ms.date: 07/20/2015
ms.assetid: b242c90a-d2b8-4309-8a1e-e4e70736c727
ms.openlocfilehash: b2059ccd4638d2fb77c524773cb4bd50f721b5b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398036"
---
# <a name="how-to-debug-empty-query-results-sets-visual-basic"></a><span data-ttu-id="74fb8-102">Procédure : déboguer des ensembles de résultats de requête vides (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74fb8-102">How to: Debug Empty Query Results Sets (Visual Basic)</span></span>

<span data-ttu-id="74fb8-103">L'un des problèmes les plus courants lors de l'interrogation d'une arborescence XML est que si celle-ci possède un espace de noms par défaut, le développeur écrit parfois la requête comme si le code XML n'était dans aucun espace de noms.</span><span class="sxs-lookup"><span data-stu-id="74fb8-103">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>

<span data-ttu-id="74fb8-104">Le premier ensemble d'exemples dans cette rubrique illustre le chargement de code XML dans un espace de noms par défaut et son interrogation incorrecte.</span><span class="sxs-lookup"><span data-stu-id="74fb8-104">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, and is queried improperly.</span></span>

<span data-ttu-id="74fb8-105">Le deuxième ensemble d'exemples illustre les corrections que vous devez apporter pour pouvoir interroger du code XML dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="74fb8-105">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>

<span data-ttu-id="74fb8-106">Pour plus d’informations, consultez [vue d’ensemble des espaces de noms (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="74fb8-106">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>

## <a name="example"></a><span data-ttu-id="74fb8-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="74fb8-107">Example</span></span>

<span data-ttu-id="74fb8-108">Cet exemple illustre la création de code XML dans un espace de noms et une requête qui retourne un jeu de résultats vide.</span><span class="sxs-lookup"><span data-stu-id="74fb8-108">This example shows creation of XML in a namespace, and a query that returns an empty result set.</span></span>

```vb
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
```

<span data-ttu-id="74fb8-109">Cet exemple génère le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="74fb8-109">This example produces the following result:</span></span>

```console
Result set follows:
End of result set
```

## <a name="example"></a><span data-ttu-id="74fb8-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="74fb8-110">Example</span></span>

<span data-ttu-id="74fb8-111">Cet exemple illustre la création de code XML dans un espace de noms et une requête codée correctement.</span><span class="sxs-lookup"><span data-stu-id="74fb8-111">This example shows creation of XML in a namespace, and a query that is coded properly.</span></span>

<span data-ttu-id="74fb8-112">La solution consiste à déclarer et à initialiser un espace de noms global par défaut.</span><span class="sxs-lookup"><span data-stu-id="74fb8-112">The solution is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="74fb8-113">Cela place toutes les propriétés XML dans l'espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="74fb8-113">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="74fb8-114">Aucune autre modification n'est nécessaire pour que l'exemple fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="74fb8-114">No other modifications are required to the example to make it work properly.</span></span>

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
            Console.WriteLine(CInt(el))
        Next
        Console.WriteLine("End of result set")
    End Sub
End Module
```

<span data-ttu-id="74fb8-115">Cet exemple génère le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="74fb8-115">This example produces the following result:</span></span>

```console
Result set follows:
1
2
3
End of result set
```

## <a name="see-also"></a><span data-ttu-id="74fb8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74fb8-116">See also</span></span>

- [<span data-ttu-id="74fb8-117">Requêtes de base (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="74fb8-117">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](basic-queries-linq-to-xml.md)

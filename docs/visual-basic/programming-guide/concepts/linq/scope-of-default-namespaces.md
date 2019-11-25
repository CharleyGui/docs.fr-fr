---
title: Étendue des espaces de noms par défaut
ms.date: 07/20/2015
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
ms.openlocfilehash: 8ba4d13b6d40180a88651f0503d1323f2b78f36c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343644"
---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="8286e-102">Scope of Default Namespaces in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8286e-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="8286e-103">Les espaces de noms tels que représentés dans l'arborescence XML par défaut ne sont pas dans la portée pour les requêtes.</span><span class="sxs-lookup"><span data-stu-id="8286e-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="8286e-104">Si vous avez du code XML qui est dans un espace de noms par défaut, vous devez déclarer une variable <xref:System.Xml.Linq.XNamespace> et la combiner avec le nom local afin de créer un nom complet utilisable dans la requête.</span><span class="sxs-lookup"><span data-stu-id="8286e-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="8286e-105">L'un des problèmes les plus courants lors de l'interrogation d'une arborescence XML est que si celle-ci possède un espace de noms par défaut, le développeur écrit parfois la requête comme si le code XML n'était dans aucun espace de noms.</span><span class="sxs-lookup"><span data-stu-id="8286e-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="8286e-106">Le premier ensemble d'exemples de cette rubrique illustre le chargement de code XML dans un espace de noms par défaut, mais son interrogation est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="8286e-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="8286e-107">Le deuxième ensemble d'exemples illustre les corrections que vous devez apporter pour pouvoir interroger du code XML dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="8286e-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8286e-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="8286e-108">Example</span></span>  
 <span data-ttu-id="8286e-109">Cet exemple illustre la création de code XML dans un espace de noms et une requête qui retourne un jeu de résultats vide.</span><span class="sxs-lookup"><span data-stu-id="8286e-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8286e-110">Code</span><span class="sxs-lookup"><span data-stu-id="8286e-110">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="8286e-111">Comments</span><span class="sxs-lookup"><span data-stu-id="8286e-111">Comments</span></span>  
 <span data-ttu-id="8286e-112">Cet exemple génère le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="8286e-112">This example produces the following result:</span></span>  
  
```console  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="8286e-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="8286e-113">Example</span></span>  
 <span data-ttu-id="8286e-114">Cet exemple illustre la création de code XML dans un espace de noms et une requête codée correctement.</span><span class="sxs-lookup"><span data-stu-id="8286e-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="8286e-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span><span class="sxs-lookup"><span data-stu-id="8286e-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="8286e-116">Cela place toutes les propriétés XML dans l'espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="8286e-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="8286e-117">Aucune autre modification n'est nécessaire pour que l'exemple fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="8286e-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="8286e-118">Code</span><span class="sxs-lookup"><span data-stu-id="8286e-118">Code</span></span>  
  
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
  
### <a name="comments"></a><span data-ttu-id="8286e-119">Comments</span><span class="sxs-lookup"><span data-stu-id="8286e-119">Comments</span></span>  
 <span data-ttu-id="8286e-120">Cet exemple génère le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="8286e-120">This example produces the following result:</span></span>  
  
```console  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="8286e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8286e-121">See also</span></span>

- [<span data-ttu-id="8286e-122">Namespaces Overview (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8286e-122">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)

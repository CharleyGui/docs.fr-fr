---
title: Comment créer un document avec des espaces de noms dans Visual Basic LINQ to XML
description: Utilisez des littéraux XML dans Visual Basic pour créer des documents qui ont des espaces de noms ou des espaces de noms par défaut avec un préfixe.
ms.date: 07/20/2015
ms.assetid: cc5b0d4d-360c-4ada-94fa-2d2916e989be
ms.openlocfilehash: 48e2a1abf8f7a82df3db5cb2f580804d67776b15
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553508"
---
# <a name="how-to-create-a-document-with-namespaces-in-visual-basic-linq-to-xml"></a><span data-ttu-id="8b711-103">Comment créer un document avec des espaces de noms dans Visual Basic (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="8b711-103">How to create a document with namespaces in Visual Basic (LINQ to XML)</span></span>

<span data-ttu-id="8b711-104">Cet article explique comment créer un document avec des espaces de noms dans Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8b711-104">This article shows how to create a document with namespaces in Visual Basic.</span></span>

<span data-ttu-id="8b711-105">Lorsque vous utilisez des littéraux XML en Visual Basic, les utilisateurs peuvent définir un espace de noms XML global par défaut.</span><span class="sxs-lookup"><span data-stu-id="8b711-105">When using XML literals in Visual Basic, users can define one global default XML namespace.</span></span> <span data-ttu-id="8b711-106">Cet espace de noms est l'espace de noms par défaut pour les littéraux XML et les propriétés XML.</span><span class="sxs-lookup"><span data-stu-id="8b711-106">This namespace is the default namespace for both XML literals and XML properties.</span></span> <span data-ttu-id="8b711-107">L'espace de noms XML par défaut peut être défini au niveau projet ou au niveau fichier.</span><span class="sxs-lookup"><span data-stu-id="8b711-107">The default XML namespace can be defined at either the project level or the file level.</span></span> <span data-ttu-id="8b711-108">S’il est défini au niveau du fichier, il se substitue à l’espace de noms par défaut au niveau du projet.</span><span class="sxs-lookup"><span data-stu-id="8b711-108">If it's defined at the file level, it overrides the default namespace at the project level.</span></span>

<span data-ttu-id="8b711-109">Vous pouvez également définir d'autres espaces de noms et spécifier les préfixes d'espaces de noms de ces espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="8b711-109">You can also define other namespaces, and specify the namespace prefixes for those namespaces.</span></span> <span data-ttu-id="8b711-110">Vous utilisez le `Imports` mot clé pour définir les deux types d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="8b711-110">You use the `Imports` keyword to define both types of namespace.</span></span>

<span data-ttu-id="8b711-111">Pour plus d’informations, consultez [littéraux XML dans Visual Basic](xml-literals.md).</span><span class="sxs-lookup"><span data-stu-id="8b711-111">For more information, see [XML literals in Visual Basic](xml-literals.md).</span></span>

<span data-ttu-id="8b711-112">Notez que l'espace de noms XML par défaut s'applique uniquement aux éléments, et non aux attributs.</span><span class="sxs-lookup"><span data-stu-id="8b711-112">Note that the default XML namespace only applies to elements and not to attributes.</span></span> <span data-ttu-id="8b711-113">Les attributs sont par défaut dans l’espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="8b711-113">Attributes are by default in the default namespace.</span></span> <span data-ttu-id="8b711-114">Toutefois, vous pouvez utiliser un préfixe d'espace de noms pour placer un attribut dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="8b711-114">However, you can use a namespace prefix to put an attribute in a namespace.</span></span>

## <a name="example-create-a-document-that-has-a-namespace"></a><span data-ttu-id="8b711-115">Exemple : créer un document avec un espace de noms</span><span class="sxs-lookup"><span data-stu-id="8b711-115">Example: Create a document that has a namespace</span></span>

<span data-ttu-id="8b711-116">Cet exemple crée un document qui contient un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="8b711-116">This example creates a document that contains a namespace.</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child aw:Att="attvalue"/>
            </aw:Root>
        Console.WriteLine(root)
    End Sub
End Module
```

<span data-ttu-id="8b711-117">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="8b711-117">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child aw:Att="attvalue" />
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a><span data-ttu-id="8b711-118">Exemple : créer un document qui a deux espaces de noms, un avec un préfixe</span><span class="sxs-lookup"><span data-stu-id="8b711-118">Example: Create a document that has two namespaces, one with a prefix</span></span>

<span data-ttu-id="8b711-119">Cet exemple crée un document qui contient deux espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="8b711-119">This example creates a document that contains two namespaces.</span></span> <span data-ttu-id="8b711-120">L’un est l’espace de noms par défaut, l’autre le préfixe.</span><span class="sxs-lookup"><span data-stu-id="8b711-120">One is the default namespace, the other has a prefix.</span></span>

```vb
Imports <xmlns="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child Att="attvalue"/>
                <fc:Child2>child2 content</fc:Child2>
            </Root>
        Console.WriteLine(root)
    End Sub

End Module
```

<span data-ttu-id="8b711-121">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="8b711-121">This example produces the following output:</span></span>

```xml
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">
  <Child Att="attvalue" />
  <fc:Child2>child2 content</fc:Child2>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a><span data-ttu-id="8b711-122">Exemple : créer un document qui a deux espaces de noms, tous deux avec des préfixes</span><span class="sxs-lookup"><span data-stu-id="8b711-122">Example: Create a document that has two namespaces, both with prefixes</span></span>

<span data-ttu-id="8b711-123">L’exemple suivant crée un document qui contient deux espaces de noms, tous deux avec des préfixes d’espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="8b711-123">The following example creates a document that contains two namespaces, both having namespace prefixes.</span></span>

<span data-ttu-id="8b711-124">Lors de la sérialisation d’une arborescence XML, LINQ to XML émet des déclarations d’espaces de noms selon les besoins afin que chaque élément soit dans son espace de noms désigné.</span><span class="sxs-lookup"><span data-stu-id="8b711-124">When serializing an XML tree, LINQ to XML emits namespace declarations as required so that each element is in its designated namespace.</span></span>

```vb
Imports <xmlns:aw="http://www.adventure-works.com">
Imports <xmlns:fc="www.fourthcoffee.com">

Module Module1

    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <fc:Child>
                    <aw:DifferentChild>other content</aw:DifferentChild>
                </fc:Child>
                <aw:Child2>c2 content</aw:Child2>
                <fc:Child3>c3 content</fc:Child3>
            </aw:Root>
        Console.WriteLine(root)
    End Sub

End Module
```

<span data-ttu-id="8b711-125">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="8b711-125">This example produces the following output:</span></span>

```xml
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a><span data-ttu-id="8b711-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b711-126">See also</span></span>

- [<span data-ttu-id="8b711-127">Vue d’ensemble des espaces de noms</span><span class="sxs-lookup"><span data-stu-id="8b711-127">Namespaces overview</span></span>](namespaces-overview.md)

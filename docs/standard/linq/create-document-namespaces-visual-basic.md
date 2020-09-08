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
# <a name="how-to-create-a-document-with-namespaces-in-visual-basic-linq-to-xml"></a>Comment créer un document avec des espaces de noms dans Visual Basic (LINQ to XML)

Cet article explique comment créer un document avec des espaces de noms dans Visual Basic.

Lorsque vous utilisez des littéraux XML en Visual Basic, les utilisateurs peuvent définir un espace de noms XML global par défaut. Cet espace de noms est l'espace de noms par défaut pour les littéraux XML et les propriétés XML. L'espace de noms XML par défaut peut être défini au niveau projet ou au niveau fichier. S’il est défini au niveau du fichier, il se substitue à l’espace de noms par défaut au niveau du projet.

Vous pouvez également définir d'autres espaces de noms et spécifier les préfixes d'espaces de noms de ces espaces de noms. Vous utilisez le `Imports` mot clé pour définir les deux types d’espace de noms.

Pour plus d’informations, consultez [littéraux XML dans Visual Basic](xml-literals.md).

Notez que l'espace de noms XML par défaut s'applique uniquement aux éléments, et non aux attributs. Les attributs sont par défaut dans l’espace de noms par défaut. Toutefois, vous pouvez utiliser un préfixe d'espace de noms pour placer un attribut dans un espace de noms.

## <a name="example-create-a-document-that-has-a-namespace"></a>Exemple : créer un document avec un espace de noms

Cet exemple crée un document qui contient un espace de noms.

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

Cet exemple produit la sortie suivante :

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com">
  <aw:Child aw:Att="attvalue" />
</aw:Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-one-with-a-prefix"></a>Exemple : créer un document qui a deux espaces de noms, un avec un préfixe

Cet exemple crée un document qui contient deux espaces de noms. L’un est l’espace de noms par défaut, l’autre le préfixe.

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

Cet exemple produit la sortie suivante :

```xml
<Root xmlns:fc="www.fourthcoffee.com" xmlns="http://www.adventure-works.com">
  <Child Att="attvalue" />
  <fc:Child2>child2 content</fc:Child2>
</Root>
```

## <a name="example-create-a-document-that-has-two-namespaces-both-with-prefixes"></a>Exemple : créer un document qui a deux espaces de noms, tous deux avec des préfixes

L’exemple suivant crée un document qui contient deux espaces de noms, tous deux avec des préfixes d’espaces de noms.

Lors de la sérialisation d’une arborescence XML, LINQ to XML émet des déclarations d’espaces de noms selon les besoins afin que chaque élément soit dans son espace de noms désigné.

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

Cet exemple produit la sortie suivante :

```xml
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">
  <fc:Child>
    <aw:DifferentChild>other content</aw:DifferentChild>
  </fc:Child>
  <aw:Child2>c2 content</aw:Child2>
  <fc:Child3>c3 content</fc:Child3>
</aw:Root>
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des espaces de noms](namespaces-overview.md)

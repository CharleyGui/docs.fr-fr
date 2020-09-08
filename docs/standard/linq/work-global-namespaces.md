---
title: Utiliser des espaces de noms globaux dans Visual Basic LINQ to XML
description: Vous déclarez un espace de noms dans Visual Basic à l’aide de l’instruction Imports, que l’espace de noms soit un espace de noms par défaut ou un préfixe. Cet article traite des instructions d’importation et d’autres aspects de l’utilisation des espaces de noms.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: f05fcab6788388e36e2b68a2d4f022ea63e74280
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553821"
---
# <a name="work-with-global-namespaces-in-visual-basic-linq-to-xml"></a>Utiliser des espaces de noms globaux dans Visual Basic (LINQ to XML)

L’une des principales fonctionnalités des littéraux XML dans Visual Basic est la possibilité de déclarer des espaces de noms XML à l’aide de l' `Imports` instruction. Grâce à cette fonctionnalité, vous pouvez déclarer un espace de noms XML qui utilise un préfixe ou déclarer un espace de noms XML par défaut.

Cette fonctionnalité est utile dans deux situations :

- Les espaces de noms déclarés dans les littéraux XML ne sont pas reportés dans les expressions incorporées. La déclaration d’espaces de noms globaux réduit la quantité de travail nécessaire à l’utilisation d’expressions incorporées avec des espaces de noms.
- Vous devez déclarer des espaces de noms globaux afin d’utiliser des espaces de noms avec des propriétés XML.

Vous pouvez déclarer des espaces de noms globaux au niveau du projet. Vous pouvez également déclarer des espaces de noms globaux au niveau du module, ce qui substitue les espaces de noms globaux au niveau du projet. Pour finir, vous pouvez substituer des espaces de noms globaux dans un littéral XML.

Lorsque vous utilisez des littéraux XML ou des propriétés XML qui se trouvent dans des espaces de noms déclarés globalement, vous pouvez afficher le nom développé des littéraux ou des propriétés XML en pointant dessus dans Visual Studio. Le nom développé s’affiche alors dans une info-bulle.

Vous pouvez obtenir un objet <xref:System.Xml.Linq.XNamespace> qui correspond à un espace de noms global à l'aide de la méthode `GetXmlNamespace`.

## <a name="example-use-imports-to-declare-a-global-namespace"></a>Exemple : utilisation `Imports` pour déclarer un espace de noms global

L’exemple suivant déclare un espace de noms global par défaut avec l' `Imports` instruction, puis initialise un <xref:System.Xml.Linq.XElement> objet dans cet espace de noms avec un littéral XML :

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```xml
<Root xmlns="http://www.adventure-works.com" />
```

## <a name="example-declare-a-global-namespace-that-has-a-prefix"></a>Exemple : déclarer un espace de noms global qui a un préfixe

L’exemple suivant déclare un espace de noms global avec un préfixe et initialise un élément avec un littéral XML :

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Console.WriteLine(root)
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```xml
<aw:Root xmlns:aw="http://www.adventure-works.com" />
```

## <a name="example-declare-a-default-namespace-and-use-an-embedded-expression-for-the-child-element"></a>Exemple : déclarer un espace de noms par défaut et utiliser une expression incorporée pour l' `Child` élément

Les espaces de noms déclarés dans des littéraux XML ne sont pas reportés dans les expressions incorporées. L’exemple suivant déclare un espace de noms par défaut, puis utilise une expression incorporée pour l' `Child` élément.

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child/> %>
    </Root>
Console.WriteLine(root)
```

Cet exemple produit la sortie suivante :

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="" />
</Root>
```

Le XML obtenu comprend une déclaration d’un espace de noms par défaut, de sorte que l' `Child` élément ne se trouve pas dans un espace de noms.

Vous pouvez déclarer un espace de noms différent dans l’expression incorporée, comme suit :

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <%= <Child xmlns="http://www.adventure-works.com"/> %>
    </Root>
Console.WriteLine(root)
```

Cet exemple produit la sortie suivante :

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child xmlns="http://www.adventure-works.com" />
</Root>
```

Toutefois, avec l’espace de noms global par défaut, vous pouvez utiliser des littéraux XML sans déclarer d’espaces de noms. Le code XML résultant sera dans l’espace de noms par défaut déclaré globalement, comme dans cet exemple :

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <Root>
                                   <%= <Child/> %>
                               </Root>
        Console.WriteLine(root)
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```xml
<Root xmlns="http://www.adventure-works.com">
  <Child />
</Root>
```

## <a name="example-use-namespaces-with-xml-properties"></a>Exemple : utiliser des espaces de noms avec des propriétés XML

Si vous travaillez avec une arborescence XML qui se trouve dans un espace de noms et que vous utilisez des propriétés XML, vous devez utiliser un espace de noms global afin que les propriétés XML se trouvent également dans l’espace de noms approprié. L’exemple suivant déclare une arborescence XML dans un espace de noms, puis imprime le nombre d' `Child` éléments.

```vb
Dim root As XElement = _
    <Root xmlns="http://www.adventure-works.com">
        <Child>content</Child>
    </Root>
Console.WriteLine(root.<Child>.Count())
```

Cet exemple indique qu'il n'existe aucun élément `Child`. Il génère cette sortie :

```output
0
```

Si toutefois vous déclarez un espace de noms global par défaut, le littéral XML et la propriété XML sont tous deux dans l'espace de noms global par défaut :

```vb
Imports <xmlns="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <Root>
                <Child>content</Child>
            </Root>
        Console.WriteLine(root.<Child>.Count())
    End Sub
End Module
```

Cet exemple indique qu'il existe un élément `Child`. Il génère cette sortie :

```output
1
```

Si vous déclarez un espace de noms global qui a un préfixe, vous pouvez utiliser le préfixe à la fois pour les littéraux XML et les propriétés XML :

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = _
            <aw:Root>
                <aw:Child>content</aw:Child>
            </aw:Root>
        Console.WriteLine(root.<aw:Child>.Count())
    End Sub
End Module
```

## <a name="example-use-getxmlnamespace-to-get-an-xnamespace"></a>Exemple : utilisez `GetXmlNamespace` pour récupérer un `XNamespace`

Vous pouvez obtenir un <xref:System.Xml.Linq.XNamespace> objet à l’aide de la `GetXmlNamespace` méthode :

```vb
Imports <xmlns:aw="http://www.adventure-works.com">

Module Module1
    Sub Main()
        Dim root As XElement = <aw:Root/>
        Dim xn As XNamespace = GetXmlNamespace(aw)
        Console.WriteLine(xn)
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```output
http://www.adventure-works.com
```

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des espaces de noms](namespaces-overview.md)

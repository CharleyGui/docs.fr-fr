---
title: Littéraux XML dans Visual Basic LINQ to XML
description: Vous pouvez créer une arborescence XML dans Visual Basic à l’aide de littéraux XML et d’expressions incorporées. Les expressions incorporées vous permettent d’évaluer une expression et d’insérer les résultats de l’expression dans l’arborescence XML.
ms.date: 07/20/2015
ms.assetid: 94fc0e03-978e-4c08-ab6c-0dc3c1e64f10
ms.openlocfilehash: e3b1213672a6a7ddd71fcc38b4502108a6f49881
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553207"
---
# <a name="xml-literals-in-visual-basic-linq-to-xml"></a>Littéraux XML dans Visual Basic (LINQ to XML)

Cet article fournit des informations sur la création d’arborescences XML dans Visual Basic à l’aide de littéraux XML et d’expressions incorporées.

## <a name="example-use-xml-literals-to-create-an-xml-tree"></a>Exemple : utilisation de littéraux XML pour créer une arborescence XML

L’exemple suivant montre comment créer un <xref:System.Xml.Linq.XElement> , dans ce cas `contacts` , avec des littéraux XML :

```vb
Dim contacts As XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone>206-555-0144</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

## <a name="example-use-xml-literals-to-create-an-xelement-with-simple-content"></a>Exemple : utilisation de littéraux XML pour créer un XElement avec un contenu simple

Vous pouvez créer un objet <xref:System.Xml.Linq.XElement> qui contient du contenu simple, comme suit :

```vb
Dim n as XElement = <Customer>Adventure Works</Customer>
Console.WriteLine(n)
```

Cet exemple produit la sortie suivante :

```xml
<Customer>Adventure Works</Customer>
```

## <a name="example-use-an-xml-literal-to-create-an-empty-element"></a>Exemple : utiliser un littéral XML pour créer un élément vide

Vous pouvez créer un objet <xref:System.Xml.Linq.XElement> vide comme suit :

```vb
Dim n As XElement = <Customer/>
Console.WriteLine(n)
```

Cet exemple produit la sortie suivante :

```xml
<Customer />
```

## <a name="use-embedded-expressions-to-create-content"></a>Utiliser des expressions incorporées pour créer du contenu

L’une des fonctionnalités importantes des littéraux XML est qu’ils autorisent la présence d’expressions incorporées. Les expressions incorporées vous permettent d’évaluer une expression et d’insérer les résultats de l’expression dans l’arborescence XML. Si l'expression est évaluée à un type de <xref:System.Xml.Linq.XElement>, un élément est inséré dans l'arborescence. Si l’expression est évaluée à un type de <xref:System.Xml.Linq.XAttribute>, un attribut est inséré dans l’arborescence. Vous pouvez insérer des éléments et des attributs dans l’arborescence uniquement là où ils sont valides.

Il est important de noter qu’une seule expression peut être insérée dans une expression incorporée. Vous ne pouvez pas incorporer plusieurs instructions. Si une expression s'étend au-delà d'une seule ligne, vous devez utiliser le caractère de continuation de ligne.

Si vous utilisez une expression incorporée pour ajouter des nœuds (y compris des éléments) et des attributs existants à une nouvelle arborescence XML et si les nœuds existants sont déjà apparentés, les nœuds sont clonés. Les nœuds nouvellement clonés sont attachés à la nouvelle arborescence XML. Si les nœuds existants ne sont pas apparentés, les nœuds sont simplement attachés à la nouvelle arborescence XML. Le dernier exemple de cet article illustre cela.

## <a name="example-use-an-embedded-expression-to-insert-an-element"></a>Exemple : utilisation d’une expression incorporée pour insérer un élément

L’exemple suivant utilise une expression incorporée pour insérer un élément dans l’arborescence :

```vb
xmlTree1 As XElement = _
    <Root>
        <Child>Contents</Child>
    </Root>
Dim xmlTree2 As XElement = _
    <Root>
        <%= xmlTree1.<Child> %>
    </Root>
Console.WriteLine(xmlTree2)
```

Cet exemple produit la sortie suivante :

```xml
<Root>
  <Child>Contents</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-for-content"></a>Exemple : utilisation d’une expression incorporée pour le contenu

Vous pouvez utiliser une expression incorporée pour fournir le contenu d'un élément :

```vb
Dim str As String
str = "Some content"
Dim root As XElement = <Root><%= str %></Root>
Console.WriteLine(root)
```

Cet exemple produit la sortie suivante :

```xml
<Root>Some content</Root>
```

## <a name="example-use-a-linq-query-in-an-embedded-expression"></a>Exemple : utilisation d’une requête LINQ dans une expression incorporée

Vous pouvez utiliser les résultats d’une requête LINQ pour fournir le contenu d’un élément :

```vb
Dim arr As Integer() = {1, 2, 3}

Dim n As XElement = _
    <Root>
        <%= From i In arr Select <Child><%= i %></Child> %>
    </Root>

Console.WriteLine(n)
```

Cet exemple produit la sortie suivante :

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Child>3</Child>
</Root>
```

## <a name="example-use-an-embedded-expression-to-provide-node-names"></a>Exemple : utilisation d’une expression incorporée pour fournir des noms de nœud

Vous pouvez également utiliser une expression incorporée pour calculer les noms d’attribut, les valeurs d’attribut, les noms d’éléments et les valeurs d’élément :

```vb
Dim eleName As String = "ele"
Dim attName As String = "att"
Dim attValue As String = "aValue"
Dim eleValue As String = "eValue"
Dim n As XElement = _
    <Root <%= attName %>=<%= attValue %>>
        <<%= eleName %>>
            <%= eleValue %>
        </>
    </Root>
Console.WriteLine(n)
```

Cet exemple produit la sortie suivante :

```xml
<Root att="aValue">
  <ele>eValue</ele>
</Root>
```

## <a name="example-use-an-embedded-expression-to-clone-and-attach-nodes"></a>Exemple : utilisation d’une expression incorporée pour cloner et attacher des nœuds

Comme mentionné précédemment, si vous utilisez une expression incorporée pour ajouter des nœuds existants (y compris des éléments) et des attributs à une nouvelle arborescence XML, et si les nœuds ajoutés sont déjà apparentés, les nœuds sont clonés et les clones sont attachés à la nouvelle arborescence XML. Si les nœuds existants ne sont pas apparentés, ils sont simplement attachés à la nouvelle arborescence XML.

Le code suivant illustre le comportement lorsque vous ajoutez un élément apparenté à une arborescence et lorsque vous ajoutez un élément non apparenté à une arborescence.

```vb
' Create a tree with a child element.
Dim xmlTree1 As XElement = _
    <Root>
        <Child1>1</Child1>
    </Root>

' Create an element that's not parented.
Dim child2 As XElement = <Child2>2</Child2>

' Create a tree and add Child1 and Child2 to it.
Dim xmlTree2 As XElement = _
    <Root>
        <%= xmlTree1.<Child1>(0) %>
        <%= child2 %>
    </Root>

' Compare Child1 identity.
Console.WriteLine("Child1 was {0}", _
    IIf(xmlTree1.Element("Child1") Is xmlTree2.Element("Child1"), _
    "attached", "cloned"))

' Compare Child2 identity.
Console.WriteLine("Child2 was {0}", _
    IIf(child2 Is xmlTree2.Element("Child2"), _
    "attached", "cloned"))
```

Cet exemple produit la sortie suivante :

```output
Child1 was cloned
Child2 was attached
```

## <a name="see-also"></a>Voir aussi

- [Construction fonctionnelle](functional-construction.md)

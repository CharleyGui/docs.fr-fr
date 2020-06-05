---
title: 'Procédure : utiliser des annotations dans le but de transformer des arborescences LINQ to XML en un style XSLT'
ms.date: 07/20/2015
ms.assetid: 08e91fa2-dac2-4463-9ef1-87b1ac3fa890
ms.openlocfilehash: 099457eaab8c80605138d7e67d7bc2823e316234
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364446"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-visual-basic"></a>Comment : utiliser des annotations pour transformer des arbres LINQ to XML dans un style XSLT (Visual Basic)

Les annotations peuvent servir à faciliter les transformations d’une arborescence XML.

Certains documents XML sont « centrés sur les documents avec du contenu mixte ». Avec ces documents, vous ne connaissez pas nécessairement la forme des enfants nœuds d'un élément. Par exemple, un nœud qui contient du texte peut se présenter comme suit :

```xml
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>
```

Pour tout nœud de texte donné, il peut exister une quantité quelconque d'éléments enfants `<b>` et `<i>`. Cette approche s’étend à plusieurs autres situations : par exemple, des pages qui peuvent contenir divers éléments enfants, tels que des paragraphes réguliers, des paragraphes à puces et des bitmaps. Les cellules d’un tableau peuvent contenir du texte, des listes déroulantes ou des bitmaps. L'une des principales caractéristiques du code XML centré sur les documents est que vous ne savez pas quel élément enfant un élément particulier aura.

Si vous souhaitez transformer des éléments d'une arborescence dans laquelle vous ne connaissez pas forcément grand chose des enfants des éléments que vous souhaitez transformer, cette approche qui utilise des annotations est une approche efficace.

La synthèse de l'approche est la suivante :

- Tout d'abord, annotez les éléments de l'arborescence avec un élément de remplacement.

- Ensuite, itérez l'ensemble de l'arborescence et créez une nouvelle arborescence où vous remplacez chaque élément par son annotation. Cet exemple implémente l'itération et la création de la nouvelle arborescence dans une fonction nommée `XForm`.

En détail, l'approche se compose des étapes suivantes :

- Exécutez une ou plusieurs requêtes LINQ to XML qui retournent l'ensemble d'éléments que vous souhaitez transformer d'une forme à une autre. Pour chaque élément dans la requête, ajoutez un nouvel objet <xref:System.Xml.Linq.XElement> en tant qu'annotation de l'élément. Ce nouvel élément remplacera l’élément annoté dans la nouvelle arborescence transformée. Ce code est simple à écrire, comme illustré dans l'exemple.

- Le nouvel élément ajouté en tant qu'annotation peut contenir de nouveaux nœuds enfants ; il peut former une sous-arborescence de toute forme souhaitée.

- Il existe une règle spéciale : si un nœud enfant du nouvel élément est dans un espace de noms différent, un espace de noms créé à cet effet (dans cet exemple, l'espace de noms est `http://www.microsoft.com/LinqToXmlTransform/2007`), cet élément enfant n'est pas copié dans la nouvelle arborescence. Au lieu de cela, si l'espace de noms est l'espace de noms spécial mentionné ci-dessus et que le nom local de l'élément est `ApplyTransforms`, les nœuds enfants de l'élément dans l'arborescence source sont itérés et copiés dans la nouvelle arborescence (hormis le fait que les éléments enfants annotés sont eux-mêmes transformés conformément à ces règles).

- Cela est quelque peu analogue à la spécification des transformations en XSL. La requête qui sélectionne un ensemble de nœuds est analogue à l'expression XPath pour un modèle. Le code permettant de créer le nouvel objet <xref:System.Xml.Linq.XElement> qui est enregistré en tant qu'annotation est analogue au constructeur de séquence en XSL et l'élément `ApplyTransforms` est analogue en termes de fonction à l'élément `xsl:apply-templates` en XSL.

- L’un des avantages offerts par cette approche est que lorsque vous formulez des requêtes, vous écrivez toujours des requêtes sur l’arborescence source non modifiée. Vous n'avez pas à vous soucier de l'impact des modifications apportées à l'arborescence sur les requêtes que vous écrivez.

## <a name="transforming-a-tree"></a>Transformation d'une arborescence

Le premier exemple renomme tous les `Paragraph` nœuds en `para` :

```vb
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    Sub Main()
        Dim root As XElement = _
            <Root>
                <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>
                <Paragraph>More text.</Paragraph>
            </Root>

        ' Replace Paragraph with p.
        For Each el In root...<Paragraph>
            ' same idea as xsl:apply-templates
            el.AddAnnotation( _
                <para>
                    <<%= at %>></>
                </para>)
        Next

        ' The XForm function, shown later in this topic, accomplishes the transform
        Dim newRoot As XElement = XForm(root)
        Console.WriteLine(newRoot)
    End Sub
End Module
```

 Cet exemple produit la sortie suivante :

```xml
<Root>
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>
  <para>More text.</para>
</Root>
```

## <a name="a-more-complicated-transform"></a>Transformation plus complexe

L'exemple suivant interroge l'arborescence et calcule la moyenne et la somme des éléments `Data`, puis les ajoute à l'arborescence en tant que nouveaux éléments.

```vb
Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    Sub Main()
        Dim data As XElement = _
            <Root>
                <Data>20</Data>
                <Data>10</Data>
                <Data>3</Data>
            </Root>

        ' While adding annotations, you can query the source tree all you want,
        ' as the tree is not mutated while annotating.
        data.AddAnnotation( _
            <Root>
                <<%= at %>/>
                <Average>
                    <%= _
                        String.Format("{0:F4}", _
                        data.Elements("Data") _
                        .Select(Function(z) CDec(z)).Average()) _
                    %>
                </Average>
                <Sum>
                    <%= _
                        data.Elements("Data").Select(Function(z) CInt(z)).Sum() _
                    %>
                </Sum>
            </Root> _
        )

        Console.WriteLine("Before Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(data)
        Console.WriteLine(vbNewLine)

        ' The XForm function, shown later in this topic, accomplishes the transform
        Dim newData As XElement = XForm(data)

        Console.WriteLine("After Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(newData)
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```console
Before Transform
----------------
<Root>
  <Data>20</Data>
  <Data>10</Data>
  <Data>3</Data>
</Root>

After Transform
----------------
<Root>
  <Data>20</Data>
  <Data>10</Data>
  <Data>3</Data>
  <Average>11.0000</Average>
  <Sum>33</Sum>
</Root>
```

## <a name="effecting-the-transform"></a>Effet de la transformation

Une petite fonction, `XForm`, crée une nouvelle arborescence transformée à partir de l'arborescence d'origine annotée.

Le pseudo code de la fonction est assez simple :

> La fonction prend un XElement comme argument et retourne un XElement.
>
> Si un élément a une annotation XElement, retourne un nouveau XElement :
>
> - Le nom du nouveau XElement est le nom de l’élément d’annotation.
> - Tous les attributs sont copiés de l’annotation vers le nouveau nœud.
> - Tous les nœuds enfants sont copiés à partir de l’annotation, à l’exception près que le nœud spécial XF : ApplyTransforms est reconnu et que les nœuds enfants de l’élément source sont itérés. Si le nœud enfant source n’est pas un XElement, il est copié dans la nouvelle arborescence. Si la source enfant est un XElement, elle est transformée en appelant cette fonction de manière récursive.
>
> Si un élément n’est pas annoté :
>
> - Retourner un nouveau XElement
>   - Le nom du nouveau XElement est le nom de l’élément source.
>   - Tous les attributs sont copiés de l’élément source vers l’élément de destination.
>   - Tous les nœuds enfants sont copiés à partir de l’élément source.
>   - Si le nœud enfant source n’est pas un XElement, il est copié dans la nouvelle arborescence. Si la source enfant est un XElement, elle est transformée en appelant cette fonction de manière récursive.

Le code suivant est l’implémentation de cette fonction :

```vb
' Build a transformed XML tree per the annotations.
Function XForm(ByVal source As XElement) As XElement
    If source.Annotation(Of XElement)() IsNot Nothing Then
        Dim anno As XElement = source.Annotation(Of XElement)()
        Return _
            <<%= anno.Name.ToString() %>>
                <%= anno.Attributes() %>
                <%= anno.Nodes().Select(Function(n As XNode) _
                    GetSubNodes(n, source)) %>
            </>
    Else
        Return _
            <<%= source.Name %>>
                <%= source.Attributes() %>
                <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>
            </>
    End If
End Function

Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object
    Dim annoEl As XElement = TryCast(n, XElement)
    If annoEl IsNot Nothing Then
        If annoEl.Name = at Then
            Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))
        End If
    End If
    Return n
End Function

Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode
    Dim e2 As XElement = TryCast(n2, XElement)
    If e2 Is Nothing Then
        Return n2
    Else
        Return XForm(e2)
    End If
End Function
```

## <a name="complete-example"></a>Exemple complet

Le code suivant est un exemple complet qui inclut la fonction `XForm`. Il comprend certaines des utilisations courantes de ce type de transformation :

```vb
Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports System.Xml
Imports System.Xml.Linq

Imports <xmlns:xf="http://www.microsoft.com/LinqToXmlTransform/2007">

Module Module1
    Dim at As XName = GetXmlNamespace(xf) + "ApplyTransforms"

    ' Build a transformed XML tree per the annotations.
    Function XForm(ByVal source As XElement) As XElement
        If source.Annotation(Of XElement)() IsNot Nothing Then
            Dim anno As XElement = source.Annotation(Of XElement)()
            Return _
                <<%= anno.Name.ToString() %>>
                    <%= anno.Attributes() %>
                    <%= anno.Nodes().Select(Function(n As XNode) _
                        GetSubNodes(n, source)) %>
                </>
        Else
            Return _
                <<%= source.Name %>>
                    <%= source.Attributes() %>
                    <%= source.Nodes().Select(Function(n) GetExpandedNodes(n)) %>
                </>
        End If
    End Function

    Private Function GetSubNodes(ByVal n As XNode, ByVal s As XElement) As Object
        Dim annoEl As XElement = TryCast(n, XElement)
        If annoEl IsNot Nothing Then
            If annoEl.Name = at Then
                Return s.Nodes().Select(Function(n2 As XNode) GetExpandedNodes(n2))
            End If
        End If
        Return n
    End Function

    Private Function GetExpandedNodes(ByVal n2 As XNode) As XNode
        Dim e2 As XElement = TryCast(n2, XElement)
        If e2 Is Nothing Then
            Return n2
        Else
            Return XForm(e2)
        End If
    End Function

    Sub Main()
        Dim root As XElement = _
<Root Att1='123'>
    <!--A comment-->
    <Child>1</Child>
    <Child>2</Child>
    <Other>
        <GC>3</GC>
        <GC>4</GC>
    </Other>
    <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>
    <AnUnchangedElement>42</AnUnchangedElement>
</Root>

        ' Each of the following serves the same semantic purpose as
        ' XSLT templates and sequence constructors.

        ' Replace Child with NewChild.
        For Each el In root.<Child>
            el.AddAnnotation(<NewChild><%= CStr(el) %></NewChild>)
        Next

        ' Replace first GC with GrandChild, add an attribute.
        For Each el In root...<GC>.Take(1)
            el.AddAnnotation(<GrandChild ANewAttribute='999'><%= CStr(el) %></GrandChild>)
        Next

        ' Replace Other with NewOther, add new child elements around original content.
        For Each el In root.<Other>
            el.AddAnnotation( _
                <NewOther>
                    <MyNewChild>1</MyNewChild>
                    <<%= at %>></>
                    <ChildThatComesAfter/>
                </NewOther>)
        Next

        ' Change name of element that has mixed content.
        root...<SomeMixedContent>(0).AddAnnotation( _
                <MixedContent><<%= at %>></></MixedContent>)

        ' Replace <b> with <Bold>.
        For Each el In root...<b>
            el.AddAnnotation(<Bold><<%= at %>></></Bold>)
        Next

        ' Replace <i> with <Italic>.
        For Each el In root...<i>
            el.AddAnnotation(<Italic><<%= at %>></></Italic>)
        Next

        Console.WriteLine("Before Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(root)
        Console.WriteLine(vbNewLine)
        Dim newRoot As XElement = XForm(root)

        Console.WriteLine("After Transform")
        Console.WriteLine("----------------")
        Console.WriteLine(newRoot)
    End Sub
End Module
```

Cet exemple produit la sortie suivante :

```console
Before Transform
----------------
<Root Att1="123">
  <!--A comment-->
  <Child>1</Child>
  <Child>2</Child>
  <Other>
    <GC>3</GC>
    <GC>4</GC>
  </Other>
  <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>
  <AnUnchangedElement>42</AnUnchangedElement>
</Root>

After Transform
----------------
<Root Att1="123">
  <!--A comment-->
  <NewChild>1</NewChild>
  <NewChild>2</NewChild>
  <NewOther>
    <MyNewChild>1</MyNewChild>
    <GrandChild ANewAttribute="999">3</GrandChild>
    <GC>4</GC>
    <ChildThatComesAfter />
  </NewOther>
  <MixedContent>This is <Italic>an</Italic> element that <Bold>has</Bold> some mixed content</MixedContent>
  <AnUnchangedElement>42</AnUnchangedElement>
</Root>
```

## <a name="see-also"></a>Voir aussi

- [Visual Basic (Advanced LINQ to XML Programming)](advanced-linq-to-xml-programming.md)

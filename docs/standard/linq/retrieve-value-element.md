---
title: Comment récupérer la valeur d’un élément-LINQ to XML
description: 'Découvrez les deux principales façons d’obtenir la valeur d’un élément ou d’un attribut : effectuez un cast vers le type souhaité, ou utilisez les propriétés XElement. Value et XAttribute. Value.'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
ms.openlocfilehash: 010af5db9ec991bfe0345c93def3241150aa15e2
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553644"
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml"></a>Comment récupérer la valeur d’un élément (LINQ to XML)

Cet article montre comment récupérer la valeur des éléments. Il existe deux façons principales d’acquérir la valeur :

- Effectuez un cast d’un <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> d’un vers le type souhaité. L'opérateur de conversion explicite convertit alors le contenu de l'élément ou attribut vers le type spécifié et l'affecte à votre variable.

- Utilisez les <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> Propriétés ou. Vous pouvez également définir la valeur à l’aide de ces propriétés.

Avec C#, la conversion est généralement la meilleure approche. Si vous effectuez un cast de l’élément ou de l’attribut en un type valeur Nullable, le code est plus simple à écrire lors de la récupération de la valeur d’un élément (ou attribut) qui n’existe peut-être pas. Le dernier exemple de cet article illustre cela. Toutefois, vous ne pouvez pas définir le contenu d’un élément via la conversion, comme vous pouvez le faire via la <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> propriété.

Avec Visual Basic, la meilleure approche consiste à utiliser la <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> propriété.

## <a name="string-cast-example"></a>Exemple de conversion de chaîne  

Pour récupérer la valeur d’un élément, effectuez un cast de l' <xref:System.Xml.Linq.XElement> objet vers le type souhaité. Vous pouvez convertir un élément en chaîne, comme suit :

```csharp
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);
Console.WriteLine("Value of e:" + (string)e);
```

```vb
Dim e As XElement = <StringElement>abcde</StringElement>
Console.WriteLine(e)
Console.WriteLine("Value of e:" & e.Value)
```

Cet exemple produit la sortie suivante :

```output
<StringElement>abcde</StringElement>
Value of e:abcde
```

## <a name="integer-cast-example"></a>Exemple de cast d’entier  

Vous pouvez également convertir des éléments vers des types autres que des chaînes. Par exemple, si vous avez un élément qui contient un entier, vous pouvez le convertir en `int`, comme illustré dans le code suivant :  

```csharp
XElement e = new XElement("Age", "44");
Console.WriteLine(e);
Console.WriteLine("Value of e:" + (int)e);
```

```vb
Dim e As XElement = <Age>44</Age>
Console.WriteLine(e)
Console.WriteLine("Value of e:" & CInt(e))
```

Cet exemple produit la sortie suivante :

```output
<Age>44</Age>
Value of e:44
```

LINQ to XML fournit des opérateurs de cast explicites pour les types de données suivants : `string` , `bool` ,,,, `bool?` `int` `int?` `uint` ,,,,, `uint?` `long` `long?` `ulong` `ulong?` , `float` , `float?` , `double` , `double?` , `decimal` , `decimal?` , `DateTime` ,,,, `DateTime?` `TimeSpan` `TimeSpan?` `GUID` et `GUID?` .

LINQ to XML fournit les mêmes opérateurs de conversion pour les <xref:System.Xml.Linq.XAttribute> objets.

## <a name="value-property-example"></a>Exemple de propriété Value

Vous pouvez utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A> pour récupérer le contenu d'un élément :

```csharp
XElement e = new XElement("StringElement", "abcde");
Console.WriteLine(e);
Console.WriteLine("Value of e:" + e.Value);
```

```vb
Dim e As XElement = <StringElement>abcde</StringElement>
Console.WriteLine(e)
Console.WriteLine("Value of e:" & e.Value)
```

Cet exemple produit la sortie suivante :

```output
<StringElement>abcde</StringElement>
Value of e:abcde
```

## <a name="element-might-not-exist-example"></a>L’élément n’existe peut-être pas

Parfois, vous tentez de récupérer la valeur d’un élément même si vous n’êtes pas certain qu’il existe. Dans ce cas, lorsque vous assignez l’élément casté à un type de référence Nullable ou à un type de valeur Nullable, si l’élément n’existe pas, la variable assignée est définie sur `null` (C#) ou `nothing` (Visual Basic). Le code suivant montre que lorsque l’élément n’existe pas, il est plus facile d’utiliser la conversion que d’utiliser la <xref:System.Xml.Linq.XElement.Value%2A> propriété.

```csharp
XElement root = new XElement("Root",
    new XElement("Child1", "child 1 content"),
    new XElement("Child2", "2")
);

// The following assignments show why it's easier to use
// casting when the element might or might not exist.

string c1 = (string)root.Element("Child1");
Console.WriteLine("c1:{0}", c1 == null ? "element doesn't exist" : c1);

int? c2 = (int?)root.Element("Child2");
Console.WriteLine("c2:{0}", c2 == null ? "element doesn't exist" : c2.ToString());

string c3 = (string)root.Element("Child3");
Console.WriteLine("c3:{0}", c3 == null ? "element doesn't exist" : c3);

int? c4 = (int?)root.Element("Child4");
Console.WriteLine("c4:{0}", c4 == null ? "element doesn't exist" : c4.ToString());

Console.WriteLine();

// The following assignments show the required code when using
// the Value property when the element might or might not exist.
// Notice that this is more difficult than the casting approach.

XElement e1 = root.Element("Child1");
string v1;
if (e1 == null)
    v1 = null;
else
    v1 = e1.Value;
Console.WriteLine("v1:{0}", v1 == null ? "element doesn't exist" : v1);

XElement e2 = root.Element("Child2");
int? v2;
if (e2 == null)
    v2 = null;
else
    v2 = Int32.Parse(e2.Value);
Console.WriteLine("v2:{0}", v2 == null ? "element doesn't exist" : v2.ToString());

XElement e3 = root.Element("Child3");
string v3;
if (e3 == null)
    v3 = null;
else
    v3 = e3.Value;
Console.WriteLine("v3:{0}", v3 == null ? "element doesn't exist" : v3);

XElement e4 = root.Element("Child4");
int? v4;
if (e4 == null)
    v4 = null;
else
    v4 = Int32.Parse(e4.Value);
Console.WriteLine("v4:{0}", v4 == null ? "element doesn't exist" : v4.ToString());
```

```vb
Dim root As XElement = <Root>
                           <Child1>child 1 content</Child1>
                           <Child2>2</Child2>
                       </Root>

' The following assignments show why it's easier to use
' casting when the element might or might not exist.

Dim c1 As String = CStr(root.Element("Child1"))
Console.WriteLine("c1:{0}", IIf(c1 Is Nothing, "element doesn't exist", c1))

Dim c2 As Nullable(Of Integer) = CType(root.Element("Child2"), Nullable(Of Integer))
Console.WriteLine("c2:{0}", IIf(Not (c2.HasValue), "element doesn't exist", c2.ToString()))

Dim c3 As String = CStr(root.Element("Child3"))
Console.WriteLine("c3:{0}", IIf(c3 Is Nothing, "element doesn't exist", c3))

Dim c4 As Nullable(Of Integer) = CType(root.Element("Child4"), Nullable(Of Integer))
Console.WriteLine("c4:{0}", IIf(Not (c4.HasValue), "element doesn't exist", c4.ToString()))

Console.WriteLine()

' The following assignments show the required code when using
' the Value property when the attribute might or might not exist.
' Notice that this is more difficult than the casting approach.

Dim e1 As XElement = root.Element("Child1")
Dim v1 As String
If (e1 Is Nothing) Then
    v1 = Nothing
Else
    v1 = e1.Value
End If
Console.WriteLine("v1:{0}", IIf(v1 Is Nothing, "element doesn't exist", v1))

Dim e2 As XElement = root.Element("Child2")
Dim v2 As Nullable(Of Integer)
If (e2 Is Nothing) Then
    v2 = Nothing
Else
    v2 = e2.Value
End If
Console.WriteLine("v2:{0}", IIf(Not (v2.HasValue), "element doesn't exist", v2))

Dim e3 As XElement = root.Element("Child3")
Dim v3 As String
If (e3 Is Nothing) Then
    v3 = Nothing
Else
    v3 = e3.Value
End If
Console.WriteLine("v3:{0}", IIf(v3 Is Nothing, "element doesn't exist", v3))

Dim e4 As XElement = root.Element("Child4")
Dim v4 As Nullable(Of Integer)
If (e4 Is Nothing) Then
    v4 = Nothing
Else
    v4 = e4.Value
End If
Console.WriteLine("v4:{0}", IIf(Not (v4.HasValue), "element doesn't exist", v4))
```

Cet exemple produit la sortie suivante :

```output
c1:child 1 content
c2:2
c3:element doesn't exist
c4:element doesn't exist

v1:child 1 content
v2:2
v3:element doesn't exist
v4:element doesn't exist
```

En général, vous pouvez écrire du code plus simple en effectuant un cast pour récupérer le contenu d’éléments et d’attributs.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des axes LINQ to XML](linq-xml-axes-overview.md)

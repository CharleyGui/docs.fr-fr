---
title: Comment utiliser des dictionnaires à l’aide de LINQ to XML LINQ to XML
description: Vous pouvez convertir de nombreux types de structures de données en XML, et vous pouvez convertir du code XML en structures. Voici un exemple qui convertit un dictionnaire. dictionary générique en XML et inversement.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 57bcefe3-8433-4d3b-935a-511c9bcbdfa8
ms.openlocfilehash: ea61a79549488765526f45852dae7a4df7cacb64
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553215"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml"></a><span data-ttu-id="0dd4b-104">Comment utiliser des dictionnaires à l’aide de LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="0dd4b-104">How to work with dictionaries using LINQ to XML</span></span>

<span data-ttu-id="0dd4b-105">Il est souvent pratique de convertir des structures de données de différents genres en XML, puis de XML vers d’autres structures de données.</span><span class="sxs-lookup"><span data-stu-id="0dd4b-105">It's often convenient to convert data structures of various kinds to XML, and then from XML to other data structures.</span></span> <span data-ttu-id="0dd4b-106">Cet article présente une conversion de <xref:System.Collections.Generic.Dictionary%602> en XML et inversement.</span><span class="sxs-lookup"><span data-stu-id="0dd4b-106">This article shows a conversion of a <xref:System.Collections.Generic.Dictionary%602> to XML and back.</span></span>

## <a name="example-create-a-dictionary-and-convert-its-contents-to-xml"></a><span data-ttu-id="0dd4b-107">Exemple : créer un dictionnaire et convertir son contenu en XML</span><span class="sxs-lookup"><span data-stu-id="0dd4b-107">Example: Create a Dictionary and convert its contents to XML</span></span>

<span data-ttu-id="0dd4b-108">Ce premier exemple crée un <xref:System.Collections.Generic.Dictionary%602> , puis le convertit en XML.</span><span class="sxs-lookup"><span data-stu-id="0dd4b-108">This first example creates a <xref:System.Collections.Generic.Dictionary%602>, and then converts it to XML.</span></span>

<span data-ttu-id="0dd4b-109">Cette version C# de l’exemple utilise une forme de construction fonctionnelle dans laquelle une requête projette de nouveaux <xref:System.Xml.Linq.XElement> objets et la collection résultante est passée comme argument au constructeur de l' <xref:System.Xml.Linq.XElement> objet racine.</span><span class="sxs-lookup"><span data-stu-id="0dd4b-109">This C# version of the example uses a form of functional construction in which a query projects new <xref:System.Xml.Linq.XElement> objects, and the resulting collection is passed as an argument to the constructor of the Root <xref:System.Xml.Linq.XElement> object.</span></span>

<span data-ttu-id="0dd4b-110">La version Visual Basic utilise des littéraux XML et une requête dans une expression incorporée.</span><span class="sxs-lookup"><span data-stu-id="0dd4b-110">The Visual Basic version uses XML literals and a query in an embedded expression.</span></span> <span data-ttu-id="0dd4b-111">La requête projette de nouveaux <xref:System.Xml.Linq.XElement> objets qui deviennent ensuite le nouveau contenu de l' `Root` <xref:System.Xml.Linq.XElement> objet.</span><span class="sxs-lookup"><span data-stu-id="0dd4b-111">The query projects new <xref:System.Xml.Linq.XElement> objects which then become the new content for the `Root` <xref:System.Xml.Linq.XElement> object.</span></span>

```csharp
Dictionary<string, string> dict = new Dictionary<string, string>();
dict.Add("Child1", "Value1");
dict.Add("Child2", "Value2");
dict.Add("Child3", "Value3");
dict.Add("Child4", "Value4");
XElement root = new XElement("Root",
    from keyValue in dict
    select new XElement(keyValue.Key, keyValue.Value)
);
Console.WriteLine(root);
```

```vb
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()
dict.Add("Child1", "Value1")
dict.Add("Child2", "Value2")
dict.Add("Child3", "Value3")
dict.Add("Child4", "Value4")
Dim root As XElement = _
    <Root>
        <%= From keyValue In dict _
            Select New XElement(keyValue.Key, keyValue.Value) %>
    </Root>
Console.WriteLine(root)
```

<span data-ttu-id="0dd4b-112">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0dd4b-112">This example produces the following output:</span></span>

```xml
<Root>
  <Child1>Value1</Child1>
  <Child2>Value2</Child2>
  <Child3>Value3</Child3>
  <Child4>Value4</Child4>
</Root>
```

## <a name="example-create-a-dictionary-and-load-it-from-xml-data"></a><span data-ttu-id="0dd4b-113">Exemple : créer un dictionnaire et le charger à partir de données XML</span><span class="sxs-lookup"><span data-stu-id="0dd4b-113">Example: Create a dictionary and load it from XML data</span></span>

<span data-ttu-id="0dd4b-114">L’exemple suivant crée un chargement de dictionnaire qui le charge à partir de données XML.</span><span class="sxs-lookup"><span data-stu-id="0dd4b-114">The next example creates a dictionary loads loads it from XML data.</span></span>

```csharp
XElement root = new XElement("Root",
    new XElement("Child1", "Value1"),
    new XElement("Child2", "Value2"),
    new XElement("Child3", "Value3"),
    new XElement("Child4", "Value4")
);

Dictionary<string, string> dict = new Dictionary<string, string>();
foreach (XElement el in root.Elements())
    dict.Add(el.Name.LocalName, el.Value);
foreach (string str in dict.Keys)
    Console.WriteLine("{0}:{1}", str, dict[str]);
```

```vb
Dim root As XElement = _
        <Root>
            <Child1>Value1</Child1>
            <Child2>Value2</Child2>
            <Child3>Value3</Child3>
            <Child4>Value4</Child4>
        </Root>

Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)
For Each el As XElement In root.Elements
    dict.Add(el.Name.LocalName, el.Value)
Next
For Each str As String In dict.Keys
    Console.WriteLine("{0}:{1}", str, dict(str))
Next
```

<span data-ttu-id="0dd4b-115">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0dd4b-115">This example produces the following output:</span></span>

```output
Child1:Value1
Child2:Value2
Child3:Value3
Child4:Value4
```

## <a name="see-also"></a><span data-ttu-id="0dd4b-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0dd4b-116">See also</span></span>

- [<span data-ttu-id="0dd4b-117">Projections et transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0dd4b-117">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)

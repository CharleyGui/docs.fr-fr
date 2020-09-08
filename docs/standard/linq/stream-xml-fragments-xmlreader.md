---
title: Comment diffuser en continu des fragments XML à partir d’un XmlReader-LINQ to XML
description: Vous pouvez diffuser en continu des fragments XML à partir d’un XmlReader à l’aide d’une méthode d’axe personnalisée en C# et Visual Basic. Il s’agit d’une approche qui peut fonctionner lorsque le chargement de l’intégralité de l’arborescence XML en mémoire est irréalisable.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: e3a7a6260c66f0295216552c6aa56f71a8536bdf
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552469"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-linq-to-xml"></a><span data-ttu-id="efe45-104">Comment diffuser en continu des fragments XML à partir d’un XmlReader (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="efe45-104">How to stream XML fragments from an XmlReader (LINQ to XML)</span></span>

<span data-ttu-id="efe45-105">Lorsque vous devez traiter de grands fichiers XML, il peut être impossible de charger l’intégralité de l’arborescence XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="efe45-105">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="efe45-106">Cet article montre comment diffuser des fragments en continu à l’aide d’un <xref:System.Xml.XmlReader> en C# et d’Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="efe45-106">This article shows how to stream fragments using an <xref:System.Xml.XmlReader> in C# and Visual Basic.</span></span>

<span data-ttu-id="efe45-107">L'une des manières les plus efficaces d'utiliser un objet <xref:System.Xml.XmlReader> pour lire des objets <xref:System.Xml.Linq.XElement> consiste à écrire votre propre méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="efe45-107">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="efe45-108">Une méthode d’axe retourne généralement une collection telle que <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement> , comme illustré dans l’exemple de cet article.</span><span class="sxs-lookup"><span data-stu-id="efe45-108">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this article.</span></span> <span data-ttu-id="efe45-109">Dans la méthode d'axe personnalisée, après avoir créé le fragment XML en appelant la méthode <xref:System.Xml.Linq.XNode.ReadFrom%2A>, retournez la collection à l'aide de `yield return`.</span><span class="sxs-lookup"><span data-stu-id="efe45-109">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="efe45-110">Cela fournit une sémantique d'exécution différée à votre méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="efe45-110">This provides deferred execution semantics to your custom axis method.</span></span>

<span data-ttu-id="efe45-111">Lorsque vous créez une arborescence XML à partir d'un objet <xref:System.Xml.XmlReader>, l'objet <xref:System.Xml.XmlReader> doit être positionné sur un élément.</span><span class="sxs-lookup"><span data-stu-id="efe45-111">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="efe45-112">La <xref:System.Xml.Linq.XNode.ReadFrom%2A> méthode ne retourne pas jusqu’à ce qu’elle ait lu la balise de fermeture de l’élément.</span><span class="sxs-lookup"><span data-stu-id="efe45-112">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method doesn't return until it has read the close tag of the element.</span></span>

<span data-ttu-id="efe45-113">Si vous souhaitez créer une arborescence partielle, vous pouvez instancier un objet <xref:System.Xml.XmlReader>, positionner le lecteur sur le nœud que vous souhaitez convertir en une arborescence <xref:System.Xml.Linq.XElement>, puis créer l'objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="efe45-113">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>

<span data-ttu-id="efe45-114">L’article [Comment diffuser en continu des fragments XML avec accès aux informations d’en-tête](stream-xml-fragments-access-header-information.md) contient des informations sur la diffusion en continu d’un document plus complexe.</span><span class="sxs-lookup"><span data-stu-id="efe45-114">The article [How to stream XML fragments with access to header information](stream-xml-fragments-access-header-information.md) contains information on streaming a more complex document.</span></span>

<span data-ttu-id="efe45-115">L’article [Comment effectuer une transformation de diffusion en continu de documents XML volumineux](perform-streaming-transform-large-xml-documents.md) contient un exemple d’utilisation de LINQ to XML pour transformer des documents XML extrêmement volumineux tout en conservant un faible encombrement mémoire.</span><span class="sxs-lookup"><span data-stu-id="efe45-115">The article [How to perform streaming transform of large XML documents](perform-streaming-transform-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>

## <a name="example-create-a-custom-axis-method"></a><span data-ttu-id="efe45-116">Exemple : créer une méthode d’axe personnalisée</span><span class="sxs-lookup"><span data-stu-id="efe45-116">Example: Create a custom axis method</span></span>

<span data-ttu-id="efe45-117">Cet exemple crée une méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="efe45-117">This example creates a custom axis method.</span></span> <span data-ttu-id="efe45-118">Vous pouvez l’interroger à l’aide d’une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="efe45-118">You can query it by using a LINQ query.</span></span> <span data-ttu-id="efe45-119">La méthode d’axe personnalisée `StreamRootChildDoc` peut lire un document qui possède un `Child` élément répétitif.</span><span class="sxs-lookup"><span data-stu-id="efe45-119">The custom axis method `StreamRootChildDoc` can read a document that has a repeating `Child` element.</span></span>

```csharp
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)
{
    using (XmlReader reader = XmlReader.Create(stringReader))
    {
        reader.MoveToContent();
        // Parse the file and display each of the nodes.
        while (reader.Read())
        {
            switch (reader.NodeType)
            {
                case XmlNodeType.Element:
                    if (reader.Name == "Child") {
                        XElement el = XElement.ReadFrom(reader) as XElement;
                        if (el != null)
                            yield return el;
                    }
                    break;
            }
        }
    }
}

static void Main(string[] args)
{
    string markup = @"<Root>
      <Child Key=""01"">
        <GrandChild>aaa</GrandChild>
      </Child>
      <Child Key=""02"">
        <GrandChild>bbb</GrandChild>
      </Child>
      <Child Key=""03"">
        <GrandChild>ccc</GrandChild>
      </Child>
    </Root>";

    IEnumerable<string> grandChildData =
        from el in StreamRootChildDoc(new StringReader(markup))
        where (int)el.Attribute("Key") > 1
        select (string)el.Element("GrandChild");

    foreach (string str in grandChildData) {
        Console.WriteLine(str);
    }
}
```

```vb
Module Module1
    Sub Main()
        Dim markup = "<Root>" &
                     "  <Child Key=""01"">" &
                     "    <GrandChild>aaa</GrandChild>" &
                     "  </Child>" &
                     "  <Child Key=""02"">" &
                     "    <GrandChild>bbb</GrandChild>" &
                     "  </Child>" &
                     "  <Child Key=""03"">" &
                     "    <GrandChild>ccc</GrandChild>" &
                     "  </Child>" &
                     "</Root>"

        Dim grandChildData =
             From el In New StreamRootChildDoc(New IO.StringReader(markup))
             Where CInt(el.@Key) > 1
             Select el.<GrandChild>.Value

        For Each s In grandChildData
            Console.WriteLine(s)
        Next
    End Sub
End Module

Public Class StreamRootChildDoc
    Implements IEnumerable(Of XElement)

    Private _stringReader As IO.StringReader

    Public Sub New(ByVal stringReader As IO.StringReader)
        _stringReader = stringReader
    End Sub

    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator
        Return New StreamChildEnumerator(_stringReader)
    End Function

    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator
        Return Me.GetEnumerator()
    End Function
End Class

Public Class StreamChildEnumerator
    Implements IEnumerator(Of XElement)

    Private _current As XElement
    Private _reader As Xml.XmlReader
    Private _stringReader As IO.StringReader

    Public Sub New(ByVal stringReader As IO.StringReader)
        _stringReader = stringReader
        _reader = Xml.XmlReader.Create(_stringReader)
        _reader.MoveToContent()
    End Sub

    Public ReadOnly Property Current As XElement Implements IEnumerator(Of XElement).Current
        Get
            Return _current
        End Get
    End Property

    Public ReadOnly Property Current1 As Object Implements IEnumerator.Current
        Get
            Return Me.Current
        End Get
    End Property

    Public Function MoveNext() As Boolean Implements IEnumerator.MoveNext
        While _reader.Read()
            Select Case _reader.NodeType
                Case Xml.XmlNodeType.Element
                    Dim el = TryCast(XElement.ReadFrom(_reader), XElement)
                    If el IsNot Nothing Then
                        _current = el
                        Return True
                    End If
            End Select
        End While

        Return False
    End Function

    Public Sub Reset() Implements IEnumerator.Reset
        _reader = Xml.XmlReader.Create(_stringReader)
        _reader.MoveToContent()
    End Sub

#Region "IDisposable Support"

    Private disposedValue As Boolean ' To detect redundant calls

    ' IDisposable
    Protected Overridable Sub Dispose(ByVal disposing As Boolean)
        If Not Me.disposedValue Then
            If disposing Then
                _reader.Close()
            End If
        End If
        Me.disposedValue = True
    End Sub

    Public Sub Dispose() Implements IDisposable.Dispose
        Dispose(True)
        GC.SuppressFinalize(Me)
    End Sub
#End Region

End Class
```

<span data-ttu-id="efe45-120">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="efe45-120">This example produces the following output:</span></span>

```output
bbb
ccc
```

<span data-ttu-id="efe45-121">La technique utilisée dans cet exemple conserve un faible encombrement mémoire même pour des millions d' `Child` éléments.</span><span class="sxs-lookup"><span data-stu-id="efe45-121">The technique used in this example maintains a small memory footprint even for millions of `Child` elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="efe45-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="efe45-122">See also</span></span>

- [<span data-ttu-id="efe45-123">XML Parse</span><span class="sxs-lookup"><span data-stu-id="efe45-123">Parse XML</span></span>](parse-string.md)

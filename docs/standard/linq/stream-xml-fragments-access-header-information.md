---
title: Comment diffuser en continu des fragments XML avec accès aux informations d’en-tête-LINQ to XML
description: Découvrez comment implémenter et utiliser une méthode d’axe personnalisée qui diffuse en continu des fragments XML à partir du fichier spécifié par un URI.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: d50c29feb305341155257cd215e0292350689e7b
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553255"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-linq-to-xml"></a><span data-ttu-id="3461b-103">Comment diffuser en continu des fragments XML avec accès aux informations d’en-tête (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="3461b-103">How to stream XML fragments with access to header information (LINQ to XML)</span></span>

<span data-ttu-id="3461b-104">Vous devez parfois lire des fichiers XML arbitrairement volumineux et écrire votre application de sorte que son encombrement mémoire soit prévisible.</span><span class="sxs-lookup"><span data-stu-id="3461b-104">Sometimes you have to read arbitrarily large XML files, and write your application so that the memory footprint of the application is predictable.</span></span> <span data-ttu-id="3461b-105">Si vous tentez de remplir une arborescence XML avec un grand fichier XML, l'utilisation de la mémoire sera proportionnelle à la taille du fichier (c'est-à-dire excessive).</span><span class="sxs-lookup"><span data-stu-id="3461b-105">If you attempt to populate an XML tree with a large XML file, your memory usage will be proportional to the size of the file—that is, excessive.</span></span> <span data-ttu-id="3461b-106">Par conséquent, vous devez utiliser une technique de diffusion en continu à la place.</span><span class="sxs-lookup"><span data-stu-id="3461b-106">Therefore, you should use a streaming technique instead.</span></span>

<span data-ttu-id="3461b-107">L'une des options consiste à écrire votre application à l'aide de <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="3461b-107">One option is to write your application using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="3461b-108">Toutefois, vous souhaiterez peut-être utiliser LINQ pour interroger l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="3461b-108">However, you might want to use LINQ to query the XML tree.</span></span> <span data-ttu-id="3461b-109">Si c’est le cas, vous pouvez écrire votre propre méthode d’axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="3461b-109">If so, you can write your own custom axis method.</span></span> <span data-ttu-id="3461b-110">Pour plus d’informations, consultez [Comment écrire une méthode d’axe LINQ to XML](write-linq-xml-axis-method.md).</span><span class="sxs-lookup"><span data-stu-id="3461b-110">For more information, see [How to write a LINQ to XML axis method](write-linq-xml-axis-method.md).</span></span>

<span data-ttu-id="3461b-111">Pour écrire votre propre méthode d’axe, vous écrivez une petite méthode qui utilise le <xref:System.Xml.XmlReader> pour lire des nœuds jusqu’à atteindre l’un des nœuds qui vous intéressent.</span><span class="sxs-lookup"><span data-stu-id="3461b-111">To write your own axis method, you write a small method that uses the <xref:System.Xml.XmlReader> to read nodes until it reaches one of the nodes in which you're interested.</span></span> <span data-ttu-id="3461b-112">La méthode appelle ensuite <xref:System.Xml.Linq.XNode.ReadFrom%2A>, qui lit à partir de l'objet <xref:System.Xml.XmlReader> et instancie un fragment XML.</span><span class="sxs-lookup"><span data-stu-id="3461b-112">The method then calls <xref:System.Xml.Linq.XNode.ReadFrom%2A>, which reads from the <xref:System.Xml.XmlReader> and instantiates an XML fragment.</span></span> <span data-ttu-id="3461b-113">Il produit ensuite chaque fragment par `yield return` le biais de la méthode qui énumère votre méthode d’axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="3461b-113">It then yields each fragment through `yield return` to the method that's enumerating your custom axis method.</span></span> <span data-ttu-id="3461b-114">Vous pouvez ensuite écrire des requêtes LINQ sur votre méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="3461b-114">You can then write LINQ queries on your custom axis method.</span></span>

<span data-ttu-id="3461b-115">Il est préférable d'appliquer des techniques de diffusion en continu dans les situations où vous devez traiter le document source une seule fois et où vous pouvez traiter les éléments dans l'ordre du document.</span><span class="sxs-lookup"><span data-stu-id="3461b-115">Streaming techniques are best applied in situations where you need to process the source document only once, and you can process the elements in document order.</span></span> <span data-ttu-id="3461b-116">Certains opérateurs de requête standard, tels que <xref:System.Linq.Enumerable.OrderBy%2A>, itèrent au sein de leur source, recueillent toutes les données, les trient, puis produisent le premier élément de la séquence.</span><span class="sxs-lookup"><span data-stu-id="3461b-116">Certain standard query operators, such as <xref:System.Linq.Enumerable.OrderBy%2A>, iterate their source, collect all of the data, sort it, and then finally yield the first item in the sequence.</span></span> <span data-ttu-id="3461b-117">Si vous utilisez un opérateur de requête qui matérialise sa source avant de produire le premier élément, vous ne conserverez pas un faible encombrement mémoire.</span><span class="sxs-lookup"><span data-stu-id="3461b-117">If you use a query operator that materializes its source before yielding the first item, you won't retain a small memory footprint.</span></span>

## <a name="example-implement-and-use-a-custom-axis-method-that-streams-xml-fragments-from-the-file-specified-by-a-uri"></a><span data-ttu-id="3461b-118">Exemple : implémenter et utiliser une méthode d’axe personnalisée qui diffuse en continu des fragments XML à partir du fichier spécifié par un URI</span><span class="sxs-lookup"><span data-stu-id="3461b-118">Example: Implement and use a custom axis method that streams XML fragments from the file specified by a URI</span></span>

<span data-ttu-id="3461b-119">Le problème peut parfois être un peu plus épineux.</span><span class="sxs-lookup"><span data-stu-id="3461b-119">Sometimes the problem gets just a little more interesting.</span></span> <span data-ttu-id="3461b-120">Dans le document XML suivant, le consommateur de votre méthode d'axe personnalisée doit également connaître le nom du client auquel appartient chaque élément.</span><span class="sxs-lookup"><span data-stu-id="3461b-120">In the following XML document, the consumer of your custom axis method also has to know the name of the customer that each item belongs to.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<Root>
  <Customer>
    <Name>A. Datum Corporation</Name>
    <Item>
      <Key>0001</Key>
    </Item>
    <Item>
      <Key>0002</Key>
    </Item>
    <Item>
      <Key>0003</Key>
    </Item>
    <Item>
      <Key>0004</Key>
    </Item>
  </Customer>
  <Customer>
    <Name>Fabrikam, Inc.</Name>
    <Item>
      <Key>0005</Key>
    </Item>
    <Item>
      <Key>0006</Key>
    </Item>
    <Item>
      <Key>0007</Key>
    </Item>
    <Item>
      <Key>0008</Key>
    </Item>
  </Customer>
  <Customer>
    <Name>Southridge Video</Name>
    <Item>
      <Key>0009</Key>
    </Item>
    <Item>
      <Key>0010</Key>
    </Item>
  </Customer>
</Root>
```

<span data-ttu-id="3461b-121">L’approche que cet exemple utilise consiste également à surveiller les informations d’en-tête, à enregistrer les informations d’en-tête, puis à générer une petite arborescence XML qui contient à la fois les informations d’en-tête et le détail que vous énumérez.</span><span class="sxs-lookup"><span data-stu-id="3461b-121">The approach that this example takes is to also watch for this header information, save the header information, and then build a small XML tree that contains both the header information and the detail that you're enumerating.</span></span> <span data-ttu-id="3461b-122">La méthode d'axe produit ensuite cette nouvelle petite arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="3461b-122">The axis method then yields this new, small XML tree.</span></span> <span data-ttu-id="3461b-123">La requête a alors accès aux informations d'en-tête et aux informations de détail.</span><span class="sxs-lookup"><span data-stu-id="3461b-123">The query then has access to the header information as well as the detail information.</span></span>

<span data-ttu-id="3461b-124">Cette approche présente un faible encombrement mémoire.</span><span class="sxs-lookup"><span data-stu-id="3461b-124">This approach has a small memory footprint.</span></span> <span data-ttu-id="3461b-125">À mesure que chaque fragment XML de détail est produit, aucune référence n’est conservée dans le fragment précédent et il est disponible pour garbage collection.</span><span class="sxs-lookup"><span data-stu-id="3461b-125">As each detail XML fragment is yielded, no references are kept to the previous fragment, and it's available for garbage collection.</span></span> <span data-ttu-id="3461b-126">Cette technique crée de nombreux objets éphémères sur le tas.</span><span class="sxs-lookup"><span data-stu-id="3461b-126">This technique creates many short lived objects on the heap.</span></span>

<span data-ttu-id="3461b-127">L'exemple suivant montre comment implémenter et utiliser une méthode d'axe personnalisée qui diffuse en continu des fragments XML à partir du fichier spécifié par l'URI.</span><span class="sxs-lookup"><span data-stu-id="3461b-127">The following example shows how to implement and use a custom axis method that streams XML fragments from the file specified by the URI.</span></span> <span data-ttu-id="3461b-128">Cet axe personnalisé est écrit de façon à ce qu’il attende un document contenant des `Customer` éléments, et `Name` `Item` , et que ces éléments soient disposés comme dans le document ci-dessus `Source.xml` .</span><span class="sxs-lookup"><span data-stu-id="3461b-128">This custom axis is written such that it expects a document that has `Customer`, `Name`, and `Item` elements, and that those elements will be arranged as in the above `Source.xml` document.</span></span> <span data-ttu-id="3461b-129">Il s’agit d’une implémentation simpliste.</span><span class="sxs-lookup"><span data-stu-id="3461b-129">It's a simplistic implementation.</span></span> <span data-ttu-id="3461b-130">Une implémentation plus robuste serait préparée à analyser un document non valide.</span><span class="sxs-lookup"><span data-stu-id="3461b-130">A more robust implementation would be prepared to parse an invalid document.</span></span>

```csharp
static IEnumerable<XElement> StreamCustomerItem(string uri)
{
    using (XmlReader reader = XmlReader.Create(uri))
    {
        XElement name = null;
        XElement item = null;

        reader.MoveToContent();

        // Parse the file, save header information when encountered, and yield the
        // Item XElement objects as they're created.

        // loop through Customer elements
        while (reader.Read())
        {
            if (reader.NodeType == XmlNodeType.Element
                && reader.Name == "Customer")
            {
                // move to Name element
                while (reader.Read())
                {
                    if (reader.NodeType == XmlNodeType.Element &&
                        reader.Name == "Name")
                    {
                        name = XElement.ReadFrom(reader) as XElement;
                        break;
                    }
                }

                // Loop through Item elements
                while (reader.Read())
                {
                    if (reader.NodeType == XmlNodeType.EndElement)
                        break;
                    if (reader.NodeType == XmlNodeType.Element
                        && reader.Name == "Item")
                    {
                        item = XElement.ReadFrom(reader) as XElement;
                        if (item != null) {
                            XElement tempRoot = new XElement("Root",
                                new XElement(name)
                            );
                            tempRoot.Add(item);
                            yield return item;
                        }
                    }
                }
            }
        }
    }
}

static void Main(string[] args)
{
    XElement xmlTree = new XElement("Root",
        from el in StreamCustomerItem("Source.xml")
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7
        select new XElement("Item",
            new XElement("Customer", (string)el.Parent.Element("Name")),
            new XElement(el.Element("Key"))
        )
    );
    Console.WriteLine(xmlTree);
}
```

```vb
Module Module1

    Sub Main()
        Dim xmlTree = <Root>
                          <%=
                              From el In New StreamCustomerItem("Source.xml")
                              Let itemKey = CInt(el.<Key>.Value)
                              Where itemKey >= 3 AndAlso itemKey <= 7
                              Select <Item>
                                         <Customer><%= el.Parent.<Name>.Value %></Customer>
                                         <%= el.<Key> %>
                                     </Item>
                          %>
                      </Root>

        Console.WriteLine(xmlTree)
    End Sub

End Module

Public Class StreamCustomerItem
    Implements IEnumerable(Of XElement)

    Private _uri As String

    Public Sub New(ByVal uri As String)
        _uri = uri
    End Sub

    Public Function GetEnumerator() As IEnumerator(Of XElement) Implements IEnumerable(Of XElement).GetEnumerator
        Return New StreamCustomerItemEnumerator(_uri)
    End Function

    Public Function GetEnumerator1() As IEnumerator Implements IEnumerable.GetEnumerator
        Return Me.GetEnumerator()
    End Function
End Class

Public Class StreamCustomerItemEnumerator
    Implements IEnumerator(Of XElement)

    Private _current As XElement
    Private _customerName As String
    Private _reader As Xml.XmlReader
    Private _uri As String

    Public Sub New(ByVal uri As String)
        _uri = uri
        _reader = Xml.XmlReader.Create(_uri)
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
        Dim item As XElement
        Dim name As XElement

        ' Parse the file, save header information when encountered, and return the
        ' current Item XElement.

        ' loop through Customer elements
        While _reader.Read()
            If _reader.NodeType = Xml.XmlNodeType.Element Then
                Select Case _reader.Name
                    Case "Customer"
                        ' move to Name element
                        While _reader.Read()

                            If _reader.NodeType = Xml.XmlNodeType.Element AndAlso
                                _reader.Name = "Name" Then

                                name = TryCast(XElement.ReadFrom(_reader), XElement)
                                _customerName = If(name IsNot Nothing, name.Value, "")
                                Exit While
                            End If

                        End While
                    Case "Item"
                        item = TryCast(XElement.ReadFrom(_reader), XElement)
                        Dim tempRoot = <Root>
                                           <Name><%= _customerName %></Name>
                                           <%= item %>
                                       </Root>
                        _current = item
                        Return True
                End Select
            End If
        End While

        Return False
    End Function

    Public Sub Reset() Implements IEnumerator.Reset
        _reader = Xml.XmlReader.Create(_uri)
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

 <span data-ttu-id="3461b-131">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3461b-131">This code produces the following output:</span></span>

```xml
<Root>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0003</Key>
  </Item>
  <Item>
    <Customer>A. Datum Corporation</Customer>
    <Key>0004</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0005</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0006</Key>
  </Item>
  <Item>
    <Customer>Fabrikam, Inc.</Customer>
    <Key>0007</Key>
  </Item>
</Root>
```

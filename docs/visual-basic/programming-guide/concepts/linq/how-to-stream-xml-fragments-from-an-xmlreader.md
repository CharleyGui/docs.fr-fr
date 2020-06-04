---
title: 'Procédure : effectuer le streaming de fragments XML à partir d’un XmlReader'
ms.date: 07/20/2015
ms.assetid: f67ce598-4a12-4dcb-9a07-24deca02a111
ms.openlocfilehash: ff22625767c4e0752ca19d5a315395934b566230
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397698"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-visual-basic"></a><span data-ttu-id="13e36-102">Comment : diffuser des fragments XML en continu à partir d’un XmlReader (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13e36-102">How to: Stream XML Fragments from an XmlReader (Visual Basic)</span></span>
<span data-ttu-id="13e36-103">Lorsque vous devez traiter de grands fichiers XML, il peut être impossible de charger l’intégralité de l’arborescence XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="13e36-103">When you have to process large XML files, it might not be feasible to load the whole XML tree into memory.</span></span> <span data-ttu-id="13e36-104">Cette rubrique montre comment diffuser des fragments en continu à l'aide d'un objet <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="13e36-104">This topic shows how to stream fragments using an <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="13e36-105">L'une des manières les plus efficaces d'utiliser un objet <xref:System.Xml.XmlReader> pour lire des objets <xref:System.Xml.Linq.XElement> consiste à écrire votre propre méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="13e36-105">One of the most effective ways to use an <xref:System.Xml.XmlReader> to read <xref:System.Xml.Linq.XElement> objects is to write your own custom axis method.</span></span> <span data-ttu-id="13e36-106">Une méthode d'axe retourne généralement une collection telle que <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, comme illustré dans l'exemple de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="13e36-106">An axis method typically returns a collection such as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, as shown in the example in this topic.</span></span> <span data-ttu-id="13e36-107">Dans la méthode d'axe personnalisée, après avoir créé le fragment XML en appelant la méthode <xref:System.Xml.Linq.XNode.ReadFrom%2A>, retournez la collection à l'aide de `yield return`.</span><span class="sxs-lookup"><span data-stu-id="13e36-107">In the custom axis method, after you create the XML fragment by calling the <xref:System.Xml.Linq.XNode.ReadFrom%2A> method, return the collection using `yield return`.</span></span> <span data-ttu-id="13e36-108">Cela fournit une sémantique d'exécution différée à votre méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="13e36-108">This provides deferred execution semantics to your custom axis method.</span></span>  
  
 <span data-ttu-id="13e36-109">Lorsque vous créez une arborescence XML à partir d'un objet <xref:System.Xml.XmlReader>, l'objet <xref:System.Xml.XmlReader> doit être positionné sur un élément.</span><span class="sxs-lookup"><span data-stu-id="13e36-109">When you create an XML tree from an <xref:System.Xml.XmlReader> object, the <xref:System.Xml.XmlReader> must be positioned on an element.</span></span> <span data-ttu-id="13e36-110">La méthode <xref:System.Xml.Linq.XNode.ReadFrom%2A> ne retourne que lorsqu'elle a lu la balise de fermeture de l'élément.</span><span class="sxs-lookup"><span data-stu-id="13e36-110">The <xref:System.Xml.Linq.XNode.ReadFrom%2A> method does not return until it has read the close tag of the element.</span></span>  
  
 <span data-ttu-id="13e36-111">Si vous souhaitez créer une arborescence partielle, vous pouvez instancier un objet <xref:System.Xml.XmlReader>, positionner le lecteur sur le nœud que vous souhaitez convertir en une arborescence <xref:System.Xml.Linq.XElement>, puis créer l'objet <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="13e36-111">If you want to create a partial tree, you can instantiate an <xref:System.Xml.XmlReader>, position the reader on the node that you want to convert to an <xref:System.Xml.Linq.XElement> tree, and then create the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
 <span data-ttu-id="13e36-112">La rubrique Guide pratique [pour diffuser des fragments XML en continu avec accès aux informations d’en-tête (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md) contient des informations et un exemple sur la façon de diffuser un document plus complexe.</span><span class="sxs-lookup"><span data-stu-id="13e36-112">The topic [How to: Stream XML Fragments with Access to Header Information (Visual Basic)](how-to-stream-xml-fragments-with-access-to-header-information.md) contains information and an example on how to stream a more complex document.</span></span>  
  
 <span data-ttu-id="13e36-113">La rubrique [procédure : effectuer une transformation de diffusion en continu de documents XML volumineux (Visual Basic)](how-to-perform-streaming-transform-of-large-xml-documents.md) contient un exemple d’utilisation de LINQ to XML pour transformer des documents XML extrêmement volumineux tout en conservant un faible encombrement mémoire.</span><span class="sxs-lookup"><span data-stu-id="13e36-113">The topic [How to: Perform Streaming Transform of Large XML Documents (Visual Basic)](how-to-perform-streaming-transform-of-large-xml-documents.md) contains an example of using LINQ to XML to transform extremely large XML documents while maintaining a small memory footprint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13e36-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="13e36-114">Example</span></span>  
 <span data-ttu-id="13e36-115">Cet exemple crée une méthode d'axe personnalisée.</span><span class="sxs-lookup"><span data-stu-id="13e36-115">This example creates a custom axis method.</span></span> <span data-ttu-id="13e36-116">Vous pouvez l’interroger à l’aide d’une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="13e36-116">You can query it by using a LINQ query.</span></span> <span data-ttu-id="13e36-117">La méthode d'axe personnalisée, `StreamRootChildDoc`, est une méthode conçue spécifiquement pour lire un document qui possède un élément `Child` à répétition.</span><span class="sxs-lookup"><span data-stu-id="13e36-117">The custom axis method, `StreamRootChildDoc`, is a method that is designed specifically to read a document that has a repeating `Child` element.</span></span>  
  
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
  
 <span data-ttu-id="13e36-118">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="13e36-118">This example produces the following output:</span></span>  
  
```console  
bbb  
ccc  
```  
  
 <span data-ttu-id="13e36-119">Dans cet exemple, le document source est très petit.</span><span class="sxs-lookup"><span data-stu-id="13e36-119">In this example, the source document is very small.</span></span> <span data-ttu-id="13e36-120">Toutefois, cet exemple aurait un faible encombrement mémoire même s'il y avait des millions d'éléments `Child`.</span><span class="sxs-lookup"><span data-stu-id="13e36-120">However, even if there were millions of `Child` elements, this example would still have a small memory footprint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13e36-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13e36-121">See also</span></span>

- [<span data-ttu-id="13e36-122">Procédure pas à pas : implémentation d'IEnumerable(Of T) en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13e36-122">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>](../../language-features/control-flow/walkthrough-implementing-ienumerable-of-t.md)
- [<span data-ttu-id="13e36-123">Analyse XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="13e36-123">Parsing XML (Visual Basic)</span></span>](parsing-xml.md)

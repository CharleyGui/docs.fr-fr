---
title: Affichage de la liste de tous les nœuds dans un LINQ to XML d’arborescence
description: Vous pouvez utiliser XPath pour répertorier tous les nœuds d’une arborescence XML. Cet article fournit un exemple pour C# et Visual Basic qui répertorie les nœuds d’une arborescence. Chaque nœud est représenté par une expression XPath qui spécifie l’emplacement du nœud dans l’arborescence.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 3e934371-f4c6-458b-9f6b-f9061b596f5b
ms.openlocfilehash: b2a02beea34434da52cd8770d7f9802acf227760
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553311"
---
# <a name="how-to-list-all-nodes-in-a-tree-linq-to-xml"></a><span data-ttu-id="9bbd8-105">Affichage de la liste de tous les nœuds d’une arborescence (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="9bbd8-105">How to list all nodes in a tree (LINQ to XML)</span></span>

<span data-ttu-id="9bbd8-106">Il est parfois utile de répertorier tous les nœuds d’une arborescence, par exemple, pour savoir exactement comment une méthode ou une propriété affecte l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="9bbd8-106">Sometimes, it's helpful to list all nodes in a tree – for example, to learn exactly how a method or property affects the tree.</span></span> <span data-ttu-id="9bbd8-107">L’exemple suivant pour C# et Visual Basic répertorie les nœuds d’une arborescence.</span><span class="sxs-lookup"><span data-stu-id="9bbd8-107">The following example for C# and Visual Basic lists the nodes of a tree.</span></span> <span data-ttu-id="9bbd8-108">Chaque nœud est représenté par une expression XPath qui spécifie l’emplacement du nœud dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="9bbd8-108">Each node is represented by an XPath expression that specifies the location of the node in the tree.</span></span>

> [!NOTE]
> <span data-ttu-id="9bbd8-109">Il n’est pas particulièrement utile d’exécuter des expressions XPath à l’aide de LINQ to XML.</span><span class="sxs-lookup"><span data-stu-id="9bbd8-109">It's not particularly helpful to execute XPath expressions using LINQ to XML.</span></span> <span data-ttu-id="9bbd8-110">LINQ to XML les requêtes sont plus performantes que les expressions XPath et sont bien plus puissantes.</span><span class="sxs-lookup"><span data-stu-id="9bbd8-110">LINQ to XML queries perform better than XPath expressions and are much more powerful.</span></span> <span data-ttu-id="9bbd8-111">Toutefois, XPath fonctionne bien comme méthode d’identification des nœuds de l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="9bbd8-111">However, as a way to identify nodes in the XML tree, XPath works well.</span></span>

## <a name="example-use-xpath-to-list-all-nodes-in-a-tree"></a><span data-ttu-id="9bbd8-112">Exemple : utiliser XPath pour répertorier tous les nœuds d’une arborescence</span><span class="sxs-lookup"><span data-stu-id="9bbd8-112">Example: Use XPath to list all nodes in a tree</span></span>

<span data-ttu-id="9bbd8-113">Cet exemple a une fonction nommée `GetXPath` qui génère une expression XPath spécifique pour tout nœud de l’arborescence XML.</span><span class="sxs-lookup"><span data-stu-id="9bbd8-113">This example has a function named `GetXPath` that generates a specific XPath expression for any node in the XML tree.</span></span> <span data-ttu-id="9bbd8-114">Cela se fait même lorsque les nœuds sont dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="9bbd8-114">It does this even when nodes are in a namespace.</span></span> <span data-ttu-id="9bbd8-115">Les éléments des expressions XPath générées ont des préfixes d’espace de noms si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="9bbd8-115">The elements in the generated XPath expressions have namespace prefixes as needed.</span></span>

<span data-ttu-id="9bbd8-116">L’exemple crée d’abord une petite arborescence XML qui contient plusieurs types de nœuds.</span><span class="sxs-lookup"><span data-stu-id="9bbd8-116">The example first creates a small XML tree that contains several types of nodes.</span></span> <span data-ttu-id="9bbd8-117">Il itère ensuite au sein des nœuds et imprime l’expression XPath pour chaque nœud.</span><span class="sxs-lookup"><span data-stu-id="9bbd8-117">It then iterates through the nodes and prints the XPath expression for each node.</span></span>

<span data-ttu-id="9bbd8-118">La déclaration XML n’est pas un nœud dans l’arborescence.</span><span class="sxs-lookup"><span data-stu-id="9bbd8-118">The XML declaration isn't a node in the tree.</span></span>

<span data-ttu-id="9bbd8-119">Voici l’arborescence XML qui sert d’entrée :</span><span class="sxs-lookup"><span data-stu-id="9bbd8-119">Here is the XML tree that serves as input:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<?target data?>
<Root AttName="An Attribute" xmlns:aw="http://www.adventure-works.com">
  <!--This is a comment-->
  <Child>Text</Child>
  <Child>Other Text</Child>
  <ChildWithMixedContent>text<b>BoldText</b>otherText</ChildWithMixedContent>
  <aw:ElementInNamespace>
    <aw:ChildInNamespace />
  </aw:ElementInNamespace>
</Root>
```

<span data-ttu-id="9bbd8-120">Voici la liste des nœuds dans l’arborescence XML, comme défini par les expressions XPath :</span><span class="sxs-lookup"><span data-stu-id="9bbd8-120">Here is the list of nodes in the XML tree, as defined by XPath expressions:</span></span>

```text
/processing-instruction()
/Root
/Root/@AttName
/Root/@xmlns:aw
/Root/comment()
/Root/Child[1]
/Root/Child[1]/text()
/Root/Child[2]
/Root/Child[2]/text()
/Root/ChildWithMixedContent
/Root/ChildWithMixedContent/text()[1]
/Root/ChildWithMixedContent/b
/Root/ChildWithMixedContent/b/text()
/Root/ChildWithMixedContent/text()[2]
/Root/aw:ElementInNamespace
/Root/aw:ElementInNamespace/aw:ChildInNamespace
```

<span data-ttu-id="9bbd8-121">Voici le code de l’exemple :</span><span class="sxs-lookup"><span data-stu-id="9bbd8-121">Here is the code for the example:</span></span>

```csharp
public static class MyExtensions
{
    private static string GetQName(XElement xe)
    {
        string prefix = xe.GetPrefixOfNamespace(xe.Name.Namespace);
        if (xe.Name.Namespace == XNamespace.None || prefix == null)
            return xe.Name.LocalName.ToString();
        else
            return prefix + ":" + xe.Name.LocalName.ToString();
    }

    private static string GetQName(XAttribute xa)
    {
        string prefix =
            xa.Parent.GetPrefixOfNamespace(xa.Name.Namespace);
        if (xa.Name.Namespace == XNamespace.None || prefix == null)
            return xa.Name.ToString();
        else
            return prefix + ":" + xa.Name.LocalName;
    }

    private static string NameWithPredicate(XElement el)
    {
        if (el.Parent != null && el.Parent.Elements(el.Name).Count() != 1)
            return GetQName(el) + "[" +
                (el.ElementsBeforeSelf(el.Name).Count() + 1) + "]";
        else
            return GetQName(el);
    }

    public static string StrCat<T>(this IEnumerable<T> source,
        string separator)
    {
        return source.Aggregate(new StringBuilder(),
                   (sb, i) => sb
                       .Append(i.ToString())
                       .Append(separator),
                   s => s.ToString());
    }

    public static string GetXPath(this XObject xobj)
    {
        if (xobj.Parent == null)
        {
            XDocument doc = xobj as XDocument;
            if (doc != null)
                return ".";
            XElement el = xobj as XElement;
            if (el != null)
                return "/" + NameWithPredicate(el);
            // The XPath data model doesn't include white space text nodes
            // that are children of a document, so this method returns null.
            XText xt = xobj as XText;
            if (xt != null)
                return null;
            XComment com = xobj as XComment;
            if (com != null)
                return
                    "/" +
                    (
                        com
                        .Document
                        .Nodes()
                        .OfType<XComment>()
                        .Count() != 1 ?
                        "comment()[" +
                        (com
                        .NodesBeforeSelf()
                        .OfType<XComment>()
                        .Count() + 1) +
                        "]" :
                        "comment()"
                    );
            XProcessingInstruction pi = xobj as XProcessingInstruction;
            if (pi != null)
                return
                    "/" +
                    (
                        pi.Document.Nodes()
                        .OfType<XProcessingInstruction>()
                        .Count() != 1 ?
                        "processing-instruction()[" +
                        (pi
                        .NodesBeforeSelf()
                        .OfType<XProcessingInstruction>()
                        .Count() + 1) +
                        "]" :
                        "processing-instruction()"
                    );
            return null;
        }
        else
        {
            XElement el = xobj as XElement;
            if (el != null)
            {
                return
                    "/" +
                    el
                    .Ancestors()
                    .InDocumentOrder()
                    .Select(e => NameWithPredicate(e))
                    .StrCat("/") +
                    NameWithPredicate(el);
            }
            XAttribute at = xobj as XAttribute;
            if (at != null)
                return
                    "/" +
                    at
                    .Parent
                    .AncestorsAndSelf()
                    .InDocumentOrder()
                    .Select(e => NameWithPredicate(e))
                    .StrCat("/") +
                    "@" + GetQName(at);
            XComment com = xobj as XComment;
            if (com != null)
                return
                    "/" +
                    com
                    .Parent
                    .AncestorsAndSelf()
                    .InDocumentOrder()
                    .Select(e => NameWithPredicate(e))
                    .StrCat("/") +
                    (
                        com
                        .Parent
                        .Nodes()
                        .OfType<XComment>()
                        .Count() != 1 ?
                        "comment()[" +
                        (com
                        .NodesBeforeSelf()
                        .OfType<XComment>()
                        .Count() + 1) + "]" :
                        "comment()"
                    );
            XCData cd = xobj as XCData;
            if (cd != null)
                return
                    "/" +
                    cd
                    .Parent
                    .AncestorsAndSelf()
                    .InDocumentOrder()
                    .Select(e => NameWithPredicate(e))
                    .StrCat("/") +
                    (
                        cd
                        .Parent
                        .Nodes()
                        .OfType<XText>()
                        .Count() != 1 ?
                        "text()[" +
                        (cd
                        .NodesBeforeSelf()
                        .OfType<XText>()
                        .Count() + 1) + "]" :
                        "text()"
                    );
            XText tx = xobj as XText;
            if (tx != null)
                return
                    "/" +
                    tx
                    .Parent
                    .AncestorsAndSelf()
                    .InDocumentOrder()
                    .Select(e => NameWithPredicate(e))
                    .StrCat("/") +
                    (
                        tx
                        .Parent
                        .Nodes()
                        .OfType<XText>()
                        .Count() != 1 ?
                        "text()[" +
                        (tx
                        .NodesBeforeSelf()
                        .OfType<XText>()
                        .Count() + 1) + "]" :
                        "text()"
                    );
            XProcessingInstruction pi = xobj as XProcessingInstruction;
            if (pi != null)
                return
                    "/" +
                    pi
                    .Parent
                    .AncestorsAndSelf()
                    .InDocumentOrder()
                    .Select(e => NameWithPredicate(e))
                    .StrCat("/") +
                    (
                        pi
                        .Parent
                        .Nodes()
                        .OfType<XProcessingInstruction>()
                        .Count() != 1 ?
                        "processing-instruction()[" +
                        (pi
                        .NodesBeforeSelf()
                        .OfType<XProcessingInstruction>()
                        .Count() + 1) + "]" :
                        "processing-instruction()"
                    );
            return null;
        }
    }
}

class Program
{
    static void Main(string[] args)
    {
        XNamespace aw = "http://www.adventure-works.com";
        XDocument doc = new XDocument(
            new XDeclaration("1.0", "utf-8", "yes"),
            new XProcessingInstruction("target", "data"),
            new XElement("Root",
                new XAttribute("AttName", "An Attribute"),
                new XAttribute(XNamespace.Xmlns + "aw", aw.ToString()),
                new XComment("This is a comment"),
                new XElement("Child",
                    new XText("Text")
                ),
                new XElement("Child",
                    new XText("Other Text")
                ),
                new XElement("ChildWithMixedContent",
                    new XText("text"),
                    new XElement("b", "BoldText"),
                    new XText("otherText")
                ),
                new XElement(aw + "ElementInNamespace",
                    new XElement(aw + "ChildInNamespace")
                )
            )
        );
        doc.Save("Test.xml");
        Console.WriteLine(File.ReadAllText("Test.xml"));
        Console.WriteLine("------");
        foreach (XObject obj in doc.DescendantNodes())
        {
            Console.WriteLine(obj.GetXPath());
            XElement el = obj as XElement;
            if (el != null)
                foreach (XAttribute at in el.Attributes())
                    Console.WriteLine(at.GetXPath());
        }
    }
}
```

```vb
Module Module1
<System.Runtime.CompilerServices.Extension()> _
    Private Function StrCat(Of T)(ByVal source As IEnumerable(Of T), _
                                  ByVal separator As String) As String
        Return _
        source.Aggregate(New StringBuilder(), _
            Function(sb, i) sb _
                .Append(i.ToString()) _
                .Append(separator), _
                Function(s) s.ToString())
    End Function

    <System.Runtime.CompilerServices.Extension()> _
    Public Function GetXPath(ByVal xobj As XObject) As String
        Dim retStr As String
        If xobj.Parent Is Nothing Then
            Dim doc As XDocument = TryCast(xobj, XDocument)
            If doc IsNot Nothing Then
                Return "."
            End If
            Dim el As XElement = TryCast(xobj, XElement)
            If el IsNot Nothing Then
                Return ("/" & NameWithPredicate(el))
            End If

            ' The XPath data model doesn't include white space text nodes
            ' that are children of a document, so this method returns null.
            Dim xt As XText = TryCast(xobj, XText)
            If xt IsNot Nothing Then
                Return Nothing
            End If
            Dim com As XComment = TryCast(xobj, XComment)
            If com IsNot Nothing Then
                If com.Document().Nodes().OfType(Of XComment)().Count() <> 1 Then
                    Return "/comment()[" & (com.NodesBeforeSelf().OfType _
                        (Of XComment)().Count() + 1) & "]"
                Else
                    Return "/comment()"
                End If
            End If

            Dim pi As XProcessingInstruction = TryCast(xobj, XProcessingInstruction)
            If pi IsNot Nothing Then
                If pi.Document.Nodes().OfType(Of XProcessingInstruction)(). _
                        Count() <> 1 Then
                    Return "/processing-instruction()[" & _
                        (pi.NodesBeforeSelf().OfType(Of XProcessingInstruction)() _
                        .Count() + 1) & "]"
                Else
                    Return "/processing-instruction()"
                End If
            End If
        Else
            Dim el As XElement = TryCast(xobj, XElement)
            If el IsNot Nothing Then
                Return "/" & el.Ancestors().InDocumentOrder(). _
                    Select(Function(e) NameWithPredicate(e)) _
                    .StrCat("/") & NameWithPredicate(el)
            End If

            Dim at As XAttribute = TryCast(xobj, XAttribute)
            If at IsNot Nothing Then
                Return "/" & at.Parent().AncestorsAndSelf().InDocumentOrder(). _
                    Select(Function(e) NameWithPredicate(e)).StrCat("/") & _
                    "@" & GetQName(at)
            End If

            Dim com As XComment = TryCast(xobj, XComment)
            If com IsNot Nothing Then
                retStr = "/" & com.Parent.AncestorsAndSelf().InDocumentOrder(). _
                Select(Function(e) NameWithPredicate(e)).StrCat("/") & "comment()"
                If com.Parent().Nodes().OfType(Of XComment)().Count() <> 1 Then
                    retStr &= "[" & (com.NodesBeforeSelf().OfType(Of XComment)().Count() + 1) & "]"
                End If
                Return retStr
            End If

            Dim cd As XCData = TryCast(xobj, XCData)
            If cd IsNot Nothing Then
                retStr = "/" & cd.Parent.AncestorsAndSelf().InDocumentOrder(). _
                    Select(Function(e) NameWithPredicate(e)).StrCat("/") & "text()"
                If cd.Parent.Nodes().OfType(Of XText)().Count() <> 1 Then
                    retStr &= "[" & (cd.NodesBeforeSelf().OfType(Of XText)(). _
                        Count() + 1) & "]"
                End If
                Return retStr
            End If

            Dim tx As XText = TryCast(xobj, XText)
            If tx IsNot Nothing Then
                retStr = "/" & tx.Parent.AncestorsAndSelf().InDocumentOrder(). _
                    Select(Function(e) NameWithPredicate(e)).StrCat("/") & "text()"
                If tx.Parent.Nodes().OfType(Of XText)().Count() <> 1 Then
                    retStr &= "[" & (tx.NodesBeforeSelf().OfType(Of XText)(). _
                        Count() + 1) & "]"
                End If
                Return retStr
            End If

            Dim pi As XProcessingInstruction = TryCast(xobj, XProcessingInstruction)
            If pi IsNot Nothing Then
                retStr = "/" & pi.Parent.AncestorsAndSelf().InDocumentOrder(). _
                    Select(Function(e) NameWithPredicate(e)). _
                    StrCat("/") & "processing-instruction()"
                If pi.Parent.Nodes().OfType(Of XProcessingInstruction)().Count() <> 1 Then
                    retStr &= "[" & (pi.NodesBeforeSelf().OfType(Of XProcessingInstruction)(). _
                        Count() + 1) & "]"
                End If
            End If
        End If
        Return Nothing
    End Function

    Private Function GetQName(ByVal xe As XElement) As String
        Dim prefix As String = xe.GetPrefixOfNamespace(xe.Name.Namespace)
        If xe.Name.Namespace = XNamespace.None Or prefix Is Nothing Then
            Return xe.Name.LocalName.ToString()
        Else
            Return prefix + ":" & xe.Name.LocalName.ToString()
        End If
    End Function

    Private Function GetQName(ByVal xa As XAttribute) As String
        Dim prefix As String = _
            xa.Parent.GetPrefixOfNamespace(xa.Name.Namespace)
        If xa.Name.Namespace = XNamespace.None Or prefix Is Nothing Then
            Return xa.Name.ToString()
        Else
            Return prefix + ":" & xa.Name.LocalName
        End If
    End Function

    Public Function NameWithPredicate(ByVal el As XElement) As String
        If el.Parent IsNot Nothing AndAlso el.Parent.Elements(el.Name).Count() <> 1 Then
            Return GetQName(el) + "[" & _
                (el.ElementsBeforeSelf(el.Name).Count() + 1) & "]"
        Else
            Return GetQName(el)
        End If
    End Function

    Sub Main()
        Dim aw As XNamespace = "http://www.adventure-works.com"
        Dim doc As XDocument = _
            <?xml version='1.0' encoding="utf-8" standalone='yes'?>
            <?target data?>
            <Root AttName='An Attribute' xmlns:aw='http://www.adventure-works.com'>
                <!--This is a comment-->
                <Child>Text</Child>
                <Child>Other Text</Child>
                <ChildWithMixedContent>text<b>BoldText</b>otherText</ChildWithMixedContent>
                <aw:ElementInNamespace>
                    <aw:ChildInNamespace/>
                </aw:ElementInNamespace>
            </Root>
        doc.Save("Test.xml")
        Console.WriteLine(File.ReadAllText("Test.xml"))
        Console.WriteLine("------")
        For Each obj As XObject In doc.DescendantNodes()
            Console.WriteLine(obj.GetXPath())
            Dim el As XElement = TryCast(obj, XElement)
            If el IsNot Nothing Then
                For Each at As XAttribute In el.Attributes()
                    Console.WriteLine(at.GetXPath())
                Next
            End If
        Next
    End Sub
End Module
```

<span data-ttu-id="9bbd8-122">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="9bbd8-122">This example produces the following output:</span></span>

```output
<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<?target data?>
<Root AttName="An Attribute" xmlns:aw="http://www.adventure-works.com">
  <!--This is a comment-->
  <Child>Text</Child>
  <Child>Other Text</Child>
  <ChildWithMixedContent>text<b>BoldText</b>otherText</ChildWithMixedContent>
  <aw:ElementInNamespace>
    <aw:ChildInNamespace />
  </aw:ElementInNamespace>
</Root>
------
/processing-instruction()
/Root
/Root/@AttName
/Root/@xmlns:aw
/Root/comment()
/Root/Child[1]
/Root/Child[1]/text()
/Root/Child[2]
/Root/Child[2]/text()
/Root/ChildWithMixedContent
/Root/ChildWithMixedContent/text()[1]
/Root/ChildWithMixedContent/b
/Root/ChildWithMixedContent/b/text()
/Root/ChildWithMixedContent/text()[2]
/Root/aw:ElementInNamespace
/Root/aw:ElementInNamespace/aw:ChildInNamespace
```

---
title: Comment transformer la forme d’une arborescence XML-LINQ to XML
description: Vous pouvez utiliser la construction fonctionnelle pour modifier la forme d’un document XML. autrement dit, pour conserver les données, mais modifier des éléments tels que des noms d’éléments, des noms d’attributs et des hiérarchies.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 6b4127571d5a6a9fa8e92079424dd19eaf5a2f29
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552532"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-linq-to-xml"></a><span data-ttu-id="f8fcc-103">Comment transformer la forme d’une arborescence XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f8fcc-103">How to transform the shape of an XML tree (LINQ to XML)</span></span>

<span data-ttu-id="f8fcc-104">La *forme* d’un document XML fait référence à ses noms d’éléments, à ses noms d’attributs et aux caractéristiques de sa hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-104">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>

<span data-ttu-id="f8fcc-105">Parfois, vous devrez modifier la forme d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-105">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="f8fcc-106">Par exemple, vous devrez peut-être envoyer un document XML existant à un autre système qui requiert des noms d'éléments et d'attributs différents.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-106">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="f8fcc-107">Vous pourriez parcourir le document et supprimer et renommer les éléments selon les besoins, mais l'utilisation de la construction fonctionnelle permet de disposer d'un code plus facile à lire et à maintenir.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-107">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="f8fcc-108">Pour plus d’informations sur la construction fonctionnelle, consultez [construction fonctionnelle](functional-construction.md).</span><span class="sxs-lookup"><span data-stu-id="f8fcc-108">For more information about functional construction, see [Functional construction](functional-construction.md).</span></span>

<span data-ttu-id="f8fcc-109">Le premier exemple de cet article modifie l’organisation d’un document XML.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-109">The first example in this article changes the organization of an XML document.</span></span> <span data-ttu-id="f8fcc-110">Il déplace des éléments complexes d'un emplacement vers un autre dans l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-110">It moves complex elements from one location in the tree to another.</span></span>

<span data-ttu-id="f8fcc-111">Le deuxième exemple crée un document XML dont la forme diffère de celle du document source.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-111">The second example creates an XML document whose shape differs from that of the source document.</span></span> <span data-ttu-id="f8fcc-112">Il omet certains éléments, renomme d’autres, et modifie la casse des noms d’éléments.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-112">It omits some elements, renames others, and changes the casing of the element names.</span></span>

## <a name="example-use-embedded-query-expressions-to-change-the-shape-of-an-xml-tree"></a><span data-ttu-id="f8fcc-113">Exemple : utiliser des expressions de requête incorporées pour modifier la forme d’une arborescence XML</span><span class="sxs-lookup"><span data-stu-id="f8fcc-113">Example: Use embedded query expressions to change the shape of an XML tree</span></span>

<span data-ttu-id="f8fcc-114">L’exemple suivant modifie la forme d’un fichier XML à l’aide d’expressions de requête incorporées.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-114">The following example changes the shape of an XML file using embedded query expressions.</span></span>

<span data-ttu-id="f8fcc-115">Le document XML source pour cet exemple, [exemple de fichier XML : Customers et Orders](sample-xml-file-customers-orders.md), contient un `Customers` élément sous l' `Root` élément qui contient tous les clients.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-115">The source XML document for this example, [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md), contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="f8fcc-116">Il contient également un élément `Orders` sous l'élément `Root` qui contient toutes les commandes.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-116">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="f8fcc-117">L’exemple crée une nouvelle arborescence XML dans laquelle les commandes de chaque client sont contenues dans un `Orders` élément au sein de l' `Customer` élément.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-117">The example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="f8fcc-118">Le document d’origine contient également un `CustomerID` élément dans l' `Order` élément ; cet élément est omis de la nouvelle arborescence.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-118">The original document also contains a `CustomerID` element in the `Order` element; this element is omitted from the new tree.</span></span>

```csharp
XElement co = XElement.Load("CustomersOrders.xml");
XElement newCustOrd =
    new XElement("Root",
        from cust in co.Element("Customers").Elements("Customer")
        select new XElement("Customer",
            cust.Attributes(),
            cust.Elements(),
            new XElement("Orders",
                from ord in co.Element("Orders").Elements("Order")
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")
                select new XElement("Order",
                    ord.Attributes(),
                    ord.Element("EmployeeID"),
                    ord.Element("OrderDate"),
                    ord.Element("RequiredDate"),
                    ord.Element("ShipInfo")
                )
            )
        )
    );
Console.WriteLine(newCustOrd);
```

 ```vb
Dim co As XElement = XElement.Load("CustomersOrders.xml")
Dim newCustOrd = _
    <Root>
        <%= From cust In co.<Customers>.<Customer> _
            Select _
            <Customer>
                <%= cust.Attributes() %>
                <%= cust.Elements() %>
                <Orders>
                    <%= From ord In co.<Orders>.<Order> _
                        Where ord.<CustomerID>.Value = cust.@CustomerID _
                        Select _
                        <Order>
                            <%= ord.Attributes() %>
                            <%= ord.<EmployeeID> %>
                            <%= ord.<OrderDate> %>
                            <%= ord.<RequiredDate> %>
                            <%= ord.<ShipInfo> %>
                        </Order> _
                    %>
                </Orders>
            </Customer> _
        %>
    </Root>
Console.WriteLine(newCustOrd)
```

<span data-ttu-id="f8fcc-119">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f8fcc-119">This example produces the following output:</span></span>

```xml
<Root>
  <Customer CustomerID="GREAL">
    <CompanyName>Great Lakes Food Market</CompanyName>
    <ContactName>Howard Snyder</ContactName>
    <ContactTitle>Marketing Manager</ContactTitle>
    <Phone>(503) 555-7555</Phone>
    <FullAddress>
      <Address>2732 Baker Blvd.</Address>
      <City>Eugene</City>
      <Region>OR</Region>
      <PostalCode>97403</PostalCode>
      <Country>USA</Country>
    </FullAddress>
    <Orders />
  </Customer>
  <Customer CustomerID="HUNGC">
    <CompanyName>Hungry Coyote Import Store</CompanyName>
    <ContactName>Yoshi Latimer</ContactName>
    <ContactTitle>Sales Representative</ContactTitle>
    <Phone>(503) 555-6874</Phone>
    <Fax>(503) 555-2376</Fax>
    <FullAddress>
      <Address>City Center Plaza 516 Main St.</Address>
      <City>Elgin</City>
      <Region>OR</Region>
      <PostalCode>97827</PostalCode>
      <Country>USA</Country>
    </FullAddress>
    <Orders />
  </Customer>
  ...
</Root>
```

## <a name="example-create-a-document-whose-shape-differs-from-that-of-the-source-document"></a><span data-ttu-id="f8fcc-120">Exemple : créer un document dont la forme diffère de celle du document source</span><span class="sxs-lookup"><span data-stu-id="f8fcc-120">Example: Create a document whose shape differs from that of the source document</span></span>

<span data-ttu-id="f8fcc-121">Cet exemple renomme certains éléments et convertit certains attributs en éléments.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-121">This example renames some elements and converts some attributes to elements.</span></span> <span data-ttu-id="f8fcc-122">Elle appelle `ConvertAddress` , qui retourne une liste d' <xref:System.Xml.Linq.XElement> objets.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-122">It calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="f8fcc-123">L'argument de la méthode est une requête qui détermine l'élément complexe `Address` où l'attribut `Type` a la valeur `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="f8fcc-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span> <span data-ttu-id="f8fcc-124">L’exemple utilise un document XML [exemple de fichier XML : commande fournisseur typique](sample-xml-file-typical-purchase-order.md).</span><span class="sxs-lookup"><span data-stu-id="f8fcc-124">The example uses XML document [Sample XML file: Typical purchase order](sample-xml-file-typical-purchase-order.md).</span></span>

```csharp
static IEnumerable<XElement> ConvertAddress(XElement add)
{
    List<XElement> fragment = new List<XElement>() {
        new XElement("NAME", (string)add.Element("Name")),
        new XElement("STREET", (string)add.Element("Street")),
        new XElement("CITY", (string)add.Element("City")),
        new XElement("ST", (string)add.Element("State")),
        new XElement("POSTALCODE", (string)add.Element("Zip")),
        new XElement("COUNTRY", (string)add.Element("Country"))
    };
    return fragment;
}

static void Main(string[] args)
{
    XElement po = XElement.Load("PurchaseOrder.xml");
    XElement newPo = new XElement("PO",
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),
        ConvertAddress(
            (from el in po.Elements("Address")
            where (string)el.Attribute("Type") == "Shipping"
            select el)
            .First()
        )
    );
    Console.WriteLine(newPo);
}
```

```vb
Function ConvertAddress(ByVal add As XElement) As IEnumerable(Of XElement)
    Dim fragment = New List(Of XElement)
    fragment.Add(<NAME><%= add.<Name>.Value %></NAME>)
    fragment.Add(<STREET><%= add.<Street>.Value %></STREET>)
    fragment.Add(<CITY><%= add.<City>.Value %></CITY>)
    fragment.Add(<ST><%= add.<State>.Value %></ST>)
    fragment.Add(<POSTALCODE><%= add.<Zip>.Value %></POSTALCODE>)
    fragment.Add(<COUNTRY><%= add.<Country>.Value %></COUNTRY>)
    Return fragment
End Function

Sub Main()
    Dim po As XElement = XElement.Load("PurchaseOrder.xml")
    Dim newPo As XElement = _
        <PO>
            <ID><%= po.@PurchaseOrderNumber %></ID>
            <DATE><%= CDate(po.@OrderDate) %></DATE>
            <%= _
                ConvertAddress( _
                (From el In po.<Address> _
                Where el.@Type = "Shipping" _
                Select el) _
                .First() _
                ) _
            %>
        </PO>
    Console.WriteLine(newPo)
End Sub
```

<span data-ttu-id="f8fcc-125">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="f8fcc-125">This example produces the following output:</span></span>

```xml
<PO>
  <ID>99503</ID>
  <DATE>1999-10-20T00:00:00</DATE>
  <NAME>Ellen Adams</NAME>
  <STREET>123 Maple Street</STREET>
  <CITY>Mill Valley</CITY>
  <ST>CA</ST>
  <POSTALCODE>10999</POSTALCODE>
  <COUNTRY>USA</COUNTRY>
</PO>
```

## <a name="see-also"></a><span data-ttu-id="f8fcc-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8fcc-126">See also</span></span>

- [<span data-ttu-id="f8fcc-127">Projections et transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8fcc-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)

---
title: Comment transformer la forme d’une arborescence XML-LINQ to XML
description: Vous pouvez utiliser la construction fonctionnelle pour modifier la forme d’un document XML. autrement dit, pour conserver les données, mais modifier des éléments tels que des noms d’éléments, des noms d’attributs et des hiérarchies.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 7f78cb2542357be674d771f93825b7f4a56abea0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554505"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-linq-to-xml"></a>Comment transformer la forme d’une arborescence XML (LINQ to XML)

La *forme* d’un document XML fait référence à ses noms d’éléments, à ses noms d’attributs et aux caractéristiques de sa hiérarchie.

Parfois, vous devrez modifier la forme d'un document XML. Par exemple, vous devrez peut-être envoyer un document XML existant à un autre système qui requiert des noms d'éléments et d'attributs différents. Vous pourriez parcourir le document et supprimer et renommer les éléments selon les besoins, mais l'utilisation de la construction fonctionnelle permet de disposer d'un code plus facile à lire et à maintenir. Pour plus d’informations sur la construction fonctionnelle, consultez [construction fonctionnelle](functional-construction.md).

Le premier exemple de cet article modifie l’organisation d’un document XML. Il déplace des éléments complexes d'un emplacement vers un autre dans l'arborescence.

Le deuxième exemple crée un document XML dont la forme diffère de celle du document source. Il omet certains éléments, renomme d’autres, et modifie la casse des noms d’éléments.

## <a name="example-use-embedded-query-expressions-to-change-the-shape-of-an-xml-tree"></a>Exemple : utiliser des expressions de requête incorporées pour modifier la forme d’une arborescence XML

L’exemple suivant modifie la forme d’un fichier XML à l’aide d’expressions de requête incorporées.

Le document XML source pour cet exemple, [exemple de fichier XML : Customers et Orders](sample-xml-file-customers-orders.md), contient un `Customers` élément sous l' `Root` élément qui contient tous les clients. Il contient également un élément `Orders` sous l'élément `Root` qui contient toutes les commandes. L’exemple crée une nouvelle arborescence XML dans laquelle les commandes de chaque client sont contenues dans un `Orders` élément au sein de l' `Customer` élément. Le document d’origine contient également un `CustomerID` élément dans l' `Order` élément ; cet élément est omis de la nouvelle arborescence.

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

Cet exemple produit la sortie suivante :

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

## <a name="example-create-a-document-whose-shape-differs-from-that-of-the-source-document"></a>Exemple : créer un document dont la forme diffère de celle du document source

Cet exemple renomme certains éléments et convertit certains attributs en éléments. Elle appelle `ConvertAddress` , qui retourne une liste d' <xref:System.Xml.Linq.XElement> objets. L'argument de la méthode est une requête qui détermine l'élément complexe `Address` où l'attribut `Type` a la valeur `"Shipping"`. L’exemple utilise un document XML [exemple de fichier XML : commande fournisseur typique](sample-xml-file-typical-purchase-order.md).

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

Cet exemple produit la sortie suivante :

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

## <a name="see-also"></a>Voir aussi

- [Projections et transformations (LINQ to XML) (Visual Basic)](./work-dictionaries-linq-xml.md)

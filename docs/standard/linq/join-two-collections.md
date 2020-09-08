---
title: Comment joindre deux collections-LINQ to XML
description: Un fichier XSD peut établir des relations dans un fichier XML, pour permettre la jointure d’éléments afin de créer de nouveaux types d’éléments. Cet article fournit un exemple pour C# et Visual Basic qui joint des éléments et crée un nouveau document XML.
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
dev_langs:
- csharp
- vb
ms.openlocfilehash: 2ab74f861cfd046e202a861378b8fd8792c7bac4
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553380"
---
# <a name="how-to-join-two-collections-linq-to-xml"></a>Comment joindre deux collections (LINQ to XML)

Un fichier XSD peut établir des relations dans un fichier XML, pour permettre la jointure d’éléments afin de créer de nouveaux types d’éléments. Cet article fournit un exemple pour C# et Visual Basic qui joint des éléments et crée un nouveau document XML.

Un élément ou attribut dans un document XML peut parfois faire référence à un autre élément ou attribut. Par exemple, document XML [exemple de fichier XML : Customers et Orders](sample-xml-file-customers-orders.md) contient une liste de clients et une liste de commandes. Chaque `Customer` élément a un `CustomerID` attribut et chaque `Order` élément contient un `CustomerID` élément. La `CustomerID` valeur de l’élément dans un `Order` élément fait référence à l' `Customer` élément qui a une `CustomerID` valeur d’attribut correspondante.

L’article [exemple de fichier XSD : Customers et Orders](sample-xsd-file-customers-orders.md) contient un XSD qui peut être utilisé pour valider le `Customers and orders` document. Elle utilise les `xs:key` `xs:keyref` fonctionnalités et de XSD pour établir que l' `CustomerID` attribut de l' `Customer` élément est une clé et pour établir une relation entre la clé et l' `CustomerID` élément des  `Order` éléments.

Avec LINQ to XML, vous pouvez tirer parti de cette relation en utilisant la `join` clause pour joindre des informations sur les clients aux informations de commande.

Pour plus d’informations sur `join` , consultez [opérations de jointure (C#)](../../csharp/programming-guide/concepts/linq/join-operations.md) et [opérations de jointure (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/join-operations.md).
> [!NOTE]
> Les jointures sont effectuées à l’aide de recherches linéaires. Il n’y a pas d’index pour améliorer les performances de recherche.

## <a name="example-create-a-new-xml-document-that-has-customer-and-order-elements-joined"></a>Exemple : créer un document XML contenant `Customer` des éléments et `Order` joints

L’exemple suivant génère un nouveau document XML qui joint les `Customer` éléments de l' [exemple de fichier XML : Customers et Orders](sample-xml-file-customers-orders.md) aux `Order` éléments, et comprend l' `CompanyName` élément dans les commandes.

Avant d’exécuter la requête, l’exemple vérifie que le document est conforme au schéma de l' [exemple de fichier XSD : Customers et Orders](sample-xsd-file-customers-orders.md). Cela permet de s’assurer que la clause de jointure fonctionnera.

La requête sélectionne uniquement les commandes pour les clients dont le est `CustomerID` supérieur à « K ». Il projette de nouveaux `Order` éléments qui contiennent les informations sur les clients dans chaque commande.

```csharp
XmlSchemaSet schemas = new XmlSchemaSet();
schemas.Add("", "CustomersOrders.xsd");

Console.Write("Attempting to validate, ");
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");

bool errors = false;
custOrdDoc.Validate(schemas, (o, e) =>
                     {
                         Console.WriteLine("{0}", e.Message);
                         errors = true;
                     });
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");

if (!errors)
{
    // Join customers and orders, and create a new XML document with
    // a different shape.

    // The new document contains orders only for customers with a
    // CustomerID > 'K'
    XElement custOrd = custOrdDoc.Element("Root");
    XElement newCustOrd = new XElement("Root",
        from c in custOrd.Element("Customers").Elements("Customer")
        join o in custOrd.Element("Orders").Elements("Order")
                   on (string)c.Attribute("CustomerID") equals
                      (string)o.Element("CustomerID")
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0
        select new XElement("Order",
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),
            new XElement("CompanyName", (string)c.Element("CompanyName")),
            new XElement("ContactName", (string)c.Element("ContactName")),
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))
        )
    );
    Console.WriteLine(newCustOrd);
}
```

```vb
Public Class Program
    Public Shared errors As Boolean = False

    Public Shared Function LamValidEvent(ByVal o As Object, _
                 ByVal e As ValidationEventArgs) As Boolean
        Console.WriteLine("{0}", e.Message)
        errors = True
    End Function

    Shared Sub Main()
        Dim schemas As New XmlSchemaSet()
        schemas.Add("", "CustomersOrders.xsd")

        Console.Write("Attempting to validate, ")
        Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")

        custOrdDoc.Validate(schemas, Function(o, e) LamValidEvent(0, e))
        If errors Then
            Console.WriteLine("custOrdDoc did not validate")
        Else
            Console.WriteLine("custOrdDoc validated")
        End If

        If Not errors Then
            'Join customers and orders, and create a new XML document with
            ' a different shape.
            'The new document contains orders only for customers with a
            ' CustomerID > 'K'.
            Dim custOrd As XElement = custOrdDoc.<Root>.FirstOrDefault
            Dim newCustOrd As XElement = _
                <Root>
                    <%= From c In custOrd.<Customers>.<Customer> _
                        Join o In custOrd.<Orders>.<Order> _
                        On c.@CustomerID Equals o.<CustomerID>.Value _
                        Where c.@CustomerID.CompareTo("K") > 0 _
                        Select _
                        <Order>
                            <CustomerID><%= c.@CustomerID %></CustomerID>
                            <%= c.<CompanyName> %>
                            <%= c.<ContactName> %>
                            <%= o.<EmployeeID> %>
                            <%= o.<OrderDate> %>
                        </Order> _
                    %>
                </Root>
            Console.WriteLine(newCustOrd)
        End If
    End Sub
End Class
```

Cet exemple produit la sortie suivante :

```output
Attempting to validate, custOrdDoc validated
<Root>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-03-21T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-05-22T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-06-25T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-10-27T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>6</EmployeeID>
    <OrderDate>1997-11-10T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>4</EmployeeID>
    <OrderDate>1998-02-12T00:00:00</OrderDate>
  </Order>
</Root>
```

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
# <a name="how-to-join-two-collections-linq-to-xml"></a><span data-ttu-id="c5fdd-104">Comment joindre deux collections (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c5fdd-104">How to join two collections (LINQ to XML)</span></span>

<span data-ttu-id="c5fdd-105">Un fichier XSD peut établir des relations dans un fichier XML, pour permettre la jointure d’éléments afin de créer de nouveaux types d’éléments.</span><span class="sxs-lookup"><span data-stu-id="c5fdd-105">An XSD file can establish relationships in an XML file, to enable joining of elements to create new types of elements.</span></span> <span data-ttu-id="c5fdd-106">Cet article fournit un exemple pour C# et Visual Basic qui joint des éléments et crée un nouveau document XML.</span><span class="sxs-lookup"><span data-stu-id="c5fdd-106">This article provides an example for C# and Visual Basic that joins elements and creates a new XML document.</span></span>

<span data-ttu-id="c5fdd-107">Un élément ou attribut dans un document XML peut parfois faire référence à un autre élément ou attribut.</span><span class="sxs-lookup"><span data-stu-id="c5fdd-107">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="c5fdd-108">Par exemple, document XML [exemple de fichier XML : Customers et Orders](sample-xml-file-customers-orders.md) contient une liste de clients et une liste de commandes.</span><span class="sxs-lookup"><span data-stu-id="c5fdd-108">For example, XML document [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md) contains a list of customers and a list of orders.</span></span> <span data-ttu-id="c5fdd-109">Chaque `Customer` élément a un `CustomerID` attribut et chaque `Order` élément contient un `CustomerID` élément.</span><span class="sxs-lookup"><span data-stu-id="c5fdd-109">Every `Customer` element has a `CustomerID` attribute, and every `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="c5fdd-110">La `CustomerID` valeur de l’élément dans un `Order` élément fait référence à l' `Customer` élément qui a une `CustomerID` valeur d’attribut correspondante.</span><span class="sxs-lookup"><span data-stu-id="c5fdd-110">The `CustomerID` element value in an `Order` element refers to the `Customer` element that has a matching `CustomerID` attribute value.</span></span>

<span data-ttu-id="c5fdd-111">L’article [exemple de fichier XSD : Customers et Orders](sample-xsd-file-customers-orders.md) contient un XSD qui peut être utilisé pour valider le `Customers and orders` document.</span><span class="sxs-lookup"><span data-stu-id="c5fdd-111">The article [Sample XSD file: Customers and orders](sample-xsd-file-customers-orders.md) contains an XSD that can be used to validate the `Customers and orders` document.</span></span> <span data-ttu-id="c5fdd-112">Elle utilise les `xs:key` `xs:keyref` fonctionnalités et de XSD pour établir que l' `CustomerID` attribut de l' `Customer` élément est une clé et pour établir une relation entre la clé et l' `CustomerID` élément des  `Order` éléments.</span><span class="sxs-lookup"><span data-stu-id="c5fdd-112">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the key and the `CustomerID` element of the  `Order`elements.</span></span>

<span data-ttu-id="c5fdd-113">Avec LINQ to XML, vous pouvez tirer parti de cette relation en utilisant la `join` clause pour joindre des informations sur les clients aux informations de commande.</span><span class="sxs-lookup"><span data-stu-id="c5fdd-113">With LINQ to XML, you can take advantage of this relationship by using the `join` clause to join customer information to order information.</span></span>

<span data-ttu-id="c5fdd-114">Pour plus d’informations sur `join` , consultez [opérations de jointure (C#)](../../csharp/programming-guide/concepts/linq/join-operations.md) et [opérations de jointure (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="c5fdd-114">For more detailed information about `join`, see [Join Operations (C#)](../../csharp/programming-guide/concepts/linq/join-operations.md) and [Join Operations (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span></span>
> [!NOTE]
> <span data-ttu-id="c5fdd-115">Les jointures sont effectuées à l’aide de recherches linéaires.</span><span class="sxs-lookup"><span data-stu-id="c5fdd-115">Joins are done using linear searches.</span></span> <span data-ttu-id="c5fdd-116">Il n’y a pas d’index pour améliorer les performances de recherche.</span><span class="sxs-lookup"><span data-stu-id="c5fdd-116">There are no indexes to boost search performance.</span></span>

## <a name="example-create-a-new-xml-document-that-has-customer-and-order-elements-joined"></a><span data-ttu-id="c5fdd-117">Exemple : créer un document XML contenant `Customer` des éléments et `Order` joints</span><span class="sxs-lookup"><span data-stu-id="c5fdd-117">Example: Create a new XML document that has `Customer` and `Order` elements joined</span></span>

<span data-ttu-id="c5fdd-118">L’exemple suivant génère un nouveau document XML qui joint les `Customer` éléments de l' [exemple de fichier XML : Customers et Orders](sample-xml-file-customers-orders.md) aux `Order` éléments, et comprend l' `CompanyName` élément dans les commandes.</span><span class="sxs-lookup"><span data-stu-id="c5fdd-118">The following example generates a new XML document that joins the `Customer` elements of [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md) to the `Order` elements, and includes the `CompanyName` element in the orders.</span></span>

<span data-ttu-id="c5fdd-119">Avant d’exécuter la requête, l’exemple vérifie que le document est conforme au schéma de l' [exemple de fichier XSD : Customers et Orders](sample-xsd-file-customers-orders.md).</span><span class="sxs-lookup"><span data-stu-id="c5fdd-119">Before executing the query, the example validates that the document complies with the schema in [Sample XSD file: Customers and orders](sample-xsd-file-customers-orders.md).</span></span> <span data-ttu-id="c5fdd-120">Cela permet de s’assurer que la clause de jointure fonctionnera.</span><span class="sxs-lookup"><span data-stu-id="c5fdd-120">This ensures that the join clause will work.</span></span>

<span data-ttu-id="c5fdd-121">La requête sélectionne uniquement les commandes pour les clients dont le est `CustomerID` supérieur à « K ».</span><span class="sxs-lookup"><span data-stu-id="c5fdd-121">The query selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="c5fdd-122">Il projette de nouveaux `Order` éléments qui contiennent les informations sur les clients dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="c5fdd-122">It projects  new `Order` elements that contains the customer information within each order.</span></span>

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

<span data-ttu-id="c5fdd-123">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="c5fdd-123">This example produces the following output:</span></span>

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

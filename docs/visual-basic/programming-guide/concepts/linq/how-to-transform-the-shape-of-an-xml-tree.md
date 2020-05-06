---
title: 'Procédure : transformer la forme d’une arborescence XML'
ms.date: 07/20/2015
ms.assetid: 84b60854-48b2-452c-87f2-77d53e1d653a
ms.openlocfilehash: 24cf02d84b498fc4b41238b1adaf7316cb139a10
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796104"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-visual-basic"></a><span data-ttu-id="2f1d3-102">Comment : transformer la forme d’une arborescence XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f1d3-102">How to: Transform the Shape of an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="2f1d3-103">La *forme* d’un document XML fait référence à ses noms d’éléments, à ses noms d’attributs et aux caractéristiques de sa hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="2f1d3-104">Parfois, vous devrez modifier la forme d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="2f1d3-105">Par exemple, vous devrez peut-être envoyer un document XML existant à un autre système qui requiert des noms d'éléments et d'attributs différents.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="2f1d3-106">Vous pourriez parcourir le document et supprimer et renommer les éléments selon les besoins, mais l'utilisation de la construction fonctionnelle permet de disposer d'un code plus facile à lire et à maintenir.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="2f1d3-107">Pour plus d’informations sur la construction fonctionnelle, consultez [construction fonctionnelle (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2f1d3-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="2f1d3-108">Le premier exemple modifie l'organisation du document XML.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="2f1d3-109">Il déplace des éléments complexes d'un emplacement vers un autre dans l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="2f1d3-110">Le deuxième exemple de cette rubrique crée un document XML avec une forme différente de celle du document source.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="2f1d3-111">Il modifie la casse des noms d’éléments, renomme certains éléments et laisse certains éléments de l’arborescence source en dehors de l’arborescence transformée.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f1d3-112"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2f1d3-112">Example</span></span>  
 <span data-ttu-id="2f1d3-113">Le code suivant modifie la forme d'un fichier XML à l'aide d'expressions de requête incorporées.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="2f1d3-114">Le document XML source dans cet exemple contient un élément `Customers` sous l'élément `Root` qui contient tous les clients.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="2f1d3-115">Il contient également un élément `Orders` sous l'élément `Root` qui contient toutes les commandes.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="2f1d3-116">Cet exemple crée une nouvelle arborescence XML dans laquelle les commandes de chaque client sont contenues dans un élément `Orders` dans un élément `Customer`.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="2f1d3-117">Le document d'origine contient également un élément `CustomerID` dans l'élément `Order` ; cet élément sera supprimé du document reformé.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="2f1d3-118">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2f1d3-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="2f1d3-119">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2f1d3-119">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="2f1d3-120"> Exemple</span><span class="sxs-lookup"><span data-stu-id="2f1d3-120">Example</span></span>  
 <span data-ttu-id="2f1d3-121">Cet exemple renomme certains éléments et convertit certains attributs en éléments.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="2f1d3-122">Le code appelle `ConvertAddress`, qui renvoie une liste d'objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="2f1d3-123">L'argument de la méthode est une requête qui détermine l'élément complexe `Address` où l'attribut `Type` a la valeur `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="2f1d3-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="2f1d3-124">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="2f1d3-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span>  
  
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
  
 <span data-ttu-id="2f1d3-125">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="2f1d3-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2f1d3-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f1d3-126">See also</span></span>

- [<span data-ttu-id="2f1d3-127">Projections et transformations (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f1d3-127">Projections and Transformations (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)

---
title: 'Procédure : joindre deux collections (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: dc3cfd19d990fa81e00f4781cb15bf07eb9a80ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398049"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a><span data-ttu-id="d19c9-102">Comment : joindre deux collections (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d19c9-102">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="d19c9-103">Un élément ou attribut dans un document XML peut parfois faire référence à un autre élément ou attribut.</span><span class="sxs-lookup"><span data-stu-id="d19c9-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="d19c9-104">Par exemple, l’[Exemple de fichier XML : Clients et commandes (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md) contient une liste de clients et une liste de commandes.</span><span class="sxs-lookup"><span data-stu-id="d19c9-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="d19c9-105">Chaque élément `Customer` contient un attribut `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="d19c9-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="d19c9-106">Chaque élément `Order` contient un élément `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="d19c9-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="d19c9-107">L'élément `CustomerID` dans chaque commande fait référence à l'attribut `CustomerID` dans un client.</span><span class="sxs-lookup"><span data-stu-id="d19c9-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="d19c9-108">La rubrique [Exemple de fichier XSD : Clients et commandes](sample-xsd-file-customers-and-orders.md) contient un XSD qui peut servir à valider ce document.</span><span class="sxs-lookup"><span data-stu-id="d19c9-108">The topic [Sample XSD File: Customers and Orders](sample-xsd-file-customers-and-orders.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="d19c9-109">Il utilise les fonctionnalités `xs:key` et `xs:keyref` de XSD pour déterminer que l'attribut `CustomerID` de l'élément `Customer` est une clé et pour établir une relation entre l'élément `CustomerID` dans chaque élément `Order` et l'attribut `CustomerID` dans chaque élément `Customer`.</span><span class="sxs-lookup"><span data-stu-id="d19c9-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="d19c9-110">Avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez tirer parti de cette relation en utilisant la clause `Join`.</span><span class="sxs-lookup"><span data-stu-id="d19c9-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `Join` clause.</span></span>  
  
 <span data-ttu-id="d19c9-111">Notez que dans la mesure où aucun index n'est disponible, une telle jointure présentera de faibles performances à l'exécution.</span><span class="sxs-lookup"><span data-stu-id="d19c9-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="d19c9-112">Pour plus d’informations sur `Join` , consultez [opérations de jointure (Visual Basic)](join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d19c9-112">For more detailed information about `Join`, see [Join Operations (Visual Basic)](join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d19c9-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="d19c9-113">Example</span></span>  
 <span data-ttu-id="d19c9-114">L'exemple suivant joint les éléments `Customer` aux éléments `Order` et génère un nouveau document XML qui inclut l'élément `CompanyName` dans les commandes.</span><span class="sxs-lookup"><span data-stu-id="d19c9-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="d19c9-115">Avant d’exécuter la requête, l’exemple vérifie que le document est conforme au schéma dans [Exemple de fichier XSD : Clients et commandes](sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="d19c9-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="d19c9-116">Cela permet de s'assurer que la clause de jointure fonctionnera toujours.</span><span class="sxs-lookup"><span data-stu-id="d19c9-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="d19c9-117">Cette requête récupère d'abord tous les éléments `Customer`, puis les joint aux éléments `Order`.</span><span class="sxs-lookup"><span data-stu-id="d19c9-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="d19c9-118">Elle sélectionne uniquement les commandes pour les clients dont le `CustomerID` est supérieur à « K ».</span><span class="sxs-lookup"><span data-stu-id="d19c9-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="d19c9-119">Elle projette ensuite un nouvel élément `Order` qui contient les informations relatives aux clients dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="d19c9-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="d19c9-120">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="d19c9-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="d19c9-121">Cet exemple utilise le schéma XSD suivant : [Exemple de fichier XSD : Clients et commandes](sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="d19c9-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](sample-xsd-file-customers-and-orders.md).</span></span>  
  
 <span data-ttu-id="d19c9-122">Notez que les performances d'une telle jointure ne seront pas très bonnes.</span><span class="sxs-lookup"><span data-stu-id="d19c9-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="d19c9-123">Les jointures sont effectuées par le biais d'une recherche linéaire.</span><span class="sxs-lookup"><span data-stu-id="d19c9-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="d19c9-124">Il n'y a aucun index ou table de hachage pour améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="d19c9-124">There are no hash tables or indexes to help with performance.</span></span>  
  
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
  
 <span data-ttu-id="d19c9-125">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d19c9-125">This code produces the following output:</span></span>  
  
```console
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
  
## <a name="see-also"></a><span data-ttu-id="d19c9-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d19c9-126">See also</span></span>

- [<span data-ttu-id="d19c9-127">Techniques de requêtes avancées (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d19c9-127">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)

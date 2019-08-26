---
title: 'Procédure : Joindre deux collections (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: aa774e23cfd232709f9824826f5084fe6049ef37
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69593198"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="d8d92-102">Procédure : Joindre deux collections (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d92-102">How to: Join Two Collections (LINQ to XML) (C#)</span></span>
<span data-ttu-id="d8d92-103">Un élément ou attribut dans un document XML peut parfois faire référence à un autre élément ou attribut.</span><span class="sxs-lookup"><span data-stu-id="d8d92-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="d8d92-104">Par exemple, le document XML [Exemple de fichier XML : Clients et commandes (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) contient une liste de clients et une liste de commandes.</span><span class="sxs-lookup"><span data-stu-id="d8d92-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="d8d92-105">Chaque élément `Customer` contient un attribut `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="d8d92-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="d8d92-106">Chaque élément `Order` contient un élément `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="d8d92-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="d8d92-107">L'élément `CustomerID` dans chaque commande fait référence à l'attribut `CustomerID` dans un client.</span><span class="sxs-lookup"><span data-stu-id="d8d92-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="d8d92-108">La rubrique [Exemple de fichier XSD : Clients et commandes](./sample-xsd-file-customers-and-orders1.md) contient un XSD qui peut servir à valider ce document.</span><span class="sxs-lookup"><span data-stu-id="d8d92-108">The topic [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="d8d92-109">Il utilise les fonctionnalités `xs:key` et `xs:keyref` de XSD pour déterminer que l'attribut `CustomerID` de l'élément `Customer` est une clé et pour établir une relation entre l'élément `CustomerID` dans chaque élément `Order` et l'attribut `CustomerID` dans chaque élément `Customer`.</span><span class="sxs-lookup"><span data-stu-id="d8d92-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="d8d92-110">Avec [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], vous pouvez tirer parti de cette relation en utilisant la clause `join`.</span><span class="sxs-lookup"><span data-stu-id="d8d92-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>  
  
 <span data-ttu-id="d8d92-111">Notez que dans la mesure où aucun index n'est disponible, une telle jointure présentera de faibles performances à l'exécution.</span><span class="sxs-lookup"><span data-stu-id="d8d92-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="d8d92-112">Pour obtenir des informations détaillées sur `join`, consultez [Opérations de jointure (C#)](./join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d8d92-112">For more detailed information about `join`, see [Join Operations (C#)](./join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8d92-113">Exemples</span><span class="sxs-lookup"><span data-stu-id="d8d92-113">Example</span></span>  
 <span data-ttu-id="d8d92-114">L'exemple suivant joint les éléments `Customer` aux éléments `Order` et génère un nouveau document XML qui inclut l'élément `CompanyName` dans les commandes.</span><span class="sxs-lookup"><span data-stu-id="d8d92-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="d8d92-115">Avant d’exécuter la requête, l’exemple vérifie que le document est conforme au schéma spécifié dans [Exemple de fichier XSD : Clients et commandes](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="d8d92-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="d8d92-116">Cela permet de s'assurer que la clause de jointure fonctionnera toujours.</span><span class="sxs-lookup"><span data-stu-id="d8d92-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="d8d92-117">Cette requête récupère d'abord tous les éléments `Customer`, puis les joint aux éléments `Order`.</span><span class="sxs-lookup"><span data-stu-id="d8d92-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="d8d92-118">Elle sélectionne uniquement les commandes pour les clients dont le `CustomerID` est supérieur à « K ».</span><span class="sxs-lookup"><span data-stu-id="d8d92-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="d8d92-119">Elle projette ensuite un nouvel élément `Order` qui contient les informations relatives aux clients dans chaque commande.</span><span class="sxs-lookup"><span data-stu-id="d8d92-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="d8d92-120">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="d8d92-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="d8d92-121">Cet exemple utilise le schéma XSD suivant : [Exemple de fichier XSD : Clients et commandes](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="d8d92-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>  
  
 <span data-ttu-id="d8d92-122">Notez que les performances d'une telle jointure ne seront pas très bonnes.</span><span class="sxs-lookup"><span data-stu-id="d8d92-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="d8d92-123">Les jointures sont effectuées par le biais d'une recherche linéaire.</span><span class="sxs-lookup"><span data-stu-id="d8d92-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="d8d92-124">Il n'y a aucun index ou table de hachage pour améliorer les performances.</span><span class="sxs-lookup"><span data-stu-id="d8d92-124">There are no hash tables or indexes to help with performance.</span></span>  
  
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
  
 <span data-ttu-id="d8d92-125">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d8d92-125">This code produces the following output:</span></span>  
  
```  
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

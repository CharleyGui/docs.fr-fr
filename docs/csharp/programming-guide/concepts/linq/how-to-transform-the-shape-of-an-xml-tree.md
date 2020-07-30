---
title: Comment transformer la forme d’une arborescence XML (C#)
description: Découvrez comment transformer la forme d’une arborescence XML. La forme d’une arborescence XML fait référence à ses noms d’éléments et d’attributs, ainsi qu’à ses caractéristiques de hiérarchie.
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 4fa3cc18f235d061ae1778c177c4ac9b626f4b71
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302644"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="3f8ea-104">Comment transformer la forme d’une arborescence XML (C#)</span><span class="sxs-lookup"><span data-stu-id="3f8ea-104">How to transform the shape of an XML tree (C#)</span></span>
<span data-ttu-id="3f8ea-105">La *forme* d’un document XML fait référence à ses noms d’éléments, à ses noms d’attributs et aux caractéristiques de sa hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-105">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="3f8ea-106">Parfois, vous devrez modifier la forme d'un document XML.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-106">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="3f8ea-107">Par exemple, vous devrez peut-être envoyer un document XML existant à un autre système qui requiert des noms d'éléments et d'attributs différents.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-107">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="3f8ea-108">Vous pourriez parcourir le document et supprimer et renommer les éléments selon les besoins, mais l'utilisation de la construction fonctionnelle permet de disposer d'un code plus facile à lire et à maintenir.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-108">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="3f8ea-109">Pour plus d’informations sur la construction fonctionnelle, consultez [Construction fonctionnelle (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3f8ea-109">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="3f8ea-110">Le premier exemple modifie l'organisation du document XML.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-110">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="3f8ea-111">Il déplace des éléments complexes d'un emplacement vers un autre dans l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-111">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="3f8ea-112">Le deuxième exemple de cette rubrique crée un document XML avec une forme différente de celle du document source.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-112">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="3f8ea-113">Il modifie la casse des noms d’éléments, renomme certains éléments et laisse certains éléments de l’arborescence source en dehors de l’arborescence transformée.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-113">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f8ea-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f8ea-114">Example</span></span>  
 <span data-ttu-id="3f8ea-115">Le code suivant modifie la forme d'un fichier XML à l'aide d'expressions de requête incorporées.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-115">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="3f8ea-116">Le document XML source dans cet exemple contient un élément `Customers` sous l'élément `Root` qui contient tous les clients.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-116">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="3f8ea-117">Il contient également un élément `Orders` sous l'élément `Root` qui contient toutes les commandes.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-117">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="3f8ea-118">Cet exemple crée une nouvelle arborescence XML dans laquelle les commandes de chaque client sont contenues dans un élément `Orders` dans un élément `Customer`.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-118">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="3f8ea-119">Le document d'origine contient également un élément `CustomerID` dans l'élément `Order` ; cet élément sera supprimé du document reformé.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-119">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="3f8ea-120">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="3f8ea-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="3f8ea-121">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3f8ea-121">This code produces the following output:</span></span>  
  
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
  . . .  
```  
  
## <a name="example"></a><span data-ttu-id="3f8ea-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="3f8ea-122">Example</span></span>  
 <span data-ttu-id="3f8ea-123">Cet exemple renomme certains éléments et convertit certains attributs en éléments.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-123">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="3f8ea-124">Le code appelle `ConvertAddress`, qui renvoie une liste d'objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-124">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="3f8ea-125">L'argument de la méthode est une requête qui détermine l'élément complexe `Address` où l'attribut `Type` a la valeur `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="3f8ea-125">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="3f8ea-126">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : commande fournisseur typique (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="3f8ea-126">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
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
  
 <span data-ttu-id="3f8ea-127">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="3f8ea-127">This code produces the following output:</span></span>  
  
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

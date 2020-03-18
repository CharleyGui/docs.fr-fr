---
title: Comment valider à l’aide de XSD (LINQ à XML) (C)
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 29830457b63f36dd401a412364060339344f35cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347250"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a><span data-ttu-id="1561e-102">Comment valider à l’aide de XSD (LINQ à XML) (C)</span><span class="sxs-lookup"><span data-stu-id="1561e-102">How to validate using XSD (LINQ to XML) (C#)</span></span>
<span data-ttu-id="1561e-103">L'espace de noms <xref:System.Xml.Schema> contient des méthodes d'extension qui facilitent la validation d'une arborescence XML par rapport à un fichier XSD (XML Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="1561e-103">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="1561e-104">Pour plus d'informations, consultez la documentation sur la méthode <xref:System.Xml.Schema.Extensions.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="1561e-104">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1561e-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="1561e-105">Example</span></span>  
 <span data-ttu-id="1561e-106">L'exemple suivant crée un objet <xref:System.Xml.Schema.XmlSchemaSet>, puis valide deux objets <xref:System.Xml.Linq.XDocument> par rapport au jeu de schémas.</span><span class="sxs-lookup"><span data-stu-id="1561e-106">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="1561e-107">L'un des documents est valide, l'autre non.</span><span class="sxs-lookup"><span data-stu-id="1561e-107">One of the documents is valid, the other is not.</span></span>  
  
```csharp  
string xsdMarkup =  
    @"<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>  
       <xsd:element name='Root'>  
        <xsd:complexType>  
         <xsd:sequence>  
          <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>  
          <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>  
         </xsd:sequence>  
        </xsd:complexType>  
       </xsd:element>  
      </xsd:schema>";  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", XmlReader.Create(new StringReader(xsdMarkup)));  
  
XDocument doc1 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child2", "content1")  
    )  
);  
  
XDocument doc2 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child3", "content1")  
    )  
);  
  
Console.WriteLine("Validating doc1");  
bool errors = false;  
doc1.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc1 {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
Console.WriteLine("Validating doc2");  
errors = false;  
doc2.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc2 {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="1561e-108">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1561e-108">This example produces the following output:</span></span>  
  
```output  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="1561e-109"> Exemple</span><span class="sxs-lookup"><span data-stu-id="1561e-109">Example</span></span>  
 <span data-ttu-id="1561e-110">L’exemple suivant confirme que le document XML de l’[Exemple de fichier XML : Clients et commandes (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) est valide par rapport au schéma de l’[Exemple de fichier XSD : Clients et commandes](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="1561e-110">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) is valid per the schema from [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="1561e-111">Il modifie ensuite le document XML source.</span><span class="sxs-lookup"><span data-stu-id="1561e-111">It then modifies the source XML document.</span></span> <span data-ttu-id="1561e-112">Il modifie l'attribut `CustomerID` sur le premier client.</span><span class="sxs-lookup"><span data-stu-id="1561e-112">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="1561e-113">Après la modification, les commandes feront référence à un client qui n'existe pas ; le document XML ne sera donc plus validé.</span><span class="sxs-lookup"><span data-stu-id="1561e-113">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="1561e-114">Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="1561e-114">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="1561e-115">Cet exemple utilise le schéma XSD suivant : [Exemple de fichier XSD : Clients et commandes](./sample-xsd-file-customers-and-orders1.md).</span><span class="sxs-lookup"><span data-stu-id="1561e-115">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.WriteLine("Attempting to validate");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
// Modify the source document so that it will not validate.  
custOrdDoc.Root.Element("Orders").Element("Order").Element("CustomerID").Value = "AAAAA";  
Console.WriteLine("Attempting to validate after modification");  
errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="1561e-116">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="1561e-116">This example produces the following output:</span></span>  
  
```output  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="1561e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1561e-117">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [<span data-ttu-id="1561e-118">Création d’arborescences XML (C#)</span><span class="sxs-lookup"><span data-stu-id="1561e-118">Creating XML Trees (C#)</span></span>](creating-xml-trees-linq-to-xml-2.md)

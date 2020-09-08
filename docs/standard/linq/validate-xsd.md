---
title: Comment valider à l’aide de XSD-LINQ to XML
description: Vous pouvez utiliser des méthodes d’extension à partir de la System.Xml. Espace de noms de schéma pour valider une arborescence XML par rapport à un fichier XSD (XML Schema Definition Language).
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 275a49658ddf2524530949929a7a5f04515a8493
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553761"
---
# <a name="how-to-validate-using-xsd-linq-to-xml"></a><span data-ttu-id="98011-103">Comment valider à l’aide de XSD (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="98011-103">How to validate using XSD (LINQ to XML)</span></span>

<span data-ttu-id="98011-104">L'espace de noms <xref:System.Xml.Schema> contient des méthodes d'extension qui facilitent la validation d'une arborescence XML par rapport à un fichier XSD (XML Schema Definition Language).</span><span class="sxs-lookup"><span data-stu-id="98011-104">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="98011-105">Pour plus d'informations, consultez la documentation sur la méthode <xref:System.Xml.Schema.Extensions.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="98011-105">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>

## <a name="example-validate-xdocument-objects-against-an-xmlschemaset"></a><span data-ttu-id="98011-106">Exemple : valider des objets XDocument sur un XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="98011-106">Example: Validate XDocument objects against an XmlSchemaSet</span></span>

<span data-ttu-id="98011-107">L'exemple suivant crée un objet <xref:System.Xml.Schema.XmlSchemaSet>, puis valide deux objets <xref:System.Xml.Linq.XDocument> par rapport au jeu de schémas.</span><span class="sxs-lookup"><span data-stu-id="98011-107">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="98011-108">L’un des documents est valide, l’autre ne l’est pas.</span><span class="sxs-lookup"><span data-stu-id="98011-108">One of the documents is valid, the other isn't.</span></span>

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

```vb
Dim errors As Boolean = False

Private Sub XSDErrors(ByVal o As Object, ByVal e As ValidationEventArgs)
    Console.WriteLine("{0}", e.Message)
    errors = True
End Sub

Sub Main()
    Dim xsdMarkup As XElement = _
        <xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>
            <xsd:element name='Root'>
                <xsd:complexType>
                    <xsd:sequence>
                        <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>
                        <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>
                    </xsd:sequence>
                </xsd:complexType>
            </xsd:element>
        </xsd:schema>
    Dim schemas As XmlSchemaSet = New XmlSchemaSet()
    schemas.Add("", xsdMarkup.CreateReader)

    Dim doc1 As XDocument = _
        <?xml version='1.0'?>
        <Root>
            <Child1>content1</Child1>
            <Child2>content1</Child2>
        </Root>

    Dim doc2 As XDocument = _
        <?xml version='1.0'?>
        <Root>
            <Child1>content1</Child1>
            <Child3>content1</Child3>
        </Root>

    Console.WriteLine("Validating doc1")
    errors = False
    doc1.Validate(schemas, AddressOf XSDErrors)
    Console.WriteLine("doc1 {0}", IIf(errors = True, "did not validate", "validated"))

    Console.WriteLine()
    Console.WriteLine("Validating doc2")
    errors = False
    doc2.Validate(schemas, AddressOf XSDErrors)
    Console.WriteLine("doc2 {0}", IIf(errors = True, "did not validate", "validated"))
End Sub
```

<span data-ttu-id="98011-109">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="98011-109">This example produces the following output:</span></span>

```output
Validating doc1
doc1 validated

Validating doc2
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.
doc2 did not validate
```

## <a name="example-validate-an-xml-document-from-a-file-against-a-schema-from-a-file"></a><span data-ttu-id="98011-110">Exemple : validation d’un document XML à partir d’un fichier par rapport à un schéma à partir d’un fichier</span><span class="sxs-lookup"><span data-stu-id="98011-110">Example: Validate an XML document from a file against a schema from a file</span></span>

<span data-ttu-id="98011-111">L’exemple suivant vérifie que le document XML de l' [exemple de fichier XML : Customers et Orders](sample-xml-file-customers-orders.md) est valide pour le schéma de l' [exemple de fichier XSD : Customers et Orders](sample-xsd-file-customers-orders.md).</span><span class="sxs-lookup"><span data-stu-id="98011-111">The following example validates that the XML document from [Sample XML file: Customers and orders](sample-xml-file-customers-orders.md) is valid per the schema from [Sample XSD file: Customers and orders](sample-xsd-file-customers-orders.md).</span></span> <span data-ttu-id="98011-112">Il modifie ensuite le document XML source.</span><span class="sxs-lookup"><span data-stu-id="98011-112">It then modifies the source XML document.</span></span> <span data-ttu-id="98011-113">Il modifie l'attribut `CustomerID` sur le premier client.</span><span class="sxs-lookup"><span data-stu-id="98011-113">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="98011-114">Une fois la modification apportée, Orders fait alors référence à un client qui n’existe pas ; le document XML ne sera donc plus validé.</span><span class="sxs-lookup"><span data-stu-id="98011-114">After the change, orders will then refer to a customer that doesn't exist, so the XML document will no longer validate.</span></span>

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
// Modify the source document so that it won't validate.
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

```vb
Dim errors As Boolean = False

Private Sub XSDErrors(ByVal o As Object, ByVal e As ValidationEventArgs)
    Console.WriteLine("{0}", e.Message)
    errors = True
End Sub

Sub Main()
    Dim schemas As XmlSchemaSet = New XmlSchemaSet()
    schemas.Add("", "CustomersOrders.xsd")

    Console.WriteLine("Attempting to validate")
    Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")
    errors = False
    custOrdDoc.Validate(schemas, AddressOf XSDErrors)
    Console.WriteLine("custOrdDoc {0}", IIf(errors, "did not validate", "validated"))

    Console.WriteLine()
    ' Modify the source document so that it won't validate.
    custOrdDoc.<Root>.<Orders>.<Order>.<CustomerID>(0).Value = "AAAAA"
    Console.WriteLine("Attempting to validate after modification")
    errors = False
    custOrdDoc.Validate(schemas, AddressOf XSDErrors)
    Console.WriteLine("custOrdDoc {0}", IIf(errors, "did not validate", "validated"))
End Sub
```

<span data-ttu-id="98011-115">Cet exemple produit la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="98011-115">This example produces the following output:</span></span>

```output
Attempting to validate
custOrdDoc validated

Attempting to validate after modification
The key sequence 'AAAAA' in Keyref fails to refer to some key.
custOrdDoc did not validate
```

## <a name="see-also"></a><span data-ttu-id="98011-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98011-116">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A?displayProperty=nameWithType>
- [<span data-ttu-id="98011-117">Arborescences XML</span><span class="sxs-lookup"><span data-stu-id="98011-117">XML trees</span></span>](functional-construction.md)

---
title: Comment valider à l’aide de XSD (LINQ to XML) (C#)
description: Découvrez comment valider une arborescence XML par rapport à un fichier XSD (XML Schema Definition Language). Consultez des exemples de code et affichez des ressources supplémentaires.
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 3b4d2137d511efbe20e4d31ad27e4975d5444ec9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302631"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a>Comment valider à l’aide de XSD (LINQ to XML) (C#)
L'espace de noms <xref:System.Xml.Schema> contient des méthodes d'extension qui facilitent la validation d'une arborescence XML par rapport à un fichier XSD (XML Schema Definition Language). Pour plus d'informations, consultez la documentation sur la méthode <xref:System.Xml.Schema.Extensions.Validate%2A>.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant crée un objet <xref:System.Xml.Schema.XmlSchemaSet>, puis valide deux objets <xref:System.Xml.Linq.XDocument> par rapport au jeu de schémas. L'un des documents est valide, l'autre non.  
  
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
  
 Cet exemple produit la sortie suivante :  
  
```output  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant confirme que le document XML de l’[Exemple de fichier XML : Clients et commandes (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) est valide par rapport au schéma de l’[Exemple de fichier XSD : Clients et commandes](./sample-xsd-file-customers-and-orders1.md). Il modifie ensuite le document XML source. Il modifie l'attribut `CustomerID` sur le premier client. Après la modification, les commandes feront référence à un client qui n'existe pas ; le document XML ne sera donc plus validé.  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Clients et commandes (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
 Cet exemple utilise le schéma XSD suivant : [Exemple de fichier XSD : Clients et commandes](./sample-xsd-file-customers-and-orders1.md).  
  
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
  
 Cet exemple produit la sortie suivante :  
  
```output  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [Création d’arborescences XML (C#)](creating-xml-trees-linq-to-xml-2.md)

---
title: Validation de schéma XML (XSD) avec XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ad0b5717-3d32-41ad-a4d7-072c3e492b82
ms.openlocfilehash: 2ff8a8b85c3bfa594bd958a9a3688380885e0426
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290303"
---
# <a name="xml-schema-xsd-validation-with-xmlschemacollection"></a>Validation de schéma XML (XSD) avec XmlSchemaCollection
Vous pouvez utiliser la classe <xref:System.Xml.Schema.XmlSchemaCollection> pour valider un document XML par rapport à des schémas de langage XSD (XML Schema Definition). L'objet <xref:System.Xml.Schema.XmlSchemaCollection> améliore les performances en stockant des schémas dans la collection de sorte qu'ils ne soient pas chargés en mémoire lors de chaque validation. Si le schéma existe dans la collection de schémas, l’attribut `schemaLocation` permet de l’y rechercher.  
  
> [!IMPORTANT]
> La classe <xref:System.Xml.Schema.XmlSchemaCollection> est désormais obsolète et a été remplacée par la classe <xref:System.Xml.Schema.XmlSchemaSet>. Pour plus d’informations sur la classe <xref:System.Xml.Schema.XmlSchemaSet>, consultez [XmlSchemaSet pour la compilation de schémas](xmlschemaset-for-schema-compilation.md).  
  
 L'exemple suivant montre l'élément racine d'un fichier de données.  
  
```xml  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"  
    xmlns="urn:bookstore-schema"  
    elementFormDefault="qualified"  
    targetNamespace="urn:bookstore-schema">  
```  
  
 Pour cet exemple, la valeur de l'attribut `targetNamespace` est `urn:bookstore-schema`, qui est le même espace de noms que celui utilisé lors de l'ajout du schéma à l'objet <xref:System.Xml.Schema.XmlSchemaCollection>.  
  
 L'exemple de code suivant ajoute un schéma XML à l'objet <xref:System.Xml.Schema.XmlSchemaCollection>.  
  
```vb  
Dim xsc As New XmlSchemaCollection()  
' XML Schema.  
xsc.Add("urn:bookstore-schema", schema)
reader = New XmlTextReader(filename)  
vreader = New XmlValidatingReader(reader)  
vreader.Schemas.Add(xsc)  
```  
  
```csharp  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
// XML Schema.  
xsc.Add("urn:bookstore-schema", schema);  
reader = new XmlTextReader (filename);  
vreader = new XmlValidatingReader (reader);  
vreader.Schemas.Add(xsc);  
```  
  
 L'attribut `targetNamespace` est généralement utilisé lorsque vous ajoutez la propriété `namespaceURI` dans la méthode <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> pour l'objet <xref:System.Xml.Schema.XmlSchemaCollection>. Vous pouvez spécifier une référence null avant d'ajouter le schéma à l'objet <xref:System.Xml.Schema.XmlSchemaCollection>. Utilisez une chaîne vide ("") pour les schémas sans espace de noms. L'objet <xref:System.Xml.Schema.XmlSchemaCollection> ne peut avoir qu'un seul schéma sans espace de noms.  
  
 L'exemple de code suivant ajoute un schéma XML, HeadCount.xsd, à l'objet <xref:System.Xml.Schema.XmlSchemaCollection> et valide HeadCount.xml.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Schema  
  
Namespace ValidationSample  
  
   Class Sample  
  
      Public Shared Sub Main()  
         Dim tr As New XmlTextReader("HeadCount.xml")  
         Dim vr As New XmlValidatingReader(tr)  
  
         vr.Schemas.Add("xsdHeadCount", "HeadCount.xsd")  
         vr.ValidationType = ValidationType.Schema  
         AddHandler vr.ValidationEventHandler, AddressOf ValidationHandler  
  
         While vr.Read()  
         End While  
         Console.WriteLine("Validation finished")  
      End Sub  
      ' Main  
  
      Public Shared Sub ValidationHandler(sender As Object, args As ValidationEventArgs)  
         Console.WriteLine("***Validation error")  
         Console.WriteLine("Severity:{0}", args.Severity)  
         Console.WriteLine("Message:{0}", args.Message)  
      End Sub  
      ' ValidationHandler  
   End Class  
   ' Sample  
End Namespace  
' ValidationSample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Schema;  
  
namespace ValidationSample  
{  
   class Sample  
   {  
      public static void Main()  
      {  
         XmlTextReader tr = new XmlTextReader("HeadCount.xml");  
         XmlValidatingReader vr = new XmlValidatingReader(tr);  
  
         vr.Schemas.Add("xsdHeadCount", "HeadCount.xsd");  
         vr.ValidationType = ValidationType.Schema;  
         vr.ValidationEventHandler += new ValidationEventHandler (ValidationHandler);  
  
         while(vr.Read());  
         Console.WriteLine("Validation finished");  
      }  
  
      public static void ValidationHandler(object sender, ValidationEventArgs args)  
      {  
         Console.WriteLine("***Validation error");  
         Console.WriteLine("\tSeverity:{0}", args.Severity);  
         Console.WriteLine("\tMessage  :{0}", args.Message);  
      }  
   }  
}  
```  
  
 Le code suivant présente le contenu du fichier d'entrée, HeadCount.xml, à valider.  
  
```xml  
<!--Load HeadCount.xsd in SchemaCollection for Validation-->  
<hc:HeadCount xmlns:hc='xsdHeadCount'>  
   <Name>Waldo Pepper</Name>  
   <Name>Red Pepper</Name>  
</hc:HeadCount>  
```  
  
 Le code suivant présente le contenu du fichier de schéma XML, HeadCount.xsd, par rapport auquel la validation doit s'effectuer.  
  
```xml  
<xs:schema xmlns="xsdHeadCount" targetNamespace="xsdHeadCount" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name='HeadCount' type="HEADCOUNT"/>  
   <xs:complexType name="HEADCOUNT">  
      <xs:sequence>  
         <xs:element name='Name' type='xs:string' maxOccurs='unbounded'/>  
      </xs:sequence>  
      <xs:attribute name='division' type='xs:int' use='optional' default='8'/>  
   </xs:complexType>  
</xs:schema>  
```  
  
 L'exemple de code suivant crée un objet <xref:System.Xml.XmlValidatingReader> qui prend un objet <xref:System.Xml.XmlTextReader>. Le fichier d'entrée, sample4.xml, est validé par rapport au schéma XML sample4.xsd.  
  
```vb  
Dim tr As New XmlTextReader("sample4.xml")  
Dim vr As New XmlValidatingReader(tr)  
vr.ValidationType = ValidationType.Schema  
vr.Schemas.Add("datatypesTest", "sample4.xsd")  
AddHandler vr.ValidationEventHandler, AddressOf ValidationCallBack  
While vr.Read()  
   Console.WriteLine("NodeType: {0} NodeName: {1}", vr.NodeType, vr.Name)  
End While  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("sample4.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
vr.ValidationType = ValidationType.Schema;  
        vr.Schemas.Add("datatypesTest", "sample4.xsd");  
vr.ValidationEventHandler += new ValidationEventHandler(ValidationCallBack);  
while(vr.Read()) {  
    Console.WriteLine("NodeType: {0} NodeName: {1}", vr.NodeType, vr.Name);  
    }  
```  
  
 Le code suivant présente le contenu du fichier d'entrée, sample4.xml, à valider.  
  
```xml  
<datatypes xmlns="datatypesTest">  
    <number>  
        <number_1>123</number_1>  
    </number>  
</datatypes>  
```  
  
 Le code suivant présente le contenu du fichier de schéma XML, sample4.xsd, par rapport auquel la validation doit s'effectuer.  
  
```xml  
<xs:schema
    xmlns:xs="http://www.w3.org/2001/XMLSchema"
    xmlns:tns="datatypesTest"
    targetNamespace="datatypesTest"  
    elementFormDefault="qualified">  
  
<xs:element name = "datatypes">  
  <xs:complexType>  
    <xs:all>  
        <xs:element name="number">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="number_1" type="xs:decimal" maxOccurs="unbounded"/>  
                </xs:sequence>  
            </xs:complexType>  
        </xs:element>  
    </xs:all>  
  </xs:complexType>  
</xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.XmlParserContext>
- <xref:System.Xml.XmlValidatingReader.ValidationEventHandler?displayProperty=nameWithType>
- <xref:System.Xml.XmlValidatingReader.Schemas%2A?displayProperty=nameWithType>
- [Compilation de schéma XmlSchemaCollection](xmlschemacollection-schema-compilation.md)

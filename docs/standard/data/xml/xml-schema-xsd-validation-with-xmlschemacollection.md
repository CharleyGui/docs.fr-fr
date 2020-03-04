---
title: Validation de schéma XML (XSD) avec XmlSchemaCollection
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ad0b5717-3d32-41ad-a4d7-072c3e492b82
ms.openlocfilehash: 994153ba93848ebb120f23bdf6a979462a65142d
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159479"
---
# <a name="xml-schema-xsd-validation-with-xmlschemacollection"></a><span data-ttu-id="330cc-102">Validation de schéma XML (XSD) avec XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="330cc-102">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>
<span data-ttu-id="330cc-103">Vous pouvez utiliser la classe <xref:System.Xml.Schema.XmlSchemaCollection> pour valider un document XML par rapport à des schémas de langage XSD (XML Schema Definition).</span><span class="sxs-lookup"><span data-stu-id="330cc-103">You can use the <xref:System.Xml.Schema.XmlSchemaCollection> to validate an XML document against XML Schema definition language (XSD) schemas.</span></span> <span data-ttu-id="330cc-104">L'objet <xref:System.Xml.Schema.XmlSchemaCollection> améliore les performances en stockant des schémas dans la collection de sorte qu'ils ne soient pas chargés en mémoire lors de chaque validation.</span><span class="sxs-lookup"><span data-stu-id="330cc-104">The <xref:System.Xml.Schema.XmlSchemaCollection> improves performance by storing schemas in the collection so they are not loaded into memory each time validation occurs.</span></span> <span data-ttu-id="330cc-105">Si le schéma existe dans la collection de schémas, l’attribut `schemaLocation` permet de l’y rechercher.</span><span class="sxs-lookup"><span data-stu-id="330cc-105">If the schema exists in the schema collection, the `schemaLocation` attribute is used to look up the schema in the collection.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="330cc-106">La classe <xref:System.Xml.Schema.XmlSchemaCollection> est désormais obsolète et a été remplacée par la classe <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="330cc-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="330cc-107">Pour plus d’informations sur la classe <xref:System.Xml.Schema.XmlSchemaSet>, consultez [XmlSchemaSet pour la compilation de schémas](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="330cc-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md).</span></span>  
  
 <span data-ttu-id="330cc-108">L'exemple suivant montre l'élément racine d'un fichier de données.</span><span class="sxs-lookup"><span data-stu-id="330cc-108">The following example shows the root element of a data file.</span></span>  
  
```xml  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"  
    xmlns="urn:bookstore-schema"  
    elementFormDefault="qualified"  
    targetNamespace="urn:bookstore-schema">  
```  
  
 <span data-ttu-id="330cc-109">Pour cet exemple, la valeur de l'attribut `targetNamespace` est `urn:bookstore-schema`, qui est le même espace de noms que celui utilisé lors de l'ajout du schéma à l'objet <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="330cc-109">For this example, the value of the `targetNamespace` attribute is `urn:bookstore-schema`, which is the same namespace that is used when adding the schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span>  
  
 <span data-ttu-id="330cc-110">L'exemple de code suivant ajoute un schéma XML à l'objet <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="330cc-110">The following code example adds an XML Schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span>  
  
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
  
 <span data-ttu-id="330cc-111">L'attribut `targetNamespace` est généralement utilisé lorsque vous ajoutez la propriété `namespaceURI` dans la méthode <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> pour l'objet <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="330cc-111">The `targetNamespace` attribute is generally used when you add the `namespaceURI` property in the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method for the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span> <span data-ttu-id="330cc-112">Vous pouvez spécifier une référence null avant d'ajouter le schéma à l'objet <xref:System.Xml.Schema.XmlSchemaCollection>.</span><span class="sxs-lookup"><span data-stu-id="330cc-112">You can specify a null reference before adding the schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span> <span data-ttu-id="330cc-113">Utilisez une chaîne vide ("") pour les schémas sans espace de noms.</span><span class="sxs-lookup"><span data-stu-id="330cc-113">An empty string ("") should be used for schemas without a namespace.</span></span> <span data-ttu-id="330cc-114">L'objet <xref:System.Xml.Schema.XmlSchemaCollection> ne peut avoir qu'un seul schéma sans espace de noms.</span><span class="sxs-lookup"><span data-stu-id="330cc-114">The <xref:System.Xml.Schema.XmlSchemaCollection> can have only one schema without a namespace.</span></span>  
  
 <span data-ttu-id="330cc-115">L'exemple de code suivant ajoute un schéma XML, HeadCount.xsd, à l'objet <xref:System.Xml.Schema.XmlSchemaCollection> et valide HeadCount.xml.</span><span class="sxs-lookup"><span data-stu-id="330cc-115">The following code example adds an XML Schema, HeadCount.xsd, to the <xref:System.Xml.Schema.XmlSchemaCollection> and validates HeadCount.xml.</span></span>  
  
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
  
 <span data-ttu-id="330cc-116">Le code suivant présente le contenu du fichier d'entrée, HeadCount.xml, à valider.</span><span class="sxs-lookup"><span data-stu-id="330cc-116">The following outlines the contents of the input file, HeadCount.xml, to be validated.</span></span>  
  
```xml  
<!--Load HeadCount.xsd in SchemaCollection for Validation-->  
<hc:HeadCount xmlns:hc='xsdHeadCount'>  
   <Name>Waldo Pepper</Name>  
   <Name>Red Pepper</Name>  
</hc:HeadCount>  
```  
  
 <span data-ttu-id="330cc-117">Le code suivant présente le contenu du fichier de schéma XML, HeadCount.xsd, par rapport auquel la validation doit s'effectuer.</span><span class="sxs-lookup"><span data-stu-id="330cc-117">The following outlines the contents of the XML Schema file, HeadCount.xsd, to be validated against.</span></span>  
  
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
  
 <span data-ttu-id="330cc-118">L'exemple de code suivant crée un objet <xref:System.Xml.XmlValidatingReader> qui prend un objet <xref:System.Xml.XmlTextReader>.</span><span class="sxs-lookup"><span data-stu-id="330cc-118">The following code example creates an <xref:System.Xml.XmlValidatingReader> that takes an <xref:System.Xml.XmlTextReader>.</span></span> <span data-ttu-id="330cc-119">Le fichier d'entrée, sample4.xml, est validé par rapport au schéma XML sample4.xsd.</span><span class="sxs-lookup"><span data-stu-id="330cc-119">The input file, sample4.xml, is validated against the XML Schema, sample4.xsd.</span></span>  
  
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
  
 <span data-ttu-id="330cc-120">Le code suivant présente le contenu du fichier d'entrée, sample4.xml, à valider.</span><span class="sxs-lookup"><span data-stu-id="330cc-120">The following outlines the contents of the input file, sample4.xml, to be validated.</span></span>  
  
```xml  
<datatypes xmlns="datatypesTest">  
    <number>  
        <number_1>123</number_1>  
    </number>  
</datatypes>  
```  
  
 <span data-ttu-id="330cc-121">Le code suivant présente le contenu du fichier de schéma XML, sample4.xsd, par rapport auquel la validation doit s'effectuer.</span><span class="sxs-lookup"><span data-stu-id="330cc-121">The following outlines the contents of the XML Schema file, sample4.xsd, to be validated against.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="330cc-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="330cc-122">See also</span></span>

- <xref:System.Xml.XmlParserContext>
- <xref:System.Xml.XmlValidatingReader.ValidationEventHandler?displayProperty=nameWithType>
- <xref:System.Xml.XmlValidatingReader.Schemas%2A?displayProperty=nameWithType>
- [<span data-ttu-id="330cc-123">Compilation de schéma XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="330cc-123">XmlSchemaCollection Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemacollection-schema-compilation.md)

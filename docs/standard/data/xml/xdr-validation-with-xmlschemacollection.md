---
title: Validation par rapport à un schéma XDR à l'aide de XmlSchemaCollection
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00833027-1428-4586-83c1-42f5de3323d1
ms.openlocfilehash: 9edde2fc0da97b570162775a33c95d472cda974b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819277"
---
# <a name="xdr-validation-with-xmlschemacollection"></a><span data-ttu-id="b38b6-102">Validation par rapport à un schéma XDR à l'aide de XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="b38b6-102">XDR Validation with XmlSchemaCollection</span></span>

<span data-ttu-id="b38b6-103">Si le schéma XDR (XML-Data Reduced) par rapport auquel doit s’effectuer la validation est stocké dans **XmlSchemaCollection**, il est associé à l’URI d’espace de noms qui a été spécifié lors de l’ajout du schéma à la collection.</span><span class="sxs-lookup"><span data-stu-id="b38b6-103">If the XML-Data Reduced (XDR) schema you are validating against is stored in the **XmlSchemaCollection**, it is associated with the namespace URI specified when the schema was added to the collection.</span></span> <span data-ttu-id="b38b6-104">**XmlValidatingReader** mappe l'URI d'espace de noms du document XML au schéma correspondant à cet URI dans la collection.</span><span class="sxs-lookup"><span data-stu-id="b38b6-104">**XmlValidatingReader** maps the namespace URI in the XML document to the schema that corresponds to that URI in the collection.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b38b6-105">La classe <xref:System.Xml.Schema.XmlSchemaCollection> est désormais obsolète et a été remplacée par la classe <xref:System.Xml.Schema.XmlSchemaSet>.</span><span class="sxs-lookup"><span data-stu-id="b38b6-105">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="b38b6-106">Pour plus d’informations sur la classe <xref:System.Xml.Schema.XmlSchemaSet>, consultez [XmlSchemaSet pour la compilation de schémas](xmlschemaset-for-schema-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="b38b6-106">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](xmlschemaset-for-schema-compilation.md).</span></span>

<span data-ttu-id="b38b6-107">Par exemple, si l'élément racine du document XML est `<bookstore xmlns="urn:newbooks-schema">`, lorsque le schéma est ajouté à **XmlSchemaCollection**, il référence le même espace de noms comme suit :</span><span class="sxs-lookup"><span data-stu-id="b38b6-107">For example, if the root element of the XML document is `<bookstore xmlns="urn:newbooks-schema">`, when the schema is added to the **XmlSchemaCollection** it references the same namespace, as follows:</span></span>

```vb
xsc.Add("urn:newbooks-schema", "newbooks.xdr")
```

```csharp
xsc.Add("urn:newbooks-schema", "newbooks.xdr");
```

<span data-ttu-id="b38b6-108">L’exemple de code suivant crée un **XmlValidatingReader** qui prend **XmlTextReader** et ajoute un schéma XDR, HeadCount. XDR, à **XmlSchemaCollection**:</span><span class="sxs-lookup"><span data-stu-id="b38b6-108">The following code example creates an **XmlValidatingReader** that takes an **XmlTextReader** and adds an XDR schema, HeadCount.xdr, to the **XmlSchemaCollection**:</span></span>

```vb
Imports System.IO
Imports System.Xml
Imports System.Xml.Schema

Namespace ValidationSample

    Class Sample

        Public Shared Sub Main()
            Dim tr As New XmlTextReader("HeadCount.xml")
            Dim vr As New XmlValidatingReader(tr)

            vr.Schemas.Add("xdrHeadCount", "HeadCount.xdr")
            vr.ValidationType = ValidationType.XDR
            AddHandler vr.ValidationEventHandler, AddressOf ValidationHandler

            While vr.Read()
                PrintTypeInfo(vr)
                If vr.NodeType = XmlNodeType.Element Then
                    While vr.MoveToNextAttribute()
                        PrintTypeInfo(vr)
                    End While
                End If
            End While
            Console.WriteLine("Validation finished")
        End Sub

        Public Shared Sub PrintTypeInfo(vr As XmlValidatingReader)
            If vr.SchemaType IsNot Nothing Then
                If TypeOf vr.SchemaType Is XmlSchemaDatatype Or TypeOf vr.SchemaType Is XmlSchemaSimpleType Then
                    Dim value As Object = vr.ReadTypedValue()
                    Console.WriteLine($"{vr.NodeType}({vr.Name},{value.GetType().Name}):{value}")
                End If
            End If
        End Sub

        Public Shared Sub ValidationHandler(sender As Object, args As ValidationEventArgs)
            Console.WriteLine("**_Validation error")
            Console.WriteLine($"Severity:{args.Severity}")
            Console.WriteLine($"Message:{args.Message}")
        End Sub
    End Class
End Namespace
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
            var tr = new XmlTextReader("HeadCount.xml");
            var vr = new XmlValidatingReader(tr);

            vr.Schemas.Add("xdrHeadCount", "HeadCount.xdr");
            vr.ValidationType = ValidationType.XDR;
            vr.ValidationEventHandler += new ValidationEventHandler (ValidationHandler);

            while(vr.Read())
            {
                PrintTypeInfo(vr);
                if (vr.NodeType == XmlNodeType.Element)
                {
                   while(vr.MoveToNextAttribute())
                       PrintTypeInfo(vr);
                }
            }
            Console.WriteLine("Validation finished");
        }

        public static void PrintTypeInfo(XmlValidatingReader vr)
        {
            if (vr.SchemaType != null)
            {
                if(vr.SchemaType is XmlSchemaDatatype || vr.SchemaType is XmlSchemaSimpleType)
                {
                    object value = vr.ReadTypedValue();
                    Console.WriteLine($"{vr.NodeType}({vr.Name},{value.GetType().Name}):{value}");
                }
            }
        }

        public static void ValidationHandler(object sender, ValidationEventArgs args)
        {
            Console.WriteLine("_*_Validation error");
            Console.WriteLine($"\tSeverity:{args.Severity}");
            Console.WriteLine($"\tMessage:{args.Message}");
        }
    }
}
```

<span data-ttu-id="b38b6-109">L’exemple suivant présente le contenu du fichier d’entrée, _HeadCount.xml \*, à valider :</span><span class="sxs-lookup"><span data-stu-id="b38b6-109">The following outlines the contents of the input file, _HeadCount.xml\*, to be validated:</span></span>

```xml
<!--Load HeadCount.xdr in SchemaCollection for Validation-->
<HeadCount xmlns='xdrHeadCount'>
   <Name>Waldo Pepper</Name>
   <Name>Red Pepper</Name>
</HeadCount>
```

<span data-ttu-id="b38b6-110">Le code suivant présente le contenu du fichier de schéma XDR, *HeadCount.xdr*, par rapport auquel la validation doit s’effectuer :</span><span class="sxs-lookup"><span data-stu-id="b38b6-110">The following outlines the contents of the XDR schema file, *HeadCount.xdr*, to be validated against:</span></span>

```xml
<Schema xmlns="urn:schemas-microsoft-com:xml-data" xmlns:dt="urn:schemas-microsoft-com:datatypes">
   <ElementType name="Name" content="textOnly"/>
   <AttributeType name="Bldg" default="2"/>
   <ElementType name="HeadCount" content="eltOnly">
      <element type="Name"/>
      <attribute type="Bldg"/>
   </ElementType>
</Schema>
```

## <a name="see-also"></a><span data-ttu-id="b38b6-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b38b6-111">See also</span></span>

- <xref:System.Xml.XmlValidatingReader.ValidationType%2A>
- [<span data-ttu-id="b38b6-112">Compilation de schéma XmlSchemaCollection</span><span class="sxs-lookup"><span data-stu-id="b38b6-112">XmlSchemaCollection Schema Compilation</span></span>](xmlschemacollection-schema-compilation.md)

---
title: 'Comment : sérialiser un objet en tant que flux XML encodé selon le protocole SOAP'
description: Découvrez comment sérialiser un objet en tant que flux XML encodé selon le protocole SOAP. La classe XmlSerializer peut être utilisée pour sérialiser des classes et générer des messages SOAP encodés.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: 09f1431d05248ef3ac3fdcf24bca35ff5cc2e22b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378402"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="e7a8e-104">Comment : sérialiser un objet en tant que flux XML encodé selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="e7a8e-104">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="e7a8e-105">Un message SOAP étant basé sur du code XML, la classe <xref:System.Xml.Serialization.XmlSerializer> peut être utilisée pour sérialiser des classes et générer des messages encodés selon le protocole SOAP.</span><span class="sxs-lookup"><span data-stu-id="e7a8e-105">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="e7a8e-106">Le résultat XML est conforme à la [section 5 du document du World Wide Web Consortium (www.w3.org), « Simple Object Access Protocol (SOAP) 1.1 »](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span><span class="sxs-lookup"><span data-stu-id="e7a8e-106">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="e7a8e-107">Lorsque vous créez un service Web XML qui communique à l'aide de messages SOAP, vous pouvez personnaliser le flux de données XML en appliquant un ensemble d'attributs SOAP spéciaux aux classes et membres de classes.</span><span class="sxs-lookup"><span data-stu-id="e7a8e-107">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="e7a8e-108">Pour obtenir une liste des attributs, consultez [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="e7a8e-108">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="e7a8e-109">Pour sérialiser un objet en tant que flux de données XML encodé selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="e7a8e-109">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1. <span data-ttu-id="e7a8e-110">Créez la classe à l’aide de l’[outil XML Schema Definition (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="e7a8e-110">Create the class using the [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2. <span data-ttu-id="e7a8e-111">Appliquez un ou plusieurs des attributs spéciaux se trouvant dans `System.Xml.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="e7a8e-111">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="e7a8e-112">Consultez la liste indiquée dans « Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP ».</span><span class="sxs-lookup"><span data-stu-id="e7a8e-112">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3. <span data-ttu-id="e7a8e-113">Créez un `XmlTypeMapping` en créant un nouveau `SoapReflectionImporter` et en appelant la méthode `ImportTypeMapping` avec le type de la classe sérialisée.</span><span class="sxs-lookup"><span data-stu-id="e7a8e-113">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="e7a8e-114">L’exemple de code suivant appelle la méthode `ImportTypeMapping` de la classe `SoapReflectionImporter` pour créer un `XmlTypeMapping`.</span><span class="sxs-lookup"><span data-stu-id="e7a8e-114">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
    ```vb  
    ' Serializes a class named Group as a SOAP message.  
    Dim myTypeMapping As XmlTypeMapping =
        New SoapReflectionImporter().ImportTypeMapping(GetType(Group))  
    ```  
  
    ```csharp  
    // Serializes a class named Group as a SOAP message.  
    XmlTypeMapping myTypeMapping =
        new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
    ```  
  
4. <span data-ttu-id="e7a8e-115">Créez une instance de la classe `XmlSerializer` en passant `XmlTypeMapping` au constructeur <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29>.</span><span class="sxs-lookup"><span data-stu-id="e7a8e-115">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. <span data-ttu-id="e7a8e-116">Appelez la méthode `Serialize` ou `Deserialize`.</span><span class="sxs-lookup"><span data-stu-id="e7a8e-116">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7a8e-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7a8e-117">Example</span></span>  
  
```vb  
' Serializes a class named Group as a SOAP message.  
Dim myTypeMapping As XmlTypeMapping =
    New SoapReflectionImporter().ImportTypeMapping(GetType(Group))
Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
```  
  
```csharp  
// Serializes a class named Group as a SOAP message.  
XmlTypeMapping myTypeMapping =
    new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
```  
  
## <a name="see-also"></a><span data-ttu-id="e7a8e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7a8e-118">See also</span></span>

- [<span data-ttu-id="e7a8e-119">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="e7a8e-119">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- [<span data-ttu-id="e7a8e-120">Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="e7a8e-120">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="e7a8e-121">Sérialisation XML avec les services Web XML</span><span class="sxs-lookup"><span data-stu-id="e7a8e-121">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)
- [<span data-ttu-id="e7a8e-122">Guide pratique pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="e7a8e-122">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="e7a8e-123">Guide pratique pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="e7a8e-123">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="e7a8e-124">Guide pratique pour remplacer la sérialisation XML encodée selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="e7a8e-124">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)

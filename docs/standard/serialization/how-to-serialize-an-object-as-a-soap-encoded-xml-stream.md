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
ms.openlocfilehash: 1d38c4e334439ef41b4d4429e52cff04c6463573
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84291563"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="8017d-104">Comment : sérialiser un objet en tant que flux XML encodé selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="8017d-104">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="8017d-105">Un message SOAP étant basé sur du code XML, la classe <xref:System.Xml.Serialization.XmlSerializer> peut être utilisée pour sérialiser des classes et générer des messages encodés selon le protocole SOAP.</span><span class="sxs-lookup"><span data-stu-id="8017d-105">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="8017d-106">Le résultat XML est conforme à la [section 5 du document du World Wide Web Consortium (www.w3.org), « Simple Object Access Protocol (SOAP) 1.1 »](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span><span class="sxs-lookup"><span data-stu-id="8017d-106">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="8017d-107">Lorsque vous créez un service Web XML qui communique à l'aide de messages SOAP, vous pouvez personnaliser le flux de données XML en appliquant un ensemble d'attributs SOAP spéciaux aux classes et membres de classes.</span><span class="sxs-lookup"><span data-stu-id="8017d-107">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="8017d-108">Pour obtenir une liste des attributs, consultez [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="8017d-108">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="8017d-109">Pour sérialiser un objet en tant que flux de données XML encodé selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="8017d-109">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1. <span data-ttu-id="8017d-110">Créez la classe à l’aide de l’[outil XML Schema Definition (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8017d-110">Create the class using the [XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2. <span data-ttu-id="8017d-111">Appliquez un ou plusieurs des attributs spéciaux se trouvant dans `System.Xml.Serialization`.</span><span class="sxs-lookup"><span data-stu-id="8017d-111">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="8017d-112">Consultez la liste indiquée dans « Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP ».</span><span class="sxs-lookup"><span data-stu-id="8017d-112">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3. <span data-ttu-id="8017d-113">Créez un `XmlTypeMapping` en créant un nouveau `SoapReflectionImporter` et en appelant la méthode `ImportTypeMapping` avec le type de la classe sérialisée.</span><span class="sxs-lookup"><span data-stu-id="8017d-113">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="8017d-114">L’exemple de code suivant appelle la méthode `ImportTypeMapping` de la classe `SoapReflectionImporter` pour créer un `XmlTypeMapping`.</span><span class="sxs-lookup"><span data-stu-id="8017d-114">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
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
  
4. <span data-ttu-id="8017d-115">Créez une instance de la classe `XmlSerializer` en passant `XmlTypeMapping` au constructeur <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29>.</span><span class="sxs-lookup"><span data-stu-id="8017d-115">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. <span data-ttu-id="8017d-116">Appelez la méthode `Serialize` ou `Deserialize`.</span><span class="sxs-lookup"><span data-stu-id="8017d-116">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8017d-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="8017d-117">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8017d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8017d-118">See also</span></span>

- [<span data-ttu-id="8017d-119">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="8017d-119">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="8017d-120">Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="8017d-120">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="8017d-121">Sérialisation XML avec les services Web XML</span><span class="sxs-lookup"><span data-stu-id="8017d-121">XML Serialization with XML Web Services</span></span>](xml-serialization-with-xml-web-services.md)
- [<span data-ttu-id="8017d-122">Guide pratique pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="8017d-122">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="8017d-123">Guide pratique pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="8017d-123">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
- [<span data-ttu-id="8017d-124">Guide pratique pour remplacer la sérialisation XML encodée selon le protocole SOAP</span><span class="sxs-lookup"><span data-stu-id="8017d-124">How to: Override Encoded SOAP XML Serialization</span></span>](how-to-override-encoded-soap-xml-serialization.md)

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
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291563"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Comment : sérialiser un objet en tant que flux XML encodé selon le protocole SOAP
  
 Un message SOAP étant basé sur du code XML, la classe <xref:System.Xml.Serialization.XmlSerializer> peut être utilisée pour sérialiser des classes et générer des messages encodés selon le protocole SOAP. Le résultat XML est conforme à la [section 5 du document du World Wide Web Consortium (www.w3.org), « Simple Object Access Protocol (SOAP) 1.1 »](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512). Lorsque vous créez un service Web XML qui communique à l'aide de messages SOAP, vous pouvez personnaliser le flux de données XML en appliquant un ensemble d'attributs SOAP spéciaux aux classes et membres de classes. Pour obtenir une liste des attributs, consultez [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](attributes-that-control-encoded-soap-serialization.md).  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>Pour sérialiser un objet en tant que flux de données XML encodé selon le protocole SOAP  
  
1. Créez la classe à l’aide de l’[outil XML Schema Definition (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md).  
  
2. Appliquez un ou plusieurs des attributs spéciaux se trouvant dans `System.Xml.Serialization`. Consultez la liste indiquée dans « Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP ».  
  
3. Créez un `XmlTypeMapping` en créant un nouveau `SoapReflectionImporter` et en appelant la méthode `ImportTypeMapping` avec le type de la classe sérialisée.  
  
     L’exemple de code suivant appelle la méthode `ImportTypeMapping` de la classe `SoapReflectionImporter` pour créer un `XmlTypeMapping`.  
  
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
  
4. Créez une instance de la classe `XmlSerializer` en passant `XmlTypeMapping` au constructeur <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29>.  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. Appelez la méthode `Serialize` ou `Deserialize`.  
  
## <a name="example"></a>Exemple  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Sérialisation XML et SOAP](xml-and-soap-serialization.md)
- [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](attributes-that-control-encoded-soap-serialization.md)
- [Sérialisation XML avec les services Web XML](xml-serialization-with-xml-web-services.md)
- [Guide pratique pour sérialiser un objet](how-to-serialize-an-object.md)
- [Guide pratique pour désérialiser un objet](how-to-deserialize-an-object.md)
- [Guide pratique pour remplacer la sérialisation XML encodée selon le protocole SOAP](how-to-override-encoded-soap-xml-serialization.md)

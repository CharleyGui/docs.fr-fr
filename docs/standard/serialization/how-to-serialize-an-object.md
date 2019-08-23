---
title: 'Procédure : sérialiser un objet'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: a587a132446a5f5d74b2d534b1ca3b93ccca1480
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928988"
---
# <a name="how-to-serialize-an-object"></a>Procédure : sérialiser un objet
Pour sérialiser un objet, créez tout d'abord l'objet à sérialiser et définissez ses propriétés et champs publics. Pour ce faire, vous devez déterminer le format de transport dans lequel le flux de données XML sera stocké, sous forme de flux de données ou de fichier. Par exemple, si le flux de données XML doit être enregistré dans un formulaire permanent, créez un objet <xref:System.IO.FileStream>.  
  
> [!NOTE]
> Pour obtenir plus d’exemples de sérialisation XML, consultez [Exemples de sérialisation XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
### <a name="to-serialize-an-object"></a>Pour sérialiser un objet  
  
1. Créez l'objet et définissez ses champs et propriétés publics.  
  
2. Construisez un <xref:System.Xml.Serialization.XmlSerializer> à l'aide du type de l'objet. Pour plus d'informations, consultez les constructeurs de classe <xref:System.Xml.Serialization.XmlSerializer>.  
  
3. Appelez la méthode <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> pour générer un flux de données XML ou une représentation de fichier des propriétés et des champs publics de l'objet. L'exemple suivant illustre la création d'un fichier.  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new   
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Introduction à la sérialisation XML](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [Guide pratique : Désérialiser un objet](../../../docs/standard/serialization/how-to-deserialize-an-object.md)

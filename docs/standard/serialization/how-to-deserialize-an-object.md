---
title: Comment désérialiser un objet à l’aide de XmlSerializer
description: Découvrez comment désérialiser un objet. Le format de transport détermine s’il faut créer un objet de flux ou de fichier.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: e08ae0d77539219223650fd3bcbd1bcee4df2739
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379119"
---
# <a name="how-to-deserialize-an-object-using-xmlserializer"></a>Comment désérialiser un objet à l’aide de XmlSerializer

Lorsque vous désérialisez un objet, le format de transport vous permet de déterminer si vous créez un flux de données ou un objet de fichier. Après avoir déterminé le format de transport, vous pouvez appeler la méthode <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> ou <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A>, si nécessaire.

## <a name="to-deserialize-an-object"></a>Pour désérialiser un objet

1. Construisez un <xref:System.Xml.Serialization.XmlSerializer> à l'aide du type d'objet à désérialiser.

1. Appelez la méthode <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> pour produire un réplica de l'objet. Lors de la désérialisation, vous devez effectuer un cast de l’objet retourné vers le type de l’original, comme indiqué dans l’exemple suivant, qui désérialise l’objet à partir d’un fichier (même s’il peut également être désérialisé à partir d’un flux).

    ```vb
    ' Construct an instance of the XmlSerializer with the type
    ' of object that is being deserialized.
    Dim mySerializer As New XmlSerializer(GetType(MySerializableClass))
    ' To read the file, create a FileStream.
    Dim myFileStream As New FileStream("myFileName.xml", FileMode.Open)
    ' Call the Deserialize method and cast to the object type.
    Dim myObject = CType( _
    mySerializer.Deserialize(myFileStream), MySerializableClass)
    ```

    ```csharp
    // Construct an instance of the XmlSerializer with the type
    // of object that is being deserialized.
    var mySerializer = new XmlSerializer(typeof(MySerializableClass));
    // To read the file, create a FileStream.
    var myFileStream = new FileStream("myFileName.xml", FileMode.Open);
    // Call the Deserialize method and cast to the object type.
    var myObject = (MySerializableClass) mySerializer.Deserialize(myFileStream)
    ```

## <a name="see-also"></a>Voir aussi

- [Introduction à la sérialisation XML](introducing-xml-serialization.md)
- [Guide pratique pour sérialiser un objet](how-to-serialize-an-object.md)

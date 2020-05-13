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
# <a name="how-to-deserialize-an-object-using-xmlserializer"></a><span data-ttu-id="38010-104">Comment désérialiser un objet à l’aide de XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="38010-104">How to deserialize an object using XmlSerializer</span></span>

<span data-ttu-id="38010-105">Lorsque vous désérialisez un objet, le format de transport vous permet de déterminer si vous créez un flux de données ou un objet de fichier.</span><span class="sxs-lookup"><span data-stu-id="38010-105">When you deserialize an object, the transport format determines whether you will create a stream or file object.</span></span> <span data-ttu-id="38010-106">Après avoir déterminé le format de transport, vous pouvez appeler la méthode <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> ou <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A>, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="38010-106">After the transport format is determined, you can call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> or <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> methods, as required.</span></span>

## <a name="to-deserialize-an-object"></a><span data-ttu-id="38010-107">Pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="38010-107">To deserialize an object</span></span>

1. <span data-ttu-id="38010-108">Construisez un <xref:System.Xml.Serialization.XmlSerializer> à l'aide du type d'objet à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="38010-108">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object to deserialize.</span></span>

1. <span data-ttu-id="38010-109">Appelez la méthode <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> pour produire un réplica de l'objet.</span><span class="sxs-lookup"><span data-stu-id="38010-109">Call the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method to produce a replica of the object.</span></span> <span data-ttu-id="38010-110">Lors de la désérialisation, vous devez effectuer un cast de l’objet retourné vers le type de l’original, comme indiqué dans l’exemple suivant, qui désérialise l’objet à partir d’un fichier (même s’il peut également être désérialisé à partir d’un flux).</span><span class="sxs-lookup"><span data-stu-id="38010-110">When deserializing, you must cast the returned object to the type of the original, as shown in the following example, which deserializes the object from a file (although it could also be deserialized from a stream).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="38010-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38010-111">See also</span></span>

- [<span data-ttu-id="38010-112">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="38010-112">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="38010-113">Guide pratique pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="38010-113">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)

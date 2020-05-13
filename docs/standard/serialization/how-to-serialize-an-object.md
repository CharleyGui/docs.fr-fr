---
title: 'Comment : sérialiser un objet'
description: Cet article vous montre comment sérialiser un objet. Sélectionnez un format de transport dans lequel le flux XML est stocké, sous la forme d’un flux ou d’un fichier.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: 63446df3fa2c931c839eda91c648cee961715f93
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377554"
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="a1ce5-104">Comment : sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="a1ce5-104">How to: Serialize an Object</span></span>
<span data-ttu-id="a1ce5-105">Pour sérialiser un objet, créez tout d'abord l'objet à sérialiser et définissez ses propriétés et champs publics.</span><span class="sxs-lookup"><span data-stu-id="a1ce5-105">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="a1ce5-106">Pour ce faire, vous devez déterminer le format de transport dans lequel le flux de données XML sera stocké, sous forme de flux de données ou de fichier.</span><span class="sxs-lookup"><span data-stu-id="a1ce5-106">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="a1ce5-107">Par exemple, si le flux de données XML doit être enregistré dans un formulaire permanent, créez un objet <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="a1ce5-107">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1ce5-108">Pour obtenir plus d’exemples de sérialisation XML, consultez [Exemples de sérialisation XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="a1ce5-108">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="a1ce5-109">Pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="a1ce5-109">To serialize an object</span></span>  
  
1. <span data-ttu-id="a1ce5-110">Créez l'objet et définissez ses champs et propriétés publics.</span><span class="sxs-lookup"><span data-stu-id="a1ce5-110">Create the object and set its public fields and properties.</span></span>  
  
2. <span data-ttu-id="a1ce5-111">Construisez un <xref:System.Xml.Serialization.XmlSerializer> à l'aide du type de l'objet.</span><span class="sxs-lookup"><span data-stu-id="a1ce5-111">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="a1ce5-112">Pour plus d'informations, consultez les constructeurs de classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a1ce5-112">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3. <span data-ttu-id="a1ce5-113">Appelez la méthode <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> pour générer un flux de données XML ou une représentation de fichier des propriétés et des champs publics de l'objet.</span><span class="sxs-lookup"><span data-stu-id="a1ce5-113">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="a1ce5-114">L'exemple suivant illustre la création d'un fichier.</span><span class="sxs-lookup"><span data-stu-id="a1ce5-114">The following example creates a file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a1ce5-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1ce5-115">See also</span></span>

- [<span data-ttu-id="a1ce5-116">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="a1ce5-116">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="a1ce5-117">Guide pratique pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="a1ce5-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)

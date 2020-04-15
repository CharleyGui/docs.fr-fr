---
title: "Comment : utiliser l'outil XML Schema Definition pour générer des classes et des documents de schéma XML"
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 2bbdced0f984b653a58afba9685683e8c0891271
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389798"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="157e9-102">Comment : utiliser l'outil XML Schema Definition pour générer des classes et des documents de schéma XML</span><span class="sxs-lookup"><span data-stu-id="157e9-102">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>
<span data-ttu-id="157e9-103">L'outil XML Schema Definition (Xsd.exe) vous permet de générer un schéma XML qui décrit une classe ou de générer la classe définie par un schéma XML.</span><span class="sxs-lookup"><span data-stu-id="157e9-103">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="157e9-104">Les procédures suivantes indiquent comment exécuter ces opérations.</span><span class="sxs-lookup"><span data-stu-id="157e9-104">The following procedures show how to perform these operations.</span></span>

<span data-ttu-id="157e9-105">L’outil XML Schema Definition (Xsd.exe) se trouve habituellement dans le chemin suivant :</span><span class="sxs-lookup"><span data-stu-id="157e9-105">The XML Schema Definition tool (Xsd.exe) usually can be found in the following path:\</span></span>
<span data-ttu-id="157e9-106">_C\\: Fichiers de programme\\(x86)\\Microsoft\\SDKs\\Windows 'version' bin\\NETFX 'version' Outils\\_</span><span class="sxs-lookup"><span data-stu-id="157e9-106">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span></span>

### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="157e9-107">Pour générer des classes qui se conforment à un schéma spécifique</span><span class="sxs-lookup"><span data-stu-id="157e9-107">To generate classes that conform to a specific schema</span></span>  
  
1. <span data-ttu-id="157e9-108">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="157e9-108">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="157e9-109">Passez par exemple le schéma XML en tant qu'argument à l'outil XML Schema Definition, qui crée un ensemble de classes correspondant précisément au schéma XML :</span><span class="sxs-lookup"><span data-stu-id="157e9-109">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="157e9-110">L'outil ne peut traiter que les schémas qui référencent la spécification XML du W3C (World Wide Web Consortium) du 16 mars 2001.</span><span class="sxs-lookup"><span data-stu-id="157e9-110">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="157e9-111">En d’autres termes, l’espace dehttp://www.w3.org/2001/XMLSchemanom XML Schema doit être " comme le montre l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="157e9-111">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. <span data-ttu-id="157e9-112">Modifiez si nécessaire les classes avec les méthodes, les propriétés ou les champs.</span><span class="sxs-lookup"><span data-stu-id="157e9-112">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="157e9-113">Pour plus d’informations sur la modification d’une classe avec des attributs, consultez [Contrôle de la sérialisation XML à l’aide d’attributs](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) et [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="157e9-113">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="157e9-114">Il est souvent utile d'examiner le schéma du flux de données XML généré lorsque les instances d'une ou de plusieurs classes sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="157e9-114">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="157e9-115">Par exemple, vous pouvez publier votre schéma pour d'autres utilisateurs ou le comparer à un schéma auquel vous tentez de vous conformer.</span><span class="sxs-lookup"><span data-stu-id="157e9-115">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="157e9-116">Pour générer un document de schéma XML à partir d'un ensemble de classes</span><span class="sxs-lookup"><span data-stu-id="157e9-116">To generate an XML Schema document from a set of classes</span></span>  
  
1. <span data-ttu-id="157e9-117">Compilez la ou les classes dans une DLL.</span><span class="sxs-lookup"><span data-stu-id="157e9-117">Compile the class or classes into a DLL.</span></span>  
  
2. <span data-ttu-id="157e9-118">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="157e9-118">Open a command prompt.</span></span>  
  
3. <span data-ttu-id="157e9-119">Passez la DLL en tant qu'argument dans Xsd.exe, par exemple :</span><span class="sxs-lookup"><span data-stu-id="157e9-119">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="157e9-120">Le ou les schémas sont écrits et commencent par le nom "schema0.xsd."</span><span class="sxs-lookup"><span data-stu-id="157e9-120">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="157e9-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="157e9-121">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="157e9-122">Outil XML Schema Definition et sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="157e9-122">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="157e9-123">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="157e9-123">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="157e9-124">Outil de définition de schémas XML (Xsd.exe)</span><span class="sxs-lookup"><span data-stu-id="157e9-124">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="157e9-125">Guide pratique pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="157e9-125">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="157e9-126">Guide pratique pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="157e9-126">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)

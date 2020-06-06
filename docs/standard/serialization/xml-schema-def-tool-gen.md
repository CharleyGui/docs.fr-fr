---
title: "Comment : utiliser l'outil XML Schema Definition pour générer des classes et des documents de schéma XML"
description: Découvrez comment utiliser l’outil XML Schema Definition pour générer un schéma XML décrivant une classe ou pour générer la classe définie par un schéma XML.
ms.date: 03/30/2017
helpviewer_keywords:
- generating XML classes using XML Schema Definition tool
- generating XML Schema Document using XML Schema Definition tool
- XML Schema Definition tool, using to generate classes that conform to specific schema
- XML Schema Definition tool, using to generate XML Schema Document
ms.assetid: 51f0edc3-993d-4051-b7f2-77753694d3d1
ms.openlocfilehash: 0e4e84ea7e11b2e7a00c852d4a2075747c71267e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84288964"
---
# <a name="how-to-use-the-xml-schema-definition-tool-to-generate-classes-and-xml-schema-documents"></a><span data-ttu-id="3e540-103">Comment : utiliser l'outil XML Schema Definition pour générer des classes et des documents de schéma XML</span><span class="sxs-lookup"><span data-stu-id="3e540-103">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>
<span data-ttu-id="3e540-104">L'outil XML Schema Definition (Xsd.exe) vous permet de générer un schéma XML qui décrit une classe ou de générer la classe définie par un schéma XML.</span><span class="sxs-lookup"><span data-stu-id="3e540-104">The XML Schema Definition tool (Xsd.exe) allows you to generate an XML schema that describes a class or to generate the class defined by an XML schema.</span></span> <span data-ttu-id="3e540-105">Les procédures suivantes indiquent comment exécuter ces opérations.</span><span class="sxs-lookup"><span data-stu-id="3e540-105">The following procedures show how to perform these operations.</span></span>

<span data-ttu-id="3e540-106">L’outil XML Schema Definition (XSD. exe) se trouve généralement à l’emplacement suivant : </span><span class="sxs-lookup"><span data-stu-id="3e540-106">The XML Schema Definition tool (Xsd.exe) usually can be found in the following path:</span></span>\
<span data-ttu-id="3e540-107">_C : \\ Program Files (x86) \\ Microsoft SDK \\ Windows \\ {version} \\ bin \\ netfx {version} Tools\\_</span><span class="sxs-lookup"><span data-stu-id="3e540-107">_C:\\Program Files (x86)\\Microsoft SDKs\\Windows\\{version}\\bin\\NETFX {version} Tools\\_</span></span>

### <a name="to-generate-classes-that-conform-to-a-specific-schema"></a><span data-ttu-id="3e540-108">Pour générer des classes qui se conforment à un schéma spécifique</span><span class="sxs-lookup"><span data-stu-id="3e540-108">To generate classes that conform to a specific schema</span></span>  
  
1. <span data-ttu-id="3e540-109">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="3e540-109">Open a command prompt.</span></span>  
  
2. <span data-ttu-id="3e540-110">Passez par exemple le schéma XML en tant qu'argument à l'outil XML Schema Definition, qui crée un ensemble de classes correspondant précisément au schéma XML :</span><span class="sxs-lookup"><span data-stu-id="3e540-110">Pass the XML Schema as an argument to the XML Schema Definition tool, which creates a set of classes that are precisely matched to the XML Schema, for example:</span></span>  
  
    ```console  
    xsd mySchema.xsd  
    ```  
  
     <span data-ttu-id="3e540-111">L'outil ne peut traiter que les schémas qui référencent la spécification XML du W3C (World Wide Web Consortium) du 16 mars 2001.</span><span class="sxs-lookup"><span data-stu-id="3e540-111">The tool can only process schemas that reference the World Wide Web Consortium XML specification of March 16, 2001.</span></span> <span data-ttu-id="3e540-112">En d’autres termes, l’espace de noms du schéma XML doit être « http://www.w3.org/2001/XMLSchema », comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="3e540-112">In other words, the XML Schema namespace must be "http://www.w3.org/2001/XMLSchema" as shown in the following example.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8"?>  
    <xs:schema attributeFormDefault="qualified" elementFormDefault="qualified" targetNamespace="" xmlns:xs="http://www.w3.org/2001/XMLSchema" />  
    ```  
  
3. <span data-ttu-id="3e540-113">Modifiez si nécessaire les classes avec les méthodes, les propriétés ou les champs.</span><span class="sxs-lookup"><span data-stu-id="3e540-113">Modify the classes with methods, properties, or fields, as necessary.</span></span> <span data-ttu-id="3e540-114">Pour plus d’informations sur la modification d’une classe avec des attributs, consultez [Contrôle de la sérialisation XML à l’aide d’attributs](controlling-xml-serialization-using-attributes.md) et [Attributs qui contrôlent la sérialisation encodée selon le protocole SOAP](attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="3e540-114">For more information about modifying a class with attributes, see [Controlling XML Serialization Using Attributes](controlling-xml-serialization-using-attributes.md) and [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="3e540-115">Il est souvent utile d'examiner le schéma du flux de données XML généré lorsque les instances d'une ou de plusieurs classes sont sérialisées.</span><span class="sxs-lookup"><span data-stu-id="3e540-115">It is often useful to examine the schema of the XML stream that is generated when instances of a class (or classes) are serialized.</span></span> <span data-ttu-id="3e540-116">Par exemple, vous pouvez publier votre schéma pour d'autres utilisateurs ou le comparer à un schéma auquel vous tentez de vous conformer.</span><span class="sxs-lookup"><span data-stu-id="3e540-116">For example, you might publish your schema for others to use, or you might compare it to a schema with which you are trying to achieve conformity.</span></span>  
  
#### <a name="to-generate-an-xml-schema-document-from-a-set-of-classes"></a><span data-ttu-id="3e540-117">Pour générer un document de schéma XML à partir d'un ensemble de classes</span><span class="sxs-lookup"><span data-stu-id="3e540-117">To generate an XML Schema document from a set of classes</span></span>  
  
1. <span data-ttu-id="3e540-118">Compilez la ou les classes dans une DLL.</span><span class="sxs-lookup"><span data-stu-id="3e540-118">Compile the class or classes into a DLL.</span></span>  
  
2. <span data-ttu-id="3e540-119">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="3e540-119">Open a command prompt.</span></span>  
  
3. <span data-ttu-id="3e540-120">Passez la DLL en tant qu'argument dans Xsd.exe, par exemple :</span><span class="sxs-lookup"><span data-stu-id="3e540-120">Pass the DLL as an argument to Xsd.exe, for example:</span></span>  
  
    ```console  
    xsd MyFile.dll  
    ```  
  
     <span data-ttu-id="3e540-121">Le ou les schémas sont écrits et commencent par le nom "schema0.xsd."</span><span class="sxs-lookup"><span data-stu-id="3e540-121">The schema (or schemas) will be written, beginning with the name "schema0.xsd".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e540-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e540-122">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="3e540-123">Outil XML Schema Definition et sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="3e540-123">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="3e540-124">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="3e540-124">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="3e540-125">Outil XML Schema Definition (XSD. exe)</span><span class="sxs-lookup"><span data-stu-id="3e540-125">XML Schema Definition Tool (Xsd.exe)</span></span>](xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="3e540-126">Guide pratique pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="3e540-126">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="3e540-127">Guide pratique pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="3e540-127">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)

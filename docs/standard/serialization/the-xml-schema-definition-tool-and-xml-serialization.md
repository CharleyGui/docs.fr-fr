---
title: Outil XML Schema Definition et sérialisation XML
description: L’outil XML Schema Definition génère des fichiers de classe C# ou Visual Basic pour un schéma XSD et génère un schéma XML à partir d’une bibliothèque ou d’un fichier exécutable.
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: 258e66643dae64aec7280419911f5ac9193a2ada
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380102"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="67c7c-103">Outil XML Schema Definition et sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="67c7c-103">The XML Schema Definition Tool and XML Serialization</span></span>

<span data-ttu-id="67c7c-104">L’outil XML Schema Definition ([outil XML Schema Definition (XSD. exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) est installé avec les outils de .NET Framework dans le cadre du &reg; Kit de développement logiciel (SDK) Windows.</span><span class="sxs-lookup"><span data-stu-id="67c7c-104">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows&reg; Software Development Kit (SDK).</span></span> <span data-ttu-id="67c7c-105">L’outil a deux principaux objectifs :</span><span class="sxs-lookup"><span data-stu-id="67c7c-105">The tool is designed primarily for two purposes:</span></span>  
  
- <span data-ttu-id="67c7c-106">Générer des fichiers de classe C# ou Visual Basic conformes à un schéma de langage XSD (XML Schema Definition) spécifique.</span><span class="sxs-lookup"><span data-stu-id="67c7c-106">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="67c7c-107">L'outil considère un schéma XML comme un argument et génère un fichier qui contient plusieurs classes qui, lorsqu'elles sont sérialisées avec <xref:System.Xml.Serialization.XmlSerializer>, se conforment au schéma.</span><span class="sxs-lookup"><span data-stu-id="67c7c-107">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="67c7c-108">Pour plus d’informations sur la façon d’utiliser l’outil pour générer des classes qui se conforment à un schéma spécifique, consultez [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="67c7c-108">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
- <span data-ttu-id="67c7c-109">Générer un document de schéma XML à partir d’un fichier .dll ou .exe.</span><span class="sxs-lookup"><span data-stu-id="67c7c-109">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="67c7c-110">Pour consulter le schéma d’un ensemble de fichiers que vous avez créé ou d’un ensemble qui a été modifié avec des attributs, passez le fichier DLL ou EXE comme argument à l’outil pour générer le schéma XML.</span><span class="sxs-lookup"><span data-stu-id="67c7c-110">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="67c7c-111">Pour plus d’informations sur la façon d’utiliser l’outil pour générer un document de schéma XML à partir d’un ensemble de classes, consultez [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="67c7c-111">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
<span data-ttu-id="67c7c-112">Pour plus d’informations sur l’utilisation de l’outil, consultez [outil XML Schema Definition (XSD. exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="67c7c-112">For more information about using the tool, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67c7c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67c7c-113">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="67c7c-114">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="67c7c-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="67c7c-115">Outil XML Schema Definition (XSD. exe)</span><span class="sxs-lookup"><span data-stu-id="67c7c-115">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="67c7c-116">Guide pratique pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="67c7c-116">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="67c7c-117">Guide pratique pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="67c7c-117">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="67c7c-118">Guide pratique pour utiliser l’outil XML Schema Definition pour la génération de classes et de documents de schéma XML</span><span class="sxs-lookup"><span data-stu-id="67c7c-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)
- <span data-ttu-id="67c7c-119">[Prise en charge de la liaison de schéma XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="67c7c-119">[XML Schema Binding Support](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span></span>

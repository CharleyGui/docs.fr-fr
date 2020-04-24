---
title: Outil XML Schema Definition et sérialisation XML
ms.date: 03/30/2017
helpviewer_keywords:
- Xsd.exe
- XML serialization, XML Schema Definition tool
- XML Schema Definition tool
- serialization, XML Schema Definition tool
ms.assetid: 3c03f855-f931-47ff-bbc6-50c0367a16e4
ms.openlocfilehash: b51b9a0112893d9a7838155f4af051e7079c8cdd
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588386"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="02b54-102">Outil XML Schema Definition et sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="02b54-102">The XML Schema Definition Tool and XML Serialization</span></span>

<span data-ttu-id="02b54-103">L’outil XML Schema Definition ([outil XML Schema Definition (XSD. exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) est installé avec les outils de .NET Framework dans le cadre du kit&reg; de développement logiciel (SDK) Windows.</span><span class="sxs-lookup"><span data-stu-id="02b54-103">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows&reg; Software Development Kit (SDK).</span></span> <span data-ttu-id="02b54-104">L’outil a deux principaux objectifs :</span><span class="sxs-lookup"><span data-stu-id="02b54-104">The tool is designed primarily for two purposes:</span></span>  
  
- <span data-ttu-id="02b54-105">Générer des fichiers de classe C# ou Visual Basic conformes à un schéma de langage XSD (XML Schema Definition) spécifique.</span><span class="sxs-lookup"><span data-stu-id="02b54-105">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="02b54-106">L'outil considère un schéma XML comme un argument et génère un fichier qui contient plusieurs classes qui, lorsqu'elles sont sérialisées avec <xref:System.Xml.Serialization.XmlSerializer>, se conforment au schéma.</span><span class="sxs-lookup"><span data-stu-id="02b54-106">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="02b54-107">Pour plus d’informations sur la façon d’utiliser l’outil pour générer des classes qui se conforment à un schéma spécifique, consultez [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="02b54-107">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
- <span data-ttu-id="02b54-108">Générer un document de schéma XML à partir d’un fichier .dll ou .exe.</span><span class="sxs-lookup"><span data-stu-id="02b54-108">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="02b54-109">Pour consulter le schéma d’un ensemble de fichiers que vous avez créé ou d’un ensemble qui a été modifié avec des attributs, passez le fichier DLL ou EXE comme argument à l’outil pour générer le schéma XML.</span><span class="sxs-lookup"><span data-stu-id="02b54-109">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="02b54-110">Pour plus d’informations sur la façon d’utiliser l’outil pour générer un document de schéma XML à partir d’un ensemble de classes, consultez [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="02b54-110">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](../../../docs/standard/serialization/xml-schema-def-tool-gen.md).</span></span>  
  
<span data-ttu-id="02b54-111">Pour plus d’informations sur l’utilisation de l’outil, consultez [outil XML Schema Definition (XSD. exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="02b54-111">For more information about using the tool, see [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02b54-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02b54-112">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="02b54-113">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="02b54-113">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="02b54-114">Outil XML Schema Definition (XSD. exe)</span><span class="sxs-lookup"><span data-stu-id="02b54-114">XML Schema Definition Tool (Xsd.exe)</span></span>](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="02b54-115">Guide pratique pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="02b54-115">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="02b54-116">Guide pratique pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="02b54-116">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="02b54-117">Guide pratique pour utiliser l’outil XML Schema Definition pour la génération de classes et de documents de schéma XML</span><span class="sxs-lookup"><span data-stu-id="02b54-117">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](../../../docs/standard/serialization/xml-schema-def-tool-gen.md)
- <span data-ttu-id="02b54-118">[Prise en charge de la liaison de schéma XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="02b54-118">[XML Schema Binding Support](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span></span>

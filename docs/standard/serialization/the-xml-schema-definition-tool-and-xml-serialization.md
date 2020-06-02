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
ms.openlocfilehash: c88770403d4c2abfb5ce99f44ea1bec1f8337545
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279774"
---
# <a name="the-xml-schema-definition-tool-and-xml-serialization"></a><span data-ttu-id="a9aa9-103">Outil XML Schema Definition et sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="a9aa9-103">The XML Schema Definition Tool and XML Serialization</span></span>

<span data-ttu-id="a9aa9-104">L’outil XML Schema Definition ([outil XML Schema Definition (XSD. exe)](xml-schema-definition-tool-xsd-exe.md)) est installé avec les outils de .NET Framework dans le cadre du &reg; Kit de développement logiciel (SDK) Windows.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-104">The XML Schema Definition tool ([XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md)) is installed along with the .NET Framework tools as part of the Windows&reg; Software Development Kit (SDK).</span></span> <span data-ttu-id="a9aa9-105">L’outil a deux principaux objectifs :</span><span class="sxs-lookup"><span data-stu-id="a9aa9-105">The tool is designed primarily for two purposes:</span></span>  
  
- <span data-ttu-id="a9aa9-106">Générer des fichiers de classe C# ou Visual Basic conformes à un schéma de langage XSD (XML Schema Definition) spécifique.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-106">To generate either C# or Visual Basic class files that conform to a specific XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="a9aa9-107">L'outil considère un schéma XML comme un argument et génère un fichier qui contient plusieurs classes qui, lorsqu'elles sont sérialisées avec <xref:System.Xml.Serialization.XmlSerializer>, se conforment au schéma.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-107">The tool takes an XML Schema as an argument and outputs a file that contains a number of classes that, when serialized with the <xref:System.Xml.Serialization.XmlSerializer>, conform to the schema.</span></span> <span data-ttu-id="a9aa9-108">Pour plus d’informations sur la façon d’utiliser l’outil pour générer des classes qui se conforment à un schéma spécifique, consultez [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="a9aa9-108">For information about how to use the tool to generate classes that conform to a specific schema, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](xml-schema-def-tool-gen.md).</span></span>  
  
- <span data-ttu-id="a9aa9-109">Générer un document de schéma XML à partir d’un fichier .dll ou .exe.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-109">To generate an XML Schema document from a .dll file or .exe file.</span></span> <span data-ttu-id="a9aa9-110">Pour consulter le schéma d’un ensemble de fichiers que vous avez créé ou d’un ensemble qui a été modifié avec des attributs, passez le fichier DLL ou EXE comme argument à l’outil pour générer le schéma XML.</span><span class="sxs-lookup"><span data-stu-id="a9aa9-110">To see the schema of a set of files that you have either created or one that has been modified with attributes, pass the DLL or EXE as an argument to the tool to generate the XML schema.</span></span> <span data-ttu-id="a9aa9-111">Pour plus d’informations sur la façon d’utiliser l’outil pour générer un document de schéma XML à partir d’un ensemble de classes, consultez [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](xml-schema-def-tool-gen.md).</span><span class="sxs-lookup"><span data-stu-id="a9aa9-111">For information about how to use the tool to generate an XML Schema Document from a set of classes, see [How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents](xml-schema-def-tool-gen.md).</span></span>  
  
<span data-ttu-id="a9aa9-112">Pour plus d’informations sur l’utilisation de l’outil, consultez [outil XML Schema Definition (XSD. exe)](xml-schema-definition-tool-xsd-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a9aa9-112">For more information about using the tool, see [XML Schema Definition Tool (Xsd.exe)](xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9aa9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9aa9-113">See also</span></span>

- <xref:System.Data.DataSet>
- [<span data-ttu-id="a9aa9-114">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="a9aa9-114">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="a9aa9-115">Outil XML Schema Definition (XSD. exe)</span><span class="sxs-lookup"><span data-stu-id="a9aa9-115">XML Schema Definition Tool (Xsd.exe)</span></span>](xml-schema-definition-tool-xsd-exe.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="a9aa9-116">Guide pratique pour sérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="a9aa9-116">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="a9aa9-117">Guide pratique pour désérialiser un objet</span><span class="sxs-lookup"><span data-stu-id="a9aa9-117">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
- [<span data-ttu-id="a9aa9-118">Guide pratique pour utiliser l’outil XML Schema Definition pour la génération de classes et de documents de schéma XML</span><span class="sxs-lookup"><span data-stu-id="a9aa9-118">How to: Use the XML Schema Definition Tool to Generate Classes and XML Schema Documents</span></span>](xml-schema-def-tool-gen.md)
- <span data-ttu-id="a9aa9-119">[Prise en charge de la liaison de schéma XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a9aa9-119">[XML Schema Binding Support](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/sh1e66zd(v=vs.100))</span></span>

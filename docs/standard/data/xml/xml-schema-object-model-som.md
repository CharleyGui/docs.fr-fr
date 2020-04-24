---
title: Modèle Objet du schéma (SOM) XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a897a599-ffd1-43f9-8807-e58c8a7194cd
ms.openlocfilehash: 45bfba7bdab31b3edda59a350788e50182123ce0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709905"
---
# <a name="xml-schema-object-model-som"></a><span data-ttu-id="a2e3a-102">Modèle Objet du schéma (SOM) XML</span><span class="sxs-lookup"><span data-stu-id="a2e3a-102">XML Schema Object Model (SOM)</span></span>
<span data-ttu-id="a2e3a-103">Un schéma XML est un outil puissant et complexe permettant de créer et valider une structure dans des documents XML conformes.</span><span class="sxs-lookup"><span data-stu-id="a2e3a-103">An XML schema is a powerful and complex tool for creating and validating structure in compliant XML documents.</span></span> <span data-ttu-id="a2e3a-104">De même que la modélisation de données dans une base de données relationnelles, un schéma permet de définir la structure de documents XML en spécifiant les éléments qui peuvent y figurer, ainsi que la structure et les types que ces éléments doivent suivre pour être valides pour le schéma en question.</span><span class="sxs-lookup"><span data-stu-id="a2e3a-104">Similar to data modeling in a relational database, a schema provides a way to define the structure of XML documents, by specifying the elements that can be used in the documents, as well as the structure and types that these elements must follow in order to be valid for that specific schema.</span></span>  
  
 <span data-ttu-id="a2e3a-105">Le modèle Objet du schéma (SOM) fournit un ensemble de classes dans l'espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType> qui permettent de lire un schéma à partir d'un fichier ou de créer par programme un cache de schéma en mémoire.</span><span class="sxs-lookup"><span data-stu-id="a2e3a-105">The Schema Object Model (SOM) provides a set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that allow you to read a schema from a file or to programmatically create a schema in-memory.</span></span> <span data-ttu-id="a2e3a-106">Le schéma peut alors être parcouru, édité, compilé, validé ou enregistré dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="a2e3a-106">The schema can then be traversed, editing, compiled, validated, or written to a file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2e3a-107">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a2e3a-107">In This Section</span></span>  
 [<span data-ttu-id="a2e3a-108">Vue d'ensemble du Modèle Objet du schéma XML</span><span class="sxs-lookup"><span data-stu-id="a2e3a-108">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 <span data-ttu-id="a2e3a-109">Décrit le modèle Objet du schéma (SOM) ainsi que les fonctions et classes qu'il fournit.</span><span class="sxs-lookup"><span data-stu-id="a2e3a-109">Describes the Schema Object Model (SOM) and the features and classes it provides.</span></span>  
  
 [<span data-ttu-id="a2e3a-110">Lecture et écriture de schémas XML</span><span class="sxs-lookup"><span data-stu-id="a2e3a-110">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 <span data-ttu-id="a2e3a-111">Explique comment lire et écrire des schémas XML dans des fichiers ou d'autres sources.</span><span class="sxs-lookup"><span data-stu-id="a2e3a-111">Describes how to read and write XML schemas from files or other sources.</span></span>  
  
 [<span data-ttu-id="a2e3a-112">Création de schémas XML</span><span class="sxs-lookup"><span data-stu-id="a2e3a-112">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 <span data-ttu-id="a2e3a-113">Décrit l'utilisation des classes de l'espace de noms <xref:System.Xml.Schema?displayProperty=nameWithType> pour créer des schémas XML en mémoire.</span><span class="sxs-lookup"><span data-stu-id="a2e3a-113">Describes how to use the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace to build XML schemas in-memory.</span></span>  
  
 [<span data-ttu-id="a2e3a-114">Traversée de schémas XML</span><span class="sxs-lookup"><span data-stu-id="a2e3a-114">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 <span data-ttu-id="a2e3a-115">Explique comment parcourir un schéma XML afin d'accéder aux éléments, attributs et types stockés dans le SOM.</span><span class="sxs-lookup"><span data-stu-id="a2e3a-115">Describes how to traverse an XML schema to access the elements, attributes, and types stored in the SOM.</span></span>  
  
 [<span data-ttu-id="a2e3a-116">Modification de schémas XML</span><span class="sxs-lookup"><span data-stu-id="a2e3a-116">Editing XML Schemas</span></span>](../../../../docs/standard/data/xml/editing-xml-schemas.md)  
 <span data-ttu-id="a2e3a-117">Explique comment modifier un schéma XML.</span><span class="sxs-lookup"><span data-stu-id="a2e3a-117">Describes how to edit an XML schema.</span></span>  
  
 [<span data-ttu-id="a2e3a-118">Inclusion ou importation de schémas XML</span><span class="sxs-lookup"><span data-stu-id="a2e3a-118">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 <span data-ttu-id="a2e3a-119">Explique comment inclure ou importer d'autres schémas XML pour compléter la structure du schéma où ils sont inclus ou importés.</span><span class="sxs-lookup"><span data-stu-id="a2e3a-119">Describes how to include or import other XML schemas to supplement the structure of the schema that includes or imports them.</span></span>

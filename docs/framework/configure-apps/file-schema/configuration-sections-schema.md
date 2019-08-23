---
title: Schéma des sections de configuration
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 120733873a7ea29303fe7f82c4c324d411532897
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921210"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="d397a-102">Schéma des sections de configuration</span><span class="sxs-lookup"><span data-stu-id="d397a-102">Configuration sections schema</span></span>

<span data-ttu-id="d397a-103">Le schéma des sections de configuration contient des éléments qui définissent des paramètres personnalisés dans les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="d397a-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="d397a-104">Pour obtenir des informations générales sur les fichiers de configuration et les schémas, consultez [schéma du fichier de configuration pour le .NET Framework](index.md).</span><span class="sxs-lookup"><span data-stu-id="d397a-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

<span data-ttu-id="d397a-105">[ **\<configuration>** ](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d397a-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="d397a-106">[ **\<configSections>** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d397a-106">[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="d397a-107">[ **\<clear>** ](clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="d397a-107">[**\<clear>**](clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="d397a-108">[ **\<remove>** ](remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="d397a-108">[**\<remove>**](remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="d397a-109">[ **\<section>** ](section-element.md) </span><span class="sxs-lookup"><span data-stu-id="d397a-109">[**\<section>**](section-element.md) </span></span>  
[<span data-ttu-id="d397a-110"> **\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="d397a-110">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="d397a-111">Description</span><span class="sxs-lookup"><span data-stu-id="d397a-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="d397a-112">Effacer > pour  **\<**  **configSections>\<** </span><span class="sxs-lookup"><span data-stu-id="d397a-112">**\<clear>** for **\<configSections>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="d397a-113">Efface toutes les sections et tous les groupes de sections précédemment définis.</span><span class="sxs-lookup"><span data-stu-id="d397a-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="d397a-114"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="d397a-114">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="d397a-115">Efface toutes les sections et tous les groupes de sections précédemment définis.</span><span class="sxs-lookup"><span data-stu-id="d397a-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="d397a-116"> **\<configSections>** </span><span class="sxs-lookup"><span data-stu-id="d397a-116">**\<configSections>**</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="d397a-117">Contient la section de configuration et les déclarations d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d397a-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="d397a-118">supprimer > pour  **\<**  **configSections>\<** </span><span class="sxs-lookup"><span data-stu-id="d397a-118">**\<remove>** for **\<configSections>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="d397a-119">Supprime un groupe de sections ou de sections prédéfini.</span><span class="sxs-lookup"><span data-stu-id="d397a-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="d397a-120">> de section pour  **\<configSections >** et  **\<sectionGroup >**  **\<** </span><span class="sxs-lookup"><span data-stu-id="d397a-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="d397a-121">Contient une déclaration de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="d397a-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="d397a-122">> sectionGroup pour  **\<**  **configSections>\<** </span><span class="sxs-lookup"><span data-stu-id="d397a-122">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="d397a-123">Définit un espace de noms pour les sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="d397a-123">Defines a namespace for configuration sections.</span></span> |

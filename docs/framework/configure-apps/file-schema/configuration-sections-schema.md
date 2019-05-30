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
ms.openlocfilehash: c7559a95099608ea462c838591ddb43e18d8f80c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301231"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="2b83c-102">Schéma des sections de configuration</span><span class="sxs-lookup"><span data-stu-id="2b83c-102">Configuration sections schema</span></span>

<span data-ttu-id="2b83c-103">Le schéma des sections de configuration contient des éléments qui définissent les paramètres personnalisés dans les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="2b83c-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="2b83c-104">Pour obtenir des informations générales sur les fichiers de configuration et les schémas, consultez [schéma de fichier de Configuration pour le .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="2b83c-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="2b83c-105">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2b83c-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="2b83c-106">[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="2b83c-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="2b83c-107">[ **\<clear>** ](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="2b83c-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="2b83c-108">[ **\<remove>** ](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="2b83c-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="2b83c-109">[ **\<section>** ](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="2b83c-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="2b83c-110"> *\*\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="2b83c-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="2b83c-111">Description</span><span class="sxs-lookup"><span data-stu-id="2b83c-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="2b83c-112"> *\*\<Désactivez >** pour  *\*\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="2b83c-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="2b83c-113">Efface toutes les sections précédemment définies et les groupes de sections.</span><span class="sxs-lookup"><span data-stu-id="2b83c-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="2b83c-114"> *\*\<clear>** </span><span class="sxs-lookup"><span data-stu-id="2b83c-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="2b83c-115">Efface toutes les sections précédemment définies et les groupes de sections.</span><span class="sxs-lookup"><span data-stu-id="2b83c-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="2b83c-116"> *\*\<configSections>** </span><span class="sxs-lookup"><span data-stu-id="2b83c-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="2b83c-117">Contient des déclarations d’espace de noms et de la section de configuration.</span><span class="sxs-lookup"><span data-stu-id="2b83c-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="2b83c-118"> *\*\<Supprimer >** pour  *\*\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="2b83c-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="2b83c-119">Supprime une section prédéfinie ou le groupe de section.</span><span class="sxs-lookup"><span data-stu-id="2b83c-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="2b83c-120"> *\*\<section >** pour  *\*\<configSections >** et  *\*\<sectionGroup >** </span><span class="sxs-lookup"><span data-stu-id="2b83c-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="2b83c-121">Contient une déclaration de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="2b83c-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="2b83c-122"> *\*\<sectionGroup >** pour  *\*\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="2b83c-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="2b83c-123">Définit un espace de noms pour les sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="2b83c-123">Defines a namespace for configuration sections.</span></span> |

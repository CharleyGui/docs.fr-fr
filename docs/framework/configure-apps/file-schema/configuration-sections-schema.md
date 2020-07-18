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
ms.openlocfilehash: fc43a9c32ba33629b6e89120cf57f6d212ab3a56
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441659"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="fa5cb-102">Schéma des sections de configuration</span><span class="sxs-lookup"><span data-stu-id="fa5cb-102">Configuration sections schema</span></span>

<span data-ttu-id="fa5cb-103">Le schéma des sections de configuration contient des éléments qui définissent des paramètres personnalisés dans les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="fa5cb-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="fa5cb-104">Pour obtenir des informations générales sur les fichiers de configuration et les schémas, consultez [schéma du fichier de configuration pour le .NET Framework](index.md).</span><span class="sxs-lookup"><span data-stu-id="fa5cb-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="fa5cb-105">Description</span><span class="sxs-lookup"><span data-stu-id="fa5cb-105">Description</span></span> |
| --- | ----------- |
| [**\<configSections>**](configsections-element-for-configuration.md) | <span data-ttu-id="fa5cb-106">Contient la section de configuration et les déclarations d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="fa5cb-106">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="fa5cb-107">**\<section>** pour **\<configSections>** et**\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="fa5cb-107">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="fa5cb-108">Contient une déclaration de section de configuration.</span><span class="sxs-lookup"><span data-stu-id="fa5cb-108">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="fa5cb-109">**\<sectionGroup>** pour**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="fa5cb-109">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="fa5cb-110">Définit un espace de noms pour les sections de configuration.</span><span class="sxs-lookup"><span data-stu-id="fa5cb-110">Defines a namespace for configuration sections.</span></span> |

<a name="dep"></a>

## <a name="unimplemented-elements"></a><span data-ttu-id="fa5cb-111">Éléments non implémentés</span><span class="sxs-lookup"><span data-stu-id="fa5cb-111">Unimplemented elements</span></span>

<span data-ttu-id="fa5cb-112">Les éléments suivants n’ont aucun impact et ne doivent pas être utilisés :</span><span class="sxs-lookup"><span data-stu-id="fa5cb-112">The following elements have no impact and should not be used:</span></span>

* **\<clear>**
* **\<remove>**

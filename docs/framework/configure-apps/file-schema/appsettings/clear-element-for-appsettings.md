---
title: <clear>, élément de <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 5d4d96143dbd1db440de2247a7dc2f0c66f20403
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301297"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="e3505-102">\<Désactivez >, élément pour \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="e3505-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="e3505-103">Efface les paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="e3505-103">Clears custom application settings.</span></span>

<span data-ttu-id="e3505-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="e3505-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="e3505-105">&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="e3505-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="e3505-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**</span><span class="sxs-lookup"><span data-stu-id="e3505-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e3505-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3505-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="e3505-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="e3505-108">Attributes</span></span>

<span data-ttu-id="e3505-109">None</span><span class="sxs-lookup"><span data-stu-id="e3505-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="e3505-110">Élément parent</span><span class="sxs-lookup"><span data-stu-id="e3505-110">Parent element</span></span>

|     | <span data-ttu-id="e3505-111">Description</span><span class="sxs-lookup"><span data-stu-id="e3505-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="e3505-112"> *\*\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="e3505-112">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="e3505-113">Contient les paramètres d’application personnalisés, tels que les chemins d’accès, des URL de service Web XML ou d’autres informations de configuration d’application personnalisée.</span><span class="sxs-lookup"><span data-stu-id="e3505-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="e3505-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e3505-114">Child elements</span></span>

<span data-ttu-id="e3505-115">None</span><span class="sxs-lookup"><span data-stu-id="e3505-115">None</span></span>

## <a name="example"></a><span data-ttu-id="e3505-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="e3505-116">Example</span></span>

<span data-ttu-id="e3505-117">L’exemple suivant montre comment effacer les paramètres de configuration personnalisée :</span><span class="sxs-lookup"><span data-stu-id="e3505-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="e3505-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3505-118">See also</span></span>

- [<span data-ttu-id="e3505-119">Schéma de fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e3505-119">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)

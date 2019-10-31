---
title: <clear>, élément de <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3e1c3a3cfd61a9fa8e7abdae9a25ec1bc674492
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119227"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="7a0c7-102">\<> élément Clear pour \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="7a0c7-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="7a0c7-103">Efface les paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7a0c7-103">Clears custom application settings.</span></span>

<span data-ttu-id="7a0c7-104">[ **\<configuration>** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7a0c7-104">[**\<configuration>**](../configuration-element.md) </span></span>  
<span data-ttu-id="7a0c7-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="7a0c7-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="7a0c7-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="7a0c7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="7a0c7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a0c7-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="7a0c7-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="7a0c7-108">Attributes</span></span>

<span data-ttu-id="7a0c7-109">aucune.</span><span class="sxs-lookup"><span data-stu-id="7a0c7-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="7a0c7-110">Élément parent</span><span class="sxs-lookup"><span data-stu-id="7a0c7-110">Parent element</span></span>

|     | <span data-ttu-id="7a0c7-111">Description</span><span class="sxs-lookup"><span data-stu-id="7a0c7-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="7a0c7-112"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="7a0c7-112">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="7a0c7-113">Contient des paramètres d’application personnalisés, tels que des chemins d’accès aux fichiers, des URL de service Web XML ou d’autres informations de configuration d’application personnalisées.</span><span class="sxs-lookup"><span data-stu-id="7a0c7-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="7a0c7-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7a0c7-114">Child elements</span></span>

<span data-ttu-id="7a0c7-115">aucune.</span><span class="sxs-lookup"><span data-stu-id="7a0c7-115">None</span></span>

## <a name="example"></a><span data-ttu-id="7a0c7-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="7a0c7-116">Example</span></span>

<span data-ttu-id="7a0c7-117">L’exemple suivant montre comment effacer les paramètres de configuration personnalisés :</span><span class="sxs-lookup"><span data-stu-id="7a0c7-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="7a0c7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a0c7-118">See also</span></span>

- [<span data-ttu-id="7a0c7-119">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7a0c7-119">Configuration file schema for the .NET Framework</span></span>](../index.md)

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
ms.openlocfilehash: d321f3169344e9aa40d65b1722a533549de5315a
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088734"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="b2d0a-102">\<> élément Clear pour \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="b2d0a-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="b2d0a-103">Efface les paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="b2d0a-103">Clears custom application settings.</span></span>

<span data-ttu-id="b2d0a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b2d0a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b2d0a-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="b2d0a-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="b2d0a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="b2d0a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b2d0a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2d0a-107">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="b2d0a-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="b2d0a-108">Attributes</span></span>

<span data-ttu-id="b2d0a-109">aucune.</span><span class="sxs-lookup"><span data-stu-id="b2d0a-109">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="b2d0a-110">Élément parent</span><span class="sxs-lookup"><span data-stu-id="b2d0a-110">Parent element</span></span>

|     | <span data-ttu-id="b2d0a-111">Description</span><span class="sxs-lookup"><span data-stu-id="b2d0a-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b2d0a-112"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="b2d0a-112">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="b2d0a-113">Contient des paramètres d’application personnalisés, tels que des chemins d’accès aux fichiers, des URL de service Web XML ou d’autres informations de configuration d’application personnalisées.</span><span class="sxs-lookup"><span data-stu-id="b2d0a-113">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="b2d0a-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b2d0a-114">Child elements</span></span>

<span data-ttu-id="b2d0a-115">aucune.</span><span class="sxs-lookup"><span data-stu-id="b2d0a-115">None</span></span>

## <a name="example"></a><span data-ttu-id="b2d0a-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="b2d0a-116">Example</span></span>

<span data-ttu-id="b2d0a-117">L’exemple suivant montre comment effacer les paramètres de configuration personnalisés :</span><span class="sxs-lookup"><span data-stu-id="b2d0a-117">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="b2d0a-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2d0a-118">See also</span></span>

- [<span data-ttu-id="b2d0a-119">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b2d0a-119">Configuration file schema for the .NET Framework</span></span>](../index.md)

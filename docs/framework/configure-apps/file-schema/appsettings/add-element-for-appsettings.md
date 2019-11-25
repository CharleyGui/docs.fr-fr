---
title: <add>, élément de <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 865c693bf8f23bf050064ac097b72aa6fa3b371e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088746"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="479a7-102">\<ajoutez > élément pour \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="479a7-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="479a7-103">Ajoute un paramètre d’application personnalisé.</span><span class="sxs-lookup"><span data-stu-id="479a7-103">Adds a custom application setting.</span></span>

<span data-ttu-id="479a7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="479a7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="479a7-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="479a7-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="479a7-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<ajouter des >**</span><span class="sxs-lookup"><span data-stu-id="479a7-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="479a7-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="479a7-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="479a7-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="479a7-108">Attributes</span></span>

|           | <span data-ttu-id="479a7-109">Description</span><span class="sxs-lookup"><span data-stu-id="479a7-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="479a7-110">**key**</span><span class="sxs-lookup"><span data-stu-id="479a7-110">**key**</span></span>   | <span data-ttu-id="479a7-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="479a7-111">Required attribute.</span></span><br><br><span data-ttu-id="479a7-112">Spécifie le nom de la clé à ajouter.</span><span class="sxs-lookup"><span data-stu-id="479a7-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="479a7-113">**valeur**</span><span class="sxs-lookup"><span data-stu-id="479a7-113">**value**</span></span> | <span data-ttu-id="479a7-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="479a7-114">Required attribute.</span></span><br><br><span data-ttu-id="479a7-115">Spécifie la valeur de la clé à ajouter.</span><span class="sxs-lookup"><span data-stu-id="479a7-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="479a7-116">Élément parent</span><span class="sxs-lookup"><span data-stu-id="479a7-116">Parent element</span></span>

|     | <span data-ttu-id="479a7-117">Description</span><span class="sxs-lookup"><span data-stu-id="479a7-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="479a7-118"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="479a7-118">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="479a7-119">Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="479a7-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="479a7-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="479a7-120">Child elements</span></span>

<span data-ttu-id="479a7-121">aucune.</span><span class="sxs-lookup"><span data-stu-id="479a7-121">None</span></span>

## <a name="example"></a><span data-ttu-id="479a7-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="479a7-122">Example</span></span>

<span data-ttu-id="479a7-123">L’exemple suivant montre comment ajouter un paramètre de configuration personnalisé pour le nom de l’application :</span><span class="sxs-lookup"><span data-stu-id="479a7-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="479a7-124">L’exemple suivant utilise l’élément `<add>` pour définir deux paramètres de compatibilité dans une application ASP.NET :</span><span class="sxs-lookup"><span data-stu-id="479a7-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="479a7-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="479a7-125">See also</span></span>

- [<span data-ttu-id="479a7-126">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="479a7-126">Configuration file schema for the .NET Framework</span></span>](../index.md)

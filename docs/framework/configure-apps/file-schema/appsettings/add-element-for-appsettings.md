---
title: <add>, élément de <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: f8b426dc0e1e180afbfccce50d3b45774991a572
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301350"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="01022-102">\<Ajouter > élément pour \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="01022-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="01022-103">Ajoute un paramètre d’application personnalisé.</span><span class="sxs-lookup"><span data-stu-id="01022-103">Adds a custom application setting.</span></span>

<span data-ttu-id="01022-104">[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="01022-104">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="01022-105">&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="01022-105">&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) </span></span>  
<span data-ttu-id="01022-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**</span><span class="sxs-lookup"><span data-stu-id="01022-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="01022-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01022-107">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="01022-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="01022-108">Attributes</span></span>

|           | <span data-ttu-id="01022-109">Description</span><span class="sxs-lookup"><span data-stu-id="01022-109">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="01022-110">**key**</span><span class="sxs-lookup"><span data-stu-id="01022-110">**key**</span></span>   | <span data-ttu-id="01022-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="01022-111">Required attribute.</span></span><br><br><span data-ttu-id="01022-112">Spécifie le nom de la clé à ajouter.</span><span class="sxs-lookup"><span data-stu-id="01022-112">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="01022-113">**value**</span><span class="sxs-lookup"><span data-stu-id="01022-113">**value**</span></span> | <span data-ttu-id="01022-114">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="01022-114">Required attribute.</span></span><br><br><span data-ttu-id="01022-115">Spécifie la valeur de la clé à ajouter.</span><span class="sxs-lookup"><span data-stu-id="01022-115">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="01022-116">Élément parent</span><span class="sxs-lookup"><span data-stu-id="01022-116">Parent element</span></span>

|     | <span data-ttu-id="01022-117">Description</span><span class="sxs-lookup"><span data-stu-id="01022-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="01022-118"> *\*\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="01022-118">**\<appSettings>**</span></span>](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | <span data-ttu-id="01022-119">Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="01022-119">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="01022-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="01022-120">Child elements</span></span>

<span data-ttu-id="01022-121">None</span><span class="sxs-lookup"><span data-stu-id="01022-121">None</span></span>

## <a name="example"></a><span data-ttu-id="01022-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="01022-122">Example</span></span>

<span data-ttu-id="01022-123">L’exemple suivant montre comment ajouter un paramètre de configuration personnalisée pour le nom de l’application :</span><span class="sxs-lookup"><span data-stu-id="01022-123">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="01022-124">L’exemple suivant utilise le `<add>` élément pour définir les deux paramètres de compatibilité dans une application ASP.NET :</span><span class="sxs-lookup"><span data-stu-id="01022-124">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="01022-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01022-125">See also</span></span>

- [<span data-ttu-id="01022-126">Schéma de fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="01022-126">Configuration file schema for the .NET Framework</span></span>](~/docs/framework/configure-apps/file-schema/index.md)

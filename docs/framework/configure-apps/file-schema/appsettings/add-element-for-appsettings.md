---
title: <add>, élément de <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
ms.openlocfilehash: 5c7de79ec626966e71d461dd3865b294a8979db2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214809"
---
# <a name="add-element-for-appsettings"></a><span data-ttu-id="39408-102">\<add>, élément de \<appSettings></span><span class="sxs-lookup"><span data-stu-id="39408-102">\<add> element for \<appSettings></span></span>

<span data-ttu-id="39408-103">Ajoute un paramètre d’application personnalisé.</span><span class="sxs-lookup"><span data-stu-id="39408-103">Adds a custom application setting.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="39408-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39408-104">Syntax</span></span>

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="39408-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="39408-105">Attributes</span></span>

|           | <span data-ttu-id="39408-106">Description</span><span class="sxs-lookup"><span data-stu-id="39408-106">Description</span></span> |
| --------- | ----------- |
| <span data-ttu-id="39408-107">**key**</span><span class="sxs-lookup"><span data-stu-id="39408-107">**key**</span></span>   | <span data-ttu-id="39408-108">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="39408-108">Required attribute.</span></span><br><br><span data-ttu-id="39408-109">Spécifie le nom de la clé à ajouter.</span><span class="sxs-lookup"><span data-stu-id="39408-109">Specifies the name of the key to add.</span></span> |
| <span data-ttu-id="39408-110">**value**</span><span class="sxs-lookup"><span data-stu-id="39408-110">**value**</span></span> | <span data-ttu-id="39408-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="39408-111">Required attribute.</span></span><br><br><span data-ttu-id="39408-112">Spécifie la valeur de la clé à ajouter.</span><span class="sxs-lookup"><span data-stu-id="39408-112">Specifies the value of the key to add.</span></span> |

## <a name="parent-element"></a><span data-ttu-id="39408-113">Élément parent</span><span class="sxs-lookup"><span data-stu-id="39408-113">Parent element</span></span>

|     | <span data-ttu-id="39408-114">Description</span><span class="sxs-lookup"><span data-stu-id="39408-114">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="39408-115">Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="39408-115">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="39408-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="39408-116">Child elements</span></span>

<span data-ttu-id="39408-117">None</span><span class="sxs-lookup"><span data-stu-id="39408-117">None</span></span>

## <a name="example"></a><span data-ttu-id="39408-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="39408-118">Example</span></span>

<span data-ttu-id="39408-119">L’exemple suivant montre comment ajouter un paramètre de configuration personnalisé pour le nom de l’application :</span><span class="sxs-lookup"><span data-stu-id="39408-119">The following example shows how to add a custom configuration setting for the application's name:</span></span>

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

<span data-ttu-id="39408-120">L’exemple suivant utilise l' `<add>` élément pour définir deux paramètres de compatibilité dans une application ASP.net :</span><span class="sxs-lookup"><span data-stu-id="39408-120">The following example uses the `<add>` element to define two compatibility settings in an ASP.NET application:</span></span>

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="39408-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="39408-121">See also</span></span>

- [<span data-ttu-id="39408-122">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="39408-122">Configuration file schema for the .NET Framework</span></span>](../index.md)

---
title: <remove>, élément de <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0fcdb75aa733a9d7634ec1c3b31dcbbb87e090e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088721"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="4daa2-102">\<supprimer > élément de \<appSettings ></span><span class="sxs-lookup"><span data-stu-id="4daa2-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="4daa2-103">Supprime les paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="4daa2-103">Removes custom application settings.</span></span>

<span data-ttu-id="4daa2-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4daa2-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4daa2-105">&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)</span><span class="sxs-lookup"><span data-stu-id="4daa2-105">&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)</span></span>\
<span data-ttu-id="4daa2-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<supprimer >**</span><span class="sxs-lookup"><span data-stu-id="4daa2-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="4daa2-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4daa2-107">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="4daa2-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="4daa2-108">Attribute</span></span>

|         | <span data-ttu-id="4daa2-109">Description</span><span class="sxs-lookup"><span data-stu-id="4daa2-109">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="4daa2-110">**key**</span><span class="sxs-lookup"><span data-stu-id="4daa2-110">**key**</span></span> | <span data-ttu-id="4daa2-111">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="4daa2-111">Required attribute.</span></span><br><br><span data-ttu-id="4daa2-112">Spécifie le nom de la clé à supprimer.</span><span class="sxs-lookup"><span data-stu-id="4daa2-112">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="4daa2-113">Élément parent</span><span class="sxs-lookup"><span data-stu-id="4daa2-113">Parent element</span></span>

|     | <span data-ttu-id="4daa2-114">Description</span><span class="sxs-lookup"><span data-stu-id="4daa2-114">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="4daa2-115"> **\<appSettings>** </span><span class="sxs-lookup"><span data-stu-id="4daa2-115">**\<appSettings>**</span></span>](appsettings-element-for-configuration.md) | <span data-ttu-id="4daa2-116">Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="4daa2-116">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="4daa2-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4daa2-117">Child elements</span></span>

<span data-ttu-id="4daa2-118">aucune.</span><span class="sxs-lookup"><span data-stu-id="4daa2-118">None</span></span>

## <a name="example"></a><span data-ttu-id="4daa2-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="4daa2-119">Example</span></span>

<span data-ttu-id="4daa2-120">L’exemple suivant montre comment supprimer un paramètre de configuration personnalisé pour `ApplicationName`:</span><span class="sxs-lookup"><span data-stu-id="4daa2-120">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="4daa2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4daa2-121">See also</span></span>

- [<span data-ttu-id="4daa2-122">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4daa2-122">Configuration file schema for the .NET Framework</span></span>](../index.md)

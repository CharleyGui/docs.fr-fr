---
title: <remove>, élément de <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: 83abbdbf0d3e4dfd16c0e8c649200c4ecc7329f7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77215497"
---
# <a name="remove-element-for-appsettings"></a><span data-ttu-id="453b3-102">\<remove>, élément de \<appSettings></span><span class="sxs-lookup"><span data-stu-id="453b3-102">\<remove> element for \<appSettings></span></span>

<span data-ttu-id="453b3-103">Supprime les paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="453b3-103">Removes custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="453b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="453b3-104">Syntax</span></span>

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a><span data-ttu-id="453b3-105">Attribut</span><span class="sxs-lookup"><span data-stu-id="453b3-105">Attribute</span></span>

|         | <span data-ttu-id="453b3-106">Description</span><span class="sxs-lookup"><span data-stu-id="453b3-106">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="453b3-107">**key**</span><span class="sxs-lookup"><span data-stu-id="453b3-107">**key**</span></span> | <span data-ttu-id="453b3-108">Attribut requis.</span><span class="sxs-lookup"><span data-stu-id="453b3-108">Required attribute.</span></span><br><br><span data-ttu-id="453b3-109">Spécifie le nom de la clé à supprimer.</span><span class="sxs-lookup"><span data-stu-id="453b3-109">Specifies the name of the key to remove.</span></span> |

### <a name="parent-element"></a><span data-ttu-id="453b3-110">Élément parent</span><span class="sxs-lookup"><span data-stu-id="453b3-110">Parent element</span></span>

|     | <span data-ttu-id="453b3-111">Description</span><span class="sxs-lookup"><span data-stu-id="453b3-111">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="453b3-112">Contient des paramètres d’application personnalisés, tels que des chemins d’accès, des URL de service web XML ou d’autres informations de configuration personnalisée pour une application.</span><span class="sxs-lookup"><span data-stu-id="453b3-112">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom configuration information for an application.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="453b3-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="453b3-113">Child elements</span></span>

<span data-ttu-id="453b3-114">None</span><span class="sxs-lookup"><span data-stu-id="453b3-114">None</span></span>

## <a name="example"></a><span data-ttu-id="453b3-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="453b3-115">Example</span></span>

<span data-ttu-id="453b3-116">L’exemple suivant montre comment supprimer un paramètre de configuration personnalisé pour `ApplicationName` :</span><span class="sxs-lookup"><span data-stu-id="453b3-116">The following example shows how to remove a custom configuration setting for `ApplicationName`:</span></span>

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="453b3-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="453b3-117">See also</span></span>

- [<span data-ttu-id="453b3-118">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="453b3-118">Configuration file schema for the .NET Framework</span></span>](../index.md)

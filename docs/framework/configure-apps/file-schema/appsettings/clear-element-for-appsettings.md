---
title: <clear>, élément de <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
ms.openlocfilehash: 266d32ccb8b322f0472e0f552f9c0fc877c9a78e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "77214802"
---
# <a name="clear-element-for-appsettings"></a><span data-ttu-id="7a54c-102">\<clear>, élément de \<appSettings></span><span class="sxs-lookup"><span data-stu-id="7a54c-102">\<clear> element for \<appSettings></span></span>

<span data-ttu-id="7a54c-103">Efface les paramètres d’application personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7a54c-103">Clears custom application settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<appSettings>**](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="7a54c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a54c-104">Syntax</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a><span data-ttu-id="7a54c-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="7a54c-105">Attributes</span></span>

<span data-ttu-id="7a54c-106">Aucune</span><span class="sxs-lookup"><span data-stu-id="7a54c-106">None</span></span>

## <a name="parent-element"></a><span data-ttu-id="7a54c-107">Élément parent</span><span class="sxs-lookup"><span data-stu-id="7a54c-107">Parent element</span></span>

|     | <span data-ttu-id="7a54c-108">Description</span><span class="sxs-lookup"><span data-stu-id="7a54c-108">Description</span></span> |
| --- | ----------- |
| [**\<appSettings>**](appsettings-element-for-configuration.md) | <span data-ttu-id="7a54c-109">Contient des paramètres d’application personnalisés, tels que des chemins d’accès aux fichiers, des URL de service Web XML ou d’autres informations de configuration d’application personnalisées.</span><span class="sxs-lookup"><span data-stu-id="7a54c-109">Contains custom application settings, such as file paths, XML Web service URLs, or any other custom application configuration information.</span></span> |

## <a name="child-elements"></a><span data-ttu-id="7a54c-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7a54c-110">Child elements</span></span>

<span data-ttu-id="7a54c-111">None</span><span class="sxs-lookup"><span data-stu-id="7a54c-111">None</span></span>

## <a name="example"></a><span data-ttu-id="7a54c-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="7a54c-112">Example</span></span>

<span data-ttu-id="7a54c-113">L’exemple suivant montre comment effacer les paramètres de configuration personnalisés :</span><span class="sxs-lookup"><span data-stu-id="7a54c-113">The following example shows how to clear custom configuration settings:</span></span>

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a><span data-ttu-id="7a54c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a54c-114">See also</span></span>

- [<span data-ttu-id="7a54c-115">Schéma du fichier de configuration pour le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7a54c-115">Configuration file schema for the .NET Framework</span></span>](../index.md)

---
title: <webProxyScript>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webProxyScript
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/webProxyScript
helpviewer_keywords:
- <webProxyScript> element
- webProxyScript element
ms.assetid: a13c26db-6218-4af3-9696-38f24b23bfac
ms.openlocfilehash: e36b470b1ec348085b13a58630b0ac6833e43946
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178305"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="7c329-102">\<webProxyScript>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="7c329-102">\<webProxyScript> Element (Network Settings)</span></span>

<span data-ttu-id="7c329-103">Configure les caractéristiques du script utilisé pour découvrir les proxys Web.</span><span class="sxs-lookup"><span data-stu-id="7c329-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**

## <a name="syntax"></a><span data-ttu-id="7c329-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c329-104">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c329-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7c329-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7c329-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7c329-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c329-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="7c329-107">Attributes</span></span>  
  
|<span data-ttu-id="7c329-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="7c329-108">Attribute</span></span>|<span data-ttu-id="7c329-109">Description</span><span class="sxs-lookup"><span data-stu-id="7c329-109">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="7c329-110">Spécifie la durée maximale de téléchargement du script en heures, minutes et secondes.</span><span class="sxs-lookup"><span data-stu-id="7c329-110">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="7c329-111">La valeur par défaut est d’une minute.</span><span class="sxs-lookup"><span data-stu-id="7c329-111">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c329-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7c329-112">Child Elements</span></span>  

 <span data-ttu-id="7c329-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7c329-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c329-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7c329-114">Parent Elements</span></span>  
  
|<span data-ttu-id="7c329-115">Élément</span><span class="sxs-lookup"><span data-stu-id="7c329-115">Element</span></span>|<span data-ttu-id="7c329-116">Description</span><span class="sxs-lookup"><span data-stu-id="7c329-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c329-117">settings</span><span class="sxs-lookup"><span data-stu-id="7c329-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="7c329-118">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="7c329-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c329-119">Notes</span><span class="sxs-lookup"><span data-stu-id="7c329-119">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7c329-120">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="7c329-120">Configuration Files</span></span>  

 <span data-ttu-id="7c329-121">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="7c329-121">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c329-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c329-122">See also</span></span>

- [<span data-ttu-id="7c329-123">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="7c329-123">Network Settings Schema</span></span>](index.md)

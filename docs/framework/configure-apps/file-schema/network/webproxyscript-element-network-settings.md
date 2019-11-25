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
ms.openlocfilehash: dbad888cd0537f63c09840ac1053f924db9ea9bc
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089064"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="c75de-102">\<webProxyScript >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="c75de-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="c75de-103">Configure les caractéristiques du script utilisé pour découvrir les proxys Web.</span><span class="sxs-lookup"><span data-stu-id="c75de-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  

<span data-ttu-id="c75de-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c75de-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c75de-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c75de-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="c75de-106">&nbsp;&nbsp;&nbsp;&nbsp;[**paramètres**](settings-element-network-settings.md)\<</span><span class="sxs-lookup"><span data-stu-id="c75de-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\</span></span>
<span data-ttu-id="c75de-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**webProxyScript >**</span><span class="sxs-lookup"><span data-stu-id="c75de-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webProxyScript>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c75de-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c75de-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c75de-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c75de-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c75de-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c75de-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c75de-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="c75de-111">Attributes</span></span>  
  
|<span data-ttu-id="c75de-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="c75de-112">Attribute</span></span>|<span data-ttu-id="c75de-113">Description</span><span class="sxs-lookup"><span data-stu-id="c75de-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="c75de-114">Spécifie la durée maximale de téléchargement du script en heures, minutes et secondes.</span><span class="sxs-lookup"><span data-stu-id="c75de-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="c75de-115">La valeur par défaut est d’une minute.</span><span class="sxs-lookup"><span data-stu-id="c75de-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c75de-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c75de-116">Child Elements</span></span>  
 <span data-ttu-id="c75de-117">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="c75de-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c75de-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c75de-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c75de-119">Élément</span><span class="sxs-lookup"><span data-stu-id="c75de-119">Element</span></span>|<span data-ttu-id="c75de-120">Description</span><span class="sxs-lookup"><span data-stu-id="c75de-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c75de-121">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c75de-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="c75de-122">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="c75de-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c75de-123">Notes</span><span class="sxs-lookup"><span data-stu-id="c75de-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="c75de-124">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="c75de-124">Configuration Files</span></span>  
 <span data-ttu-id="c75de-125">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="c75de-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75de-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c75de-126">See also</span></span>

- [<span data-ttu-id="c75de-127">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="c75de-127">Network Settings Schema</span></span>](index.md)

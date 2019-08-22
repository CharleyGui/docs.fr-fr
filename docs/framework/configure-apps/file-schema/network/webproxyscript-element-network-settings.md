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
ms.openlocfilehash: 8a77c2567401fd80e355bb7fcee17b6684653ebe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659047"
---
# <a name="webproxyscript-element-network-settings"></a><span data-ttu-id="a98dc-102">\<webProxyScript >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="a98dc-102">\<webProxyScript> Element (Network Settings)</span></span>
<span data-ttu-id="a98dc-103">Configure les caractéristiques du script utilisé pour découvrir les proxys Web.</span><span class="sxs-lookup"><span data-stu-id="a98dc-103">Configures the characteristics of the script used to discover Web proxies.</span></span>  
  
 <span data-ttu-id="a98dc-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="a98dc-104">\<configuration></span></span>  
<span data-ttu-id="a98dc-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="a98dc-105">\<system.net></span></span>  
<span data-ttu-id="a98dc-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="a98dc-106">\<settings></span></span>  
<span data-ttu-id="a98dc-107">\<webProxyScript></span><span class="sxs-lookup"><span data-stu-id="a98dc-107">\<webProxyScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a98dc-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a98dc-108">Syntax</span></span>  
  
```xml  
<webProxyScript  
  downloadTimeout="hh:mm:ss"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a98dc-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a98dc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a98dc-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a98dc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a98dc-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="a98dc-111">Attributes</span></span>  
  
|<span data-ttu-id="a98dc-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="a98dc-112">Attribute</span></span>|<span data-ttu-id="a98dc-113">Description</span><span class="sxs-lookup"><span data-stu-id="a98dc-113">Description</span></span>|  
|---------------|-----------------|  
|`downloadTimeout`|<span data-ttu-id="a98dc-114">Spécifie la durée maximale de téléchargement du script en heures, minutes et secondes.</span><span class="sxs-lookup"><span data-stu-id="a98dc-114">Specifies the maximum time to download the script in hours, minutes, and seconds.</span></span> <span data-ttu-id="a98dc-115">La valeur par défaut est d’une minute.</span><span class="sxs-lookup"><span data-stu-id="a98dc-115">The default value is one minute.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a98dc-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a98dc-116">Child Elements</span></span>  
 <span data-ttu-id="a98dc-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="a98dc-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a98dc-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a98dc-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a98dc-119">Élément</span><span class="sxs-lookup"><span data-stu-id="a98dc-119">Element</span></span>|<span data-ttu-id="a98dc-120">Description</span><span class="sxs-lookup"><span data-stu-id="a98dc-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a98dc-121">settings</span><span class="sxs-lookup"><span data-stu-id="a98dc-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="a98dc-122">Configure les options réseau de base pour l’espace de noms <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="a98dc-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a98dc-123">Notes</span><span class="sxs-lookup"><span data-stu-id="a98dc-123">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a98dc-124">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="a98dc-124">Configuration Files</span></span>  
 <span data-ttu-id="a98dc-125">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a98dc-125">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a98dc-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a98dc-126">See also</span></span>

- [<span data-ttu-id="a98dc-127">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="a98dc-127">Network Settings Schema</span></span>](index.md)

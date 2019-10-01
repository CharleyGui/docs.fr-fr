---
title: <settings>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: ba08f630dc602c950da309bf29482d85b41af7ef
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697684"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="7a427-102">\<settings >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="7a427-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="7a427-103">Configure les options réseau de base pour l’espace de noms <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7a427-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
[<span data-ttu-id="7a427-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="7a427-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="7a427-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="7a427-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="7a427-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<settings >**</span><span class="sxs-lookup"><span data-stu-id="7a427-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a427-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a427-107">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a427-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7a427-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7a427-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7a427-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a427-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="7a427-110">Attributes</span></span>  
 <span data-ttu-id="7a427-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7a427-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7a427-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7a427-112">Child Elements</span></span>  
  
|<span data-ttu-id="7a427-113">Élément</span><span class="sxs-lookup"><span data-stu-id="7a427-113">Element</span></span>|<span data-ttu-id="7a427-114">Description</span><span class="sxs-lookup"><span data-stu-id="7a427-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a427-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="7a427-115">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="7a427-116">Personnalise les paramètres utilisés par la classe <xref:System.Net.HttpListener>.</span><span class="sxs-lookup"><span data-stu-id="7a427-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="7a427-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="7a427-117">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="7a427-118">Personnalise les paramètres de la demande Web.</span><span class="sxs-lookup"><span data-stu-id="7a427-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="7a427-119">ipv6</span><span class="sxs-lookup"><span data-stu-id="7a427-119">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="7a427-120">Active la prise en charge du protocole IPv6 (Internet Protocol version 6).</span><span class="sxs-lookup"><span data-stu-id="7a427-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="7a427-121">\<performanceCounter >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="7a427-121">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="7a427-122">Active les compteurs de performances réseau.</span><span class="sxs-lookup"><span data-stu-id="7a427-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="7a427-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="7a427-123">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="7a427-124">Configure les connexions aux ressources réseau.</span><span class="sxs-lookup"><span data-stu-id="7a427-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="7a427-125">socket</span><span class="sxs-lookup"><span data-stu-id="7a427-125">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="7a427-126">Spécifie si les opérations de socket utilisent des ports de terminaison.</span><span class="sxs-lookup"><span data-stu-id="7a427-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="7a427-127">\<webProxyScript >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="7a427-127">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="7a427-128">Configure les caractéristiques du script utilisé pour découvrir les proxys Web.</span><span class="sxs-lookup"><span data-stu-id="7a427-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7a427-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7a427-129">Parent Elements</span></span>  
  
|<span data-ttu-id="7a427-130">Élément</span><span class="sxs-lookup"><span data-stu-id="7a427-130">Element</span></span>|<span data-ttu-id="7a427-131">Description</span><span class="sxs-lookup"><span data-stu-id="7a427-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7a427-132">system.net</span><span class="sxs-lookup"><span data-stu-id="7a427-132">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="7a427-133">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="7a427-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a427-134">Notes</span><span class="sxs-lookup"><span data-stu-id="7a427-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="7a427-135">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="7a427-135">Configuration Files</span></span>  
 <span data-ttu-id="7a427-136">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="7a427-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a427-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a427-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="7a427-138">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="7a427-138">Network Settings Schema</span></span>](index.md)

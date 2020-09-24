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
ms.openlocfilehash: c5fe0b9eccd1c429c0041fcfab06b0cc20a20aa2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167273"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="3b6b4-102">\<settings>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="3b6b4-102">\<settings> Element (Network Settings)</span></span>

<span data-ttu-id="3b6b4-103">Configure les options réseau de base pour l’espace de noms <xref:System.Net?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3b6b4-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a><span data-ttu-id="3b6b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b6b4-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b6b4-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="3b6b4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="3b6b4-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="3b6b4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b6b4-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="3b6b4-107">Attributes</span></span>  

 <span data-ttu-id="3b6b4-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="3b6b4-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3b6b4-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="3b6b4-109">Child Elements</span></span>  
  
|<span data-ttu-id="3b6b4-110">Élément</span><span class="sxs-lookup"><span data-stu-id="3b6b4-110">Element</span></span>|<span data-ttu-id="3b6b4-111">Description</span><span class="sxs-lookup"><span data-stu-id="3b6b4-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b6b4-112">httpListener</span><span class="sxs-lookup"><span data-stu-id="3b6b4-112">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="3b6b4-113">Personnalise les paramètres utilisés par la <xref:System.Net.HttpListener> classe.</span><span class="sxs-lookup"><span data-stu-id="3b6b4-113">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="3b6b4-114">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="3b6b4-114">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="3b6b4-115">Personnalise les paramètres de la demande Web.</span><span class="sxs-lookup"><span data-stu-id="3b6b4-115">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="3b6b4-116">protocoles</span><span class="sxs-lookup"><span data-stu-id="3b6b4-116">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="3b6b4-117">Active la prise en charge du protocole IPv6 (Internet Protocol version 6).</span><span class="sxs-lookup"><span data-stu-id="3b6b4-117">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="3b6b4-118">\<performanceCounter> , Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="3b6b4-118">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="3b6b4-119">Active les compteurs de performances réseau.</span><span class="sxs-lookup"><span data-stu-id="3b6b4-119">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="3b6b4-120">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="3b6b4-120">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="3b6b4-121">Configure les connexions aux ressources réseau.</span><span class="sxs-lookup"><span data-stu-id="3b6b4-121">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="3b6b4-122">socle</span><span class="sxs-lookup"><span data-stu-id="3b6b4-122">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="3b6b4-123">Spécifie si les opérations de socket utilisent des ports de terminaison.</span><span class="sxs-lookup"><span data-stu-id="3b6b4-123">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="3b6b4-124">\<webProxyScript> , Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="3b6b4-124">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="3b6b4-125">Configure les caractéristiques du script utilisé pour découvrir les proxys Web.</span><span class="sxs-lookup"><span data-stu-id="3b6b4-125">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3b6b4-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="3b6b4-126">Parent Elements</span></span>  
  
|<span data-ttu-id="3b6b4-127">Élément</span><span class="sxs-lookup"><span data-stu-id="3b6b4-127">Element</span></span>|<span data-ttu-id="3b6b4-128">Description</span><span class="sxs-lookup"><span data-stu-id="3b6b4-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b6b4-129">system.net</span><span class="sxs-lookup"><span data-stu-id="3b6b4-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="3b6b4-130">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="3b6b4-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b6b4-131">Notes</span><span class="sxs-lookup"><span data-stu-id="3b6b4-131">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3b6b4-132">Fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="3b6b4-132">Configuration Files</span></span>  

 <span data-ttu-id="3b6b4-133">Cet élément peut être défini dans le fichier de configuration de l'application ou dans le fichier de configuration de l'ordinateur (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="3b6b4-133">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b6b4-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b6b4-134">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="3b6b4-135">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="3b6b4-135">Network Settings Schema</span></span>](index.md)

---
title: <requestCaching>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: 3eb32b7ae643efdb19892410b669c1e7ff80e0ad
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174158"
---
# <a name="requestcaching-element-network-settings"></a><span data-ttu-id="28447-102">\<requestCaching>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="28447-102">\<requestCaching> Element (Network Settings)</span></span>

<span data-ttu-id="28447-103">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="28447-103">Controls the caching mechanism for network requests.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**  
  
## <a name="syntax"></a><span data-ttu-id="28447-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="28447-104">Syntax</span></span>  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh:mm:ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="28447-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="28447-105">Attributes and Elements</span></span>  

 <span data-ttu-id="28447-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="28447-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="28447-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="28447-107">Attributes</span></span>  
  
|<span data-ttu-id="28447-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="28447-108">Attribute</span></span>|<span data-ttu-id="28447-109">Description</span><span class="sxs-lookup"><span data-stu-id="28447-109">Description</span></span>|  
|---------------|-----------------|  
|`isPrivateCache`|<span data-ttu-id="28447-110">Spécifie si le cache assure l’isolement entre les informations des différents utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="28447-110">Specifies whether the cache provides isolation between the information of different users.</span></span> <span data-ttu-id="28447-111">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="28447-111">The default value is `true`.</span></span> <span data-ttu-id="28447-112">Cette valeur doit être `false` pour les applications de niveau intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="28447-112">This value should be `false` for middle tier applications.</span></span>|  
|`disableAllCaching`|<span data-ttu-id="28447-113">Spécifie que la mise en cache est désactivée pour toutes les réponses Web et ne peut pas être substituée par programmation.</span><span class="sxs-lookup"><span data-stu-id="28447-113">Specifies that caching is disabled for all Web responses, and cannot be overridden programmatically.</span></span>|  
|`defaultPolicyLevel`|<span data-ttu-id="28447-114">Une des valeurs dans l'énumération <xref:System.Net.Cache.RequestCacheLevel>.</span><span class="sxs-lookup"><span data-stu-id="28447-114">One of the values in the <xref:System.Net.Cache.RequestCacheLevel> enumeration.</span></span> <span data-ttu-id="28447-115">La valeur par défaut est `BypassCache`.</span><span class="sxs-lookup"><span data-stu-id="28447-115">The default value is `BypassCache`.</span></span>|  
|`unspecifiedMaximumAge`|<span data-ttu-id="28447-116">Spécifie l’heure par défaut après laquelle le contenu est marqué comme ayant expiré.</span><span class="sxs-lookup"><span data-stu-id="28447-116">Specifies the default time after which content is marked as expired.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="28447-117">policyLevel (attribut)</span><span class="sxs-lookup"><span data-stu-id="28447-117">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="28447-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="28447-118">Value</span></span>|<span data-ttu-id="28447-119">Description</span><span class="sxs-lookup"><span data-stu-id="28447-119">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="28447-120">Retourne la ressource mise en cache si la ressource est actualisée, si la longueur du contenu est exacte et si les attributs d’expiration, de modification et de longueur du contenu sont présents.</span><span class="sxs-lookup"><span data-stu-id="28447-120">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="28447-121">Retourne la ressource à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="28447-121">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="28447-122">Retourne la ressource mise en cache si la longueur du contenu est présente et correspond à la taille de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="28447-122">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="28447-123">Retourne la ressource mise en cache si la longueur du contenu est fournie et correspond à la taille de l’entrée ; dans le cas contraire, la ressource est téléchargée à partir du serveur et est retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="28447-123">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="28447-124">Retourne la ressource mise en cache si l’horodateur de la ressource mise en cache est le même que celui de la ressource sur le serveur ; dans le cas contraire, la ressource est téléchargée à partir du serveur, stockée dans le cache, et est retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="28447-124">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and is returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="28447-125">Télécharge la ressource à partir du serveur, la stocke dans le cache et retourne la ressource à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="28447-125">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="28447-126">Si une ressource mise en cache existe, elle est supprimée.</span><span class="sxs-lookup"><span data-stu-id="28447-126">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="28447-127">La ressource est téléchargée à partir du serveur et est retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="28447-127">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="28447-128">Satisfait une demande en utilisant la copie mise en cache de la ressource si l’horodatage est le même que celui de la ressource sur le serveur ; dans le cas contraire, la ressource est téléchargée à partir du serveur, présentée à l’appelant et stockée dans le cache.</span><span class="sxs-lookup"><span data-stu-id="28447-128">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and is stored in the cache,</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="28447-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="28447-129">Child Elements</span></span>  
  
|<span data-ttu-id="28447-130">Élément</span><span class="sxs-lookup"><span data-stu-id="28447-130">Element</span></span>|<span data-ttu-id="28447-131">Description</span><span class="sxs-lookup"><span data-stu-id="28447-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28447-132">defaultHttpCachePolicy</span><span class="sxs-lookup"><span data-stu-id="28447-132">defaultHttpCachePolicy</span></span>](defaulthttpcachepolicy-element-network-settings.md)|<span data-ttu-id="28447-133">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="28447-133">Optional element.</span></span><br /><br /> <span data-ttu-id="28447-134">Indique si la mise en cache HTTP est active et décrit la stratégie de mise en cache par défaut.</span><span class="sxs-lookup"><span data-stu-id="28447-134">Describes whether HTTP caching is active and describes the default caching policy.</span></span>|  
|[<span data-ttu-id="28447-135">\<defaultFtpCachePolicy> , Élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="28447-135">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>](defaultftpcachepolicy-element-network-settings.md)|<span data-ttu-id="28447-136">Élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="28447-136">Optional element.</span></span><br /><br /> <span data-ttu-id="28447-137">Indique si la mise en cache FTP est active et décrit la stratégie de mise en cache par défaut.</span><span class="sxs-lookup"><span data-stu-id="28447-137">Describes whether FTP caching is active and describes the default caching policy.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="28447-138">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="28447-138">Parent Elements</span></span>  
  
|<span data-ttu-id="28447-139">Élément</span><span class="sxs-lookup"><span data-stu-id="28447-139">Element</span></span>|<span data-ttu-id="28447-140">Description</span><span class="sxs-lookup"><span data-stu-id="28447-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28447-141">system.net</span><span class="sxs-lookup"><span data-stu-id="28447-141">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="28447-142">Contient des paramètres qui spécifient la manière dont .NET Framework se connecte au réseau.</span><span class="sxs-lookup"><span data-stu-id="28447-142">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="28447-143">Exemple</span><span class="sxs-lookup"><span data-stu-id="28447-143">Example</span></span>  

 <span data-ttu-id="28447-144">L’exemple suivant montre comment désactiver toute la mise en cache.</span><span class="sxs-lookup"><span data-stu-id="28447-144">The following example shows how to disable all caching.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="28447-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="28447-145">See also</span></span>

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [<span data-ttu-id="28447-146">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="28447-146">Network Settings Schema</span></span>](index.md)

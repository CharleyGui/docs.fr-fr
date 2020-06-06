---
title: <defaultFtpCachePolicy>, élément (paramètres réseau)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: 9261a430642cb4d5ac4507835bd0fd3561bd8c02
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088425"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="8fe9c-102">\<defaultFtpCachePolicy>, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="8fe9c-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="8fe9c-103">Indique si la mise en cache FTP est active et décrit la stratégie de mise en cache par défaut.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**

## <a name="syntax"></a><span data-ttu-id="8fe9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fe9c-104">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8fe9c-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8fe9c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8fe9c-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8fe9c-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="8fe9c-107">Attributes</span></span>  
  
|<span data-ttu-id="8fe9c-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="8fe9c-108">Attribute</span></span>|<span data-ttu-id="8fe9c-109">Description</span><span class="sxs-lookup"><span data-stu-id="8fe9c-109">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="8fe9c-110">Spécifie la stratégie de mise en cache FTP.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-110">Specifies the FTP caching policy.</span></span> <span data-ttu-id="8fe9c-111">La valeur par défaut est `Default`.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-111">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="8fe9c-112">policyLevel (attribut)</span><span class="sxs-lookup"><span data-stu-id="8fe9c-112">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="8fe9c-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="8fe9c-113">Value</span></span>|<span data-ttu-id="8fe9c-114">Description</span><span class="sxs-lookup"><span data-stu-id="8fe9c-114">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="8fe9c-115">Retourne la ressource mise en cache si la ressource est actualisée, si la longueur du contenu est exacte et si les attributs d’expiration, de modification et de longueur du contenu sont présents.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-115">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="8fe9c-116">Retourne la ressource à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-116">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="8fe9c-117">Retourne la ressource mise en cache si la longueur du contenu est présente et correspond à la taille de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-117">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="8fe9c-118">Retourne la ressource mise en cache si la longueur du contenu est fournie et correspond à la taille de l’entrée ; dans le cas contraire, la ressource est téléchargée à partir du serveur et est retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-118">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="8fe9c-119">Retourne la ressource mise en cache si l’horodateur de la ressource mise en cache est le même que celui de la ressource sur le serveur ; dans le cas contraire, la ressource est téléchargée à partir du serveur, stockée dans le cache et retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-119">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="8fe9c-120">Télécharge la ressource à partir du serveur, la stocke dans le cache et retourne la ressource à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-120">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="8fe9c-121">Si une ressource mise en cache existe, elle est supprimée.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-121">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="8fe9c-122">La ressource est téléchargée à partir du serveur et est retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-122">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="8fe9c-123">Satisfait une demande en utilisant la copie mise en cache de la ressource si l'horodatage est le même que celui de la ressource sur le serveur ; sinon, la ressource est téléchargée à partir du serveur, présentée à l'appelant et stockée dans le cache.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-123">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8fe9c-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8fe9c-124">Child Elements</span></span>  
 <span data-ttu-id="8fe9c-125">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8fe9c-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8fe9c-126">Parent Elements</span></span>  
  
|<span data-ttu-id="8fe9c-127">Élément</span><span class="sxs-lookup"><span data-stu-id="8fe9c-127">Element</span></span>|<span data-ttu-id="8fe9c-128">Description</span><span class="sxs-lookup"><span data-stu-id="8fe9c-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8fe9c-129">requestCaching</span><span class="sxs-lookup"><span data-stu-id="8fe9c-129">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="8fe9c-130">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="8fe9c-130">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fe9c-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="8fe9c-131">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fe9c-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="8fe9c-132">Example</span></span>  
 <span data-ttu-id="8fe9c-133">L’exemple suivant montre comment spécifier une stratégie de mise en cache FTP de `NoCacheNoStore` .</span><span class="sxs-lookup"><span data-stu-id="8fe9c-133">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8fe9c-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8fe9c-134">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="8fe9c-135">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="8fe9c-135">Network Settings Schema</span></span>](index.md)

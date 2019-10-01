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
ms.openlocfilehash: fd1649edbf7a2c8546992019df667f27df68e02c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698314"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="98ebe-102">\<defaultFtpCachePolicy >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="98ebe-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="98ebe-103">Indique si la mise en cache FTP est active et décrit la stratégie de mise en cache par défaut.</span><span class="sxs-lookup"><span data-stu-id="98ebe-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  
  
[<span data-ttu-id="98ebe-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="98ebe-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="98ebe-105">&nbsp; @ no__t-1[ **@no__t -4System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="98ebe-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="98ebe-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<requestCaching >** ](requestcaching-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="98ebe-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)</span></span>  
<span data-ttu-id="98ebe-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<defaultFtpCachePolicy >**</span><span class="sxs-lookup"><span data-stu-id="98ebe-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98ebe-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98ebe-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98ebe-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="98ebe-109">Attributes and Elements</span></span>  
 <span data-ttu-id="98ebe-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="98ebe-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98ebe-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="98ebe-111">Attributes</span></span>  
  
|<span data-ttu-id="98ebe-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="98ebe-112">Attribute</span></span>|<span data-ttu-id="98ebe-113">Description</span><span class="sxs-lookup"><span data-stu-id="98ebe-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="98ebe-114">Spécifie la stratégie de mise en cache FTP.</span><span class="sxs-lookup"><span data-stu-id="98ebe-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="98ebe-115">La valeur par défaut est `Default`.</span><span class="sxs-lookup"><span data-stu-id="98ebe-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="98ebe-116">policyLevel (attribut)</span><span class="sxs-lookup"><span data-stu-id="98ebe-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="98ebe-117">Value</span><span class="sxs-lookup"><span data-stu-id="98ebe-117">Value</span></span>|<span data-ttu-id="98ebe-118">Description</span><span class="sxs-lookup"><span data-stu-id="98ebe-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="98ebe-119">Retourne la ressource mise en cache si la ressource est actualisée, si la longueur du contenu est exacte et si les attributs d’expiration, de modification et de longueur du contenu sont présents.</span><span class="sxs-lookup"><span data-stu-id="98ebe-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="98ebe-120">Retourne la ressource à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="98ebe-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="98ebe-121">Retourne la ressource mise en cache si la longueur du contenu est présente et correspond à la taille de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="98ebe-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="98ebe-122">Retourne la ressource mise en cache si la longueur du contenu est fournie et correspond à la taille de l’entrée ; dans le cas contraire, la ressource est téléchargée à partir du serveur et est retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="98ebe-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="98ebe-123">Retourne la ressource mise en cache si l’horodateur de la ressource mise en cache est le même que celui de la ressource sur le serveur ; dans le cas contraire, la ressource est téléchargée à partir du serveur, stockée dans le cache et retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="98ebe-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="98ebe-124">Télécharge la ressource à partir du serveur, la stocke dans le cache et retourne la ressource à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="98ebe-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="98ebe-125">Si une ressource mise en cache existe, elle est supprimée.</span><span class="sxs-lookup"><span data-stu-id="98ebe-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="98ebe-126">La ressource est téléchargée à partir du serveur et est retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="98ebe-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="98ebe-127">Satisfait une demande en utilisant la copie mise en cache de la ressource si l’horodatage est le même que celui de la ressource sur le serveur ; dans le cas contraire, la ressource est téléchargée à partir du serveur, présentée à l’appelant et stockée dans le cache.</span><span class="sxs-lookup"><span data-stu-id="98ebe-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98ebe-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="98ebe-128">Child Elements</span></span>  
 <span data-ttu-id="98ebe-129">Aucun.</span><span class="sxs-lookup"><span data-stu-id="98ebe-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98ebe-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="98ebe-130">Parent Elements</span></span>  
  
|<span data-ttu-id="98ebe-131">Élément</span><span class="sxs-lookup"><span data-stu-id="98ebe-131">Element</span></span>|<span data-ttu-id="98ebe-132">Description</span><span class="sxs-lookup"><span data-stu-id="98ebe-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98ebe-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="98ebe-133">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="98ebe-134">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="98ebe-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98ebe-135">Notes</span><span class="sxs-lookup"><span data-stu-id="98ebe-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="98ebe-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="98ebe-136">Example</span></span>  
 <span data-ttu-id="98ebe-137">L’exemple suivant montre comment spécifier une stratégie de mise en cache FTP de `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="98ebe-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="98ebe-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98ebe-138">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="98ebe-139">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="98ebe-139">Network Settings Schema</span></span>](index.md)

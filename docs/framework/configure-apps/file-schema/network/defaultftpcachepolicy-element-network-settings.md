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
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088425"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a><span data-ttu-id="bb497-102">\<defaultFtpCachePolicy >, élément (paramètres réseau)</span><span class="sxs-lookup"><span data-stu-id="bb497-102">\<defaultFtpCachePolicy> Element (Network Settings)</span></span>
<span data-ttu-id="bb497-103">Indique si la mise en cache FTP est active et décrit la stratégie de mise en cache par défaut.</span><span class="sxs-lookup"><span data-stu-id="bb497-103">Describes whether FTP caching is active and describes the default caching policy.</span></span>  

<span data-ttu-id="bb497-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bb497-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bb497-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="bb497-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="bb497-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<requestCaching**](requestcaching-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="bb497-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<requestCaching>**](requestcaching-element-network-settings.md)</span></span>\
<span data-ttu-id="bb497-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**defaultFtpCachePolicy >**</span><span class="sxs-lookup"><span data-stu-id="bb497-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<defaultFtpCachePolicy>**</span></span>

## <a name="syntax"></a><span data-ttu-id="bb497-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bb497-108">Syntax</span></span>  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb497-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bb497-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bb497-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bb497-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb497-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="bb497-111">Attributes</span></span>  
  
|<span data-ttu-id="bb497-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="bb497-112">Attribute</span></span>|<span data-ttu-id="bb497-113">Description</span><span class="sxs-lookup"><span data-stu-id="bb497-113">Description</span></span>|  
|---------------|-----------------|  
|`policyLevel`|<span data-ttu-id="bb497-114">Spécifie la stratégie de mise en cache FTP.</span><span class="sxs-lookup"><span data-stu-id="bb497-114">Specifies the FTP caching policy.</span></span> <span data-ttu-id="bb497-115">La valeur par défaut est `Default`.</span><span class="sxs-lookup"><span data-stu-id="bb497-115">The default value is `Default`.</span></span>|  
  
## <a name="policylevel-attribute"></a><span data-ttu-id="bb497-116">policyLevel (attribut)</span><span class="sxs-lookup"><span data-stu-id="bb497-116">policyLevel Attribute</span></span>  
  
|<span data-ttu-id="bb497-117">valeur</span><span class="sxs-lookup"><span data-stu-id="bb497-117">Value</span></span>|<span data-ttu-id="bb497-118">Description</span><span class="sxs-lookup"><span data-stu-id="bb497-118">Description</span></span>|  
|-----------|-----------------|  
|`Default`|<span data-ttu-id="bb497-119">Retourne la ressource mise en cache si la ressource est actualisée, si la longueur du contenu est exacte et si les attributs d’expiration, de modification et de longueur du contenu sont présents.</span><span class="sxs-lookup"><span data-stu-id="bb497-119">Returns the cached resource if the resource is fresh, the content length is accurate, and the expiration, modification, and content length attributes are present.</span></span>|  
|`BypassCache`|<span data-ttu-id="bb497-120">Retourne la ressource à partir du serveur.</span><span class="sxs-lookup"><span data-stu-id="bb497-120">Returns the resource from the server.</span></span>|  
|`CacheOnly`|<span data-ttu-id="bb497-121">Retourne la ressource mise en cache si la longueur du contenu est présente et correspond à la taille de l’entrée.</span><span class="sxs-lookup"><span data-stu-id="bb497-121">Returns the cached resource if the content length is present and matches the entry size.</span></span>|  
|`CacheIfAvailable`|<span data-ttu-id="bb497-122">Retourne la ressource mise en cache si la longueur du contenu est fournie et correspond à la taille de l’entrée ; dans le cas contraire, la ressource est téléchargée à partir du serveur et est retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="bb497-122">Returns the cached resource if the content length is provided and matches the entry size; otherwise, the resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="bb497-123">Retourne la ressource mise en cache si l’horodateur de la ressource mise en cache est le même que celui de la ressource sur le serveur ; dans le cas contraire, la ressource est téléchargée à partir du serveur, stockée dans le cache et retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="bb497-123">Returns the cached resource if the timestamp of the cached resource is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, stored in the cache, and returned to the caller.</span></span>|  
|`Reload`|<span data-ttu-id="bb497-124">Télécharge la ressource à partir du serveur, la stocke dans le cache et retourne la ressource à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="bb497-124">Downloads the resource from the server, stores it in the cache, and returns the resource to the caller.</span></span>|  
|`NoCacheNoStore`|<span data-ttu-id="bb497-125">Si une ressource mise en cache existe, elle est supprimée.</span><span class="sxs-lookup"><span data-stu-id="bb497-125">If a cached resource exists, it is deleted.</span></span> <span data-ttu-id="bb497-126">La ressource est téléchargée à partir du serveur et est retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="bb497-126">The resource is downloaded from the server and is returned to the caller.</span></span>|  
|`Revalidate`|<span data-ttu-id="bb497-127">Satisfait une demande en utilisant la copie mise en cache de la ressource si l’horodatage est le même que celui de la ressource sur le serveur ; dans le cas contraire, la ressource est téléchargée à partir du serveur, présentée à l’appelant et stockée dans le cache.</span><span class="sxs-lookup"><span data-stu-id="bb497-127">Satisfies a request by using the cached copy of the resource if the timestamp is the same as the timestamp of the resource on the server; otherwise, the resource is downloaded from the server, presented to the caller, and stored in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb497-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bb497-128">Child Elements</span></span>  
 <span data-ttu-id="bb497-129">Aucun(e).</span><span class="sxs-lookup"><span data-stu-id="bb497-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb497-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bb497-130">Parent Elements</span></span>  
  
|<span data-ttu-id="bb497-131">Élément</span><span class="sxs-lookup"><span data-stu-id="bb497-131">Element</span></span>|<span data-ttu-id="bb497-132">Description</span><span class="sxs-lookup"><span data-stu-id="bb497-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb497-133">requestCaching</span><span class="sxs-lookup"><span data-stu-id="bb497-133">requestCaching</span></span>](requestcaching-element-network-settings.md)|<span data-ttu-id="bb497-134">Contrôle le mécanisme de mise en cache pour les demandes réseau.</span><span class="sxs-lookup"><span data-stu-id="bb497-134">Controls the caching mechanism for network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb497-135">Notes</span><span class="sxs-lookup"><span data-stu-id="bb497-135">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb497-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="bb497-136">Example</span></span>  
 <span data-ttu-id="bb497-137">L’exemple suivant montre comment spécifier une stratégie de mise en cache FTP de `NoCacheNoStore`.</span><span class="sxs-lookup"><span data-stu-id="bb497-137">The following example shows how to specify an FTP caching policy of `NoCacheNoStore`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bb497-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bb497-138">See also</span></span>

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [<span data-ttu-id="bb497-139">Schéma des paramètres réseau</span><span class="sxs-lookup"><span data-stu-id="bb497-139">Network Settings Schema</span></span>](index.md)

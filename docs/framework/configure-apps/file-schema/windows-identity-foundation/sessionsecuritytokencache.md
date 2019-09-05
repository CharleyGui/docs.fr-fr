---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: e949b16f76f20191b84bbbbb6e8b019d913316f0
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251828"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="95da6-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="95da6-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="95da6-102">Inscrit un cache pour les jetons de session avec un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="95da6-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="95da6-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="95da6-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="95da6-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="95da6-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="95da6-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="95da6-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="95da6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<caches >** ](caches.md)</span><span class="sxs-lookup"><span data-stu-id="95da6-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="95da6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sessionSecurityTokenCache >**</span><span class="sxs-lookup"><span data-stu-id="95da6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95da6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95da6-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95da6-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="95da6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="95da6-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="95da6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95da6-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="95da6-111">Attributes</span></span>  
  
|<span data-ttu-id="95da6-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="95da6-112">Attribute</span></span>|<span data-ttu-id="95da6-113">Description</span><span class="sxs-lookup"><span data-stu-id="95da6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95da6-114">type</span><span class="sxs-lookup"><span data-stu-id="95da6-114">type</span></span>|<span data-ttu-id="95da6-115">Type qui dérive de la <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> classe.</span><span class="sxs-lookup"><span data-stu-id="95da6-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95da6-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="95da6-116">Child Elements</span></span>  
 <span data-ttu-id="95da6-117">Aucun</span><span class="sxs-lookup"><span data-stu-id="95da6-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="95da6-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="95da6-118">Parent Elements</span></span>  
  
|<span data-ttu-id="95da6-119">Élément</span><span class="sxs-lookup"><span data-stu-id="95da6-119">Element</span></span>|<span data-ttu-id="95da6-120">Description</span><span class="sxs-lookup"><span data-stu-id="95da6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95da6-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="95da6-121">\<caches></span></span>](caches.md)|<span data-ttu-id="95da6-122">Inscrit les caches utilisés par un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="95da6-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="95da6-123">Exemples</span><span class="sxs-lookup"><span data-stu-id="95da6-123">Example</span></span>  
 <span data-ttu-id="95da6-124">Le code XML suivant montre la configuration d’un cache personnalisé pour la conservation des jetons de<xref:System.IdentityModel.Tokens.SessionSecurityToken>sécurité de session ().</span><span class="sxs-lookup"><span data-stu-id="95da6-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="95da6-125">La configuration est extraite de `ClaimsAwareWebFarm` l’exemple.</span><span class="sxs-lookup"><span data-stu-id="95da6-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="95da6-126">Pour plus d’informations sur cet exemple, consultez [exemple d’index de code WIF](../../../security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="95da6-126">For more information about this sample, see [WIF Code Sample Index](../../../security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95da6-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95da6-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>

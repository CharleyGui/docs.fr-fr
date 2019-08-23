---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 9be3bf980c3756678d26d8652271113d4daaba43
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943709"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="afb1b-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="afb1b-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="afb1b-102">Inscrit un cache pour les jetons de session avec un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="afb1b-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="afb1b-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="afb1b-103">\<system.identityModel></span></span>  
<span data-ttu-id="afb1b-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="afb1b-104">\<identityConfiguration></span></span>  
<span data-ttu-id="afb1b-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="afb1b-105">\<caches></span></span>  
<span data-ttu-id="afb1b-106">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="afb1b-106">\<sessionSecurityTokenCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afb1b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afb1b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afb1b-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="afb1b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="afb1b-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="afb1b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afb1b-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="afb1b-110">Attributes</span></span>  
  
|<span data-ttu-id="afb1b-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="afb1b-111">Attribute</span></span>|<span data-ttu-id="afb1b-112">Description</span><span class="sxs-lookup"><span data-stu-id="afb1b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="afb1b-113">type</span><span class="sxs-lookup"><span data-stu-id="afb1b-113">type</span></span>|<span data-ttu-id="afb1b-114">Type qui dérive de la <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> classe.</span><span class="sxs-lookup"><span data-stu-id="afb1b-114">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="afb1b-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="afb1b-115">Child Elements</span></span>  
 <span data-ttu-id="afb1b-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="afb1b-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="afb1b-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="afb1b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="afb1b-118">Élément</span><span class="sxs-lookup"><span data-stu-id="afb1b-118">Element</span></span>|<span data-ttu-id="afb1b-119">Description</span><span class="sxs-lookup"><span data-stu-id="afb1b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afb1b-120">\<caches></span><span class="sxs-lookup"><span data-stu-id="afb1b-120">\<caches></span></span>](caches.md)|<span data-ttu-id="afb1b-121">Inscrit les caches utilisés par un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="afb1b-121">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="afb1b-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="afb1b-122">Example</span></span>  
 <span data-ttu-id="afb1b-123">Le code XML suivant montre la configuration d’un cache personnalisé pour la conservation des jetons de<xref:System.IdentityModel.Tokens.SessionSecurityToken>sécurité de session ().</span><span class="sxs-lookup"><span data-stu-id="afb1b-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="afb1b-124">La configuration est extraite de `ClaimsAwareWebFarm` l’exemple.</span><span class="sxs-lookup"><span data-stu-id="afb1b-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="afb1b-125">Pour plus d’informations sur cet exemple, consultez [exemple d’index de code WIF](../../../security/wif-code-sample-index.md).</span><span class="sxs-lookup"><span data-stu-id="afb1b-125">For more information about this sample, see [WIF Code Sample Index](../../../security/wif-code-sample-index.md).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="afb1b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="afb1b-126">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>

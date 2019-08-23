---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 5ad75ae18772d6e7c724f2cbf40c1e3083d5c345
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941966"
---
# <a name="caches"></a><span data-ttu-id="5bd7b-101">\<caches></span><span class="sxs-lookup"><span data-stu-id="5bd7b-101">\<caches></span></span>
<span data-ttu-id="5bd7b-102">Inscrit les caches utilisés pour les jetons de session et la détection de relecture de jetons.</span><span class="sxs-lookup"><span data-stu-id="5bd7b-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
 <span data-ttu-id="5bd7b-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5bd7b-103">\<system.identityModel></span></span>  
<span data-ttu-id="5bd7b-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="5bd7b-104">\<identityConfiguration></span></span>  
<span data-ttu-id="5bd7b-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="5bd7b-105">\<caches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bd7b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bd7b-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bd7b-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5bd7b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="5bd7b-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5bd7b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bd7b-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="5bd7b-109">Attributes</span></span>  
 <span data-ttu-id="5bd7b-110">Aucun</span><span class="sxs-lookup"><span data-stu-id="5bd7b-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5bd7b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5bd7b-111">Child Elements</span></span>  
  
|<span data-ttu-id="5bd7b-112">Élément</span><span class="sxs-lookup"><span data-stu-id="5bd7b-112">Element</span></span>|<span data-ttu-id="5bd7b-113">Description</span><span class="sxs-lookup"><span data-stu-id="5bd7b-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bd7b-114">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="5bd7b-114">\<sessionSecurityTokenCache></span></span>](sessionsecuritytokencache.md)|<span data-ttu-id="5bd7b-115">Inscrit un cache pour les jetons de session avec un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="5bd7b-115">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="5bd7b-116">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="5bd7b-116">\<tokenReplayCache></span></span>](tokenreplaycache.md)|<span data-ttu-id="5bd7b-117">Inscrit un cache de relecture de jetons avec un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="5bd7b-117">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5bd7b-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5bd7b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5bd7b-119">Élément</span><span class="sxs-lookup"><span data-stu-id="5bd7b-119">Element</span></span>|<span data-ttu-id="5bd7b-120">Description</span><span class="sxs-lookup"><span data-stu-id="5bd7b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bd7b-121">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="5bd7b-121">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="5bd7b-122">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="5bd7b-122">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="5bd7b-123">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="5bd7b-123">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="5bd7b-124">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="5bd7b-124">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bd7b-125">Notes</span><span class="sxs-lookup"><span data-stu-id="5bd7b-125">Remarks</span></span>  
 <span data-ttu-id="5bd7b-126">Un `<caches>` élément peut être spécifié au niveau du service sous l' `<identityConfiguration>` élément ou au niveau de la collection du gestionnaire de jetons `<securityTokenHandlerConfiguration>` de sécurité sous l’élément.</span><span class="sxs-lookup"><span data-stu-id="5bd7b-126">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="5bd7b-127">Les paramètres d’une collection de gestionnaires de jetons remplacent ceux spécifiés sur le service.</span><span class="sxs-lookup"><span data-stu-id="5bd7b-127">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="5bd7b-128">L' `<caches>` élément est représenté par la <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> classe.</span><span class="sxs-lookup"><span data-stu-id="5bd7b-128">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="5bd7b-129">Les caches configurés sont représentés par <xref:System.IdentityModel.Configuration.IdentityModelCaches> la classe.</span><span class="sxs-lookup"><span data-stu-id="5bd7b-129">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bd7b-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="5bd7b-130">Example</span></span>  
 <span data-ttu-id="5bd7b-131">Le code XML suivant montre la configuration d’un cache personnalisé pour la conservation des jetons de<xref:System.IdentityModel.Tokens.SessionSecurityToken>sécurité de session ().</span><span class="sxs-lookup"><span data-stu-id="5bd7b-131">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="5bd7b-132">La configuration est extraite de `ClaimsAwareWebFarm` l’exemple.</span><span class="sxs-lookup"><span data-stu-id="5bd7b-132">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```

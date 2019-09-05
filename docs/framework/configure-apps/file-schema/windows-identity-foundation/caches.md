---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252161"
---
# <a name="caches"></a><span data-ttu-id="25274-101">\<caches></span><span class="sxs-lookup"><span data-stu-id="25274-101">\<caches></span></span>
<span data-ttu-id="25274-102">Inscrit les caches utilisés pour les jetons de session et la détection de relecture de jetons.</span><span class="sxs-lookup"><span data-stu-id="25274-102">Registers the caches used for session tokens and token replay detection.</span></span>  
  
<span data-ttu-id="25274-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="25274-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="25274-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="25274-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="25274-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="25274-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="25274-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<caches >**</span><span class="sxs-lookup"><span data-stu-id="25274-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25274-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25274-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25274-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="25274-108">Attributes and Elements</span></span>  
 <span data-ttu-id="25274-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="25274-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25274-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="25274-110">Attributes</span></span>  
 <span data-ttu-id="25274-111">Aucun</span><span class="sxs-lookup"><span data-stu-id="25274-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="25274-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="25274-112">Child Elements</span></span>  
  
|<span data-ttu-id="25274-113">Élément</span><span class="sxs-lookup"><span data-stu-id="25274-113">Element</span></span>|<span data-ttu-id="25274-114">Description</span><span class="sxs-lookup"><span data-stu-id="25274-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25274-115">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="25274-115">\<sessionSecurityTokenCache></span></span>](sessionsecuritytokencache.md)|<span data-ttu-id="25274-116">Inscrit un cache pour les jetons de session avec un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="25274-116">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[<span data-ttu-id="25274-117">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="25274-117">\<tokenReplayCache></span></span>](tokenreplaycache.md)|<span data-ttu-id="25274-118">Inscrit un cache de relecture de jetons avec un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="25274-118">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="25274-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="25274-119">Parent Elements</span></span>  
  
|<span data-ttu-id="25274-120">Élément</span><span class="sxs-lookup"><span data-stu-id="25274-120">Element</span></span>|<span data-ttu-id="25274-121">Description</span><span class="sxs-lookup"><span data-stu-id="25274-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25274-122">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="25274-122">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="25274-123">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="25274-123">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="25274-124">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="25274-124">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="25274-125">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="25274-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25274-126">Notes</span><span class="sxs-lookup"><span data-stu-id="25274-126">Remarks</span></span>  
 <span data-ttu-id="25274-127">Un `<caches>` élément peut être spécifié au niveau du service sous l' `<identityConfiguration>` élément ou au niveau de la collection du gestionnaire de jetons `<securityTokenHandlerConfiguration>` de sécurité sous l’élément.</span><span class="sxs-lookup"><span data-stu-id="25274-127">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="25274-128">Les paramètres d’une collection de gestionnaires de jetons remplacent ceux spécifiés sur le service.</span><span class="sxs-lookup"><span data-stu-id="25274-128">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="25274-129">L' `<caches>` élément est représenté par la <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> classe.</span><span class="sxs-lookup"><span data-stu-id="25274-129">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="25274-130">Les caches configurés sont représentés par <xref:System.IdentityModel.Configuration.IdentityModelCaches> la classe.</span><span class="sxs-lookup"><span data-stu-id="25274-130">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25274-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="25274-131">Example</span></span>  
 <span data-ttu-id="25274-132">Le code XML suivant montre la configuration d’un cache personnalisé pour la conservation des jetons de<xref:System.IdentityModel.Tokens.SessionSecurityToken>sécurité de session ().</span><span class="sxs-lookup"><span data-stu-id="25274-132">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="25274-133">La configuration est extraite de `ClaimsAwareWebFarm` l’exemple.</span><span class="sxs-lookup"><span data-stu-id="25274-133">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```

---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252161"
---
# \<caches>
<span data-ttu-id="488e9-101">Inscrit les caches utilisés pour les jetons de session et la détection de relecture de jetons.</span><span class="sxs-lookup"><span data-stu-id="488e9-101">Registers the caches used for session tokens and token replay detection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a><span data-ttu-id="488e9-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="488e9-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="488e9-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="488e9-103">Attributes and Elements</span></span>  
 <span data-ttu-id="488e9-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="488e9-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="488e9-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="488e9-105">Attributes</span></span>  
 <span data-ttu-id="488e9-106">Aucune</span><span class="sxs-lookup"><span data-stu-id="488e9-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="488e9-107">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="488e9-107">Child Elements</span></span>  
  
|<span data-ttu-id="488e9-108">Élément</span><span class="sxs-lookup"><span data-stu-id="488e9-108">Element</span></span>|<span data-ttu-id="488e9-109">Description</span><span class="sxs-lookup"><span data-stu-id="488e9-109">Description</span></span>|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|<span data-ttu-id="488e9-110">Inscrit un cache pour les jetons de session avec un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="488e9-110">Registers a cache for session tokens with a service or a security token handler collection.</span></span>|  
|[\<tokenReplayCache>](tokenreplaycache.md)|<span data-ttu-id="488e9-111">Inscrit un cache de relecture de jetons avec un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="488e9-111">Registers a token replay cache with a service or a security token handler collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="488e9-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="488e9-112">Parent Elements</span></span>  
  
|<span data-ttu-id="488e9-113">Élément</span><span class="sxs-lookup"><span data-stu-id="488e9-113">Element</span></span>|<span data-ttu-id="488e9-114">Description</span><span class="sxs-lookup"><span data-stu-id="488e9-114">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="488e9-115">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="488e9-115">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="488e9-116">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="488e9-116">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="488e9-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="488e9-117">Remarks</span></span>  
 <span data-ttu-id="488e9-118">Un `<caches>` élément peut être spécifié au niveau du service sous l' `<identityConfiguration>` élément ou au niveau de la collection du gestionnaire de jetons de sécurité sous l' `<securityTokenHandlerConfiguration>` élément.</span><span class="sxs-lookup"><span data-stu-id="488e9-118">A `<caches>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="488e9-119">Les paramètres d’une collection de gestionnaires de jetons remplacent ceux spécifiés sur le service.</span><span class="sxs-lookup"><span data-stu-id="488e9-119">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="488e9-120">L' `<caches>` élément est représenté par la <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> classe.</span><span class="sxs-lookup"><span data-stu-id="488e9-120">The `<caches>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> class.</span></span> <span data-ttu-id="488e9-121">Les caches configurés sont représentés par la <xref:System.IdentityModel.Configuration.IdentityModelCaches> classe.</span><span class="sxs-lookup"><span data-stu-id="488e9-121">The configured caches are represented by the <xref:System.IdentityModel.Configuration.IdentityModelCaches> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="488e9-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="488e9-122">Example</span></span>  
 <span data-ttu-id="488e9-123">Le code XML suivant montre la configuration d’un cache personnalisé pour la conservation des jetons de sécurité de session ( <xref:System.IdentityModel.Tokens.SessionSecurityToken> ).</span><span class="sxs-lookup"><span data-stu-id="488e9-123">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="488e9-124">La configuration est extraite de l' `ClaimsAwareWebFarm` exemple.</span><span class="sxs-lookup"><span data-stu-id="488e9-124">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```

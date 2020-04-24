---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: a0db10ceb75a470dbf799d717b2059355dd104bb
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646068"
---
# <a name="sessionsecuritytokencache"></a><span data-ttu-id="86f66-101">\<sessionSecurityTokenCache></span><span class="sxs-lookup"><span data-stu-id="86f66-101">\<sessionSecurityTokenCache></span></span>
<span data-ttu-id="86f66-102">Enregistre un cache pour les jetons de session avec un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="86f66-102">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="86f66-103">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="86f66-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="86f66-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="86f66-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="86f66-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identitéConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="86f66-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="86f66-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span><span class="sxs-lookup"><span data-stu-id="86f66-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="86f66-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**</span><span class="sxs-lookup"><span data-stu-id="86f66-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f66-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86f66-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86f66-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="86f66-109">Attributes and Elements</span></span>  
 <span data-ttu-id="86f66-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="86f66-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86f66-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="86f66-111">Attributes</span></span>  
  
|<span data-ttu-id="86f66-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="86f66-112">Attribute</span></span>|<span data-ttu-id="86f66-113">Description</span><span class="sxs-lookup"><span data-stu-id="86f66-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86f66-114">type</span><span class="sxs-lookup"><span data-stu-id="86f66-114">type</span></span>|<span data-ttu-id="86f66-115">Un type qui dérive <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> de la classe.</span><span class="sxs-lookup"><span data-stu-id="86f66-115">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86f66-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="86f66-116">Child Elements</span></span>  
 <span data-ttu-id="86f66-117">None</span><span class="sxs-lookup"><span data-stu-id="86f66-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86f66-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="86f66-118">Parent Elements</span></span>  
  
|<span data-ttu-id="86f66-119">Élément</span><span class="sxs-lookup"><span data-stu-id="86f66-119">Element</span></span>|<span data-ttu-id="86f66-120">Description</span><span class="sxs-lookup"><span data-stu-id="86f66-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86f66-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="86f66-121">\<caches></span></span>](caches.md)|<span data-ttu-id="86f66-122">Enregistre les caches utilisées par un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="86f66-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="86f66-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="86f66-123">Example</span></span>  
 <span data-ttu-id="86f66-124">Le XML suivant montre la configuration d’un cache<xref:System.IdentityModel.Tokens.SessionSecurityToken>personnalisé pour la tenue de jetons de sécurité de session ( ).</span><span class="sxs-lookup"><span data-stu-id="86f66-124">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="86f66-125">La configuration est `ClaimsAwareWebFarm` prélevée sur l’échantillon.</span><span class="sxs-lookup"><span data-stu-id="86f66-125">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="86f66-126">Pour plus d’informations sur cet exemple, voir [L’indice d’échantillon de code WIF](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span><span class="sxs-lookup"><span data-stu-id="86f66-126">For more information about this sample, see [WIF Code Sample Index](https://docs.microsoft.com/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="86f66-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="86f66-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>

---
title: <sessionSecurityTokenCache>
ms.date: 03/30/2017
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
author: BrucePerlerMS
ms.openlocfilehash: 4169fe307e9ef7c391500a2292fcc247f435caa9
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555885"
---
# \<sessionSecurityTokenCache>
<span data-ttu-id="adec3-101">Inscrit un cache pour les jetons de session avec un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="adec3-101">Registers a cache for session tokens with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sessionSecurityTokenCache>**  
  
## <a name="syntax"></a><span data-ttu-id="adec3-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adec3-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adec3-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="adec3-103">Attributes and Elements</span></span>  
 <span data-ttu-id="adec3-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="adec3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adec3-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="adec3-105">Attributes</span></span>  
  
|<span data-ttu-id="adec3-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="adec3-106">Attribute</span></span>|<span data-ttu-id="adec3-107">Description</span><span class="sxs-lookup"><span data-stu-id="adec3-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="adec3-108">type</span><span class="sxs-lookup"><span data-stu-id="adec3-108">type</span></span>|<span data-ttu-id="adec3-109">Type qui dérive de la <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> classe.</span><span class="sxs-lookup"><span data-stu-id="adec3-109">A type that derives from the <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache> class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adec3-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="adec3-110">Child Elements</span></span>  
 <span data-ttu-id="adec3-111">None</span><span class="sxs-lookup"><span data-stu-id="adec3-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="adec3-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="adec3-112">Parent Elements</span></span>  
  
|<span data-ttu-id="adec3-113">Élément</span><span class="sxs-lookup"><span data-stu-id="adec3-113">Element</span></span>|<span data-ttu-id="adec3-114">Description</span><span class="sxs-lookup"><span data-stu-id="adec3-114">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="adec3-115">Inscrit les caches utilisés par un service ou une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="adec3-115">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="adec3-116"> Exemple</span><span class="sxs-lookup"><span data-stu-id="adec3-116">Example</span></span>  
 <span data-ttu-id="adec3-117">Le code XML suivant montre la configuration d’un cache personnalisé pour la conservation des jetons de sécurité de session ( <xref:System.IdentityModel.Tokens.SessionSecurityToken> ).</span><span class="sxs-lookup"><span data-stu-id="adec3-117">The following XML shows the configuration of a custom cache for holding session security tokens (<xref:System.IdentityModel.Tokens.SessionSecurityToken>).</span></span> <span data-ttu-id="adec3-118">La configuration est extraite de l' `ClaimsAwareWebFarm` exemple.</span><span class="sxs-lookup"><span data-stu-id="adec3-118">The configuration is taken from the `ClaimsAwareWebFarm` sample.</span></span> <span data-ttu-id="adec3-119">Pour plus d’informations sur cet exemple, consultez [exemple d’index de code WIF](/previous-versions/dotnet/framework/security/wif-code-sample-index).</span><span class="sxs-lookup"><span data-stu-id="adec3-119">For more information about this sample, see [WIF Code Sample Index](/previous-versions/dotnet/framework/security/wif-code-sample-index).</span></span>  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="adec3-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adec3-120">See also</span></span>

- <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>

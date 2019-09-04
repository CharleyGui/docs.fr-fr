---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: a4454042e1d97fb3cc2d6f2735104dadda6e7b5a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251772"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="d3617-101">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="d3617-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="d3617-102">Active la détection de relecture de jetons et spécifie l’heure d’expiration des jetons.</span><span class="sxs-lookup"><span data-stu-id="d3617-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
<span data-ttu-id="d3617-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d3617-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d3617-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="d3617-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="d3617-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d3617-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="d3617-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tokenReplayDetection >**</span><span class="sxs-lookup"><span data-stu-id="d3617-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3617-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3617-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="d3617-108">Type</span><span class="sxs-lookup"><span data-stu-id="d3617-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3617-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d3617-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d3617-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d3617-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3617-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="d3617-111">Attributes</span></span>  
  
|<span data-ttu-id="d3617-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="d3617-112">Attribute</span></span>|<span data-ttu-id="d3617-113">Description</span><span class="sxs-lookup"><span data-stu-id="d3617-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3617-114">enabled</span><span class="sxs-lookup"><span data-stu-id="d3617-114">enabled</span></span>|<span data-ttu-id="d3617-115">Valeur qui spécifie si la détection de relecture de jetons est activée ; « true » pour activer la détection de relecture de jetons.</span><span class="sxs-lookup"><span data-stu-id="d3617-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="d3617-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="d3617-116">expirationPeriod</span></span>|<span data-ttu-id="d3617-117"><xref:System.TimeSpan> Qui spécifie la durée maximale avant qu’un élément soit considéré comme expiré et supprimé du cache.</span><span class="sxs-lookup"><span data-stu-id="d3617-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="d3617-118">Pour plus d’informations sur la spécification <xref:System.TimeSpan> des valeurs, consultez [TimeSpan values](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="d3617-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3617-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d3617-119">Child Elements</span></span>  
 <span data-ttu-id="d3617-120">Aucun</span><span class="sxs-lookup"><span data-stu-id="d3617-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3617-121">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d3617-121">Parent Elements</span></span>  
  
|<span data-ttu-id="d3617-122">Élément</span><span class="sxs-lookup"><span data-stu-id="d3617-122">Element</span></span>|<span data-ttu-id="d3617-123">Description</span><span class="sxs-lookup"><span data-stu-id="d3617-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3617-124">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d3617-124">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="d3617-125">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="d3617-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="d3617-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="d3617-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="d3617-127">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="d3617-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3617-128">Notes</span><span class="sxs-lookup"><span data-stu-id="d3617-128">Remarks</span></span>  
 <span data-ttu-id="d3617-129">Un `<tokenReplayDetection>` élément peut être spécifié au niveau du service sous l' `<identityConfiguration>` élément ou au niveau de la collection du gestionnaire de jetons `<securityTokenHandlerConfiguration>` de sécurité sous l’élément.</span><span class="sxs-lookup"><span data-stu-id="d3617-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="d3617-130">Les paramètres d’une collection de gestionnaires de jetons remplacent ceux spécifiés sur le service.</span><span class="sxs-lookup"><span data-stu-id="d3617-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="d3617-131">Le type de cache de relecture de jetons est spécifié par l' [ \<élément tokenReplayCache >](tokenreplaycache.md) .</span><span class="sxs-lookup"><span data-stu-id="d3617-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>

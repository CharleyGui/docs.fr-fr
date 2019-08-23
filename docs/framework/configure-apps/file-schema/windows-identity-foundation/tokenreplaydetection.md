---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: 2e2159a73ca79fc362a8138eea95dbd173dafb11
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944300"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="1e980-101">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="1e980-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="1e980-102">Active la détection de relecture de jetons et spécifie l’heure d’expiration des jetons.</span><span class="sxs-lookup"><span data-stu-id="1e980-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="1e980-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1e980-103">\<system.identityModel></span></span>  
<span data-ttu-id="1e980-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="1e980-104">\<identityConfiguration></span></span>  
<span data-ttu-id="1e980-105">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="1e980-105">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e980-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e980-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="1e980-107">Type</span><span class="sxs-lookup"><span data-stu-id="1e980-107">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e980-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1e980-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1e980-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1e980-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e980-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="1e980-110">Attributes</span></span>  
  
|<span data-ttu-id="1e980-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="1e980-111">Attribute</span></span>|<span data-ttu-id="1e980-112">Description</span><span class="sxs-lookup"><span data-stu-id="1e980-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1e980-113">enabled</span><span class="sxs-lookup"><span data-stu-id="1e980-113">enabled</span></span>|<span data-ttu-id="1e980-114">Valeur qui spécifie si la détection de relecture de jetons est activée; «true» pour activer la détection de relecture de jetons.</span><span class="sxs-lookup"><span data-stu-id="1e980-114">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="1e980-115">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="1e980-115">expirationPeriod</span></span>|<span data-ttu-id="1e980-116"><xref:System.TimeSpan> Qui spécifie la durée maximale avant qu’un élément soit considéré comme expiré et supprimé du cache.</span><span class="sxs-lookup"><span data-stu-id="1e980-116">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="1e980-117">Pour plus d’informations sur la spécification <xref:System.TimeSpan> des valeurs, consultez [TimeSpan values](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="1e980-117">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e980-118">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1e980-118">Child Elements</span></span>  
 <span data-ttu-id="1e980-119">Aucun</span><span class="sxs-lookup"><span data-stu-id="1e980-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e980-120">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1e980-120">Parent Elements</span></span>  
  
|<span data-ttu-id="1e980-121">Élément</span><span class="sxs-lookup"><span data-stu-id="1e980-121">Element</span></span>|<span data-ttu-id="1e980-122">Description</span><span class="sxs-lookup"><span data-stu-id="1e980-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e980-123">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="1e980-123">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="1e980-124">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="1e980-124">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="1e980-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="1e980-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="1e980-126">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="1e980-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e980-127">Notes</span><span class="sxs-lookup"><span data-stu-id="1e980-127">Remarks</span></span>  
 <span data-ttu-id="1e980-128">Un `<tokenReplayDetection>` élément peut être spécifié au niveau du service sous l' `<identityConfiguration>` élément ou au niveau de la collection du gestionnaire de jetons `<securityTokenHandlerConfiguration>` de sécurité sous l’élément.</span><span class="sxs-lookup"><span data-stu-id="1e980-128">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="1e980-129">Les paramètres d’une collection de gestionnaires de jetons remplacent ceux spécifiés sur le service.</span><span class="sxs-lookup"><span data-stu-id="1e980-129">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="1e980-130">Le type de cache de relecture de jetons est spécifié par l' [ \<élément tokenReplayCache >](tokenreplaycache.md) .</span><span class="sxs-lookup"><span data-stu-id="1e980-130">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>

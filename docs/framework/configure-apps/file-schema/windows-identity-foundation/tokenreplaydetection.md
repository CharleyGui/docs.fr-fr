---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: df512960b522f17dc9247bb5959e246c8c1f15b8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169802"
---
# \<tokenReplayDetection>

<span data-ttu-id="03ffa-101">Active la détection de relecture de jetons et spécifie l’heure d’expiration des jetons.</span><span class="sxs-lookup"><span data-stu-id="03ffa-101">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**  
  
## <a name="syntax"></a><span data-ttu-id="03ffa-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03ffa-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="03ffa-103">Type</span><span class="sxs-lookup"><span data-stu-id="03ffa-103">Type</span></span>  

 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03ffa-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="03ffa-104">Attributes and Elements</span></span>  

 <span data-ttu-id="03ffa-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="03ffa-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03ffa-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="03ffa-106">Attributes</span></span>  
  
|<span data-ttu-id="03ffa-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="03ffa-107">Attribute</span></span>|<span data-ttu-id="03ffa-108">Description</span><span class="sxs-lookup"><span data-stu-id="03ffa-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="03ffa-109">enabled</span><span class="sxs-lookup"><span data-stu-id="03ffa-109">enabled</span></span>|<span data-ttu-id="03ffa-110">Valeur qui spécifie si la détection de relecture de jetons est activée ; « true » pour activer la détection de relecture de jetons.</span><span class="sxs-lookup"><span data-stu-id="03ffa-110">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="03ffa-111">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="03ffa-111">expirationPeriod</span></span>|<span data-ttu-id="03ffa-112"><xref:System.TimeSpan>Qui spécifie la durée maximale avant qu’un élément soit considéré comme expiré et supprimé du cache.</span><span class="sxs-lookup"><span data-stu-id="03ffa-112">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="03ffa-113">Pour plus d’informations sur la spécification des <xref:System.TimeSpan> valeurs, consultez [TimeSpan values](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="03ffa-113">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="03ffa-114">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="03ffa-114">Child Elements</span></span>  

 <span data-ttu-id="03ffa-115">None</span><span class="sxs-lookup"><span data-stu-id="03ffa-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="03ffa-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="03ffa-116">Parent Elements</span></span>  
  
|<span data-ttu-id="03ffa-117">Élément</span><span class="sxs-lookup"><span data-stu-id="03ffa-117">Element</span></span>|<span data-ttu-id="03ffa-118">Description</span><span class="sxs-lookup"><span data-stu-id="03ffa-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="03ffa-119">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="03ffa-119">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="03ffa-120">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="03ffa-120">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03ffa-121">Notes</span><span class="sxs-lookup"><span data-stu-id="03ffa-121">Remarks</span></span>  

 <span data-ttu-id="03ffa-122">Un `<tokenReplayDetection>` élément peut être spécifié au niveau du service sous l' `<identityConfiguration>` élément ou au niveau de la collection du gestionnaire de jetons de sécurité sous l' `<securityTokenHandlerConfiguration>` élément.</span><span class="sxs-lookup"><span data-stu-id="03ffa-122">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="03ffa-123">Les paramètres d’une collection de gestionnaires de jetons remplacent ceux spécifiés sur le service.</span><span class="sxs-lookup"><span data-stu-id="03ffa-123">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="03ffa-124">Le type du cache de relecture de jetons est spécifié par l' [\<tokenReplayCache>](tokenreplaycache.md) élément.</span><span class="sxs-lookup"><span data-stu-id="03ffa-124">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>

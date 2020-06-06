---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 017309436660991c69da569e9cc4219e842ecaa3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251878"
---
# \<securityTokenHandlers>
<span data-ttu-id="94d42-101">Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="94d42-101">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
## <a name="syntax"></a><span data-ttu-id="94d42-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94d42-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94d42-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="94d42-103">Attributes and Elements</span></span>  
 <span data-ttu-id="94d42-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="94d42-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94d42-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="94d42-105">Attributes</span></span>  
  
|<span data-ttu-id="94d42-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="94d42-106">Attribute</span></span>|<span data-ttu-id="94d42-107">Description</span><span class="sxs-lookup"><span data-stu-id="94d42-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94d42-108">name</span><span class="sxs-lookup"><span data-stu-id="94d42-108">name</span></span>|<span data-ttu-id="94d42-109">Spécifie le nom d’une collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="94d42-109">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="94d42-110">Les seules valeurs reconnues par l’infrastructure sont « ActAs » et « OnBehalfOf ».</span><span class="sxs-lookup"><span data-stu-id="94d42-110">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="94d42-111">Si les collections de gestionnaires de jetons sont spécifiées avec l’un de ces noms, la collection sera utilisée lors du traitement des jetons ActAs ou OnBehalfOf, respectivement.</span><span class="sxs-lookup"><span data-stu-id="94d42-111">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94d42-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="94d42-112">Child Elements</span></span>  
  
|<span data-ttu-id="94d42-113">Élément</span><span class="sxs-lookup"><span data-stu-id="94d42-113">Element</span></span>|<span data-ttu-id="94d42-114">Description</span><span class="sxs-lookup"><span data-stu-id="94d42-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="94d42-115">Ajoute un gestionnaire de jetons de sécurité à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="94d42-115">Adds a security token handler to the token handler collection.</span></span>|  
|[\<clear>](clear.md)|<span data-ttu-id="94d42-116">Efface tous les gestionnaires de jetons de sécurité de la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="94d42-116">Clears all security token handlers from the token handler collection.</span></span>|  
|[\<remove>](remove.md)|<span data-ttu-id="94d42-117">Supprime un gestionnaire de jetons de sécurité de la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="94d42-117">Removes a security token handler from the token handler collection.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="94d42-118">Fournit la configuration pour la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="94d42-118">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="94d42-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="94d42-119">Parent Elements</span></span>  
  
|<span data-ttu-id="94d42-120">Élément</span><span class="sxs-lookup"><span data-stu-id="94d42-120">Element</span></span>|<span data-ttu-id="94d42-121">Description</span><span class="sxs-lookup"><span data-stu-id="94d42-121">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="94d42-122">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="94d42-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94d42-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="94d42-123">Remarks</span></span>  
 <span data-ttu-id="94d42-124">Vous pouvez spécifier une ou plusieurs collections nommées de gestionnaires de jetons de sécurité dans une configuration de service.</span><span class="sxs-lookup"><span data-stu-id="94d42-124">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="94d42-125">Vous pouvez spécifier un nom pour une collection à l’aide de l' `name` attribut.</span><span class="sxs-lookup"><span data-stu-id="94d42-125">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="94d42-126">Les seuls noms que le Framework gère sont « ActAs » et « OnBehalfOf ».</span><span class="sxs-lookup"><span data-stu-id="94d42-126">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="94d42-127">Si des gestionnaires existent dans ces collections, ils sont utilisés par un service d’émission de jeton de sécurité (STS) à la place des gestionnaires par défaut lors du traitement `ActAs` et des `OnBehalfOf` jetons.</span><span class="sxs-lookup"><span data-stu-id="94d42-127">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="94d42-128">Par défaut, la collection est remplie avec les types de gestionnaires suivants : <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ,,,, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> et <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="94d42-128">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="94d42-129">Vous pouvez modifier la collection à l’aide `<add>` des `<remove>` éléments, et `<clear>` .</span><span class="sxs-lookup"><span data-stu-id="94d42-129">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="94d42-130">Vous devez vous assurer qu’il n’existe qu’un seul gestionnaire d’un type particulier dans la collection.</span><span class="sxs-lookup"><span data-stu-id="94d42-130">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="94d42-131">Par exemple, si vous dérivez un gestionnaire de la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe, votre gestionnaire ou le <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> peut être configuré dans une seule collection, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="94d42-131">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="94d42-132">Utilisez l' `<securityTokenHandlerConfiguration>` élément pour spécifier les paramètres de configuration des gestionnaires dans la collection.</span><span class="sxs-lookup"><span data-stu-id="94d42-132">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="94d42-133">Les paramètres spécifiés par le biais de cet élément remplacent ceux spécifiés sur le service par le biais de l' [\<identityConfiguration>](identityconfiguration.md) élément.</span><span class="sxs-lookup"><span data-stu-id="94d42-133">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="94d42-134">Certains gestionnaires (y compris plusieurs des types de gestionnaires intégrés) peuvent prendre en charge une configuration supplémentaire via un élément enfant de l' `<add>` élément.</span><span class="sxs-lookup"><span data-stu-id="94d42-134">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="94d42-135">Les paramètres spécifiés sur un gestionnaire substituent les paramètres équivalents spécifiés dans la collection ou le service.</span><span class="sxs-lookup"><span data-stu-id="94d42-135">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>

---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: d892fbd802ed366ca7af9b85fbf5c23d4d27e0f1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157003"
---
# \<securityTokenHandlers>

<span data-ttu-id="73176-101">Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="73176-101">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
## <a name="syntax"></a><span data-ttu-id="73176-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73176-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73176-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="73176-103">Attributes and Elements</span></span>  

 <span data-ttu-id="73176-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="73176-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73176-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="73176-105">Attributes</span></span>  
  
|<span data-ttu-id="73176-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="73176-106">Attribute</span></span>|<span data-ttu-id="73176-107">Description</span><span class="sxs-lookup"><span data-stu-id="73176-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73176-108">name</span><span class="sxs-lookup"><span data-stu-id="73176-108">name</span></span>|<span data-ttu-id="73176-109">Spécifie le nom d’une collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="73176-109">Specifies the name of a token handler collection.</span></span> <span data-ttu-id="73176-110">Les seules valeurs reconnues par l’infrastructure sont « ActAs » et « OnBehalfOf ».</span><span class="sxs-lookup"><span data-stu-id="73176-110">The only values recognized by the framework are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="73176-111">Si les collections de gestionnaires de jetons sont spécifiées avec l’un de ces noms, la collection sera utilisée lors du traitement des jetons ActAs ou OnBehalfOf, respectivement.</span><span class="sxs-lookup"><span data-stu-id="73176-111">If token handler collections are specified with either of these names, the collection will be used when processing ActAs or OnBehalfOf tokens respectively.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73176-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="73176-112">Child Elements</span></span>  
  
|<span data-ttu-id="73176-113">Élément</span><span class="sxs-lookup"><span data-stu-id="73176-113">Element</span></span>|<span data-ttu-id="73176-114">Description</span><span class="sxs-lookup"><span data-stu-id="73176-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="73176-115">Ajoute un gestionnaire de jetons de sécurité à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="73176-115">Adds a security token handler to the token handler collection.</span></span>|  
|[\<clear>](clear.md)|<span data-ttu-id="73176-116">Efface tous les gestionnaires de jetons de sécurité de la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="73176-116">Clears all security token handlers from the token handler collection.</span></span>|  
|[\<remove>](remove.md)|<span data-ttu-id="73176-117">Supprime un gestionnaire de jetons de sécurité de la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="73176-117">Removes a security token handler from the token handler collection.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="73176-118">Fournit la configuration pour la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="73176-118">Provides configuration for the collection of token handlers.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73176-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="73176-119">Parent Elements</span></span>  
  
|<span data-ttu-id="73176-120">Élément</span><span class="sxs-lookup"><span data-stu-id="73176-120">Element</span></span>|<span data-ttu-id="73176-121">Description</span><span class="sxs-lookup"><span data-stu-id="73176-121">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="73176-122">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="73176-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73176-123">Notes</span><span class="sxs-lookup"><span data-stu-id="73176-123">Remarks</span></span>  

 <span data-ttu-id="73176-124">Vous pouvez spécifier une ou plusieurs collections nommées de gestionnaires de jetons de sécurité dans une configuration de service.</span><span class="sxs-lookup"><span data-stu-id="73176-124">You can specify one or more named collections of security token handlers in a service configuration.</span></span> <span data-ttu-id="73176-125">Vous pouvez spécifier un nom pour une collection à l’aide de l' `name` attribut.</span><span class="sxs-lookup"><span data-stu-id="73176-125">You can specify a name for a collection by using the `name` attribute.</span></span> <span data-ttu-id="73176-126">Les seuls noms que le Framework gère sont « ActAs » et « OnBehalfOf ».</span><span class="sxs-lookup"><span data-stu-id="73176-126">The only names that the framework handles are "ActAs" and "OnBehalfOf".</span></span> <span data-ttu-id="73176-127">Si des gestionnaires existent dans ces collections, ils sont utilisés par un service d’émission de jeton de sécurité (STS) à la place des gestionnaires par défaut lors du traitement `ActAs` et des `OnBehalfOf` jetons.</span><span class="sxs-lookup"><span data-stu-id="73176-127">If handlers exist in these collections, they are used by a security token service (STS) instead of the default handlers when processing `ActAs` and `OnBehalfOf` tokens.</span></span>  
  
 <span data-ttu-id="73176-128">Par défaut, la collection est remplie avec les types de gestionnaires suivants : <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ,,,, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> et <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="73176-128">By default, the collection is populated with the following handler types: <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>.</span></span> <span data-ttu-id="73176-129">Vous pouvez modifier la collection à l’aide `<add>` des `<remove>` éléments, et `<clear>` .</span><span class="sxs-lookup"><span data-stu-id="73176-129">You can modify the collection by using the `<add>`, `<remove>`, and `<clear>` elements.</span></span> <span data-ttu-id="73176-130">Vous devez vous assurer qu’il n’existe qu’un seul gestionnaire d’un type particulier dans la collection.</span><span class="sxs-lookup"><span data-stu-id="73176-130">You must ensure that only a single handler of any particular type exists in the collection.</span></span> <span data-ttu-id="73176-131">Par exemple, si vous dérivez un gestionnaire de la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe, votre gestionnaire ou le <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> peut être configuré dans une seule collection, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="73176-131">For example, if you derive a handler from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, either your handler or the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> may be configured in a single collection, but not both.</span></span>  
  
 <span data-ttu-id="73176-132">Utilisez l' `<securityTokenHandlerConfiguration>` élément pour spécifier les paramètres de configuration des gestionnaires dans la collection.</span><span class="sxs-lookup"><span data-stu-id="73176-132">Use the `<securityTokenHandlerConfiguration>` element to specify configuration settings for the handlers in the collection.</span></span> <span data-ttu-id="73176-133">Les paramètres spécifiés par le biais de cet élément remplacent ceux spécifiés sur le service par le biais de l' [\<identityConfiguration>](identityconfiguration.md) élément.</span><span class="sxs-lookup"><span data-stu-id="73176-133">Settings specified through this element override those specified on the service through the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="73176-134">Certains gestionnaires (y compris plusieurs des types de gestionnaires intégrés) peuvent prendre en charge une configuration supplémentaire via un élément enfant de l' `<add>` élément.</span><span class="sxs-lookup"><span data-stu-id="73176-134">Some handlers (including several of the built-in handler types) can support additional configuration through a child element of the `<add>` element.</span></span> <span data-ttu-id="73176-135">Les paramètres spécifiés sur un gestionnaire substituent les paramètres équivalents spécifiés dans la collection ou le service.</span><span class="sxs-lookup"><span data-stu-id="73176-135">Settings specified on a handler override equivalent settings specified on the collection or the service.</span></span>

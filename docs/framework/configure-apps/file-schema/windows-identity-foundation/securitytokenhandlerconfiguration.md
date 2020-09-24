---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 4c6affbc24a58424158e466fb732e9a3b3d6f1ed
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157016"
---
# \<securityTokenHandlerConfiguration>

<span data-ttu-id="be3d6-101">Fournit la configuration pour la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="be3d6-101">Provides configuration for the collection of token handlers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="be3d6-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be3d6-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be3d6-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="be3d6-103">Attributes and Elements</span></span>  

 <span data-ttu-id="be3d6-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="be3d6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be3d6-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="be3d6-105">Attributes</span></span>  
  
|<span data-ttu-id="be3d6-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="be3d6-106">Attribute</span></span>|<span data-ttu-id="be3d6-107">Description</span><span class="sxs-lookup"><span data-stu-id="be3d6-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be3d6-108">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="be3d6-108">saveBootstrapContext</span></span>|<span data-ttu-id="be3d6-109">Spécifie si les jetons de démarrage doivent être inclus dans le jeton de session.</span><span class="sxs-lookup"><span data-stu-id="be3d6-109">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="be3d6-110">La valeur peut également être définie sur une collection de gestionnaires de jetons en définissant l' `saveBootstrapContext` attribut sur l' [\<identityConfiguration>](identityconfiguration.md) élément.</span><span class="sxs-lookup"><span data-stu-id="be3d6-110">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="be3d6-111">Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.</span><span class="sxs-lookup"><span data-stu-id="be3d6-111">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="be3d6-112">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="be3d6-112">maximumClockSkew</span></span>|<span data-ttu-id="be3d6-113"><xref:System.TimeSpan>Qui spécifie la variation d’horloge maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="be3d6-113">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="be3d6-114">Contrôle la variation d’horloge maximale autorisée lors de l’exécution d’opérations sensibles au temps, telles que la validation du délai d’expiration d’une session de connexion.</span><span class="sxs-lookup"><span data-stu-id="be3d6-114">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="be3d6-115">La valeur par défaut est 5 minutes, « 00:05:00 ».</span><span class="sxs-lookup"><span data-stu-id="be3d6-115">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="be3d6-116">Pour plus d’informations sur la spécification des <xref:System.TimeSpan> valeurs, consultez [TimeSpan values](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="be3d6-116">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="be3d6-117">Le décalage d’horloge maximal peut également être défini au niveau du service en définissant l' `maximumClockSkew` attribut sur l' [\<identityConfiguration>](identityconfiguration.md) élément.</span><span class="sxs-lookup"><span data-stu-id="be3d6-117">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="be3d6-118">Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.</span><span class="sxs-lookup"><span data-stu-id="be3d6-118">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be3d6-119">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="be3d6-119">Child Elements</span></span>  
  
|<span data-ttu-id="be3d6-120">Élément</span><span class="sxs-lookup"><span data-stu-id="be3d6-120">Element</span></span>|<span data-ttu-id="be3d6-121">Description</span><span class="sxs-lookup"><span data-stu-id="be3d6-121">Description</span></span>|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|<span data-ttu-id="be3d6-122">Spécifie l’ensemble d’URI qui sont des identificateurs acceptables de cette partie de confiance.</span><span class="sxs-lookup"><span data-stu-id="be3d6-122">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="be3d6-123">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="be3d6-123">Optional.</span></span>|  
|[\<caches>](caches.md)|<span data-ttu-id="be3d6-124">Inscrit les caches utilisés pour les jetons de session et la détection de relecture de jetons.</span><span class="sxs-lookup"><span data-stu-id="be3d6-124">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="be3d6-125">Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="be3d6-125">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="be3d6-126">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="be3d6-126">Optional.</span></span>|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="be3d6-127">Contrôle les paramètres que les gestionnaires de jetons utilisent pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="be3d6-127">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="be3d6-128">Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="be3d6-128">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="be3d6-129">Ces paramètres sont substitués si un gestionnaire spécifique est configuré avec son propre validateur.</span><span class="sxs-lookup"><span data-stu-id="be3d6-129">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="be3d6-130">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="be3d6-130">Optional.</span></span>|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="be3d6-131">Configure le registre des noms d’émetteurs qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="be3d6-131">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="be3d6-132">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="be3d6-132">Optional.</span></span>|  
|[\<issuerTokenResolver>](issuertokenresolver.md)|<span data-ttu-id="be3d6-133">Inscrit le programme de résolution de jetons d’émetteur utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="be3d6-133">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="be3d6-134">Le programme de résolution de jetons d’émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="be3d6-134">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="be3d6-135">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="be3d6-135">Optional.</span></span>|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|<span data-ttu-id="be3d6-136">Inscrit le programme de résolution de jetons de service qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="be3d6-136">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="be3d6-137">Le programme de résolution de jetons de service est utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="be3d6-137">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="be3d6-138">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="be3d6-138">Optional.</span></span>|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|<span data-ttu-id="be3d6-139">Active la détection de relecture de jetons et spécifie l’heure d’expiration des jetons.</span><span class="sxs-lookup"><span data-stu-id="be3d6-139">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="be3d6-140">Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="be3d6-140">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="be3d6-141">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="be3d6-141">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be3d6-142">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="be3d6-142">Parent Elements</span></span>  
  
|<span data-ttu-id="be3d6-143">Élément</span><span class="sxs-lookup"><span data-stu-id="be3d6-143">Element</span></span>|<span data-ttu-id="be3d6-144">Description</span><span class="sxs-lookup"><span data-stu-id="be3d6-144">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="be3d6-145">Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="be3d6-145">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be3d6-146">Notes</span><span class="sxs-lookup"><span data-stu-id="be3d6-146">Remarks</span></span>  

 <span data-ttu-id="be3d6-147">Cette section fournit des valeurs de propriété pour un <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> objet.</span><span class="sxs-lookup"><span data-stu-id="be3d6-147">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="be3d6-148">Les paramètres configurés dans cette section remplacent ceux configurés sur le service.</span><span class="sxs-lookup"><span data-stu-id="be3d6-148">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="be3d6-149">Certains de ces paramètres peuvent, à leur tour, être remplacés par les paramètres spécifiés lors de l’ajout d’un gestionnaire à la collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="be3d6-149">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be3d6-150">Exemple</span><span class="sxs-lookup"><span data-stu-id="be3d6-150">Example</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```

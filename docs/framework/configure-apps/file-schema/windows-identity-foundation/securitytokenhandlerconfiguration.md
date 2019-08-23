---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 0aefaa808dfc32085a208420fcd582b1671acc64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942444"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="16151-101">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="16151-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="16151-102">Fournit la configuration pour la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="16151-102">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="16151-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="16151-103">\<system.identityModel></span></span>  
<span data-ttu-id="16151-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="16151-104">\<identityConfiguration></span></span>  
<span data-ttu-id="16151-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="16151-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="16151-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="16151-106">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16151-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16151-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16151-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="16151-108">Attributes and Elements</span></span>  
 <span data-ttu-id="16151-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="16151-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16151-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="16151-110">Attributes</span></span>  
  
|<span data-ttu-id="16151-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="16151-111">Attribute</span></span>|<span data-ttu-id="16151-112">Description</span><span class="sxs-lookup"><span data-stu-id="16151-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16151-113">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="16151-113">saveBootstrapContext</span></span>|<span data-ttu-id="16151-114">Spécifie si les jetons de démarrage doivent être inclus dans le jeton de session.</span><span class="sxs-lookup"><span data-stu-id="16151-114">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="16151-115">La valeur peut également être définie sur une collection de gestionnaires de jetons en `saveBootstrapContext` définissant l’attribut sur l' [ \<élément identityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="16151-115">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="16151-116">Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.</span><span class="sxs-lookup"><span data-stu-id="16151-116">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="16151-117">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="16151-117">maximumClockSkew</span></span>|<span data-ttu-id="16151-118">Qui <xref:System.TimeSpan> spécifie la variation d’horloge maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="16151-118">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="16151-119">Contrôle la variation d’horloge maximale autorisée lors de l’exécution d’opérations sensibles au temps, telles que la validation du délai d’expiration d’une session de connexion.</span><span class="sxs-lookup"><span data-stu-id="16151-119">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="16151-120">La valeur par défaut est 5 minutes, «00:05:00».</span><span class="sxs-lookup"><span data-stu-id="16151-120">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="16151-121">Pour plus d’informations sur la spécification <xref:System.TimeSpan> des valeurs, consultez [TimeSpan values](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="16151-121">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="16151-122">Le décalage d’horloge maximal peut également être défini au niveau du service en définissant l' `maximumClockSkew` attribut sur l' [ \<élément identityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="16151-122">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="16151-123">Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.</span><span class="sxs-lookup"><span data-stu-id="16151-123">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16151-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="16151-124">Child Elements</span></span>  
  
|<span data-ttu-id="16151-125">Élément</span><span class="sxs-lookup"><span data-stu-id="16151-125">Element</span></span>|<span data-ttu-id="16151-126">Description</span><span class="sxs-lookup"><span data-stu-id="16151-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16151-127">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="16151-127">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="16151-128">Spécifie l’ensemble d’URI qui sont des identificateurs acceptables de cette partie de confiance.</span><span class="sxs-lookup"><span data-stu-id="16151-128">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="16151-129">facultatif.</span><span class="sxs-lookup"><span data-stu-id="16151-129">Optional.</span></span>|  
|[<span data-ttu-id="16151-130">\<caches></span><span class="sxs-lookup"><span data-stu-id="16151-130">\<caches></span></span>](caches.md)|<span data-ttu-id="16151-131">Inscrit les caches utilisés pour les jetons de session et la détection de relecture de jetons.</span><span class="sxs-lookup"><span data-stu-id="16151-131">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="16151-132">Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="16151-132">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="16151-133">facultatif.</span><span class="sxs-lookup"><span data-stu-id="16151-133">Optional.</span></span>|  
|[<span data-ttu-id="16151-134">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="16151-134">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="16151-135">Contrôle les paramètres que les gestionnaires de jetons utilisent pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="16151-135">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="16151-136">Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="16151-136">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="16151-137">Ces paramètres sont substitués si un gestionnaire spécifique est configuré avec son propre validateur.</span><span class="sxs-lookup"><span data-stu-id="16151-137">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="16151-138">facultatif.</span><span class="sxs-lookup"><span data-stu-id="16151-138">Optional.</span></span>|  
|[<span data-ttu-id="16151-139">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="16151-139">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="16151-140">Configure le registre des noms d’émetteurs qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="16151-140">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="16151-141">facultatif.</span><span class="sxs-lookup"><span data-stu-id="16151-141">Optional.</span></span>|  
|[<span data-ttu-id="16151-142">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="16151-142">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="16151-143">Inscrit le programme de résolution de jetons d’émetteur utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="16151-143">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="16151-144">Le programme de résolution de jetons d’émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="16151-144">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="16151-145">facultatif.</span><span class="sxs-lookup"><span data-stu-id="16151-145">Optional.</span></span>|  
|[<span data-ttu-id="16151-146">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="16151-146">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="16151-147">Inscrit le programme de résolution de jetons de service qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="16151-147">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="16151-148">Le programme de résolution de jetons de service est utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="16151-148">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="16151-149">facultatif.</span><span class="sxs-lookup"><span data-stu-id="16151-149">Optional.</span></span>|  
|[<span data-ttu-id="16151-150">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="16151-150">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="16151-151">Active la détection de relecture de jetons et spécifie l’heure d’expiration des jetons.</span><span class="sxs-lookup"><span data-stu-id="16151-151">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="16151-152">Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="16151-152">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="16151-153">facultatif.</span><span class="sxs-lookup"><span data-stu-id="16151-153">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="16151-154">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="16151-154">Parent Elements</span></span>  
  
|<span data-ttu-id="16151-155">Élément</span><span class="sxs-lookup"><span data-stu-id="16151-155">Element</span></span>|<span data-ttu-id="16151-156">Description</span><span class="sxs-lookup"><span data-stu-id="16151-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16151-157">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="16151-157">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="16151-158">Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="16151-158">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16151-159">Notes</span><span class="sxs-lookup"><span data-stu-id="16151-159">Remarks</span></span>  
 <span data-ttu-id="16151-160">Cette section fournit des valeurs de propriété <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> pour un objet.</span><span class="sxs-lookup"><span data-stu-id="16151-160">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="16151-161">Les paramètres configurés dans cette section remplacent ceux configurés sur le service.</span><span class="sxs-lookup"><span data-stu-id="16151-161">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="16151-162">Certains de ces paramètres peuvent, à leur tour, être remplacés par les paramètres spécifiés lors de l’ajout d’un gestionnaire à la collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="16151-162">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16151-163">Exemple</span><span class="sxs-lookup"><span data-stu-id="16151-163">Example</span></span>  
  
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

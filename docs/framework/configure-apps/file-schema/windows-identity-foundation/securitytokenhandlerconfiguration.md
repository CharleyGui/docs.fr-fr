---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 330e52bd73a8032e4073fe434c852e5bdf8e1d47
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251885"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="f666e-101">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="f666e-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="f666e-102">Fournit la configuration pour la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="f666e-102">Provides configuration for the collection of token handlers.</span></span>  
  
<span data-ttu-id="f666e-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f666e-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f666e-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="f666e-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="f666e-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="f666e-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="f666e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="f666e-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="f666e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<securityTokenHandlerConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="f666e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f666e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f666e-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f666e-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f666e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f666e-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f666e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f666e-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="f666e-111">Attributes</span></span>  
  
|<span data-ttu-id="f666e-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="f666e-112">Attribute</span></span>|<span data-ttu-id="f666e-113">Description</span><span class="sxs-lookup"><span data-stu-id="f666e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f666e-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="f666e-114">saveBootstrapContext</span></span>|<span data-ttu-id="f666e-115">Spécifie si les jetons de démarrage doivent être inclus dans le jeton de session.</span><span class="sxs-lookup"><span data-stu-id="f666e-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="f666e-116">La valeur peut également être définie sur une collection de gestionnaires de jetons en `saveBootstrapContext` définissant l’attribut sur l' [ \<élément identityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="f666e-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="f666e-117">Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.</span><span class="sxs-lookup"><span data-stu-id="f666e-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="f666e-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="f666e-118">maximumClockSkew</span></span>|<span data-ttu-id="f666e-119">Qui <xref:System.TimeSpan> spécifie la variation d’horloge maximale autorisée.</span><span class="sxs-lookup"><span data-stu-id="f666e-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="f666e-120">Contrôle la variation d’horloge maximale autorisée lors de l’exécution d’opérations sensibles au temps, telles que la validation du délai d’expiration d’une session de connexion.</span><span class="sxs-lookup"><span data-stu-id="f666e-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="f666e-121">La valeur par défaut est 5 minutes, « 00:05:00 ».</span><span class="sxs-lookup"><span data-stu-id="f666e-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="f666e-122">Pour plus d’informations sur la spécification <xref:System.TimeSpan> des valeurs, consultez [TimeSpan values](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="f666e-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="f666e-123">Le décalage d’horloge maximal peut également être défini au niveau du service en définissant l' `maximumClockSkew` attribut sur l' [ \<élément identityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="f666e-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="f666e-124">Une valeur définie sur la collection de gestionnaires de jetons remplace la valeur définie sur le service.</span><span class="sxs-lookup"><span data-stu-id="f666e-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f666e-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f666e-125">Child Elements</span></span>  
  
|<span data-ttu-id="f666e-126">Élément</span><span class="sxs-lookup"><span data-stu-id="f666e-126">Element</span></span>|<span data-ttu-id="f666e-127">Description</span><span class="sxs-lookup"><span data-stu-id="f666e-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f666e-128">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="f666e-128">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="f666e-129">Spécifie l’ensemble d’URI qui sont des identificateurs acceptables de cette partie de confiance.</span><span class="sxs-lookup"><span data-stu-id="f666e-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="f666e-130">facultatif.</span><span class="sxs-lookup"><span data-stu-id="f666e-130">Optional.</span></span>|  
|[<span data-ttu-id="f666e-131">\<caches></span><span class="sxs-lookup"><span data-stu-id="f666e-131">\<caches></span></span>](caches.md)|<span data-ttu-id="f666e-132">Inscrit les caches utilisés pour les jetons de session et la détection de relecture de jetons.</span><span class="sxs-lookup"><span data-stu-id="f666e-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="f666e-133">Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f666e-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="f666e-134">facultatif.</span><span class="sxs-lookup"><span data-stu-id="f666e-134">Optional.</span></span>|  
|[<span data-ttu-id="f666e-135">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="f666e-135">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="f666e-136">Contrôle les paramètres que les gestionnaires de jetons utilisent pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="f666e-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="f666e-137">Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f666e-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="f666e-138">Ces paramètres sont substitués si un gestionnaire spécifique est configuré avec son propre validateur.</span><span class="sxs-lookup"><span data-stu-id="f666e-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="f666e-139">facultatif.</span><span class="sxs-lookup"><span data-stu-id="f666e-139">Optional.</span></span>|  
|[<span data-ttu-id="f666e-140">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="f666e-140">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="f666e-141">Configure le registre des noms d’émetteurs qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="f666e-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="f666e-142">facultatif.</span><span class="sxs-lookup"><span data-stu-id="f666e-142">Optional.</span></span>|  
|[<span data-ttu-id="f666e-143">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="f666e-143">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="f666e-144">Inscrit le programme de résolution de jetons d’émetteur utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="f666e-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="f666e-145">Le programme de résolution de jetons d’émetteur est utilisé pour résoudre le jeton de signature sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="f666e-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="f666e-146">facultatif.</span><span class="sxs-lookup"><span data-stu-id="f666e-146">Optional.</span></span>|  
|[<span data-ttu-id="f666e-147">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="f666e-147">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="f666e-148">Inscrit le programme de résolution de jetons de service qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="f666e-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="f666e-149">Le programme de résolution de jetons de service est utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="f666e-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="f666e-150">facultatif.</span><span class="sxs-lookup"><span data-stu-id="f666e-150">Optional.</span></span>|  
|[<span data-ttu-id="f666e-151">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="f666e-151">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="f666e-152">Active la détection de relecture de jetons et spécifie l’heure d’expiration des jetons.</span><span class="sxs-lookup"><span data-stu-id="f666e-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="f666e-153">Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f666e-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="f666e-154">facultatif.</span><span class="sxs-lookup"><span data-stu-id="f666e-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f666e-155">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f666e-155">Parent Elements</span></span>  
  
|<span data-ttu-id="f666e-156">Élément</span><span class="sxs-lookup"><span data-stu-id="f666e-156">Element</span></span>|<span data-ttu-id="f666e-157">Description</span><span class="sxs-lookup"><span data-stu-id="f666e-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f666e-158">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="f666e-158">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="f666e-159">Spécifie une collection de gestionnaires de jetons de sécurité inscrits auprès du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f666e-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f666e-160">Notes</span><span class="sxs-lookup"><span data-stu-id="f666e-160">Remarks</span></span>  
 <span data-ttu-id="f666e-161">Cette section fournit des valeurs de propriété <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> pour un objet.</span><span class="sxs-lookup"><span data-stu-id="f666e-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="f666e-162">Les paramètres configurés dans cette section remplacent ceux configurés sur le service.</span><span class="sxs-lookup"><span data-stu-id="f666e-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="f666e-163">Certains de ces paramètres peuvent, à leur tour, être remplacés par les paramètres spécifiés lors de l’ajout d’un gestionnaire à la collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="f666e-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f666e-164">Exemple</span><span class="sxs-lookup"><span data-stu-id="f666e-164">Example</span></span>  
  
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

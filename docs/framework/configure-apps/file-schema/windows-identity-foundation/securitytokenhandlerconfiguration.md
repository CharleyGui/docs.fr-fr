---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152565"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="089ac-101">\<sécuritéTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="089ac-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="089ac-102">Fournit la configuration pour la collection de maîtres-livres.</span><span class="sxs-lookup"><span data-stu-id="089ac-102">Provides configuration for the collection of token handlers.</span></span>  
  
<span data-ttu-id="089ac-103">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="089ac-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="089ac-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="089ac-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="089ac-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identitéConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="089ac-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="089ac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sécuritéTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="089ac-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="089ac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sécuritéTokenHandlerConfiguration>**</span><span class="sxs-lookup"><span data-stu-id="089ac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="089ac-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="089ac-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="089ac-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="089ac-109">Attributes and Elements</span></span>  
 <span data-ttu-id="089ac-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="089ac-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="089ac-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="089ac-111">Attributes</span></span>  
  
|<span data-ttu-id="089ac-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="089ac-112">Attribute</span></span>|<span data-ttu-id="089ac-113">Description</span><span class="sxs-lookup"><span data-stu-id="089ac-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="089ac-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="089ac-114">saveBootstrapContext</span></span>|<span data-ttu-id="089ac-115">Précise si les jetons de bootstrap doivent être inclus dans le jeton de session.</span><span class="sxs-lookup"><span data-stu-id="089ac-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="089ac-116">La valeur peut également être définie sur une `saveBootstrapContext` collection de gestionnaires de jetons en définissant l’attribut sur [ \<l’élément>d’identitéconfiguration.](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="089ac-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="089ac-117">Une valeur définie sur la collection de gestionnaires de jetons l’emporte sur la valeur fixée sur le service.</span><span class="sxs-lookup"><span data-stu-id="089ac-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="089ac-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="089ac-118">maximumClockSkew</span></span>|<span data-ttu-id="089ac-119">A <xref:System.TimeSpan> qui spécifie le biais maximal autorisé de l’horloge.</span><span class="sxs-lookup"><span data-stu-id="089ac-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="089ac-120">Contrôle l’inclinaison maximale de l’horloge autorisée lors de l’exécution d’opérations sensibles au temps, telles que la validation de l’heure d’expiration d’une session de connexion.</span><span class="sxs-lookup"><span data-stu-id="089ac-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="089ac-121">La valeur par défaut est de 5 minutes, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="089ac-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="089ac-122">Pour plus d’informations <xref:System.TimeSpan> sur la façon de spécifier les valeurs, voir [Valeurs Timespan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="089ac-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="089ac-123">Le biais d’horloge maximum peut également être `maximumClockSkew` réglé au niveau du service en définissant l’attribut sur [ \<l’élément>d’identitéconfiguration.](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="089ac-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="089ac-124">Une valeur définie sur la collection de gestionnaires de jetons l’emporte sur la valeur fixée sur le service.</span><span class="sxs-lookup"><span data-stu-id="089ac-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="089ac-125">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="089ac-125">Child Elements</span></span>  
  
|<span data-ttu-id="089ac-126">Élément</span><span class="sxs-lookup"><span data-stu-id="089ac-126">Element</span></span>|<span data-ttu-id="089ac-127">Description</span><span class="sxs-lookup"><span data-stu-id="089ac-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="089ac-128">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="089ac-128">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="089ac-129">Spécifie l’ensemble d’ITI qui sont des identifiants acceptables de cette partie de compte.</span><span class="sxs-lookup"><span data-stu-id="089ac-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="089ac-130">facultatif.</span><span class="sxs-lookup"><span data-stu-id="089ac-130">Optional.</span></span>|  
|[<span data-ttu-id="089ac-131">\<caches></span><span class="sxs-lookup"><span data-stu-id="089ac-131">\<caches></span></span>](caches.md)|<span data-ttu-id="089ac-132">Enregistre les caches utilisées pour les jetons de session et la détection des relecteurs symboliques.</span><span class="sxs-lookup"><span data-stu-id="089ac-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="089ac-133">Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="089ac-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="089ac-134">facultatif.</span><span class="sxs-lookup"><span data-stu-id="089ac-134">Optional.</span></span>|  
|[<span data-ttu-id="089ac-135">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="089ac-135">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="089ac-136">Contrôle les paramètres utilisés par les gestionnaires de jetons pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="089ac-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="089ac-137">Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="089ac-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="089ac-138">Ces paramètres sont remplacés si un gestionnaire spécifique est configuré avec son propre validateur.</span><span class="sxs-lookup"><span data-stu-id="089ac-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="089ac-139">facultatif.</span><span class="sxs-lookup"><span data-stu-id="089ac-139">Optional.</span></span>|  
|[<span data-ttu-id="089ac-140">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="089ac-140">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="089ac-141">Configure le registre des noms d’émetteur qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="089ac-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="089ac-142">facultatif.</span><span class="sxs-lookup"><span data-stu-id="089ac-142">Optional.</span></span>|  
|[<span data-ttu-id="089ac-143">\<émetteurTokenResolver></span><span class="sxs-lookup"><span data-stu-id="089ac-143">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="089ac-144">Enregistre le résa résolveur de jetons de l’émetteur qui est utilisé par les gestionnaires dans la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="089ac-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="089ac-145">Le résolveur de jetons de l’émetteur est utilisé pour résoudre le jeton de signature sur les jetons entrants et les messages.</span><span class="sxs-lookup"><span data-stu-id="089ac-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="089ac-146">facultatif.</span><span class="sxs-lookup"><span data-stu-id="089ac-146">Optional.</span></span>|  
|[<span data-ttu-id="089ac-147">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="089ac-147">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="089ac-148">Enregistre le résammateur de jetons de service qui est utilisé par les gestionnaires dans la collection de manutention de jetons.</span><span class="sxs-lookup"><span data-stu-id="089ac-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="089ac-149">Le résolveur de jetons de service est utilisé pour résoudre le jeton de chiffrement sur les jetons et les messages entrants.</span><span class="sxs-lookup"><span data-stu-id="089ac-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="089ac-150">facultatif.</span><span class="sxs-lookup"><span data-stu-id="089ac-150">Optional.</span></span>|  
|[<span data-ttu-id="089ac-151">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="089ac-151">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="089ac-152">Permet la détection de relecture de jetons et spécifie le temps d’expiration des jetons.</span><span class="sxs-lookup"><span data-stu-id="089ac-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="089ac-153">Peut être spécifié au niveau du service ou sur une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="089ac-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="089ac-154">facultatif.</span><span class="sxs-lookup"><span data-stu-id="089ac-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="089ac-155">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="089ac-155">Parent Elements</span></span>  
  
|<span data-ttu-id="089ac-156">Élément</span><span class="sxs-lookup"><span data-stu-id="089ac-156">Element</span></span>|<span data-ttu-id="089ac-157">Description</span><span class="sxs-lookup"><span data-stu-id="089ac-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="089ac-158">\<sécuritéTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="089ac-158">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="089ac-159">Spécifie une collection de gestionnaires de jetons de sécurité qui sont enregistrés avec le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="089ac-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="089ac-160">Notes </span><span class="sxs-lookup"><span data-stu-id="089ac-160">Remarks</span></span>  
 <span data-ttu-id="089ac-161">Cette section fournit des <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> valeurs de propriété pour un objet.</span><span class="sxs-lookup"><span data-stu-id="089ac-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="089ac-162">Les paramètres configurés dans cette section remplacent ceux configurés sur le service.</span><span class="sxs-lookup"><span data-stu-id="089ac-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="089ac-163">Certains de ces paramètres peuvent, à leur tour, être remplacés par des paramètres qui sont spécifiés lorsqu’un gestionnaire est ajouté à la collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="089ac-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="089ac-164"> Exemple</span><span class="sxs-lookup"><span data-stu-id="089ac-164">Example</span></span>  
  
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

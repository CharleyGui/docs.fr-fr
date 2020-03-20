---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152630"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="52791-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="52791-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="52791-102">Fournit la <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> configuration pour <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> la classe, la classe, ou une classe dérivée de l’une ou l’autre de ces classes.</span><span class="sxs-lookup"><span data-stu-id="52791-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="52791-103">Représenté par <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> la classe.</span><span class="sxs-lookup"><span data-stu-id="52791-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
<span data-ttu-id="52791-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="52791-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="52791-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="52791-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="52791-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identitéConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="52791-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="52791-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sécuritéTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="52791-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="52791-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ajouter>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="52791-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="52791-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span><span class="sxs-lookup"><span data-stu-id="52791-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52791-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52791-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52791-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="52791-111">Attributes and Elements</span></span>  
 <span data-ttu-id="52791-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="52791-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52791-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="52791-113">Attributes</span></span>  
  
|<span data-ttu-id="52791-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="52791-114">Attribute</span></span>|<span data-ttu-id="52791-115">Description</span><span class="sxs-lookup"><span data-stu-id="52791-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52791-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="52791-116">mapToWindows</span></span>|<span data-ttu-id="52791-117">Précise si le gestionnaire de jetons doit cartographier le jeton valide à un compte Windows en utilisant la réclamation UPN entrante.</span><span class="sxs-lookup"><span data-stu-id="52791-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="52791-118">La valeur par défaut est « false ».</span><span class="sxs-lookup"><span data-stu-id="52791-118">The default is "false".</span></span>|  
|<span data-ttu-id="52791-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="52791-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="52791-120">Une <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valeur qui spécifie le mode de révocation à utiliser pour le certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="52791-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="52791-121">La valeur par défaut est "En ligne".</span><span class="sxs-lookup"><span data-stu-id="52791-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="52791-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="52791-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="52791-123">Une <xref:System.ServiceModel.Security.X509CertificateValidationMode> valeur qui spécifie le mode de validation à utiliser pour le certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="52791-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="52791-124">La valeur par défaut est "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="52791-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="52791-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="52791-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="52791-126">Une <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valeur qui spécifie le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="52791-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="52791-127">La valeur par défaut est "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="52791-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="52791-128">émetteurCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="52791-128">issuerCertificateValidator</span></span>|<span data-ttu-id="52791-129">Un type personnalisé qui <xref:System.IdentityModel.Selectors.X509CertificateValidator>dérive de .</span><span class="sxs-lookup"><span data-stu-id="52791-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="52791-130">Si `issuerCertificateValidationMode` l’attribut est "Custom", une instance de ce type est utilisée pour la validation des certificats d’émetteur.</span><span class="sxs-lookup"><span data-stu-id="52791-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52791-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="52791-131">Child Elements</span></span>  
  
|<span data-ttu-id="52791-132">Élément</span><span class="sxs-lookup"><span data-stu-id="52791-132">Element</span></span>|<span data-ttu-id="52791-133">Description</span><span class="sxs-lookup"><span data-stu-id="52791-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52791-134">\<nomClaimType></span><span class="sxs-lookup"><span data-stu-id="52791-134">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="52791-135">Définit le type de réclamation <xref:System.Security.Principal.IIdentity.Name%2A> qui spécifie la propriété.</span><span class="sxs-lookup"><span data-stu-id="52791-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="52791-136">\<rôleClaimType></span><span class="sxs-lookup"><span data-stu-id="52791-136">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="52791-137">Spécifie le type de réclamation qui définit <xref:System.Security.Claims.ClaimsIdentity> les revendications de type de rôle dans la collection d’objets retournés par la <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> méthode du gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="52791-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="52791-138">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="52791-138">Parent Elements</span></span>  
  
|<span data-ttu-id="52791-139">Élément</span><span class="sxs-lookup"><span data-stu-id="52791-139">Element</span></span>|<span data-ttu-id="52791-140">Description</span><span class="sxs-lookup"><span data-stu-id="52791-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52791-141">\<ajouter></span><span class="sxs-lookup"><span data-stu-id="52791-141">\<add></span></span>](add.md)|<span data-ttu-id="52791-142">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="52791-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52791-143">Notes </span><span class="sxs-lookup"><span data-stu-id="52791-143">Remarks</span></span>  
 <span data-ttu-id="52791-144">`<samlSecurityTokenRequirement>` L’élément est représenté <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> par la classe dans le `SamlSecurityTokenRequirement` modèle d’objet et est utilisé pour configurer la propriété sur un <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ou un <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="52791-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52791-145"> Exemple</span><span class="sxs-lookup"><span data-stu-id="52791-145">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```

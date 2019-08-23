---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: df259398beb242ea95efb248d6b5140b38ca3c45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942485"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="5cf5b-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="5cf5b-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="5cf5b-102">Fournit la configuration pour <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> la classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> la classe ou une classe dérivée de l’une de ces classes.</span><span class="sxs-lookup"><span data-stu-id="5cf5b-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="5cf5b-103">Représenté par la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe.</span><span class="sxs-lookup"><span data-stu-id="5cf5b-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="5cf5b-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5cf5b-104">\<system.identityModel></span></span>  
<span data-ttu-id="5cf5b-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="5cf5b-105">\<identityConfiguration></span></span>  
<span data-ttu-id="5cf5b-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="5cf5b-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="5cf5b-107">\<add></span><span class="sxs-lookup"><span data-stu-id="5cf5b-107">\<add></span></span>  
<span data-ttu-id="5cf5b-108">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="5cf5b-108">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cf5b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5cf5b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5cf5b-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5cf5b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5cf5b-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5cf5b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5cf5b-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="5cf5b-112">Attributes</span></span>  
  
|<span data-ttu-id="5cf5b-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="5cf5b-113">Attribute</span></span>|<span data-ttu-id="5cf5b-114">Description</span><span class="sxs-lookup"><span data-stu-id="5cf5b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5cf5b-115">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="5cf5b-115">mapToWindows</span></span>|<span data-ttu-id="5cf5b-116">Spécifie si le gestionnaire de jetons doit mapper le jeton de validation à un compte Windows à l’aide de la revendication UPN entrante.</span><span class="sxs-lookup"><span data-stu-id="5cf5b-116">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="5cf5b-117">La valeur par défaut est «false».</span><span class="sxs-lookup"><span data-stu-id="5cf5b-117">The default is "false".</span></span>|  
|<span data-ttu-id="5cf5b-118">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="5cf5b-118">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="5cf5b-119"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Valeur qui spécifie le mode de révocation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="5cf5b-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="5cf5b-120">La valeur par défaut est «online».</span><span class="sxs-lookup"><span data-stu-id="5cf5b-120">The default value is "Online".</span></span>|  
|<span data-ttu-id="5cf5b-121">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="5cf5b-121">issuerCertificateValidationMode</span></span>|<span data-ttu-id="5cf5b-122"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Valeur qui spécifie le mode de validation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="5cf5b-122">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="5cf5b-123">La valeur par défaut est «PeerOrChainTrust».</span><span class="sxs-lookup"><span data-stu-id="5cf5b-123">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="5cf5b-124">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="5cf5b-124">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="5cf5b-125"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Valeur qui spécifie le magasin de certificats X. 509.</span><span class="sxs-lookup"><span data-stu-id="5cf5b-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="5cf5b-126">La valeur par défaut est «LocalMachine».</span><span class="sxs-lookup"><span data-stu-id="5cf5b-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="5cf5b-127">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="5cf5b-127">issuerCertificateValidator</span></span>|<span data-ttu-id="5cf5b-128">Type personnalisé qui dérive de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="5cf5b-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="5cf5b-129">Si l' `issuerCertificateValidationMode` attribut est «Custom», une instance de ce type est utilisée pour la validation du certificat de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="5cf5b-129">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5cf5b-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5cf5b-130">Child Elements</span></span>  
  
|<span data-ttu-id="5cf5b-131">Élément</span><span class="sxs-lookup"><span data-stu-id="5cf5b-131">Element</span></span>|<span data-ttu-id="5cf5b-132">Description</span><span class="sxs-lookup"><span data-stu-id="5cf5b-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5cf5b-133">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="5cf5b-133">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="5cf5b-134">Définit le type de revendication qui spécifie la <xref:System.Security.Principal.IIdentity.Name%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="5cf5b-134">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="5cf5b-135">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="5cf5b-135">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="5cf5b-136">Spécifie le type de revendication qui définit les revendications de type de rôle <xref:System.Security.Claims.ClaimsIdentity> dans la collection d' <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> objets retournée par la méthode du gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="5cf5b-136">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5cf5b-137">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5cf5b-137">Parent Elements</span></span>  
  
|<span data-ttu-id="5cf5b-138">Élément</span><span class="sxs-lookup"><span data-stu-id="5cf5b-138">Element</span></span>|<span data-ttu-id="5cf5b-139">Description</span><span class="sxs-lookup"><span data-stu-id="5cf5b-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5cf5b-140">\<add></span><span class="sxs-lookup"><span data-stu-id="5cf5b-140">\<add></span></span>](add.md)|<span data-ttu-id="5cf5b-141">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="5cf5b-141">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cf5b-142">Notes</span><span class="sxs-lookup"><span data-stu-id="5cf5b-142">Remarks</span></span>  
 <span data-ttu-id="5cf5b-143">L' `<samlSecurityTokenRequirement>` élément est représenté par la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe dans le modèle objet et est utilisé pour configurer la `SamlSecurityTokenRequirement` propriété sur un <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ou un <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="5cf5b-143">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cf5b-144">Exemples</span><span class="sxs-lookup"><span data-stu-id="5cf5b-144">Example</span></span>  
  
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

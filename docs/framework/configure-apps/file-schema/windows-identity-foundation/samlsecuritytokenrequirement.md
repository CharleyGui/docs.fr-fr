---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: cab7572518a7a6dc26f8bbcf67cd424fa1c01085
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251900"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="78ddc-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="78ddc-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="78ddc-102">Fournit la configuration pour <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> la classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> la classe ou une classe dérivée de l’une de ces classes.</span><span class="sxs-lookup"><span data-stu-id="78ddc-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="78ddc-103">Représenté par la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe.</span><span class="sxs-lookup"><span data-stu-id="78ddc-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
<span data-ttu-id="78ddc-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="78ddc-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="78ddc-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="78ddc-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="78ddc-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="78ddc-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="78ddc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="78ddc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="78ddc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Ajouter >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="78ddc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="78ddc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<samlSecurityTokenRequirement >**</span><span class="sxs-lookup"><span data-stu-id="78ddc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78ddc-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78ddc-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78ddc-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="78ddc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="78ddc-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="78ddc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78ddc-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="78ddc-113">Attributes</span></span>  
  
|<span data-ttu-id="78ddc-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="78ddc-114">Attribute</span></span>|<span data-ttu-id="78ddc-115">Description</span><span class="sxs-lookup"><span data-stu-id="78ddc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="78ddc-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="78ddc-116">mapToWindows</span></span>|<span data-ttu-id="78ddc-117">Spécifie si le gestionnaire de jetons doit mapper le jeton de validation à un compte Windows à l’aide de la revendication UPN entrante.</span><span class="sxs-lookup"><span data-stu-id="78ddc-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="78ddc-118">La valeur par défaut est « false ».</span><span class="sxs-lookup"><span data-stu-id="78ddc-118">The default is "false".</span></span>|  
|<span data-ttu-id="78ddc-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="78ddc-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="78ddc-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Valeur qui spécifie le mode de révocation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="78ddc-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="78ddc-121">La valeur par défaut est « online ».</span><span class="sxs-lookup"><span data-stu-id="78ddc-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="78ddc-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="78ddc-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="78ddc-123"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Valeur qui spécifie le mode de validation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="78ddc-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="78ddc-124">La valeur par défaut est « PeerOrChainTrust ».</span><span class="sxs-lookup"><span data-stu-id="78ddc-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="78ddc-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="78ddc-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="78ddc-126"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Valeur qui spécifie le magasin de certificats X. 509.</span><span class="sxs-lookup"><span data-stu-id="78ddc-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="78ddc-127">La valeur par défaut est « LocalMachine ».</span><span class="sxs-lookup"><span data-stu-id="78ddc-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="78ddc-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="78ddc-128">issuerCertificateValidator</span></span>|<span data-ttu-id="78ddc-129">Type personnalisé qui dérive de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="78ddc-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="78ddc-130">Si l' `issuerCertificateValidationMode` attribut est « Custom », une instance de ce type est utilisée pour la validation du certificat de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="78ddc-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="78ddc-131">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="78ddc-131">Child Elements</span></span>  
  
|<span data-ttu-id="78ddc-132">Élément</span><span class="sxs-lookup"><span data-stu-id="78ddc-132">Element</span></span>|<span data-ttu-id="78ddc-133">Description</span><span class="sxs-lookup"><span data-stu-id="78ddc-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78ddc-134">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="78ddc-134">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="78ddc-135">Définit le type de revendication qui spécifie la <xref:System.Security.Principal.IIdentity.Name%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="78ddc-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="78ddc-136">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="78ddc-136">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="78ddc-137">Spécifie le type de revendication qui définit les revendications de type de rôle <xref:System.Security.Claims.ClaimsIdentity> dans la collection d' <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> objets retournée par la méthode du gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="78ddc-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78ddc-138">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="78ddc-138">Parent Elements</span></span>  
  
|<span data-ttu-id="78ddc-139">Élément</span><span class="sxs-lookup"><span data-stu-id="78ddc-139">Element</span></span>|<span data-ttu-id="78ddc-140">Description</span><span class="sxs-lookup"><span data-stu-id="78ddc-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78ddc-141">\<add></span><span class="sxs-lookup"><span data-stu-id="78ddc-141">\<add></span></span>](add.md)|<span data-ttu-id="78ddc-142">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="78ddc-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78ddc-143">Notes</span><span class="sxs-lookup"><span data-stu-id="78ddc-143">Remarks</span></span>  
 <span data-ttu-id="78ddc-144">L' `<samlSecurityTokenRequirement>` élément est représenté par la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe dans le modèle objet et est utilisé pour configurer la `SamlSecurityTokenRequirement` propriété sur un <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ou un <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="78ddc-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78ddc-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="78ddc-145">Example</span></span>  
  
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

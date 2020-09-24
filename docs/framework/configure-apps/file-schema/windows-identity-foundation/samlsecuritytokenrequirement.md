---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: f93ec0007b537e306a570b166eaa4cd2fe7f81e2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157029"
---
# \<samlSecurityTokenRequirement>

<span data-ttu-id="07310-101">Fournit la configuration pour la <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, la <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou une classe dérivée de l’une de ces classes.</span><span class="sxs-lookup"><span data-stu-id="07310-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="07310-102">Représenté par la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe.</span><span class="sxs-lookup"><span data-stu-id="07310-102">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="07310-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07310-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07310-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="07310-104">Attributes and Elements</span></span>  

 <span data-ttu-id="07310-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="07310-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07310-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="07310-106">Attributes</span></span>  
  
|<span data-ttu-id="07310-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="07310-107">Attribute</span></span>|<span data-ttu-id="07310-108">Description</span><span class="sxs-lookup"><span data-stu-id="07310-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="07310-109">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="07310-109">mapToWindows</span></span>|<span data-ttu-id="07310-110">Spécifie si le gestionnaire de jetons doit mapper le jeton de validation à un compte Windows à l’aide de la revendication UPN entrante.</span><span class="sxs-lookup"><span data-stu-id="07310-110">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="07310-111">La valeur par défaut est « false ».</span><span class="sxs-lookup"><span data-stu-id="07310-111">The default is "false".</span></span>|  
|<span data-ttu-id="07310-112">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="07310-112">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="07310-113"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Valeur qui spécifie le mode de révocation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="07310-113">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="07310-114">La valeur par défaut est « online ».</span><span class="sxs-lookup"><span data-stu-id="07310-114">The default value is "Online".</span></span>|  
|<span data-ttu-id="07310-115">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="07310-115">issuerCertificateValidationMode</span></span>|<span data-ttu-id="07310-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode>Valeur qui spécifie le mode de validation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="07310-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="07310-117">La valeur par défaut est « PeerOrChainTrust ».</span><span class="sxs-lookup"><span data-stu-id="07310-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="07310-118">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="07310-118">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="07310-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>Valeur qui spécifie le magasin de certificats X. 509.</span><span class="sxs-lookup"><span data-stu-id="07310-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="07310-120">La valeur par défaut est « LocalMachine ».</span><span class="sxs-lookup"><span data-stu-id="07310-120">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="07310-121">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="07310-121">issuerCertificateValidator</span></span>|<span data-ttu-id="07310-122">Type personnalisé qui dérive de <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="07310-122">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="07310-123">Si l' `issuerCertificateValidationMode` attribut est « Custom », une instance de ce type est utilisée pour la validation du certificat de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="07310-123">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07310-124">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="07310-124">Child Elements</span></span>  
  
|<span data-ttu-id="07310-125">Élément</span><span class="sxs-lookup"><span data-stu-id="07310-125">Element</span></span>|<span data-ttu-id="07310-126">Description</span><span class="sxs-lookup"><span data-stu-id="07310-126">Description</span></span>|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|<span data-ttu-id="07310-127">Définit le type de revendication qui spécifie la <xref:System.Security.Principal.IIdentity.Name%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="07310-127">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[\<roleClaimType>](roleclaimtype.md)|<span data-ttu-id="07310-128">Spécifie le type de revendication qui définit les revendications de type de rôle dans la collection d' <xref:System.Security.Claims.ClaimsIdentity> objets retournée par la <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> méthode du gestionnaire de jetons.</span><span class="sxs-lookup"><span data-stu-id="07310-128">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="07310-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="07310-129">Parent Elements</span></span>  
  
|<span data-ttu-id="07310-130">Élément</span><span class="sxs-lookup"><span data-stu-id="07310-130">Element</span></span>|<span data-ttu-id="07310-131">Description</span><span class="sxs-lookup"><span data-stu-id="07310-131">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="07310-132">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="07310-132">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07310-133">Notes</span><span class="sxs-lookup"><span data-stu-id="07310-133">Remarks</span></span>  

 <span data-ttu-id="07310-134">L' `<samlSecurityTokenRequirement>` élément est représenté par la <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe dans le modèle objet et est utilisé pour configurer la `SamlSecurityTokenRequirement` propriété sur un <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ou un <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="07310-134">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07310-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="07310-135">Example</span></span>  
  
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

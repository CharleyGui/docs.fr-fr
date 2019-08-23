---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 2851820460a34d62175929b48ad57914df557059
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945180"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="9540d-101">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="9540d-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="9540d-102">Fournit une configuration facultative pour <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> la classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="9540d-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="9540d-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="9540d-103">\<system.identityModel></span></span>  
<span data-ttu-id="9540d-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="9540d-104">\<identityConfiguration></span></span>  
<span data-ttu-id="9540d-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="9540d-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="9540d-106">\<add></span><span class="sxs-lookup"><span data-stu-id="9540d-106">\<add></span></span>  
<span data-ttu-id="9540d-107">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="9540d-107">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9540d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9540d-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9540d-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="9540d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9540d-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="9540d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9540d-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="9540d-111">Attributes</span></span>  
  
|<span data-ttu-id="9540d-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="9540d-112">Attribute</span></span>|<span data-ttu-id="9540d-113">Description</span><span class="sxs-lookup"><span data-stu-id="9540d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9540d-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="9540d-114">certificateValidationMode</span></span>|<span data-ttu-id="9540d-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Valeur qui spécifie le mode de validation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="9540d-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="9540d-116">La valeur par défaut est «PeerOrChainTrust».</span><span class="sxs-lookup"><span data-stu-id="9540d-116">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="9540d-117">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="9540d-117">mapToWindows</span></span>|<span data-ttu-id="9540d-118">Spécifie si le gestionnaire de jetons doit mapper le jeton de validation à un compte Windows à l’aide de la revendication UPN entrante.</span><span class="sxs-lookup"><span data-stu-id="9540d-118">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="9540d-119">La valeur par défaut est «false».</span><span class="sxs-lookup"><span data-stu-id="9540d-119">The default is "false".</span></span>|  
|<span data-ttu-id="9540d-120">revocationMode</span><span class="sxs-lookup"><span data-stu-id="9540d-120">revocationMode</span></span>|<span data-ttu-id="9540d-121"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Valeur qui spécifie le mode de révocation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="9540d-121">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="9540d-122">La valeur par défaut est «online».</span><span class="sxs-lookup"><span data-stu-id="9540d-122">The default value is "Online".</span></span>|  
|<span data-ttu-id="9540d-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="9540d-123">trustedStoreLocation</span></span>|<span data-ttu-id="9540d-124"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Valeur qui spécifie le magasin de certificats X. 509.</span><span class="sxs-lookup"><span data-stu-id="9540d-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="9540d-125">La valeur par défaut est «LocalMachine».</span><span class="sxs-lookup"><span data-stu-id="9540d-125">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="9540d-126">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="9540d-126">certificateValidator</span></span>|<span data-ttu-id="9540d-127">Type personnalisé qui dérive de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="9540d-127">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="9540d-128">Si l' `certificateValidationMode` attribut est «Custom», une instance de ce type est utilisée pour la validation du certificat de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="9540d-128">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9540d-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="9540d-129">Child Elements</span></span>  
 <span data-ttu-id="9540d-130">Aucun</span><span class="sxs-lookup"><span data-stu-id="9540d-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9540d-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="9540d-131">Parent Elements</span></span>  
  
|<span data-ttu-id="9540d-132">Élément</span><span class="sxs-lookup"><span data-stu-id="9540d-132">Element</span></span>|<span data-ttu-id="9540d-133">Description</span><span class="sxs-lookup"><span data-stu-id="9540d-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9540d-134">\<add></span><span class="sxs-lookup"><span data-stu-id="9540d-134">\<add></span></span>](add.md)|<span data-ttu-id="9540d-135">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="9540d-135">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9540d-136">Exemple</span><span class="sxs-lookup"><span data-stu-id="9540d-136">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```

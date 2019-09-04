---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 76eeea635fd65486a1c16bea15a49018876dae99
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251696"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="e85c0-101">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="e85c0-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="e85c0-102">Fournit une configuration facultative pour <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> la classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="e85c0-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="e85c0-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e85c0-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e85c0-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="e85c0-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="e85c0-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="e85c0-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="e85c0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="e85c0-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="e85c0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Ajouter >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="e85c0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="e85c0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<x509SecurityTokenHandlerRequirement >**</span><span class="sxs-lookup"><span data-stu-id="e85c0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e85c0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e85c0-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e85c0-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e85c0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e85c0-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e85c0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e85c0-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="e85c0-112">Attributes</span></span>  
  
|<span data-ttu-id="e85c0-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="e85c0-113">Attribute</span></span>|<span data-ttu-id="e85c0-114">Description</span><span class="sxs-lookup"><span data-stu-id="e85c0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e85c0-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="e85c0-115">certificateValidationMode</span></span>|<span data-ttu-id="e85c0-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Valeur qui spécifie le mode de validation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="e85c0-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="e85c0-117">La valeur par défaut est « PeerOrChainTrust ».</span><span class="sxs-lookup"><span data-stu-id="e85c0-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="e85c0-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="e85c0-118">mapToWindows</span></span>|<span data-ttu-id="e85c0-119">Spécifie si le gestionnaire de jetons doit mapper le jeton de validation à un compte Windows à l’aide de la revendication UPN entrante.</span><span class="sxs-lookup"><span data-stu-id="e85c0-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="e85c0-120">La valeur par défaut est « false ».</span><span class="sxs-lookup"><span data-stu-id="e85c0-120">The default is "false".</span></span>|  
|<span data-ttu-id="e85c0-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="e85c0-121">revocationMode</span></span>|<span data-ttu-id="e85c0-122"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Valeur qui spécifie le mode de révocation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="e85c0-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="e85c0-123">La valeur par défaut est « online ».</span><span class="sxs-lookup"><span data-stu-id="e85c0-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="e85c0-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="e85c0-124">trustedStoreLocation</span></span>|<span data-ttu-id="e85c0-125"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Valeur qui spécifie le magasin de certificats X. 509.</span><span class="sxs-lookup"><span data-stu-id="e85c0-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="e85c0-126">La valeur par défaut est « LocalMachine ».</span><span class="sxs-lookup"><span data-stu-id="e85c0-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="e85c0-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="e85c0-127">certificateValidator</span></span>|<span data-ttu-id="e85c0-128">Type personnalisé qui dérive de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="e85c0-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="e85c0-129">Si l' `certificateValidationMode` attribut est « Custom », une instance de ce type est utilisée pour la validation du certificat de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="e85c0-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e85c0-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e85c0-130">Child Elements</span></span>  
 <span data-ttu-id="e85c0-131">Aucun</span><span class="sxs-lookup"><span data-stu-id="e85c0-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e85c0-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e85c0-132">Parent Elements</span></span>  
  
|<span data-ttu-id="e85c0-133">Élément</span><span class="sxs-lookup"><span data-stu-id="e85c0-133">Element</span></span>|<span data-ttu-id="e85c0-134">Description</span><span class="sxs-lookup"><span data-stu-id="e85c0-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e85c0-135">\<add></span><span class="sxs-lookup"><span data-stu-id="e85c0-135">\<add></span></span>](add.md)|<span data-ttu-id="e85c0-136">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="e85c0-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e85c0-137">Exemples</span><span class="sxs-lookup"><span data-stu-id="e85c0-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```

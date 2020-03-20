---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152448"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="936be-101">\<x509SecurityTokenHandlerRequie></span><span class="sxs-lookup"><span data-stu-id="936be-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="936be-102">Fournit une configuration <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> facultative pour la classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="936be-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="936be-103">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="936be-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="936be-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="936be-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="936be-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identitéConfiguration>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="936be-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="936be-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sécuritéTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="936be-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="936be-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ajouter>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="936be-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="936be-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**</span><span class="sxs-lookup"><span data-stu-id="936be-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="936be-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="936be-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="936be-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="936be-110">Attributes and Elements</span></span>  
 <span data-ttu-id="936be-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="936be-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="936be-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="936be-112">Attributes</span></span>  
  
|<span data-ttu-id="936be-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="936be-113">Attribute</span></span>|<span data-ttu-id="936be-114">Description</span><span class="sxs-lookup"><span data-stu-id="936be-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="936be-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="936be-115">certificateValidationMode</span></span>|<span data-ttu-id="936be-116">Une <xref:System.ServiceModel.Security.X509CertificateValidationMode> valeur qui spécifie le mode de validation à utiliser pour le certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="936be-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="936be-117">La valeur par défaut est "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="936be-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="936be-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="936be-118">mapToWindows</span></span>|<span data-ttu-id="936be-119">Précise si le gestionnaire de jetons doit cartographier le jeton valide à un compte Windows en utilisant la réclamation UPN entrante.</span><span class="sxs-lookup"><span data-stu-id="936be-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="936be-120">La valeur par défaut est « false ».</span><span class="sxs-lookup"><span data-stu-id="936be-120">The default is "false".</span></span>|  
|<span data-ttu-id="936be-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="936be-121">revocationMode</span></span>|<span data-ttu-id="936be-122">Une <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valeur qui spécifie le mode de révocation à utiliser pour le certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="936be-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="936be-123">La valeur par défaut est "En ligne".</span><span class="sxs-lookup"><span data-stu-id="936be-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="936be-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="936be-124">trustedStoreLocation</span></span>|<span data-ttu-id="936be-125">Une <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valeur qui spécifie le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="936be-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="936be-126">La valeur par défaut est "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="936be-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="936be-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="936be-127">certificateValidator</span></span>|<span data-ttu-id="936be-128">Un type personnalisé qui <xref:System.IdentityModel.Selectors.X509CertificateValidator>dérive de .</span><span class="sxs-lookup"><span data-stu-id="936be-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="936be-129">Si `certificateValidationMode` l’attribut est "Custom", une instance de ce type est utilisée pour la validation des certificats d’émetteur.</span><span class="sxs-lookup"><span data-stu-id="936be-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="936be-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="936be-130">Child Elements</span></span>  
 <span data-ttu-id="936be-131">None</span><span class="sxs-lookup"><span data-stu-id="936be-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="936be-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="936be-132">Parent Elements</span></span>  
  
|<span data-ttu-id="936be-133">Élément</span><span class="sxs-lookup"><span data-stu-id="936be-133">Element</span></span>|<span data-ttu-id="936be-134">Description</span><span class="sxs-lookup"><span data-stu-id="936be-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="936be-135">\<ajouter></span><span class="sxs-lookup"><span data-stu-id="936be-135">\<add></span></span>](add.md)|<span data-ttu-id="936be-136">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="936be-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="936be-137"> Exemple</span><span class="sxs-lookup"><span data-stu-id="936be-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```

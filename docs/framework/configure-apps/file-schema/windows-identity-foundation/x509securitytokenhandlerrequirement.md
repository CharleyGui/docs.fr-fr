---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: a6a8185297e1345de9fa20c7d4d0dffbdcd8620f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185390"
---
# \<x509SecurityTokenHandlerRequirement>

<span data-ttu-id="7a0be-101">Fournit une configuration facultative pour la <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> classe ou les classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="7a0be-101">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="7a0be-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a0be-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7a0be-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7a0be-103">Attributes and Elements</span></span>  

 <span data-ttu-id="7a0be-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7a0be-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7a0be-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="7a0be-105">Attributes</span></span>  
  
|<span data-ttu-id="7a0be-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="7a0be-106">Attribute</span></span>|<span data-ttu-id="7a0be-107">Description</span><span class="sxs-lookup"><span data-stu-id="7a0be-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7a0be-108">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="7a0be-108">certificateValidationMode</span></span>|<span data-ttu-id="7a0be-109"><xref:System.ServiceModel.Security.X509CertificateValidationMode>Valeur qui spécifie le mode de validation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="7a0be-109">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="7a0be-110">La valeur par défaut est « PeerOrChainTrust ».</span><span class="sxs-lookup"><span data-stu-id="7a0be-110">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="7a0be-111">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="7a0be-111">mapToWindows</span></span>|<span data-ttu-id="7a0be-112">Spécifie si le gestionnaire de jetons doit mapper le jeton de validation à un compte Windows à l’aide de la revendication UPN entrante.</span><span class="sxs-lookup"><span data-stu-id="7a0be-112">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="7a0be-113">La valeur par défaut est « false ».</span><span class="sxs-lookup"><span data-stu-id="7a0be-113">The default is "false".</span></span>|  
|<span data-ttu-id="7a0be-114">revocationMode</span><span class="sxs-lookup"><span data-stu-id="7a0be-114">revocationMode</span></span>|<span data-ttu-id="7a0be-115"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Valeur qui spécifie le mode de révocation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="7a0be-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="7a0be-116">La valeur par défaut est « online ».</span><span class="sxs-lookup"><span data-stu-id="7a0be-116">The default value is "Online".</span></span>|  
|<span data-ttu-id="7a0be-117">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="7a0be-117">trustedStoreLocation</span></span>|<span data-ttu-id="7a0be-118"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>Valeur qui spécifie le magasin de certificats X. 509.</span><span class="sxs-lookup"><span data-stu-id="7a0be-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="7a0be-119">La valeur par défaut est « LocalMachine ».</span><span class="sxs-lookup"><span data-stu-id="7a0be-119">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="7a0be-120">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="7a0be-120">certificateValidator</span></span>|<span data-ttu-id="7a0be-121">Type personnalisé qui dérive de <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="7a0be-121">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="7a0be-122">Si l' `certificateValidationMode` attribut est « Custom », une instance de ce type est utilisée pour la validation du certificat de l’émetteur.</span><span class="sxs-lookup"><span data-stu-id="7a0be-122">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7a0be-123">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7a0be-123">Child Elements</span></span>  

 <span data-ttu-id="7a0be-124">None</span><span class="sxs-lookup"><span data-stu-id="7a0be-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7a0be-125">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7a0be-125">Parent Elements</span></span>  
  
|<span data-ttu-id="7a0be-126">Élément</span><span class="sxs-lookup"><span data-stu-id="7a0be-126">Element</span></span>|<span data-ttu-id="7a0be-127">Description</span><span class="sxs-lookup"><span data-stu-id="7a0be-127">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="7a0be-128">Ajoute le gestionnaire de jetons de sécurité spécifié à la collection de gestionnaires de jetons.</span><span class="sxs-lookup"><span data-stu-id="7a0be-128">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7a0be-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="7a0be-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```

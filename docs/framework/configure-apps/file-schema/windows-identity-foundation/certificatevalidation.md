---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 583fef7eb364c39890b3f9304770b383c1ea6d2a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183505"
---
# \<certificateValidation>

<span data-ttu-id="e3229-101">Contrôle les paramètres que les gestionnaires de jetons utilisent pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="e3229-101">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="e3229-102">Ces paramètres sont substitués si un gestionnaire spécifique est configuré avec son propre validateur.</span><span class="sxs-lookup"><span data-stu-id="e3229-102">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**  
  
## <a name="syntax"></a><span data-ttu-id="e3229-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3229-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e3229-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e3229-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e3229-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e3229-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e3229-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="e3229-106">Attributes</span></span>  
  
|<span data-ttu-id="e3229-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="e3229-107">Attribute</span></span>|<span data-ttu-id="e3229-108">Description</span><span class="sxs-lookup"><span data-stu-id="e3229-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e3229-109">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="e3229-109">certificateValidationMode</span></span>|<span data-ttu-id="e3229-110"><xref:System.ServiceModel.Security.X509CertificateValidationMode>Valeur qui spécifie le mode de validation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="e3229-110">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="e3229-111">La valeur par défaut est « PeerOrChainTrust ».</span><span class="sxs-lookup"><span data-stu-id="e3229-111">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="e3229-112">Pour spécifier un validateur personnalisé, affectez la valeur « Custom » à cet attribut et spécifiez le validateur à l’aide de l' [\<certificateValidator>](certificatevalidator.md) élément.</span><span class="sxs-lookup"><span data-stu-id="e3229-112">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="e3229-113">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="e3229-113">Optional.</span></span>|  
|<span data-ttu-id="e3229-114">revocationMode</span><span class="sxs-lookup"><span data-stu-id="e3229-114">revocationMode</span></span>|<span data-ttu-id="e3229-115"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Valeur qui spécifie le mode de révocation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="e3229-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="e3229-116">La valeur par défaut est « online ».</span><span class="sxs-lookup"><span data-stu-id="e3229-116">The default value is "Online".</span></span> <span data-ttu-id="e3229-117">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="e3229-117">Optional.</span></span>|  
|<span data-ttu-id="e3229-118">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="e3229-118">trustedStoreLocation</span></span>|<span data-ttu-id="e3229-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>Valeur qui spécifie le magasin de certificats X. 509.</span><span class="sxs-lookup"><span data-stu-id="e3229-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="e3229-120">La valeur par défaut est « LocalMachine ».</span><span class="sxs-lookup"><span data-stu-id="e3229-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="e3229-121">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="e3229-121">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e3229-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e3229-122">Child Elements</span></span>  
  
|<span data-ttu-id="e3229-123">Élément</span><span class="sxs-lookup"><span data-stu-id="e3229-123">Element</span></span>|<span data-ttu-id="e3229-124">Description</span><span class="sxs-lookup"><span data-stu-id="e3229-124">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|<span data-ttu-id="e3229-125">Spécifie un type personnalisé pour la validation du certificat.</span><span class="sxs-lookup"><span data-stu-id="e3229-125">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="e3229-126">Ce type est utilisé uniquement si l' `certificateValidationMode` attribut de l' [\<certificateValidation>](certificatevalidation.md) élément a la valeur « Custom ».</span><span class="sxs-lookup"><span data-stu-id="e3229-126">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e3229-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e3229-127">Parent Elements</span></span>  
  
|<span data-ttu-id="e3229-128">Élément</span><span class="sxs-lookup"><span data-stu-id="e3229-128">Element</span></span>|<span data-ttu-id="e3229-129">Description</span><span class="sxs-lookup"><span data-stu-id="e3229-129">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="e3229-130">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="e3229-130">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="e3229-131">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e3229-131">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3229-132">Notes</span><span class="sxs-lookup"><span data-stu-id="e3229-132">Remarks</span></span>  

 <span data-ttu-id="e3229-133">Un `<certificateValidation>` élément peut être spécifié au niveau du service sous l' `<identityConfiguration>` élément ou au niveau de la collection du gestionnaire de jetons de sécurité sous l' `<securityTokenHandlerConfiguration>` élément.</span><span class="sxs-lookup"><span data-stu-id="e3229-133">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="e3229-134">Les paramètres d’une collection de gestionnaires de jetons remplacent ceux spécifiés sur le service.</span><span class="sxs-lookup"><span data-stu-id="e3229-134">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="e3229-135">Certains gestionnaires de jetons vous permettent de spécifier des paramètres de validation de certificat dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="e3229-135">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="e3229-136">Les paramètres sur des gestionnaires de jetons individuels remplacent ceux spécifiés au niveau du service et de la collection du gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="e3229-136">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3229-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="e3229-137">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```

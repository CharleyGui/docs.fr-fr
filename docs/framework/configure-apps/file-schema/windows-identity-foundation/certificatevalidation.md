---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 8185153eb02c5794b0f6ac02a6837806f2073c07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941918"
---
# <a name="certificatevalidation"></a><span data-ttu-id="b1827-101">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="b1827-101">\<certificateValidation></span></span>
<span data-ttu-id="b1827-102">Contrôle les paramètres que les gestionnaires de jetons utilisent pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="b1827-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="b1827-103">Ces paramètres sont substitués si un gestionnaire spécifique est configuré avec son propre validateur.</span><span class="sxs-lookup"><span data-stu-id="b1827-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="b1827-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="b1827-104">\<system.identityModel></span></span>  
<span data-ttu-id="b1827-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="b1827-105">\<identityConfiguration></span></span>  
<span data-ttu-id="b1827-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="b1827-106">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1827-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1827-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1827-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b1827-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b1827-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b1827-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1827-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="b1827-110">Attributes</span></span>  
  
|<span data-ttu-id="b1827-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="b1827-111">Attribute</span></span>|<span data-ttu-id="b1827-112">Description</span><span class="sxs-lookup"><span data-stu-id="b1827-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1827-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="b1827-113">certificateValidationMode</span></span>|<span data-ttu-id="b1827-114"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Valeur qui spécifie le mode de validation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="b1827-114">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="b1827-115">La valeur par défaut est «PeerOrChainTrust».</span><span class="sxs-lookup"><span data-stu-id="b1827-115">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="b1827-116">Pour spécifier un validateur personnalisé, affectez la valeur «Custom» à cet attribut et spécifiez le validateur à l’aide de l' [ \<élément certificateValidator >](certificatevalidator.md) .</span><span class="sxs-lookup"><span data-stu-id="b1827-116">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="b1827-117">facultatif.</span><span class="sxs-lookup"><span data-stu-id="b1827-117">Optional.</span></span>|  
|<span data-ttu-id="b1827-118">revocationMode</span><span class="sxs-lookup"><span data-stu-id="b1827-118">revocationMode</span></span>|<span data-ttu-id="b1827-119"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Valeur qui spécifie le mode de révocation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="b1827-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="b1827-120">La valeur par défaut est «online».</span><span class="sxs-lookup"><span data-stu-id="b1827-120">The default value is "Online".</span></span> <span data-ttu-id="b1827-121">facultatif.</span><span class="sxs-lookup"><span data-stu-id="b1827-121">Optional.</span></span>|  
|<span data-ttu-id="b1827-122">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="b1827-122">trustedStoreLocation</span></span>|<span data-ttu-id="b1827-123"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Valeur qui spécifie le magasin de certificats X. 509.</span><span class="sxs-lookup"><span data-stu-id="b1827-123">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="b1827-124">La valeur par défaut est «LocalMachine».</span><span class="sxs-lookup"><span data-stu-id="b1827-124">The default value is "LocalMachine".</span></span> <span data-ttu-id="b1827-125">facultatif.</span><span class="sxs-lookup"><span data-stu-id="b1827-125">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1827-126">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b1827-126">Child Elements</span></span>  
  
|<span data-ttu-id="b1827-127">Élément</span><span class="sxs-lookup"><span data-stu-id="b1827-127">Element</span></span>|<span data-ttu-id="b1827-128">Description</span><span class="sxs-lookup"><span data-stu-id="b1827-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1827-129">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="b1827-129">\<certificateValidator></span></span>](certificatevalidator.md)|<span data-ttu-id="b1827-130">Spécifie un type personnalisé pour la validation du certificat.</span><span class="sxs-lookup"><span data-stu-id="b1827-130">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="b1827-131">Ce type est utilisé uniquement si l' `certificateValidationMode` attribut de l' [ \<élément certificateValidation >](certificatevalidation.md) a la valeur «Custom».</span><span class="sxs-lookup"><span data-stu-id="b1827-131">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1827-132">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b1827-132">Parent Elements</span></span>  
  
|<span data-ttu-id="b1827-133">Élément</span><span class="sxs-lookup"><span data-stu-id="b1827-133">Element</span></span>|<span data-ttu-id="b1827-134">Description</span><span class="sxs-lookup"><span data-stu-id="b1827-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1827-135">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="b1827-135">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="b1827-136">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="b1827-136">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="b1827-137">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="b1827-137">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="b1827-138">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="b1827-138">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1827-139">Notes</span><span class="sxs-lookup"><span data-stu-id="b1827-139">Remarks</span></span>  
 <span data-ttu-id="b1827-140">Un `<certificateValidation>` élément peut être spécifié au niveau du service sous l' `<identityConfiguration>` élément ou au niveau de la collection du gestionnaire de jetons `<securityTokenHandlerConfiguration>` de sécurité sous l’élément.</span><span class="sxs-lookup"><span data-stu-id="b1827-140">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="b1827-141">Les paramètres d’une collection de gestionnaires de jetons remplacent ceux spécifiés sur le service.</span><span class="sxs-lookup"><span data-stu-id="b1827-141">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="b1827-142">Certains gestionnaires de jetons vous permettent de spécifier des paramètres de validation de certificat dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="b1827-142">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="b1827-143">Les paramètres sur des gestionnaires de jetons individuels remplacent ceux spécifiés au niveau du service et de la collection du gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="b1827-143">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1827-144">Exemple</span><span class="sxs-lookup"><span data-stu-id="b1827-144">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```

---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: c2d1a5d36cb5616ef06eedc093dd70a68a164a81
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252138"
---
# <a name="certificatevalidation"></a><span data-ttu-id="0d91c-101">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="0d91c-101">\<certificateValidation></span></span>
<span data-ttu-id="0d91c-102">Contrôle les paramètres que les gestionnaires de jetons utilisent pour valider les certificats.</span><span class="sxs-lookup"><span data-stu-id="0d91c-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="0d91c-103">Ces paramètres sont substitués si un gestionnaire spécifique est configuré avec son propre validateur.</span><span class="sxs-lookup"><span data-stu-id="0d91c-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
<span data-ttu-id="0d91c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d91c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0d91c-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="0d91c-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="0d91c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="0d91c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="0d91c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateValidation >**</span><span class="sxs-lookup"><span data-stu-id="0d91c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d91c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d91c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d91c-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0d91c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0d91c-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0d91c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d91c-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="0d91c-111">Attributes</span></span>  
  
|<span data-ttu-id="0d91c-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="0d91c-112">Attribute</span></span>|<span data-ttu-id="0d91c-113">Description</span><span class="sxs-lookup"><span data-stu-id="0d91c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d91c-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="0d91c-114">certificateValidationMode</span></span>|<span data-ttu-id="0d91c-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Valeur qui spécifie le mode de validation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="0d91c-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="0d91c-116">La valeur par défaut est « PeerOrChainTrust ».</span><span class="sxs-lookup"><span data-stu-id="0d91c-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="0d91c-117">Pour spécifier un validateur personnalisé, affectez la valeur « Custom » à cet attribut et spécifiez le validateur à l’aide de l' [ \<élément certificateValidator >](certificatevalidator.md) .</span><span class="sxs-lookup"><span data-stu-id="0d91c-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="0d91c-118">facultatif.</span><span class="sxs-lookup"><span data-stu-id="0d91c-118">Optional.</span></span>|  
|<span data-ttu-id="0d91c-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="0d91c-119">revocationMode</span></span>|<span data-ttu-id="0d91c-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Valeur qui spécifie le mode de révocation à utiliser pour le certificat X. 509.</span><span class="sxs-lookup"><span data-stu-id="0d91c-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="0d91c-121">La valeur par défaut est « online ».</span><span class="sxs-lookup"><span data-stu-id="0d91c-121">The default value is "Online".</span></span> <span data-ttu-id="0d91c-122">facultatif.</span><span class="sxs-lookup"><span data-stu-id="0d91c-122">Optional.</span></span>|  
|<span data-ttu-id="0d91c-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="0d91c-123">trustedStoreLocation</span></span>|<span data-ttu-id="0d91c-124"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Valeur qui spécifie le magasin de certificats X. 509.</span><span class="sxs-lookup"><span data-stu-id="0d91c-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="0d91c-125">La valeur par défaut est « LocalMachine ».</span><span class="sxs-lookup"><span data-stu-id="0d91c-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="0d91c-126">facultatif.</span><span class="sxs-lookup"><span data-stu-id="0d91c-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d91c-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0d91c-127">Child Elements</span></span>  
  
|<span data-ttu-id="0d91c-128">Élément</span><span class="sxs-lookup"><span data-stu-id="0d91c-128">Element</span></span>|<span data-ttu-id="0d91c-129">Description</span><span class="sxs-lookup"><span data-stu-id="0d91c-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d91c-130">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="0d91c-130">\<certificateValidator></span></span>](certificatevalidator.md)|<span data-ttu-id="0d91c-131">Spécifie un type personnalisé pour la validation du certificat.</span><span class="sxs-lookup"><span data-stu-id="0d91c-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="0d91c-132">Ce type est utilisé uniquement si l' `certificateValidationMode` attribut de l' [ \<élément certificateValidation >](certificatevalidation.md) a la valeur « Custom ».</span><span class="sxs-lookup"><span data-stu-id="0d91c-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d91c-133">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0d91c-133">Parent Elements</span></span>  
  
|<span data-ttu-id="0d91c-134">Élément</span><span class="sxs-lookup"><span data-stu-id="0d91c-134">Element</span></span>|<span data-ttu-id="0d91c-135">Description</span><span class="sxs-lookup"><span data-stu-id="0d91c-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d91c-136">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="0d91c-136">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="0d91c-137">Spécifie les paramètres d’identité au niveau du service.</span><span class="sxs-lookup"><span data-stu-id="0d91c-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="0d91c-138">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="0d91c-138">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="0d91c-139">Fournit la configuration pour une collection de gestionnaires de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0d91c-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d91c-140">Notes</span><span class="sxs-lookup"><span data-stu-id="0d91c-140">Remarks</span></span>  
 <span data-ttu-id="0d91c-141">Un `<certificateValidation>` élément peut être spécifié au niveau du service sous l' `<identityConfiguration>` élément ou au niveau de la collection du gestionnaire de jetons `<securityTokenHandlerConfiguration>` de sécurité sous l’élément.</span><span class="sxs-lookup"><span data-stu-id="0d91c-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="0d91c-142">Les paramètres d’une collection de gestionnaires de jetons remplacent ceux spécifiés sur le service.</span><span class="sxs-lookup"><span data-stu-id="0d91c-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="0d91c-143">Certains gestionnaires de jetons vous permettent de spécifier des paramètres de validation de certificat dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="0d91c-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="0d91c-144">Les paramètres sur des gestionnaires de jetons individuels remplacent ceux spécifiés au niveau du service et de la collection du gestionnaire de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="0d91c-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d91c-145">Exemple</span><span class="sxs-lookup"><span data-stu-id="0d91c-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```

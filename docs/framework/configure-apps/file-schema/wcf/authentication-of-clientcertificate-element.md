---
title: <authentication>d' <clientCertificate> élément
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 99084f6b7afbdd8586ee706cd6ec44b349d81ff2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398265"
---
# <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="749c7-102">\<authentication>d' \<clientCertificate> élément</span><span class="sxs-lookup"><span data-stu-id="749c7-102">\<authentication> of \<clientCertificate> Element</span></span>
<span data-ttu-id="749c7-103">Spécifie les comportements d'authentification des certificats clients utilisés par un service.</span><span class="sxs-lookup"><span data-stu-id="749c7-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="749c7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="749c7-104">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="749c7-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="749c7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="749c7-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="749c7-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="749c7-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="749c7-107">Attributes</span></span>  
  
|<span data-ttu-id="749c7-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="749c7-108">Attribute</span></span>|<span data-ttu-id="749c7-109">Description</span><span class="sxs-lookup"><span data-stu-id="749c7-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="749c7-110">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="749c7-110">customCertificateValidatorType</span></span>|<span data-ttu-id="749c7-111">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="749c7-111">Optional string.</span></span> <span data-ttu-id="749c7-112">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="749c7-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="749c7-113">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="749c7-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="749c7-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="749c7-114">certificateValidationMode</span></span>|<span data-ttu-id="749c7-115">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="749c7-115">Optional enumeration.</span></span> <span data-ttu-id="749c7-116">Spécifie l'un des modes utilisés pour valider les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="749c7-116">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="749c7-117">Cet attribut est de type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="749c7-117">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="749c7-118">S'il est défini à <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="749c7-118">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="749c7-119">Par défaut, il s’agit de <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="749c7-119">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="749c7-120">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="749c7-120">includeWindowsGroups</span></span>|<span data-ttu-id="749c7-121">Valeur booléenne facultative.</span><span class="sxs-lookup"><span data-stu-id="749c7-121">Optional Boolean.</span></span> <span data-ttu-id="749c7-122">Spécifie si des groupes Windows sont inclus dans le contexte de sécurité.</span><span class="sxs-lookup"><span data-stu-id="749c7-122">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="749c7-123">L'affectation de la valeur `true` à cet attribut a un impact sur les performances du fait que cela provoque une expansion de groupe complète.</span><span class="sxs-lookup"><span data-stu-id="749c7-123">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="749c7-124">Affectez la valeur `false` à cet attribut s'il n'est pas nécessaire d'établir la liste des groupes auxquels appartient un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="749c7-124">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="749c7-125">mapClientCertificateToWindowsAccount</span><span class="sxs-lookup"><span data-stu-id="749c7-125">mapClientCertificateToWindowsAccount</span></span>|<span data-ttu-id="749c7-126">Propriété booléenne.</span><span class="sxs-lookup"><span data-stu-id="749c7-126">Boolean.</span></span> <span data-ttu-id="749c7-127">Spécifie si le client peut être mappé à une identité Windows à l'aide du certificat.</span><span class="sxs-lookup"><span data-stu-id="749c7-127">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="749c7-128">Active Directory doit être activé pour cela.</span><span class="sxs-lookup"><span data-stu-id="749c7-128">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="749c7-129">revocationMode</span><span class="sxs-lookup"><span data-stu-id="749c7-129">revocationMode</span></span>|<span data-ttu-id="749c7-130">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="749c7-130">Optional enumeration.</span></span> <span data-ttu-id="749c7-131">Un des modes utilisés pour vérifier des listes de certificats révoqués (RCL).</span><span class="sxs-lookup"><span data-stu-id="749c7-131">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="749c7-132">Par défaut, il s’agit de `Online`.</span><span class="sxs-lookup"><span data-stu-id="749c7-132">The default is `Online`.</span></span> <span data-ttu-id="749c7-133">Cette valeur est ignorée lors de l'utilisation de la sécurité de transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="749c7-133">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="749c7-134">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="749c7-134">trustedStoreLocation</span></span>|<span data-ttu-id="749c7-135">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="749c7-135">Optional enumeration.</span></span> <span data-ttu-id="749c7-136">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="749c7-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="749c7-137">Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.</span><span class="sxs-lookup"><span data-stu-id="749c7-137">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="749c7-138">La validation est effectuée par rapport au magasin de **personnes autorisées** dans l’emplacement de magasin spécifié.</span><span class="sxs-lookup"><span data-stu-id="749c7-138">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="749c7-139">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="749c7-139">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="749c7-140">customCertificateValidatorType, attribut</span><span class="sxs-lookup"><span data-stu-id="749c7-140">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="749c7-141">Valeur</span><span class="sxs-lookup"><span data-stu-id="749c7-141">Value</span></span>|<span data-ttu-id="749c7-142">Description</span><span class="sxs-lookup"><span data-stu-id="749c7-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="749c7-143">String</span><span class="sxs-lookup"><span data-stu-id="749c7-143">String</span></span>|<span data-ttu-id="749c7-144">Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.</span><span class="sxs-lookup"><span data-stu-id="749c7-144">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="749c7-145">certificateValidationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="749c7-145">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="749c7-146">Valeur</span><span class="sxs-lookup"><span data-stu-id="749c7-146">Value</span></span>|<span data-ttu-id="749c7-147">Description</span><span class="sxs-lookup"><span data-stu-id="749c7-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="749c7-148">Énumération</span><span class="sxs-lookup"><span data-stu-id="749c7-148">Enumeration</span></span>|<span data-ttu-id="749c7-149">Une des valeurs suivantes : None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="749c7-149">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="749c7-150">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="749c7-150">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="749c7-151">revocationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="749c7-151">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="749c7-152">Valeur</span><span class="sxs-lookup"><span data-stu-id="749c7-152">Value</span></span>|<span data-ttu-id="749c7-153">Description</span><span class="sxs-lookup"><span data-stu-id="749c7-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="749c7-154">Énumération</span><span class="sxs-lookup"><span data-stu-id="749c7-154">Enumeration</span></span>|<span data-ttu-id="749c7-155">Une des valeurs suivantes : NoCheck, Online, Offline.</span><span class="sxs-lookup"><span data-stu-id="749c7-155">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="749c7-156">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="749c7-156">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="749c7-157">trustedStoreLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="749c7-157">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="749c7-158">Valeur</span><span class="sxs-lookup"><span data-stu-id="749c7-158">Value</span></span>|<span data-ttu-id="749c7-159">Description</span><span class="sxs-lookup"><span data-stu-id="749c7-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="749c7-160">Énumération</span><span class="sxs-lookup"><span data-stu-id="749c7-160">Enumeration</span></span>|<span data-ttu-id="749c7-161">L’une des valeurs suivantes : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="749c7-161">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="749c7-162">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="749c7-162">The default is `CurrentUser`.</span></span> <span data-ttu-id="749c7-163">Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="749c7-163">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="749c7-164">Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="749c7-164">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="749c7-165">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="749c7-165">Child Elements</span></span>  
 <span data-ttu-id="749c7-166">Aucun.</span><span class="sxs-lookup"><span data-stu-id="749c7-166">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="749c7-167">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="749c7-167">Parent Elements</span></span>  
  
|<span data-ttu-id="749c7-168">Élément</span><span class="sxs-lookup"><span data-stu-id="749c7-168">Element</span></span>|<span data-ttu-id="749c7-169">Description</span><span class="sxs-lookup"><span data-stu-id="749c7-169">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="749c7-170">Définit un certificat X.509 utilisé pour authentifier un client à un service.</span><span class="sxs-lookup"><span data-stu-id="749c7-170">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="749c7-171">Remarques</span><span class="sxs-lookup"><span data-stu-id="749c7-171">Remarks</span></span>  
 <span data-ttu-id="749c7-172">L'élément `<authentication>` correspond à la classe <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>.</span><span class="sxs-lookup"><span data-stu-id="749c7-172">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="749c7-173">Il vous permet de personnaliser la manière dont les clients sont authentifiés.</span><span class="sxs-lookup"><span data-stu-id="749c7-173">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="749c7-174">Vous pouvez affecter `certificateValidationMode`, `None`, `ChainTrust`, `PeerOrChainTrust` ou `PeerTrust` à l'attribut `Custom`.</span><span class="sxs-lookup"><span data-stu-id="749c7-174">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="749c7-175">Par défaut, le niveau a la valeur `ChainTrust` , qui spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant par une *autorité racine* au sommet de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="749c7-175">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="749c7-176">C’est le mode le plus sécurisé.</span><span class="sxs-lookup"><span data-stu-id="749c7-176">This is the most secure mode.</span></span> <span data-ttu-id="749c7-177">Vous pouvez également affecter la valeur `PeerOrChainTrust`, laquelle spécifie que les certificats auto-émis (approbation homologue) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée.</span><span class="sxs-lookup"><span data-stu-id="749c7-177">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="749c7-178">Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto-émis auprès d'une autorité approuvée.</span><span class="sxs-lookup"><span data-stu-id="749c7-178">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="749c7-179">Lorsque vous déployez un client, utilisez à la place la valeur `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="749c7-179">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="749c7-180">Vous pouvez également utiliser `Custom`.</span><span class="sxs-lookup"><span data-stu-id="749c7-180">You can also set the value to `Custom`.</span></span> <span data-ttu-id="749c7-181">Lorsque vous utilisez `Custom`, vous devez également affecter l'assembly et le type utilisés pour valider le certificat à l'attribut `customCertificateValidatorType`.</span><span class="sxs-lookup"><span data-stu-id="749c7-181">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="749c7-182">Pour créer votre propre validateur personnalisé, vous devez hériter de la classe <xref:System.IdentityModel.Selectors.X509CertificateValidator> abstraite.</span><span class="sxs-lookup"><span data-stu-id="749c7-182">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="749c7-183">Pour plus d’informations, consultez [Comment : créer un service qui utilise un validateur de certificat personnalisé](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="749c7-183">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="749c7-184">Exemple</span><span class="sxs-lookup"><span data-stu-id="749c7-184">Example</span></span>  
 <span data-ttu-id="749c7-185">Le code suivant spécifie un certificat X.509 et un type de validation personnalisé dans l'élément `<authentication>`.</span><span class="sxs-lookup"><span data-stu-id="749c7-185">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="749c7-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="749c7-186">See also</span></span>

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [<span data-ttu-id="749c7-187">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="749c7-187">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="749c7-188">Guide pratique pour créer un service qui utilise un validateur de certificat personnalisé</span><span class="sxs-lookup"><span data-stu-id="749c7-188">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="749c7-189">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="749c7-189">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)

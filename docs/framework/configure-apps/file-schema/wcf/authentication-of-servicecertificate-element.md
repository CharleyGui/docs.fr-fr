---
title: <authentication>d' <serviceCertificate> élément
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 29170f032469b4d55b50f57ca06ce403a5aeaf2c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398224"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="5891c-102">\<authentication>d' \<serviceCertificate> élément</span><span class="sxs-lookup"><span data-stu-id="5891c-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="5891c-103">Spécifie les paramètres utilisés par le proxy client pour authentifier les certificats de service obtenus à l'aide de la négociation SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="5891c-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="5891c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5891c-104">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5891c-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5891c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5891c-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5891c-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5891c-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="5891c-107">Attributes</span></span>  
  
|<span data-ttu-id="5891c-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="5891c-108">Attribute</span></span>|<span data-ttu-id="5891c-109">Description</span><span class="sxs-lookup"><span data-stu-id="5891c-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5891c-110">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="5891c-110">customCertificateValidatorType</span></span>|<span data-ttu-id="5891c-111">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="5891c-111">String.</span></span> <span data-ttu-id="5891c-112">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="5891c-112">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="5891c-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="5891c-113">certificateValidationMode</span></span>|<span data-ttu-id="5891c-114">Spécifie l'un de trois modes utilisés pour valider des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="5891c-114">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="5891c-115">S'il est défini à `Custom`, un customCertificateValidator doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="5891c-115">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="5891c-116">Par défaut, il s’agit de `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="5891c-116">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="5891c-117">revocationMode</span><span class="sxs-lookup"><span data-stu-id="5891c-117">revocationMode</span></span>|<span data-ttu-id="5891c-118">Un des modes utilisés pour vérifier des listes de certificat révoqués (CRL).</span><span class="sxs-lookup"><span data-stu-id="5891c-118">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="5891c-119">Par défaut, il s’agit de `Online`.</span><span class="sxs-lookup"><span data-stu-id="5891c-119">The default is `Online`.</span></span>|  
|<span data-ttu-id="5891c-120">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="5891c-120">trustedStoreLocation</span></span>|<span data-ttu-id="5891c-121">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="5891c-121">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="5891c-122">Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.</span><span class="sxs-lookup"><span data-stu-id="5891c-122">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="5891c-123">La validation est effectuée par rapport au magasin de **personnes autorisées** dans l’emplacement de magasin spécifié.</span><span class="sxs-lookup"><span data-stu-id="5891c-123">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="5891c-124">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="5891c-124">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="5891c-125">customCertificateValidator, attribut</span><span class="sxs-lookup"><span data-stu-id="5891c-125">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="5891c-126">Valeur</span><span class="sxs-lookup"><span data-stu-id="5891c-126">Value</span></span>|<span data-ttu-id="5891c-127">Description</span><span class="sxs-lookup"><span data-stu-id="5891c-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5891c-128">String</span><span class="sxs-lookup"><span data-stu-id="5891c-128">String</span></span>|<span data-ttu-id="5891c-129">Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.</span><span class="sxs-lookup"><span data-stu-id="5891c-129">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="5891c-130">certificateValidationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="5891c-130">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="5891c-131">Valeur</span><span class="sxs-lookup"><span data-stu-id="5891c-131">Value</span></span>|<span data-ttu-id="5891c-132">Description</span><span class="sxs-lookup"><span data-stu-id="5891c-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5891c-133">Énumération</span><span class="sxs-lookup"><span data-stu-id="5891c-133">Enumeration</span></span>|<span data-ttu-id="5891c-134">Une des valeurs suivantes : None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="5891c-134">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="5891c-135">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="5891c-135">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="5891c-136">revocationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="5891c-136">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="5891c-137">Valeur</span><span class="sxs-lookup"><span data-stu-id="5891c-137">Value</span></span>|<span data-ttu-id="5891c-138">Description</span><span class="sxs-lookup"><span data-stu-id="5891c-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5891c-139">Énumération</span><span class="sxs-lookup"><span data-stu-id="5891c-139">Enumeration</span></span>|<span data-ttu-id="5891c-140">Une des valeurs suivantes : NoCheck, Online, Offline.</span><span class="sxs-lookup"><span data-stu-id="5891c-140">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="5891c-141">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="5891c-141">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="5891c-142">trustedStoreLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="5891c-142">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="5891c-143">Valeur</span><span class="sxs-lookup"><span data-stu-id="5891c-143">Value</span></span>|<span data-ttu-id="5891c-144">Description</span><span class="sxs-lookup"><span data-stu-id="5891c-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5891c-145">Énumération</span><span class="sxs-lookup"><span data-stu-id="5891c-145">Enumeration</span></span>|<span data-ttu-id="5891c-146">Une des valeurs suivantes : LocalMachine ou CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="5891c-146">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="5891c-147">La valeur par défaut est CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="5891c-147">The default is CurrentUser.</span></span> <span data-ttu-id="5891c-148">Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="5891c-148">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="5891c-149">Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="5891c-149">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5891c-150">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5891c-150">Child Elements</span></span>  
 <span data-ttu-id="5891c-151">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5891c-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5891c-152">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5891c-152">Parent Elements</span></span>  
  
|<span data-ttu-id="5891c-153">Élément</span><span class="sxs-lookup"><span data-stu-id="5891c-153">Element</span></span>|<span data-ttu-id="5891c-154">Description</span><span class="sxs-lookup"><span data-stu-id="5891c-154">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="5891c-155">Spécifie un certificat à utiliser lors de l'authentification d'un service au client.</span><span class="sxs-lookup"><span data-stu-id="5891c-155">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5891c-156">Remarques</span><span class="sxs-lookup"><span data-stu-id="5891c-156">Remarks</span></span>  
 <span data-ttu-id="5891c-157">L'attribut `certificateValidationMode` de cet élément de configuration spécifie le niveau de confiance utilisé pour authentifier les certificats.</span><span class="sxs-lookup"><span data-stu-id="5891c-157">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="5891c-158">Par défaut, le niveau a la valeur `ChainTrust`, qui spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant dans une autorité de certification approuvée au sommet de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="5891c-158">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="5891c-159">C’est le mode le plus sécurisé.</span><span class="sxs-lookup"><span data-stu-id="5891c-159">This is the most secure mode.</span></span> <span data-ttu-id="5891c-160">Vous pouvez également affecter la valeur `PeerOrChainTrust`, laquelle spécifie que les certificats auto-émis (approbation homologue) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée.</span><span class="sxs-lookup"><span data-stu-id="5891c-160">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="5891c-161">Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto-émis auprès d'une autorité approuvée.</span><span class="sxs-lookup"><span data-stu-id="5891c-161">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="5891c-162">Lorsque vous déployez un client, utilisez à la place la valeur `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="5891c-162">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="5891c-163">Vous pouvez également affecter la valeur `Custom` ou `None`.</span><span class="sxs-lookup"><span data-stu-id="5891c-163">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="5891c-164">Pour utiliser la valeur `Custom`, vous devez également affecter à l'attribut `customCertificateValidator` l'assembly et le type utilisés pour valider le certificat.</span><span class="sxs-lookup"><span data-stu-id="5891c-164">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="5891c-165">Pour créer un validateur personnalisé, vous devez hériter de la classe X509CertificateValidator abstraite.</span><span class="sxs-lookup"><span data-stu-id="5891c-165">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="5891c-166">Pour plus d’informations, consultez [Comment : créer un service qui utilise un validateur de certificat personnalisé](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="5891c-166">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="5891c-167">L'attribut `revocationMode` spécifie le mode de vérification des certificats à révoquer.</span><span class="sxs-lookup"><span data-stu-id="5891c-167">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="5891c-168">La valeur par défaut est `online`, qui indique que les certificats sont automatiquement vérifiés pour révocation.</span><span class="sxs-lookup"><span data-stu-id="5891c-168">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="5891c-169">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="5891c-169">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5891c-170">Exemple</span><span class="sxs-lookup"><span data-stu-id="5891c-170">Example</span></span>  
 <span data-ttu-id="5891c-171">Dans l’exemple suivant, deux tâches sont effectuées :</span><span class="sxs-lookup"><span data-stu-id="5891c-171">The following example does two tasks.</span></span> <span data-ttu-id="5891c-172">Il spécifie d’abord un certificat de service que le client doit utiliser lors de la communication avec les points de terminaison dont le nom de domaine se trouve `www.contoso.com` sur le protocole http.</span><span class="sxs-lookup"><span data-stu-id="5891c-172">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="5891c-173">Deuxièmement, le mode de révocation et l'emplacement de magasin utilisés pendant l'authentification sont définis.</span><span class="sxs-lookup"><span data-stu-id="5891c-173">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
     <add targetUri="http://www.contoso.com"
          findValue="www.contoso.com"
          storeLocation="LocalMachine"
          storeName="Root"
          x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="5891c-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5891c-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="5891c-175">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="5891c-175">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="5891c-176">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="5891c-176">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="5891c-177">Guide pratique pour créer un service qui utilise un validateur de certificat personnalisé</span><span class="sxs-lookup"><span data-stu-id="5891c-177">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="5891c-178">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="5891c-178">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="5891c-179">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="5891c-179">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)

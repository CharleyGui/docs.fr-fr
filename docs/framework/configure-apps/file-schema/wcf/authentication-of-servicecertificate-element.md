---
title: <authentication>d' <serviceCertificate> élément
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: d770ba1f9a0a18c927b3a4bf6d4141286e3a380c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919981"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="4e128-102">\<> d’authentification \<de l’élément > serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="4e128-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="4e128-103">Spécifie les paramètres utilisés par le proxy client pour authentifier les certificats de service obtenus à l'aide de la négociation SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="4e128-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
 <span data-ttu-id="4e128-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4e128-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4e128-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="4e128-105">\<behaviors></span></span>  
<span data-ttu-id="4e128-106">section endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="4e128-106">endpointBehaviors section</span></span>  
<span data-ttu-id="4e128-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="4e128-107">\<behavior></span></span>  
<span data-ttu-id="4e128-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="4e128-108">\<clientCredentials></span></span>  
<span data-ttu-id="4e128-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="4e128-109">\<serviceCertificate></span></span>  
<span data-ttu-id="4e128-110">\<authentication></span><span class="sxs-lookup"><span data-stu-id="4e128-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e128-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e128-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4e128-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4e128-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4e128-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4e128-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4e128-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="4e128-114">Attributes</span></span>  
  
|<span data-ttu-id="4e128-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="4e128-115">Attribute</span></span>|<span data-ttu-id="4e128-116">Description</span><span class="sxs-lookup"><span data-stu-id="4e128-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4e128-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="4e128-117">customCertificateValidatorType</span></span>|<span data-ttu-id="4e128-118">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="4e128-118">String.</span></span> <span data-ttu-id="4e128-119">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4e128-119">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="4e128-120">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="4e128-120">certificateValidationMode</span></span>|<span data-ttu-id="4e128-121">Spécifie l'un de trois modes utilisés pour valider des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="4e128-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="4e128-122">S'il est défini à `Custom`, un customCertificateValidator doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="4e128-122">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="4e128-123">Par défaut, il s’agit de `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="4e128-123">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="4e128-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="4e128-124">revocationMode</span></span>|<span data-ttu-id="4e128-125">Un des modes utilisés pour vérifier des listes de certificat révoqués (CRL).</span><span class="sxs-lookup"><span data-stu-id="4e128-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="4e128-126">Par défaut, il s’agit de `Online`.</span><span class="sxs-lookup"><span data-stu-id="4e128-126">The default is `Online`.</span></span>|  
|<span data-ttu-id="4e128-127">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="4e128-127">trustedStoreLocation</span></span>|<span data-ttu-id="4e128-128">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="4e128-128">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="4e128-129">Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.</span><span class="sxs-lookup"><span data-stu-id="4e128-129">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="4e128-130">La validation est effectuée par rapport au magasin de **personnes autorisées** dans l’emplacement de magasin spécifié.</span><span class="sxs-lookup"><span data-stu-id="4e128-130">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="4e128-131">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="4e128-131">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="4e128-132">customCertificateValidator, attribut</span><span class="sxs-lookup"><span data-stu-id="4e128-132">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="4e128-133">Valeur</span><span class="sxs-lookup"><span data-stu-id="4e128-133">Value</span></span>|<span data-ttu-id="4e128-134">Description</span><span class="sxs-lookup"><span data-stu-id="4e128-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4e128-135">String</span><span class="sxs-lookup"><span data-stu-id="4e128-135">String</span></span>|<span data-ttu-id="4e128-136">Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.</span><span class="sxs-lookup"><span data-stu-id="4e128-136">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="4e128-137">certificateValidationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="4e128-137">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="4e128-138">`Value`</span><span class="sxs-lookup"><span data-stu-id="4e128-138">Value</span></span>|<span data-ttu-id="4e128-139">Description</span><span class="sxs-lookup"><span data-stu-id="4e128-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4e128-140">Énumération</span><span class="sxs-lookup"><span data-stu-id="4e128-140">Enumeration</span></span>|<span data-ttu-id="4e128-141">L’une des valeurs suivantes : None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="4e128-141">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="4e128-142">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="4e128-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="4e128-143">revocationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="4e128-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="4e128-144">Valeur</span><span class="sxs-lookup"><span data-stu-id="4e128-144">Value</span></span>|<span data-ttu-id="4e128-145">Description</span><span class="sxs-lookup"><span data-stu-id="4e128-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4e128-146">Énumération</span><span class="sxs-lookup"><span data-stu-id="4e128-146">Enumeration</span></span>|<span data-ttu-id="4e128-147">L’une des valeurs suivantes : NOCHECK, en ligne, hors connexion.</span><span class="sxs-lookup"><span data-stu-id="4e128-147">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="4e128-148">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="4e128-148">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="4e128-149">trustedStoreLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="4e128-149">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="4e128-150">Valeur</span><span class="sxs-lookup"><span data-stu-id="4e128-150">Value</span></span>|<span data-ttu-id="4e128-151">Description</span><span class="sxs-lookup"><span data-stu-id="4e128-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4e128-152">Énumération</span><span class="sxs-lookup"><span data-stu-id="4e128-152">Enumeration</span></span>|<span data-ttu-id="4e128-153">L’une des valeurs suivantes : LocalMachine ou CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="4e128-153">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="4e128-154">La valeur par défaut est CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="4e128-154">The default is CurrentUser.</span></span> <span data-ttu-id="4e128-155">Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="4e128-155">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="4e128-156">Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="4e128-156">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4e128-157">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4e128-157">Child Elements</span></span>  
 <span data-ttu-id="4e128-158">Aucun.</span><span class="sxs-lookup"><span data-stu-id="4e128-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4e128-159">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4e128-159">Parent Elements</span></span>  
  
|<span data-ttu-id="4e128-160">Élément</span><span class="sxs-lookup"><span data-stu-id="4e128-160">Element</span></span>|<span data-ttu-id="4e128-161">Description</span><span class="sxs-lookup"><span data-stu-id="4e128-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4e128-162">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="4e128-162">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="4e128-163">Spécifie un certificat à utiliser lors de l'authentification d'un service au client.</span><span class="sxs-lookup"><span data-stu-id="4e128-163">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4e128-164">Notes</span><span class="sxs-lookup"><span data-stu-id="4e128-164">Remarks</span></span>  
 <span data-ttu-id="4e128-165">L'attribut `certificateValidationMode` de cet élément de configuration spécifie le niveau de confiance utilisé pour authentifier les certificats.</span><span class="sxs-lookup"><span data-stu-id="4e128-165">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="4e128-166">Par défaut, le niveau a la valeur `ChainTrust`, qui spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant dans une autorité de certification approuvée au sommet de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="4e128-166">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="4e128-167">C’est le mode le plus sécurisé.</span><span class="sxs-lookup"><span data-stu-id="4e128-167">This is the most secure mode.</span></span> <span data-ttu-id="4e128-168">Vous pouvez également affecter la valeur `PeerOrChainTrust`, laquelle spécifie que les certificats auto-émis (approbation homologue) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée.</span><span class="sxs-lookup"><span data-stu-id="4e128-168">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="4e128-169">Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto-émis auprès d'une autorité approuvée.</span><span class="sxs-lookup"><span data-stu-id="4e128-169">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="4e128-170">Lorsque vous déployez un client, utilisez à la place la valeur `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="4e128-170">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="4e128-171">Vous pouvez également affecter la valeur `Custom` ou `None`.</span><span class="sxs-lookup"><span data-stu-id="4e128-171">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="4e128-172">Pour utiliser la valeur `Custom`, vous devez également affecter à l'attribut `customCertificateValidator` l'assembly et le type utilisés pour valider le certificat.</span><span class="sxs-lookup"><span data-stu-id="4e128-172">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="4e128-173">Pour créer un validateur personnalisé, vous devez hériter de la classe X509CertificateValidator abstraite.</span><span class="sxs-lookup"><span data-stu-id="4e128-173">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="4e128-174">Pour plus d'informations, voir [Procédure : Créez un service qui utilise un validateur](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)de certificat personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4e128-174">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="4e128-175">L'attribut `revocationMode` spécifie le mode de vérification des certificats à révoquer.</span><span class="sxs-lookup"><span data-stu-id="4e128-175">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="4e128-176">La valeur par défaut est `online`, qui indique que les certificats sont automatiquement vérifiés pour révocation.</span><span class="sxs-lookup"><span data-stu-id="4e128-176">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="4e128-177">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="4e128-177">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e128-178">Exemple</span><span class="sxs-lookup"><span data-stu-id="4e128-178">Example</span></span>  
 <span data-ttu-id="4e128-179">Dans l’exemple suivant, deux tâches sont effectuées :</span><span class="sxs-lookup"><span data-stu-id="4e128-179">The following example does two tasks.</span></span> <span data-ttu-id="4e128-180">Il spécifie d’abord un certificat de service que le client doit utiliser lors de la communication avec les `www.contoso.com` points de terminaison dont le nom de domaine se trouve sur le protocole http.</span><span class="sxs-lookup"><span data-stu-id="4e128-180">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="4e128-181">Deuxièmement, le mode de révocation et l'emplacement de magasin utilisés pendant l'authentification sont définis.</span><span class="sxs-lookup"><span data-stu-id="4e128-181">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4e128-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4e128-182">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="4e128-183">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="4e128-183">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="4e128-184">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="4e128-184">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="4e128-185">Guide pratique pour Créer un service qui utilise un validateur de certificat personnalisé</span><span class="sxs-lookup"><span data-stu-id="4e128-185">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="4e128-186">\<authentication></span><span class="sxs-lookup"><span data-stu-id="4e128-186">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="4e128-187">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="4e128-187">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="4e128-188">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="4e128-188">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)

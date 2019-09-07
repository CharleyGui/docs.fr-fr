---
title: <authentication>d' <serviceCertificate> élément
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 29170f032469b4d55b50f57ca06ce403a5aeaf2c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398224"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="b1aae-102">\<> d’authentification \<de l’élément > serviceCertificate</span><span class="sxs-lookup"><span data-stu-id="b1aae-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="b1aae-103">Spécifie les paramètres utilisés par le proxy client pour authentifier les certificats de service obtenus à l'aide de la négociation SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="b1aae-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
<span data-ttu-id="b1aae-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1aae-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b1aae-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b1aae-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b1aae-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b1aae-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="b1aae-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b1aae-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="b1aae-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b1aae-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="b1aae-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="b1aae-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="b1aae-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1aae-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="b1aae-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> d’authentification**</span><span class="sxs-lookup"><span data-stu-id="b1aae-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1aae-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1aae-112">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1aae-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b1aae-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b1aae-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b1aae-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1aae-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="b1aae-115">Attributes</span></span>  
  
|<span data-ttu-id="b1aae-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="b1aae-116">Attribute</span></span>|<span data-ttu-id="b1aae-117">Description</span><span class="sxs-lookup"><span data-stu-id="b1aae-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1aae-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="b1aae-118">customCertificateValidatorType</span></span>|<span data-ttu-id="b1aae-119">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="b1aae-119">String.</span></span> <span data-ttu-id="b1aae-120">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b1aae-120">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="b1aae-121">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="b1aae-121">certificateValidationMode</span></span>|<span data-ttu-id="b1aae-122">Spécifie l'un de trois modes utilisés pour valider des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="b1aae-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="b1aae-123">S'il est défini à `Custom`, un customCertificateValidator doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="b1aae-123">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="b1aae-124">Par défaut, il s’agit de `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="b1aae-124">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="b1aae-125">revocationMode</span><span class="sxs-lookup"><span data-stu-id="b1aae-125">revocationMode</span></span>|<span data-ttu-id="b1aae-126">Un des modes utilisés pour vérifier des listes de certificat révoqués (CRL).</span><span class="sxs-lookup"><span data-stu-id="b1aae-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="b1aae-127">Par défaut, il s’agit de `Online`.</span><span class="sxs-lookup"><span data-stu-id="b1aae-127">The default is `Online`.</span></span>|  
|<span data-ttu-id="b1aae-128">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="b1aae-128">trustedStoreLocation</span></span>|<span data-ttu-id="b1aae-129">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b1aae-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="b1aae-130">Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.</span><span class="sxs-lookup"><span data-stu-id="b1aae-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="b1aae-131">La validation est effectuée par rapport au magasin de **personnes autorisées** dans l’emplacement de magasin spécifié.</span><span class="sxs-lookup"><span data-stu-id="b1aae-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="b1aae-132">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b1aae-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="b1aae-133">customCertificateValidator, attribut</span><span class="sxs-lookup"><span data-stu-id="b1aae-133">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="b1aae-134">`Value`</span><span class="sxs-lookup"><span data-stu-id="b1aae-134">Value</span></span>|<span data-ttu-id="b1aae-135">Description</span><span class="sxs-lookup"><span data-stu-id="b1aae-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b1aae-136">String</span><span class="sxs-lookup"><span data-stu-id="b1aae-136">String</span></span>|<span data-ttu-id="b1aae-137">Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.</span><span class="sxs-lookup"><span data-stu-id="b1aae-137">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="b1aae-138">certificateValidationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="b1aae-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="b1aae-139">`Value`</span><span class="sxs-lookup"><span data-stu-id="b1aae-139">Value</span></span>|<span data-ttu-id="b1aae-140">Description</span><span class="sxs-lookup"><span data-stu-id="b1aae-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b1aae-141">Énumération</span><span class="sxs-lookup"><span data-stu-id="b1aae-141">Enumeration</span></span>|<span data-ttu-id="b1aae-142">L’une des valeurs suivantes : None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="b1aae-142">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="b1aae-143">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="b1aae-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="b1aae-144">revocationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="b1aae-144">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="b1aae-145">`Value`</span><span class="sxs-lookup"><span data-stu-id="b1aae-145">Value</span></span>|<span data-ttu-id="b1aae-146">Description</span><span class="sxs-lookup"><span data-stu-id="b1aae-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b1aae-147">Énumération</span><span class="sxs-lookup"><span data-stu-id="b1aae-147">Enumeration</span></span>|<span data-ttu-id="b1aae-148">L’une des valeurs suivantes : NOCHECK, en ligne, hors connexion.</span><span class="sxs-lookup"><span data-stu-id="b1aae-148">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="b1aae-149">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="b1aae-149">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="b1aae-150">trustedStoreLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="b1aae-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="b1aae-151">`Value`</span><span class="sxs-lookup"><span data-stu-id="b1aae-151">Value</span></span>|<span data-ttu-id="b1aae-152">Description</span><span class="sxs-lookup"><span data-stu-id="b1aae-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b1aae-153">Énumération</span><span class="sxs-lookup"><span data-stu-id="b1aae-153">Enumeration</span></span>|<span data-ttu-id="b1aae-154">L’une des valeurs suivantes : LocalMachine ou CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="b1aae-154">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="b1aae-155">La valeur par défaut est CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="b1aae-155">The default is CurrentUser.</span></span> <span data-ttu-id="b1aae-156">Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="b1aae-156">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="b1aae-157">Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="b1aae-157">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1aae-158">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b1aae-158">Child Elements</span></span>  
 <span data-ttu-id="b1aae-159">Aucun.</span><span class="sxs-lookup"><span data-stu-id="b1aae-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1aae-160">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b1aae-160">Parent Elements</span></span>  
  
|<span data-ttu-id="b1aae-161">Élément</span><span class="sxs-lookup"><span data-stu-id="b1aae-161">Element</span></span>|<span data-ttu-id="b1aae-162">Description</span><span class="sxs-lookup"><span data-stu-id="b1aae-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1aae-163">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="b1aae-163">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="b1aae-164">Spécifie un certificat à utiliser lors de l'authentification d'un service au client.</span><span class="sxs-lookup"><span data-stu-id="b1aae-164">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1aae-165">Notes</span><span class="sxs-lookup"><span data-stu-id="b1aae-165">Remarks</span></span>  
 <span data-ttu-id="b1aae-166">L'attribut `certificateValidationMode` de cet élément de configuration spécifie le niveau de confiance utilisé pour authentifier les certificats.</span><span class="sxs-lookup"><span data-stu-id="b1aae-166">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="b1aae-167">Par défaut, le niveau a la valeur `ChainTrust`, qui spécifie que chaque certificat doit se trouver dans une hiérarchie de certificats se terminant dans une autorité de certification approuvée au sommet de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="b1aae-167">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="b1aae-168">C’est le mode le plus sécurisé.</span><span class="sxs-lookup"><span data-stu-id="b1aae-168">This is the most secure mode.</span></span> <span data-ttu-id="b1aae-169">Vous pouvez également affecter la valeur `PeerOrChainTrust`, laquelle spécifie que les certificats auto-émis (approbation homologue) sont acceptés, de même que les certificats qui se trouvent dans une chaîne approuvée.</span><span class="sxs-lookup"><span data-stu-id="b1aae-169">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="b1aae-170">Cette valeur est utilisée lors du développement et du débogage des clients et des services car il n'est pas nécessaire d'acheter les certificats auto-émis auprès d'une autorité approuvée.</span><span class="sxs-lookup"><span data-stu-id="b1aae-170">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="b1aae-171">Lorsque vous déployez un client, utilisez à la place la valeur `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="b1aae-171">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="b1aae-172">Vous pouvez également affecter la valeur `Custom` ou `None`.</span><span class="sxs-lookup"><span data-stu-id="b1aae-172">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="b1aae-173">Pour utiliser la valeur `Custom`, vous devez également affecter à l'attribut `customCertificateValidator` l'assembly et le type utilisés pour valider le certificat.</span><span class="sxs-lookup"><span data-stu-id="b1aae-173">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="b1aae-174">Pour créer un validateur personnalisé, vous devez hériter de la classe X509CertificateValidator abstraite.</span><span class="sxs-lookup"><span data-stu-id="b1aae-174">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="b1aae-175">Pour plus d'informations, voir [Procédure : Créez un service qui utilise un validateur](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)de certificat personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b1aae-175">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="b1aae-176">L'attribut `revocationMode` spécifie le mode de vérification des certificats à révoquer.</span><span class="sxs-lookup"><span data-stu-id="b1aae-176">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="b1aae-177">La valeur par défaut est `online`, qui indique que les certificats sont automatiquement vérifiés pour révocation.</span><span class="sxs-lookup"><span data-stu-id="b1aae-177">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="b1aae-178">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="b1aae-178">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1aae-179">Exemples</span><span class="sxs-lookup"><span data-stu-id="b1aae-179">Example</span></span>  
 <span data-ttu-id="b1aae-180">Dans l’exemple suivant, deux tâches sont effectuées :</span><span class="sxs-lookup"><span data-stu-id="b1aae-180">The following example does two tasks.</span></span> <span data-ttu-id="b1aae-181">Il spécifie d’abord un certificat de service que le client doit utiliser lors de la communication avec les `www.contoso.com` points de terminaison dont le nom de domaine se trouve sur le protocole http.</span><span class="sxs-lookup"><span data-stu-id="b1aae-181">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="b1aae-182">Deuxièmement, le mode de révocation et l'emplacement de magasin utilisés pendant l'authentification sont définis.</span><span class="sxs-lookup"><span data-stu-id="b1aae-182">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1aae-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1aae-183">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="b1aae-184">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="b1aae-184">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b1aae-185">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="b1aae-185">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="b1aae-186">Guide pratique pour Créer un service qui utilise un validateur de certificat personnalisé</span><span class="sxs-lookup"><span data-stu-id="b1aae-186">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="b1aae-187">\<authentication></span><span class="sxs-lookup"><span data-stu-id="b1aae-187">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="b1aae-188">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="b1aae-188">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="b1aae-189">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="b1aae-189">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)

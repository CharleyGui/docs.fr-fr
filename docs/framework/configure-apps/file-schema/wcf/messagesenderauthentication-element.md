---
title: <messageSenderAuthentication>, élément
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 804c280bcdb0fecc87f71121b7d95b5fd0268de9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423124"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="7c9c8-102">\<messageSenderAuthentication > élément</span><span class="sxs-lookup"><span data-stu-id="7c9c8-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="7c9c8-103">Spécifie les options d'authentification pour les expéditeurs du message du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="7c9c8-104">Pour plus d’informations sur la programmation de peer-to-peer, consultez [mise en réseau Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="7c9c8-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="7c9c8-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7c9c8-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="7c9c8-106">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="7c9c8-106">\<behaviors></span></span>  
<span data-ttu-id="7c9c8-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="7c9c8-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="7c9c8-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="7c9c8-108">\<behavior></span></span>  
<span data-ttu-id="7c9c8-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="7c9c8-109">\<clientCredentials></span></span>  
<span data-ttu-id="7c9c8-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="7c9c8-110">\<peer></span></span>  
<span data-ttu-id="7c9c8-111">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="7c9c8-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c9c8-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c9c8-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c9c8-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7c9c8-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7c9c8-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c9c8-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="7c9c8-115">Attributes</span></span>  
  
|<span data-ttu-id="7c9c8-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="7c9c8-116">Attribute</span></span>|<span data-ttu-id="7c9c8-117">Description</span><span class="sxs-lookup"><span data-stu-id="7c9c8-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="7c9c8-118">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-118">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="7c9c8-119">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-119">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="7c9c8-120">Spécifie l'un de trois modes utilisés pour valider des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-120">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="7c9c8-121">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-121">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="7c9c8-122">Un des modes utilisés pour vérifier des listes de certificat révoqués (CRL).</span><span class="sxs-lookup"><span data-stu-id="7c9c8-122">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="7c9c8-123">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-123">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="7c9c8-124">Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-124">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="7c9c8-125">La validation est effectuée sur le **personnes** stocker dans l’emplacement de magasin spécifié.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-125">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="7c9c8-126">customCertificateValidatorType, attribut</span><span class="sxs-lookup"><span data-stu-id="7c9c8-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="7c9c8-127">Value</span><span class="sxs-lookup"><span data-stu-id="7c9c8-127">Value</span></span>|<span data-ttu-id="7c9c8-128">Description</span><span class="sxs-lookup"><span data-stu-id="7c9c8-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7c9c8-129">Chaîne</span><span class="sxs-lookup"><span data-stu-id="7c9c8-129">String</span></span>|<span data-ttu-id="7c9c8-130">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-130">Optional.</span></span> <span data-ttu-id="7c9c8-131">Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-131">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="7c9c8-132">Au minimum, un espace de noms et un nom de type sont requis.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-132">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="7c9c8-133">Les informations facultatives incluent : le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-133">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="7c9c8-134">certificateValidationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="7c9c8-134">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="7c9c8-135">Value</span><span class="sxs-lookup"><span data-stu-id="7c9c8-135">Value</span></span>|<span data-ttu-id="7c9c8-136">Description</span><span class="sxs-lookup"><span data-stu-id="7c9c8-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7c9c8-137">Énumération</span><span class="sxs-lookup"><span data-stu-id="7c9c8-137">Enumeration</span></span>|<span data-ttu-id="7c9c8-138">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-138">Optional.</span></span> <span data-ttu-id="7c9c8-139">Une des valeurs suivantes : `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust` et `Custom`.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-139">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="7c9c8-140">La valeur par défaut est `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-140">The default is `ChainTrust`.</span></span> <span data-ttu-id="7c9c8-141">La valeur par défaut est `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-141">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="7c9c8-142">Pour plus d’informations, consultez [utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7c9c8-142">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="7c9c8-143">revocationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="7c9c8-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="7c9c8-144">Value</span><span class="sxs-lookup"><span data-stu-id="7c9c8-144">Value</span></span>|<span data-ttu-id="7c9c8-145">Description</span><span class="sxs-lookup"><span data-stu-id="7c9c8-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7c9c8-146">Énumération</span><span class="sxs-lookup"><span data-stu-id="7c9c8-146">Enumeration</span></span>|<span data-ttu-id="7c9c8-147">Une des valeurs suivantes : `NoCheck`, `Online` et `Offline`.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-147">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="7c9c8-148">La valeur par défaut est `Online`.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-148">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="7c9c8-149">Pour plus d’informations, consultez [utilisation des certificats](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7c9c8-149">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="7c9c8-150">trustedStoreLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="7c9c8-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="7c9c8-151">Value</span><span class="sxs-lookup"><span data-stu-id="7c9c8-151">Value</span></span>|<span data-ttu-id="7c9c8-152">Description</span><span class="sxs-lookup"><span data-stu-id="7c9c8-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7c9c8-153">Énumération</span><span class="sxs-lookup"><span data-stu-id="7c9c8-153">Enumeration</span></span>|<span data-ttu-id="7c9c8-154">Une des valeurs suivantes : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-154">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="7c9c8-155">La valeur par défaut est `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-155">The default is `CurrentUser`.</span></span> <span data-ttu-id="7c9c8-156">Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-156">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="7c9c8-157">Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-157">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="7c9c8-158">La valeur par défaut est `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-158">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c9c8-159">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7c9c8-159">Child Elements</span></span>  
 <span data-ttu-id="7c9c8-160">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c9c8-161">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7c9c8-161">Parent Elements</span></span>  
  
|<span data-ttu-id="7c9c8-162">Élément</span><span class="sxs-lookup"><span data-stu-id="7c9c8-162">Element</span></span>|<span data-ttu-id="7c9c8-163">Description</span><span class="sxs-lookup"><span data-stu-id="7c9c8-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c9c8-164">\<peer></span><span class="sxs-lookup"><span data-stu-id="7c9c8-164">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="7c9c8-165">Spécifie une information d'identification utilisée pour authentifier le client auprès d'un service homologue.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-165">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c9c8-166">Notes</span><span class="sxs-lookup"><span data-stu-id="7c9c8-166">Remarks</span></span>  
 <span data-ttu-id="7c9c8-167">Cet élément doit être configuré si l'authentification des messages est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-167">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="7c9c8-168">Pour les canaux de sortie, chaque message est signé à l’aide du certificat fourni par [ \<certificat >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="7c9c8-168">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="7c9c8-169">Avant d'être remis à l'application, tous les messages sont vérifiés par rapport aux informations d'identification de message à l'aide du validateur spécifié par l'attribut `customCertificateValidatorType` de cet élément.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-169">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="7c9c8-170">Le validateur peut accepter ou rejeter les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-170">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c9c8-171">Exemple</span><span class="sxs-lookup"><span data-stu-id="7c9c8-171">Example</span></span>  
 <span data-ttu-id="7c9c8-172">Les jeux de codes suivants affectent le mode de validation de l’expéditeur du message à `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="7c9c8-172">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="7c9c8-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c9c8-173">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="7c9c8-174">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="7c9c8-174">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="7c9c8-175">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="7c9c8-175">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="7c9c8-176">[Authentification de Message de canal homologue](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7c9c8-176">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="7c9c8-177">[Authentification personnalisée de canal homologue](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7c9c8-177">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="7c9c8-178">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="7c9c8-178">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)

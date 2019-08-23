---
title: <messageSenderAuthentication>, élément
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 1e63b6fa93e1abfa87c83da4b5d46f492c59b9bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931375"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="6d9e6-102">\<messageSenderAuthentication >, élément</span><span class="sxs-lookup"><span data-stu-id="6d9e6-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="6d9e6-103">Spécifie les options d'authentification pour les expéditeurs du message du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="6d9e6-104">Pour plus d’informations sur la programmation d’égal à égal, consultez [mise en réseau pair à pair](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="6d9e6-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="6d9e6-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6d9e6-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="6d9e6-106">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="6d9e6-106">\<behaviors></span></span>  
<span data-ttu-id="6d9e6-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="6d9e6-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="6d9e6-108">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="6d9e6-108">\<behavior></span></span>  
<span data-ttu-id="6d9e6-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="6d9e6-109">\<clientCredentials></span></span>  
<span data-ttu-id="6d9e6-110">\<> homologues</span><span class="sxs-lookup"><span data-stu-id="6d9e6-110">\<peer></span></span>  
<span data-ttu-id="6d9e6-111">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="6d9e6-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d9e6-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d9e6-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d9e6-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6d9e6-113">Attributes and Elements</span></span>  
 <span data-ttu-id="6d9e6-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d9e6-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="6d9e6-115">Attributes</span></span>  
  
|<span data-ttu-id="6d9e6-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="6d9e6-116">Attribute</span></span>|<span data-ttu-id="6d9e6-117">Description</span><span class="sxs-lookup"><span data-stu-id="6d9e6-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="6d9e6-118">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-118">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="6d9e6-119">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-119">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="6d9e6-120">Spécifie l'un de trois modes utilisés pour valider des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-120">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="6d9e6-121">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-121">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="6d9e6-122">Un des modes utilisés pour vérifier des listes de certificat révoqués (CRL).</span><span class="sxs-lookup"><span data-stu-id="6d9e6-122">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="6d9e6-123">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-123">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="6d9e6-124">Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-124">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="6d9e6-125">La validation est effectuée par rapport au magasin de **personnes autorisées** dans l’emplacement de magasin spécifié.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-125">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="6d9e6-126">customCertificateValidatorType, attribut</span><span class="sxs-lookup"><span data-stu-id="6d9e6-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="6d9e6-127">Valeur</span><span class="sxs-lookup"><span data-stu-id="6d9e6-127">Value</span></span>|<span data-ttu-id="6d9e6-128">Description</span><span class="sxs-lookup"><span data-stu-id="6d9e6-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6d9e6-129">String</span><span class="sxs-lookup"><span data-stu-id="6d9e6-129">String</span></span>|<span data-ttu-id="6d9e6-130">facultatif.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-130">Optional.</span></span> <span data-ttu-id="6d9e6-131">Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-131">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="6d9e6-132">Au minimum, un espace de noms et un nom de type sont requis.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-132">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="6d9e6-133">Les informations facultatives incluent : le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-133">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="6d9e6-134">certificateValidationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="6d9e6-134">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="6d9e6-135">Valeur</span><span class="sxs-lookup"><span data-stu-id="6d9e6-135">Value</span></span>|<span data-ttu-id="6d9e6-136">Description</span><span class="sxs-lookup"><span data-stu-id="6d9e6-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6d9e6-137">Énumération</span><span class="sxs-lookup"><span data-stu-id="6d9e6-137">Enumeration</span></span>|<span data-ttu-id="6d9e6-138">facultatif.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-138">Optional.</span></span> <span data-ttu-id="6d9e6-139">Une des valeurs suivantes : `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust` et `Custom`.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-139">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="6d9e6-140">Par défaut, il s’agit de `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-140">The default is `ChainTrust`.</span></span> <span data-ttu-id="6d9e6-141">Par défaut, il s’agit de `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-141">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="6d9e6-142">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6d9e6-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="6d9e6-143">revocationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="6d9e6-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="6d9e6-144">`Value`</span><span class="sxs-lookup"><span data-stu-id="6d9e6-144">Value</span></span>|<span data-ttu-id="6d9e6-145">Description</span><span class="sxs-lookup"><span data-stu-id="6d9e6-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6d9e6-146">Énumération</span><span class="sxs-lookup"><span data-stu-id="6d9e6-146">Enumeration</span></span>|<span data-ttu-id="6d9e6-147">Une des valeurs suivantes : `NoCheck`, `Online` et `Offline`.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-147">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="6d9e6-148">Par défaut, il s’agit de `Online`.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-148">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="6d9e6-149">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6d9e6-149">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="6d9e6-150">trustedStoreLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="6d9e6-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="6d9e6-151">Valeur</span><span class="sxs-lookup"><span data-stu-id="6d9e6-151">Value</span></span>|<span data-ttu-id="6d9e6-152">Description</span><span class="sxs-lookup"><span data-stu-id="6d9e6-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6d9e6-153">Énumération</span><span class="sxs-lookup"><span data-stu-id="6d9e6-153">Enumeration</span></span>|<span data-ttu-id="6d9e6-154">Une des valeurs suivantes : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-154">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="6d9e6-155">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-155">The default is `CurrentUser`.</span></span> <span data-ttu-id="6d9e6-156">Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-156">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="6d9e6-157">Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-157">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="6d9e6-158">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-158">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d9e6-159">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6d9e6-159">Child Elements</span></span>  
 <span data-ttu-id="6d9e6-160">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d9e6-161">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6d9e6-161">Parent Elements</span></span>  
  
|<span data-ttu-id="6d9e6-162">Élément</span><span class="sxs-lookup"><span data-stu-id="6d9e6-162">Element</span></span>|<span data-ttu-id="6d9e6-163">Description</span><span class="sxs-lookup"><span data-stu-id="6d9e6-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6d9e6-164">\<peer></span><span class="sxs-lookup"><span data-stu-id="6d9e6-164">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="6d9e6-165">Spécifie une information d'identification utilisée pour authentifier le client auprès d'un service homologue.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-165">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d9e6-166">Notes</span><span class="sxs-lookup"><span data-stu-id="6d9e6-166">Remarks</span></span>  
 <span data-ttu-id="6d9e6-167">Cet élément doit être configuré si l'authentification des messages est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-167">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="6d9e6-168">Pour les canaux de sortie, chaque message est signé à l’aide du certificat fourni par [ \<le certificat >](certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="6d9e6-168">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="6d9e6-169">Avant d'être remis à l'application, tous les messages sont vérifiés par rapport aux informations d'identification de message à l'aide du validateur spécifié par l'attribut `customCertificateValidatorType` de cet élément.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-169">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="6d9e6-170">Le validateur peut accepter ou rejeter les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-170">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d9e6-171">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d9e6-171">Example</span></span>  
 <span data-ttu-id="6d9e6-172">Les jeux de codes suivants affectent le mode de validation de l’expéditeur du message à `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="6d9e6-172">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6d9e6-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d9e6-173">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="6d9e6-174">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="6d9e6-174">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="6d9e6-175">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="6d9e6-175">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="6d9e6-176">[canal homologue l’authentification des messages](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6d9e6-176">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="6d9e6-177">[canal homologue l’authentification personnalisée](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6d9e6-177">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="6d9e6-178">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="6d9e6-178">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)

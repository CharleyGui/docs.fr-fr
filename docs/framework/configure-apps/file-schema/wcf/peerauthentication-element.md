---
title: Élément <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4c29c84a2cc56a890c8273e410ba31b5f3900732
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400080"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="13340-102">\<peerAuthentication >, élément</span><span class="sxs-lookup"><span data-stu-id="13340-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="13340-103">Spécifie les options d'authentification pour les clients du réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="13340-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="13340-104">Pour plus d’informations sur la programmation d’égal à égal, consultez [mise en réseau pair à pair](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="13340-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
<span data-ttu-id="13340-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="13340-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="13340-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="13340-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="13340-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="13340-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="13340-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="13340-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="13340-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="13340-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="13340-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="13340-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="13340-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> homologues**](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="13340-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="13340-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<peerAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="13340-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13340-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13340-113">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13340-114">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="13340-114">Attributes and Elements</span></span>  
 <span data-ttu-id="13340-115">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="13340-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13340-116">Attributs</span><span class="sxs-lookup"><span data-stu-id="13340-116">Attributes</span></span>  
  
|<span data-ttu-id="13340-117">Attribut</span><span class="sxs-lookup"><span data-stu-id="13340-117">Attribute</span></span>|<span data-ttu-id="13340-118">Description</span><span class="sxs-lookup"><span data-stu-id="13340-118">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="13340-119">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="13340-119">Optional string.</span></span> <span data-ttu-id="13340-120">Type et assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="13340-120">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="13340-121">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="13340-121">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="13340-122">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="13340-122">Optional enumeration.</span></span> <span data-ttu-id="13340-123">Spécifie l'un de trois modes utilisés pour valider des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="13340-123">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="13340-124">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="13340-124">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="13340-125">Par défaut, il s’agit de `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="13340-125">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="13340-126">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="13340-126">Optional enumeration.</span></span> <span data-ttu-id="13340-127">Un des modes utilisés pour vérifier des listes de certificat révoqués (CRL).</span><span class="sxs-lookup"><span data-stu-id="13340-127">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="13340-128">Par défaut, il s’agit de `Online`.</span><span class="sxs-lookup"><span data-stu-id="13340-128">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="13340-129">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="13340-129">Optional enumeration.</span></span> <span data-ttu-id="13340-130">L'un des deux emplacements du magasin du système : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="13340-130">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="13340-131">Cette valeur est utilisée lorsqu'un certificat de service est négocié au client.</span><span class="sxs-lookup"><span data-stu-id="13340-131">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="13340-132">La validation est effectuée par rapport au magasin de **personnes autorisées** dans l’emplacement de magasin spécifié.</span><span class="sxs-lookup"><span data-stu-id="13340-132">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="13340-133">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="13340-133">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="13340-134">customCertificateValidatorType, attribut</span><span class="sxs-lookup"><span data-stu-id="13340-134">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="13340-135">`Value`</span><span class="sxs-lookup"><span data-stu-id="13340-135">Value</span></span>|<span data-ttu-id="13340-136">Description</span><span class="sxs-lookup"><span data-stu-id="13340-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13340-137">String</span><span class="sxs-lookup"><span data-stu-id="13340-137">String</span></span>|<span data-ttu-id="13340-138">Spécifie le nom de type, l'assembly et d'autres données utilisées pour rechercher le type.</span><span class="sxs-lookup"><span data-stu-id="13340-138">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="13340-139">Au minimum, un espace de noms et un nom de type sont requis.</span><span class="sxs-lookup"><span data-stu-id="13340-139">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="13340-140">Les informations facultatives incluent : le nom de l'assembly, le numéro de version, la culture et le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="13340-140">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="13340-141">certificateValidationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="13340-141">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="13340-142">Valeur</span><span class="sxs-lookup"><span data-stu-id="13340-142">Value</span></span>|<span data-ttu-id="13340-143">Description</span><span class="sxs-lookup"><span data-stu-id="13340-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13340-144">Énumération</span><span class="sxs-lookup"><span data-stu-id="13340-144">Enumeration</span></span>|<span data-ttu-id="13340-145">Une des valeurs suivantes : `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust` et `Custom`.</span><span class="sxs-lookup"><span data-stu-id="13340-145">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="13340-146">Par défaut, il s’agit de `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="13340-146">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="13340-147">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="13340-147">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="13340-148">revocationMode, attribut</span><span class="sxs-lookup"><span data-stu-id="13340-148">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="13340-149">`Value`</span><span class="sxs-lookup"><span data-stu-id="13340-149">Value</span></span>|<span data-ttu-id="13340-150">Description</span><span class="sxs-lookup"><span data-stu-id="13340-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13340-151">Énumération</span><span class="sxs-lookup"><span data-stu-id="13340-151">Enumeration</span></span>|<span data-ttu-id="13340-152">Une des valeurs suivantes : `NoCheck`, `Online` et `Offline`.</span><span class="sxs-lookup"><span data-stu-id="13340-152">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="13340-153">Par défaut, il s’agit de `Online`.</span><span class="sxs-lookup"><span data-stu-id="13340-153">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="13340-154">Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="13340-154">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="13340-155">trustedStoreLocation, attribut</span><span class="sxs-lookup"><span data-stu-id="13340-155">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="13340-156">Valeur</span><span class="sxs-lookup"><span data-stu-id="13340-156">Value</span></span>|<span data-ttu-id="13340-157">Description</span><span class="sxs-lookup"><span data-stu-id="13340-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="13340-158">Énumération</span><span class="sxs-lookup"><span data-stu-id="13340-158">Enumeration</span></span>|<span data-ttu-id="13340-159">Une des valeurs suivantes : `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="13340-159">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="13340-160">Par défaut, il s’agit de `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="13340-160">The default is `CurrentUser`.</span></span> <span data-ttu-id="13340-161">Si l'application cliente s'exécute sous un compte système, le certificat se trouve généralement dans `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="13340-161">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="13340-162">Si l'application cliente s'exécute sous un compte d'utilisateur, le certificat se trouve généralement dans `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="13340-162">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13340-163">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="13340-163">Child Elements</span></span>  
 <span data-ttu-id="13340-164">Aucun.</span><span class="sxs-lookup"><span data-stu-id="13340-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13340-165">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="13340-165">Parent Elements</span></span>  
  
|<span data-ttu-id="13340-166">Élément</span><span class="sxs-lookup"><span data-stu-id="13340-166">Element</span></span>|<span data-ttu-id="13340-167">Description</span><span class="sxs-lookup"><span data-stu-id="13340-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13340-168">\<peer></span><span class="sxs-lookup"><span data-stu-id="13340-168">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="13340-169">Spécifie une information d'identification utilisée pour authentifier le client auprès d'un service homologue.</span><span class="sxs-lookup"><span data-stu-id="13340-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13340-170">Notes</span><span class="sxs-lookup"><span data-stu-id="13340-170">Remarks</span></span>  
 <span data-ttu-id="13340-171">L'élément `<authentication>` correspond à la classe <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>.</span><span class="sxs-lookup"><span data-stu-id="13340-171">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="13340-172">Cet élément spécifie un validateur, appelé pendant l'authentification de voisins dans la maille.</span><span class="sxs-lookup"><span data-stu-id="13340-172">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="13340-173">Lorsqu'un nouvel homologue essaie d'établir une connexion avec un voisin, il transmet ses propres informations d'identification à l'homologue répondant.</span><span class="sxs-lookup"><span data-stu-id="13340-173">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="13340-174">Le validateur du répondeur est appelé pour vérifier les informations d'identification du tiers distant.</span><span class="sxs-lookup"><span data-stu-id="13340-174">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="13340-175">Chaque fois qu'une connexion est établie avec un homologue de la maille, les deux homologues sont authentifiés mutuellement, ce qui signifie que des validateurs sont appelés à chaque extrémité.</span><span class="sxs-lookup"><span data-stu-id="13340-175">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13340-176">Exemple</span><span class="sxs-lookup"><span data-stu-id="13340-176">Example</span></span>  
 <span data-ttu-id="13340-177">Le code suivant affecte la valeur `PeerOrChainTrust` au mode de validation du certificat.</span><span class="sxs-lookup"><span data-stu-id="13340-177">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <peerAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="13340-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13340-178">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="13340-179">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="13340-179">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="13340-180">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="13340-180">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="13340-181">[canal homologue l’authentification des messages](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="13340-181">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="13340-182">[canal homologue l’authentification personnalisée](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="13340-182">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="13340-183">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="13340-183">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)

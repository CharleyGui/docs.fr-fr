---
title: Élément <certificate>
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: 0594f04ab17a9561e895efcc92e97c16e77c0a4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926205"
---
# <a name="certificate-element"></a><span data-ttu-id="1f798-102">\<Élément de > du certificat</span><span class="sxs-lookup"><span data-stu-id="1f798-102">\<certificate> Element</span></span>
<span data-ttu-id="1f798-103">Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les clients de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="1f798-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="1f798-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1f798-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1f798-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="1f798-105">\<behaviors></span></span>  
<span data-ttu-id="1f798-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="1f798-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="1f798-107">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="1f798-107">\<behavior></span></span>  
<span data-ttu-id="1f798-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="1f798-108">\<clientCredentials></span></span>  
<span data-ttu-id="1f798-109">\<> homologues</span><span class="sxs-lookup"><span data-stu-id="1f798-109">\<peer></span></span>  
<span data-ttu-id="1f798-110">\<certificate></span><span class="sxs-lookup"><span data-stu-id="1f798-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f798-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f798-111">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f798-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1f798-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1f798-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1f798-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f798-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="1f798-114">Attributes</span></span>  
  
|<span data-ttu-id="1f798-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="1f798-115">Attribute</span></span>|<span data-ttu-id="1f798-116">Description</span><span class="sxs-lookup"><span data-stu-id="1f798-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="1f798-117">Chaîne qui contient la valeur à rechercher dans le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="1f798-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="1f798-118">Le type contenu dans l’attribut doit répondre aux exigences du `x509FindType` spécifié.</span><span class="sxs-lookup"><span data-stu-id="1f798-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="1f798-119">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="1f798-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="1f798-120">Indique l'emplacement du magasin de certificats X.509 utilisé par le client pour valider le certificat de l'homologue.</span><span class="sxs-lookup"><span data-stu-id="1f798-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="1f798-121">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="1f798-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1f798-122">-LocalMachine: magasin de certificats attribué à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="1f798-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="1f798-123">-CurrentUser: magasin de certificats attribué à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="1f798-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="1f798-124">La valeur par défaut est LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="1f798-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="1f798-125">Spécifie le nom du magasin de certificats X.509 à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="1f798-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="1f798-126">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="1f798-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1f798-127">Carnet Magasin de certificats pour d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="1f798-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="1f798-128">-   AuthRoot: Magasin de certificats pour les autorités de certification tierces.</span><span class="sxs-lookup"><span data-stu-id="1f798-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="1f798-129">CertificateAuthority Magasin de certificats pour les autorités de certification (ca) intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="1f798-129">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="1f798-130">Interdits Magasin de certificats pour les certificats révoqués.</span><span class="sxs-lookup"><span data-stu-id="1f798-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="1f798-131">M' Magasin de certificats pour les certificats personnels.</span><span class="sxs-lookup"><span data-stu-id="1f798-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="1f798-132">Causes Magasin de certificats pour les autorités de certification racines de confiance (ca).</span><span class="sxs-lookup"><span data-stu-id="1f798-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="1f798-133">TrustedPeople Magasin de certificats pour les personnes et les ressources directement approuvées.</span><span class="sxs-lookup"><span data-stu-id="1f798-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="1f798-134">TrustedPublisher Magasin de certificats pour les éditeurs directement approuvés.</span><span class="sxs-lookup"><span data-stu-id="1f798-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="1f798-135">La valeur par défaut est My.</span><span class="sxs-lookup"><span data-stu-id="1f798-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="1f798-136">Définit le type de recherche X.509 à exécuter.</span><span class="sxs-lookup"><span data-stu-id="1f798-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="1f798-137">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="1f798-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1f798-138">-   FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="1f798-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="1f798-139">-   FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="1f798-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="1f798-140">-   FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="1f798-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="1f798-141">-   FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="1f798-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="1f798-142">-   FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="1f798-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="1f798-143">-   FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="1f798-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="1f798-144">-   FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="1f798-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="1f798-145">-   FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="1f798-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="1f798-146">-   FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="1f798-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="1f798-147">-   FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="1f798-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="1f798-148">-   FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="1f798-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="1f798-149">-   FindByExtension</span><span class="sxs-lookup"><span data-stu-id="1f798-149">-   FindByExtension</span></span><br /><span data-ttu-id="1f798-150">-   FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="1f798-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="1f798-151">-   FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="1f798-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="1f798-152">Le type contenu dans l'attribut `findValue` doit répondre aux spécifications du `X509FindType` spécifié.</span><span class="sxs-lookup"><span data-stu-id="1f798-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="1f798-153">La valeur par défaut est FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="1f798-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f798-154">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1f798-154">Child Elements</span></span>  
 <span data-ttu-id="1f798-155">Aucun.</span><span class="sxs-lookup"><span data-stu-id="1f798-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f798-156">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1f798-156">Parent Elements</span></span>  
  
|<span data-ttu-id="1f798-157">Élément</span><span class="sxs-lookup"><span data-stu-id="1f798-157">Element</span></span>|<span data-ttu-id="1f798-158">Description</span><span class="sxs-lookup"><span data-stu-id="1f798-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f798-159">\<peer></span><span class="sxs-lookup"><span data-stu-id="1f798-159">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="1f798-160">Spécifie les informations d'identification utilisées lors de l'authentification de clients de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="1f798-160">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f798-161">Notes</span><span class="sxs-lookup"><span data-stu-id="1f798-161">Remarks</span></span>  
 <span data-ttu-id="1f798-162">Cet élément de configuration contient une instance de X509Certificate2 utilisée lors de l'authentification de voisins dans la maille d'homologues.</span><span class="sxs-lookup"><span data-stu-id="1f798-162">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="1f798-163">Pour plus d’informations sur la programmation d’égal à égal, consultez [mise en réseau pair à pair](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="1f798-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f798-164">Exemple</span><span class="sxs-lookup"><span data-stu-id="1f798-164">Example</span></span>  
 <span data-ttu-id="1f798-165">Le code suivant spécifie comment rechercher le certificat utilisé dans un scénario de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="1f798-165">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="1f798-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f798-166">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="1f798-167">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="1f798-167">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="1f798-168">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="1f798-168">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="1f798-169">[canal homologue l’authentification des messages](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1f798-169">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="1f798-170">[canal homologue l’authentification personnalisée](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1f798-170">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="1f798-171">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="1f798-171">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)

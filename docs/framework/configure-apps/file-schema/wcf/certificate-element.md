---
title: Élément <certificate>
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: e28e7d16073a56f3b6126439644bfff86c9af18b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400553"
---
# <a name="certificate-element"></a><span data-ttu-id="7499a-102">\<Élément de > du certificat</span><span class="sxs-lookup"><span data-stu-id="7499a-102">\<certificate> Element</span></span>
<span data-ttu-id="7499a-103">Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les clients de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="7499a-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
<span data-ttu-id="7499a-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7499a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7499a-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7499a-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7499a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7499a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="7499a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7499a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="7499a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7499a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="7499a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="7499a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="7499a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> homologues**](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="7499a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="7499a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de certificat**</span><span class="sxs-lookup"><span data-stu-id="7499a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7499a-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7499a-112">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7499a-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7499a-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7499a-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7499a-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7499a-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="7499a-115">Attributes</span></span>  
  
|<span data-ttu-id="7499a-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="7499a-116">Attribute</span></span>|<span data-ttu-id="7499a-117">Description</span><span class="sxs-lookup"><span data-stu-id="7499a-117">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="7499a-118">Chaîne qui contient la valeur à rechercher dans le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="7499a-118">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="7499a-119">Le type contenu dans l’attribut doit répondre aux exigences du `x509FindType` spécifié.</span><span class="sxs-lookup"><span data-stu-id="7499a-119">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="7499a-120">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="7499a-120">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="7499a-121">Indique l'emplacement du magasin de certificats X.509 utilisé par le client pour valider le certificat de l'homologue.</span><span class="sxs-lookup"><span data-stu-id="7499a-121">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="7499a-122">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7499a-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7499a-123">-LocalMachine : magasin de certificats attribué à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="7499a-123">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="7499a-124">-CurrentUser : magasin de certificats attribué à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="7499a-124">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="7499a-125">La valeur par défaut est LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="7499a-125">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="7499a-126">Spécifie le nom du magasin de certificats X.509 à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="7499a-126">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="7499a-127">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7499a-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7499a-128">Carnet Magasin de certificats pour d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="7499a-128">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="7499a-129">-   AuthRoot: Magasin de certificats pour les autorités de certification tierces.</span><span class="sxs-lookup"><span data-stu-id="7499a-129">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="7499a-130">CertificateAuthority Magasin de certificats pour les autorités de certification (ca) intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="7499a-130">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="7499a-131">Interdits Magasin de certificats pour les certificats révoqués.</span><span class="sxs-lookup"><span data-stu-id="7499a-131">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="7499a-132">M' Magasin de certificats pour les certificats personnels.</span><span class="sxs-lookup"><span data-stu-id="7499a-132">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="7499a-133">Causes Magasin de certificats pour les autorités de certification racines de confiance (ca).</span><span class="sxs-lookup"><span data-stu-id="7499a-133">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="7499a-134">TrustedPeople Magasin de certificats pour les personnes et les ressources directement approuvées.</span><span class="sxs-lookup"><span data-stu-id="7499a-134">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="7499a-135">TrustedPublisher Magasin de certificats pour les éditeurs directement approuvés.</span><span class="sxs-lookup"><span data-stu-id="7499a-135">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="7499a-136">La valeur par défaut est My.</span><span class="sxs-lookup"><span data-stu-id="7499a-136">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="7499a-137">Définit le type de recherche X.509 à exécuter.</span><span class="sxs-lookup"><span data-stu-id="7499a-137">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="7499a-138">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7499a-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7499a-139">-   FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="7499a-139">-   FindByThumbPrint</span></span><br /><span data-ttu-id="7499a-140">-   FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="7499a-140">-   FindBySubjectName</span></span><br /><span data-ttu-id="7499a-141">-   FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="7499a-141">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="7499a-142">-   FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="7499a-142">-   FindByIssuerName</span></span><br /><span data-ttu-id="7499a-143">-   FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="7499a-143">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="7499a-144">-   FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="7499a-144">-   FindBySerialNumber</span></span><br /><span data-ttu-id="7499a-145">-   FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="7499a-145">-   FindByTimeValid</span></span><br /><span data-ttu-id="7499a-146">-   FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="7499a-146">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="7499a-147">-   FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="7499a-147">-   FindByTemplateName</span></span><br /><span data-ttu-id="7499a-148">-   FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="7499a-148">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="7499a-149">-   FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="7499a-149">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="7499a-150">-   FindByExtension</span><span class="sxs-lookup"><span data-stu-id="7499a-150">-   FindByExtension</span></span><br /><span data-ttu-id="7499a-151">-   FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="7499a-151">-   FindByKeyUsage</span></span><br /><span data-ttu-id="7499a-152">-   FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="7499a-152">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="7499a-153">Le type contenu dans l'attribut `findValue` doit répondre aux spécifications du `X509FindType` spécifié.</span><span class="sxs-lookup"><span data-stu-id="7499a-153">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="7499a-154">La valeur par défaut est FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="7499a-154">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7499a-155">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7499a-155">Child Elements</span></span>  
 <span data-ttu-id="7499a-156">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7499a-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7499a-157">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7499a-157">Parent Elements</span></span>  
  
|<span data-ttu-id="7499a-158">Élément</span><span class="sxs-lookup"><span data-stu-id="7499a-158">Element</span></span>|<span data-ttu-id="7499a-159">Description</span><span class="sxs-lookup"><span data-stu-id="7499a-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7499a-160">\<peer></span><span class="sxs-lookup"><span data-stu-id="7499a-160">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="7499a-161">Spécifie les informations d'identification utilisées lors de l'authentification de clients de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="7499a-161">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7499a-162">Notes</span><span class="sxs-lookup"><span data-stu-id="7499a-162">Remarks</span></span>  
 <span data-ttu-id="7499a-163">Cet élément de configuration contient une instance de X509Certificate2 utilisée lors de l'authentification de voisins dans la maille d'homologues.</span><span class="sxs-lookup"><span data-stu-id="7499a-163">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="7499a-164">Pour plus d’informations sur la programmation d’égal à égal, consultez [mise en réseau pair à pair](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="7499a-164">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7499a-165">Exemples</span><span class="sxs-lookup"><span data-stu-id="7499a-165">Example</span></span>  
 <span data-ttu-id="7499a-166">Le code suivant spécifie comment rechercher le certificat utilisé dans un scénario de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="7499a-166">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7499a-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7499a-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="7499a-168">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="7499a-168">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="7499a-169">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="7499a-169">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="7499a-170">[canal homologue l’authentification des messages](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7499a-170">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="7499a-171">[canal homologue l’authentification personnalisée](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7499a-171">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="7499a-172">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="7499a-172">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)

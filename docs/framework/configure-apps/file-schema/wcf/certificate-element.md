---
title: Élément <certificate>
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: 8cc0404a5896dd23cffce6f1f77b91a2f01f23d2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151088"
---
# <a name="certificate-element"></a><span data-ttu-id="bf948-102">Élément \<certificate></span><span class="sxs-lookup"><span data-stu-id="bf948-102">\<certificate> Element</span></span>

<span data-ttu-id="bf948-103">Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les clients de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="bf948-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="bf948-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf948-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf948-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="bf948-105">Attributes and Elements</span></span>  

 <span data-ttu-id="bf948-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="bf948-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf948-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="bf948-107">Attributes</span></span>  
  
|<span data-ttu-id="bf948-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="bf948-108">Attribute</span></span>|<span data-ttu-id="bf948-109">Description</span><span class="sxs-lookup"><span data-stu-id="bf948-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="bf948-110">Chaîne qui contient la valeur à rechercher dans le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="bf948-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="bf948-111">Le type contenu dans l’attribut doit répondre aux exigences du `x509FindType` spécifié.</span><span class="sxs-lookup"><span data-stu-id="bf948-111">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="bf948-112">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="bf948-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="bf948-113">Indique l'emplacement du magasin de certificats X.509 utilisé par le client pour valider le certificat de l'homologue.</span><span class="sxs-lookup"><span data-stu-id="bf948-113">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="bf948-114">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf948-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bf948-115">-LocalMachine : magasin de certificats attribué à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="bf948-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="bf948-116">-CurrentUser : magasin de certificats attribué à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="bf948-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="bf948-117">La valeur par défaut est LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="bf948-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="bf948-118">Spécifie le nom du magasin de certificats X.509 à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="bf948-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="bf948-119">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf948-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bf948-120">-AddressBook : magasin de certificats pour d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="bf948-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="bf948-121">-AuthRoot : magasin de certificats pour les autorités de certification tierces.</span><span class="sxs-lookup"><span data-stu-id="bf948-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="bf948-122">-CertificateAuthority : magasin de certificats pour les autorités de certification intermédiaires (ca).</span><span class="sxs-lookup"><span data-stu-id="bf948-122">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="bf948-123">-Non autorisé : magasin de certificats pour les certificats révoqués.</span><span class="sxs-lookup"><span data-stu-id="bf948-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="bf948-124">-My : magasin de certificats pour les certificats personnels.</span><span class="sxs-lookup"><span data-stu-id="bf948-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="bf948-125">-Root : magasin de certificats pour les autorités de certification racines de confiance.</span><span class="sxs-lookup"><span data-stu-id="bf948-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="bf948-126">-TrustedPeople : magasin de certificats pour les personnes et les ressources directement approuvées.</span><span class="sxs-lookup"><span data-stu-id="bf948-126">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="bf948-127">-TrustedPublisher : magasin de certificats pour les éditeurs directement approuvés.</span><span class="sxs-lookup"><span data-stu-id="bf948-127">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="bf948-128">La valeur par défaut est My.</span><span class="sxs-lookup"><span data-stu-id="bf948-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="bf948-129">Définit le type de recherche X.509 à exécuter.</span><span class="sxs-lookup"><span data-stu-id="bf948-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="bf948-130">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf948-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="bf948-131">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="bf948-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="bf948-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="bf948-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="bf948-133">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="bf948-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="bf948-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="bf948-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="bf948-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="bf948-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="bf948-136">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="bf948-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="bf948-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="bf948-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="bf948-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="bf948-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="bf948-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="bf948-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="bf948-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="bf948-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="bf948-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="bf948-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="bf948-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="bf948-142">-   FindByExtension</span></span><br /><span data-ttu-id="bf948-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="bf948-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="bf948-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="bf948-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="bf948-145">Le type contenu dans l'attribut `findValue` doit répondre aux spécifications du `X509FindType` spécifié.</span><span class="sxs-lookup"><span data-stu-id="bf948-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="bf948-146">La valeur par défaut est FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="bf948-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf948-147">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="bf948-147">Child Elements</span></span>  

 <span data-ttu-id="bf948-148">Aucun.</span><span class="sxs-lookup"><span data-stu-id="bf948-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf948-149">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="bf948-149">Parent Elements</span></span>  
  
|<span data-ttu-id="bf948-150">Élément</span><span class="sxs-lookup"><span data-stu-id="bf948-150">Element</span></span>|<span data-ttu-id="bf948-151">Description</span><span class="sxs-lookup"><span data-stu-id="bf948-151">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="bf948-152">Spécifie les informations d'identification utilisées lors de l'authentification de clients de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="bf948-152">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf948-153">Notes</span><span class="sxs-lookup"><span data-stu-id="bf948-153">Remarks</span></span>  

 <span data-ttu-id="bf948-154">Cet élément de configuration contient une instance de X509Certificate2 utilisée lors de l'authentification de voisins dans la maille d'homologues.</span><span class="sxs-lookup"><span data-stu-id="bf948-154">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="bf948-155">Pour plus d’informations sur la programmation d’égal à égal, consultez [mise en réseau pair à pair](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="bf948-155">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf948-156">Exemple</span><span class="sxs-lookup"><span data-stu-id="bf948-156">Example</span></span>  

 <span data-ttu-id="bf948-157">Le code suivant spécifie comment rechercher le certificat utilisé dans un scénario de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="bf948-157">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf948-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf948-158">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="bf948-159">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="bf948-159">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="bf948-160">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="bf948-160">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="bf948-161">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bf948-161">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="bf948-162">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bf948-162">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="bf948-163">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="bf948-163">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)

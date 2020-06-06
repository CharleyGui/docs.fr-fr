---
title: Élément <certificate>
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: e28e7d16073a56f3b6126439644bfff86c9af18b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400553"
---
# <a name="certificate-element"></a><span data-ttu-id="e7105-102">Élément \<certificate></span><span class="sxs-lookup"><span data-stu-id="e7105-102">\<certificate> Element</span></span>
<span data-ttu-id="e7105-103">Spécifie un certificat X.509 à utiliser pour signer et chiffrer des messages pour les clients de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="e7105-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="e7105-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7105-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7105-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e7105-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e7105-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e7105-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7105-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="e7105-107">Attributes</span></span>  
  
|<span data-ttu-id="e7105-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="e7105-108">Attribute</span></span>|<span data-ttu-id="e7105-109">Description</span><span class="sxs-lookup"><span data-stu-id="e7105-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="e7105-110">Chaîne qui contient la valeur à rechercher dans le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="e7105-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="e7105-111">Le type contenu dans l’attribut doit répondre aux exigences du `x509FindType` spécifié.</span><span class="sxs-lookup"><span data-stu-id="e7105-111">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="e7105-112">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="e7105-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="e7105-113">Indique l'emplacement du magasin de certificats X.509 utilisé par le client pour valider le certificat de l'homologue.</span><span class="sxs-lookup"><span data-stu-id="e7105-113">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="e7105-114">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e7105-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e7105-115">-LocalMachine : magasin de certificats attribué à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="e7105-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="e7105-116">-CurrentUser : magasin de certificats attribué à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="e7105-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="e7105-117">La valeur par défaut est LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="e7105-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="e7105-118">Spécifie le nom du magasin de certificats X.509 à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="e7105-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="e7105-119">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e7105-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e7105-120">-AddressBook : magasin de certificats pour d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="e7105-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="e7105-121">-AuthRoot : magasin de certificats pour les autorités de certification tierces.</span><span class="sxs-lookup"><span data-stu-id="e7105-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="e7105-122">-CertificateAuthority : magasin de certificats pour les autorités de certification intermédiaires (ca).</span><span class="sxs-lookup"><span data-stu-id="e7105-122">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="e7105-123">-Non autorisé : magasin de certificats pour les certificats révoqués.</span><span class="sxs-lookup"><span data-stu-id="e7105-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="e7105-124">-My : magasin de certificats pour les certificats personnels.</span><span class="sxs-lookup"><span data-stu-id="e7105-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="e7105-125">-Root : magasin de certificats pour les autorités de certification racines de confiance.</span><span class="sxs-lookup"><span data-stu-id="e7105-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="e7105-126">-TrustedPeople : magasin de certificats pour les personnes et les ressources directement approuvées.</span><span class="sxs-lookup"><span data-stu-id="e7105-126">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="e7105-127">-TrustedPublisher : magasin de certificats pour les éditeurs directement approuvés.</span><span class="sxs-lookup"><span data-stu-id="e7105-127">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="e7105-128">La valeur par défaut est My.</span><span class="sxs-lookup"><span data-stu-id="e7105-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="e7105-129">Définit le type de recherche X.509 à exécuter.</span><span class="sxs-lookup"><span data-stu-id="e7105-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="e7105-130">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="e7105-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e7105-131">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="e7105-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="e7105-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="e7105-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="e7105-133">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="e7105-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="e7105-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="e7105-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="e7105-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="e7105-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="e7105-136">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="e7105-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="e7105-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="e7105-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="e7105-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="e7105-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="e7105-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="e7105-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="e7105-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="e7105-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="e7105-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="e7105-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="e7105-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="e7105-142">-   FindByExtension</span></span><br /><span data-ttu-id="e7105-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="e7105-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="e7105-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="e7105-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="e7105-145">Le type contenu dans l'attribut `findValue` doit répondre aux spécifications du `X509FindType` spécifié.</span><span class="sxs-lookup"><span data-stu-id="e7105-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="e7105-146">La valeur par défaut est FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="e7105-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7105-147">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e7105-147">Child Elements</span></span>  
 <span data-ttu-id="e7105-148">Aucun.</span><span class="sxs-lookup"><span data-stu-id="e7105-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e7105-149">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e7105-149">Parent Elements</span></span>  
  
|<span data-ttu-id="e7105-150">Élément</span><span class="sxs-lookup"><span data-stu-id="e7105-150">Element</span></span>|<span data-ttu-id="e7105-151">Description</span><span class="sxs-lookup"><span data-stu-id="e7105-151">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="e7105-152">Spécifie les informations d'identification utilisées lors de l'authentification de clients de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="e7105-152">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7105-153">Remarques</span><span class="sxs-lookup"><span data-stu-id="e7105-153">Remarks</span></span>  
 <span data-ttu-id="e7105-154">Cet élément de configuration contient une instance de X509Certificate2 utilisée lors de l'authentification de voisins dans la maille d'homologues.</span><span class="sxs-lookup"><span data-stu-id="e7105-154">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="e7105-155">Pour plus d’informations sur la programmation d’égal à égal, consultez [mise en réseau pair à pair](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="e7105-155">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7105-156">Exemple</span><span class="sxs-lookup"><span data-stu-id="e7105-156">Example</span></span>  
 <span data-ttu-id="e7105-157">Le code suivant spécifie comment rechercher le certificat utilisé dans un scénario de réseau pair à pair.</span><span class="sxs-lookup"><span data-stu-id="e7105-157">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e7105-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7105-158">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="e7105-159">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="e7105-159">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="e7105-160">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="e7105-160">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="e7105-161">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e7105-161">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="e7105-162">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e7105-162">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="e7105-163">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="e7105-163">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)

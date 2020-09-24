---
title: <certificate> d' <clientCertificate> élément
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: 35ea3814e208921abaf44e6ef431c4e1b44cde60
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151139"
---
# <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="70e4a-102">\<certificate> d' \<clientCertificate> élément</span><span class="sxs-lookup"><span data-stu-id="70e4a-102">\<certificate> of \<clientCertificate> Element</span></span>

<span data-ttu-id="70e4a-103">Spécifie un certificat X.509 utilisé pour signer et chiffrer des messages.</span><span class="sxs-lookup"><span data-stu-id="70e4a-103">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="70e4a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70e4a-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70e4a-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="70e4a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="70e4a-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="70e4a-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70e4a-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="70e4a-107">Attributes</span></span>  
  
|<span data-ttu-id="70e4a-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="70e4a-108">Attribute</span></span>|<span data-ttu-id="70e4a-109">Description</span><span class="sxs-lookup"><span data-stu-id="70e4a-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="70e4a-110">Chaîne qui contient la valeur à rechercher dans le magasin de certificats X.509.</span><span class="sxs-lookup"><span data-stu-id="70e4a-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="70e4a-111">Le type contenu dans l'attribut doit satisfaire les spécifications du X509FindType spécifié.</span><span class="sxs-lookup"><span data-stu-id="70e4a-111">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="70e4a-112">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="70e4a-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="70e4a-113">Spécifie l'emplacement du magasin de certificats X.509 que le client utilise pour valider le certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="70e4a-113">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="70e4a-114">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="70e4a-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="70e4a-115">-LocalMachine : magasin de certificats attribué à l’ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="70e4a-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="70e4a-116">-CurrentUser : magasin de certificats attribué à l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="70e4a-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="70e4a-117">La valeur par défaut est LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="70e4a-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="70e4a-118">Spécifie le nom du magasin de certificats X.509 à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="70e4a-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="70e4a-119">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="70e4a-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="70e4a-120">-AddressBook : magasin de certificats pour d’autres utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="70e4a-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="70e4a-121">-AuthRoot : magasin de certificats pour les autorités de certification tierces.</span><span class="sxs-lookup"><span data-stu-id="70e4a-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="70e4a-122">-CertificationAuthority : magasin de certificats pour les autorités de certification intermédiaires (ca).</span><span class="sxs-lookup"><span data-stu-id="70e4a-122">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="70e4a-123">-Non autorisé : magasin de certificats pour les certificats révoqués.</span><span class="sxs-lookup"><span data-stu-id="70e4a-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="70e4a-124">-My : magasin de certificats pour les certificats personnels.</span><span class="sxs-lookup"><span data-stu-id="70e4a-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="70e4a-125">-Root : magasin de certificats pour les autorités de certification racines de confiance.</span><span class="sxs-lookup"><span data-stu-id="70e4a-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="70e4a-126">-TrustedPeople : magasin de certificats pour les personnes et les ressources directement approuvées.</span><span class="sxs-lookup"><span data-stu-id="70e4a-126">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="70e4a-127">-TrustedPublisher : magasin de certificats pour les éditeurs directement approuvés.</span><span class="sxs-lookup"><span data-stu-id="70e4a-127">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="70e4a-128">La valeur par défaut est My.</span><span class="sxs-lookup"><span data-stu-id="70e4a-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="70e4a-129">Définit le type de recherche X.509 à exécuter.</span><span class="sxs-lookup"><span data-stu-id="70e4a-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="70e4a-130">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="70e4a-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="70e4a-131">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="70e4a-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="70e4a-132">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="70e4a-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="70e4a-133">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="70e4a-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="70e4a-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="70e4a-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="70e4a-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="70e4a-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="70e4a-136">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="70e4a-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="70e4a-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="70e4a-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="70e4a-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="70e4a-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="70e4a-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="70e4a-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="70e4a-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="70e4a-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="70e4a-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="70e4a-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="70e4a-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="70e4a-142">-   FindByExtension</span></span><br /><span data-ttu-id="70e4a-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="70e4a-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="70e4a-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="70e4a-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="70e4a-145">Le type contenu dans l'attribut `findValue` doit satisfaire les spécifications du X509FindType spécifié.</span><span class="sxs-lookup"><span data-stu-id="70e4a-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="70e4a-146">La valeur par défaut est FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="70e4a-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70e4a-147">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="70e4a-147">Child Elements</span></span>  

 <span data-ttu-id="70e4a-148">Aucun.</span><span class="sxs-lookup"><span data-stu-id="70e4a-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="70e4a-149">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="70e4a-149">Parent Elements</span></span>  
  
|<span data-ttu-id="70e4a-150">Élément</span><span class="sxs-lookup"><span data-stu-id="70e4a-150">Element</span></span>|<span data-ttu-id="70e4a-151">Description</span><span class="sxs-lookup"><span data-stu-id="70e4a-151">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="70e4a-152">Notes</span><span class="sxs-lookup"><span data-stu-id="70e4a-152">Remarks</span></span>  

 <span data-ttu-id="70e4a-153">L'élément `<certificate>` est utilisé lorsque le service doit disposer du certificat du client à l'avance afin de communiquer de manière sécurisée avec le client.</span><span class="sxs-lookup"><span data-stu-id="70e4a-153">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="70e4a-154">Cela se produit lors de l'utilisation du modèle de communication duplex.</span><span class="sxs-lookup"><span data-stu-id="70e4a-154">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="70e4a-155">Dans le modèle demande-réponse classique, le client inclut son certificat dans la demande que le service utilise pour sécuriser à nouveau sa réponse au client.</span><span class="sxs-lookup"><span data-stu-id="70e4a-155">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="70e4a-156">Dans le modèle de communication duplex, toutefois, le service ne dispose pas de demande du client et, par conséquent, requiert le certificat du client à l'avance pour sécuriser l'envoi du message au client.</span><span class="sxs-lookup"><span data-stu-id="70e4a-156">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="70e4a-157">C'est pourquoi vous devez obtenir le certificat du client dans une négociation hors bande et l'indiquer à l'aide de cet élément.</span><span class="sxs-lookup"><span data-stu-id="70e4a-157">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="70e4a-158">Pour plus d’informations sur les services duplex, consultez [Comment : créer un contrat duplex](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="70e4a-158">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="70e4a-159">Exemple</span><span class="sxs-lookup"><span data-stu-id="70e4a-159">Example</span></span>  

 <span data-ttu-id="70e4a-160">Le code suivant indique comment rechercher un certificat X.509 approprié ainsi qu’un type de validation personnalisé dans l’élément `<authentication>`.</span><span class="sxs-lookup"><span data-stu-id="70e4a-160">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="70e4a-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70e4a-161">See also</span></span>

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [<span data-ttu-id="70e4a-162">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="70e4a-162">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="70e4a-163">Procédure : créer un service qui utilise un validateur de certificat personnalisé</span><span class="sxs-lookup"><span data-stu-id="70e4a-163">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="70e4a-164">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="70e4a-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)

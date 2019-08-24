---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 262ac9be6d5ce6466cf9aff33c0c2791c0e149dd
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988382"
---
# <a name="identity"></a><span data-ttu-id="912a8-101">\<identity></span><span class="sxs-lookup"><span data-stu-id="912a8-101">\<identity></span></span>
<span data-ttu-id="912a8-102">L'élément d'identité autorise un développeur client à spécifier au moment de la conception l'identité attendue du service.</span><span class="sxs-lookup"><span data-stu-id="912a8-102">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="912a8-103">Dans le processus d’établissement de liaison entre le client et le service, l’infrastructure Windows Communication Foundation (WCF) garantit que l’identité du service attendu correspond aux valeurs de cet élément et peut donc être authentifiée.</span><span class="sxs-lookup"><span data-stu-id="912a8-103">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="912a8-104">Pour plus d’informations, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="912a8-104">For more information, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="912a8-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="912a8-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="912a8-106">\<client></span><span class="sxs-lookup"><span data-stu-id="912a8-106">\<client></span></span>  
<span data-ttu-id="912a8-107">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="912a8-107">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="912a8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="912a8-108">Syntax</span></span>  
  
```xml  
<identity>
  <certificate encodedValue="String" />
  <certificateReference findValue="String"
                        isChainIncluded="Boolean"
                        storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                        storeLocation="LocalMachine/CurrentUser"
                        X509FindType="Enumeration" />
  <dns value="String" />
  <rsa value="String" />
  <servicePrincipalName value="String" />
  <userPrincipalName value="String" />
</identity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="912a8-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="912a8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="912a8-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="912a8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="912a8-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="912a8-111">Attributes</span></span>  
 <span data-ttu-id="912a8-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="912a8-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="912a8-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="912a8-113">Child Elements</span></span>  
  
|<span data-ttu-id="912a8-114">Élément</span><span class="sxs-lookup"><span data-stu-id="912a8-114">Element</span></span>|<span data-ttu-id="912a8-115">Description</span><span class="sxs-lookup"><span data-stu-id="912a8-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="912a8-116">certificate</span><span class="sxs-lookup"><span data-stu-id="912a8-116">certificate</span></span>|<span data-ttu-id="912a8-117">Spécifie les paramètres d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="912a8-117">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="912a8-118">Cet élément est de type <xref:System.ServiceModel.Configuration.CertificateElement>.</span><span class="sxs-lookup"><span data-stu-id="912a8-118">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="912a8-119">Il contient un `encodedValue` d'attribut qui est une chaîne indiquant la valeur encodée par ce certificat.</span><span class="sxs-lookup"><span data-stu-id="912a8-119">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="912a8-120">certificateReference</span><span class="sxs-lookup"><span data-stu-id="912a8-120">certificateReference</span></span>|<span data-ttu-id="912a8-121">Spécifie les paramètres de validation du certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="912a8-121">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="912a8-122">Cet élément est de type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span><span class="sxs-lookup"><span data-stu-id="912a8-122">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="912a8-123">dns</span><span class="sxs-lookup"><span data-stu-id="912a8-123">dns</span></span>|<span data-ttu-id="912a8-124">Spécifie le système DNS d'un certificat X.509 utilisé pour authentifier un service.</span><span class="sxs-lookup"><span data-stu-id="912a8-124">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="912a8-125">Cet élément contient un attribut `value` qui est une chaîne et qui contient l'identité réelle.</span><span class="sxs-lookup"><span data-stu-id="912a8-125">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="912a8-126">rsa</span><span class="sxs-lookup"><span data-stu-id="912a8-126">rsa</span></span>|<span data-ttu-id="912a8-127">Indique la valeur du champ RSA d'un certificat X.509 utilisée pour authentifier un service au niveau d'un client.</span><span class="sxs-lookup"><span data-stu-id="912a8-127">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="912a8-128">Cet élément contient un attribut `value` qui est une chaîne et qui contient l'identité réelle.</span><span class="sxs-lookup"><span data-stu-id="912a8-128">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="912a8-129">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="912a8-129">servicePrincipalName</span></span>|<span data-ttu-id="912a8-130">Indique le nom SPN correspondant au nom principal utilisé par un client pour identifier de manière unique l'instance d'un service.</span><span class="sxs-lookup"><span data-stu-id="912a8-130">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="912a8-131">Cet élément contient un `value` d'attribut qui est une chaîne contenant le nom principal réel.</span><span class="sxs-lookup"><span data-stu-id="912a8-131">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="912a8-132">Cet élément est de type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="912a8-132">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="912a8-133">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="912a8-133">userPrincipalName</span></span>|<span data-ttu-id="912a8-134">Spécifie une identité UPN correspondant au type de nom de connexion d'un utilisateur sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="912a8-134">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="912a8-135">Le nom d’utilisateur principal est constitué du nom d’objet utilisateur utilisé dans Active Directory, suivi du symbole arobase (\@), puis, généralement, du domaine parent du système de noms de domaine.</span><span class="sxs-lookup"><span data-stu-id="912a8-135">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (\@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="912a8-136">Par exemple, Jeff dans l’arborescence de domaine Fabrikam.com peut avoir le nom [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com)d’utilisateur principal.</span><span class="sxs-lookup"><span data-stu-id="912a8-136">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).</span></span>  <span data-ttu-id="912a8-137">Cet élément contient un `value` d'attribut qui est une chaîne contenant le nom principal réel.</span><span class="sxs-lookup"><span data-stu-id="912a8-137">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="912a8-138">Cet élément est de type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="912a8-138">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="912a8-139">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="912a8-139">Parent Elements</span></span>  
  
|<span data-ttu-id="912a8-140">Élément</span><span class="sxs-lookup"><span data-stu-id="912a8-140">Element</span></span>|<span data-ttu-id="912a8-141">Description</span><span class="sxs-lookup"><span data-stu-id="912a8-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="912a8-142">\<custom></span><span class="sxs-lookup"><span data-stu-id="912a8-142">\<custom></span></span>](custom.md)|<span data-ttu-id="912a8-143">Indique le programme de résolution d'homologue personnalisé pour un netPeerTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="912a8-143">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[<span data-ttu-id="912a8-144">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="912a8-144">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="912a8-145">Configure les points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="912a8-145">Configures service endpoints.</span></span>|  
|[<span data-ttu-id="912a8-146">\<> de point \<de terminaison du > client</span><span class="sxs-lookup"><span data-stu-id="912a8-146">\<endpoint> of \<client></span></span>](endpoint-of-client.md)|<span data-ttu-id="912a8-147">Configure les points de terminaison de canal.</span><span class="sxs-lookup"><span data-stu-id="912a8-147">Configures channel endpoints.</span></span>|  
|[<span data-ttu-id="912a8-148">\<issuer></span><span class="sxs-lookup"><span data-stu-id="912a8-148">\<issuer></span></span>](issuer.md)|<span data-ttu-id="912a8-149">Spécifie le service STS pour le service fédéré.</span><span class="sxs-lookup"><span data-stu-id="912a8-149">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[<span data-ttu-id="912a8-150">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="912a8-150">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="912a8-151">Spécifie le point de terminaison de métadonnées pour le service STS d'un service fédéré.</span><span class="sxs-lookup"><span data-stu-id="912a8-151">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[<span data-ttu-id="912a8-152">\<issuedTokenParameters></span><span class="sxs-lookup"><span data-stu-id="912a8-152">\<issuedTokenParameters></span></span>](issuedtokenparameters.md)|<span data-ttu-id="912a8-153">Définit des paramètres correspondant à un jeton émis dans une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="912a8-153">Defines parameters for an issued token in a custom binding.</span></span>|  
|[<span data-ttu-id="912a8-154">\<localIssuer></span><span class="sxs-lookup"><span data-stu-id="912a8-154">\<localIssuer></span></span>](localissuer.md)|<span data-ttu-id="912a8-155">Spécifie un service STS local.</span><span class="sxs-lookup"><span data-stu-id="912a8-155">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="912a8-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="912a8-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [<span data-ttu-id="912a8-157">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="912a8-157">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="912a8-158">Terminaison Adresses, liaisons et contrats</span><span class="sxs-lookup"><span data-stu-id="912a8-158">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)

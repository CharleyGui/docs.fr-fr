---
title: <identity>
ms.date: 03/30/2017
ms.assetid: c1d2ae56-e231-4a07-9c3f-9f13381dc0d8
ms.openlocfilehash: 15c9e38a141fc294c47863b1a932711444ac079a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855154"
---
# \<identity>
<span data-ttu-id="98cb6-101">L'élément d'identité autorise un développeur client à spécifier au moment de la conception l'identité attendue du service.</span><span class="sxs-lookup"><span data-stu-id="98cb6-101">The identity element allows a client developer to specify at design time the expected identity of the service.</span></span> <span data-ttu-id="98cb6-102">Dans le processus d’établissement de liaison entre le client et le service, l’infrastructure Windows Communication Foundation (WCF) garantit que l’identité du service attendu correspond aux valeurs de cet élément et peut donc être authentifiée.</span><span class="sxs-lookup"><span data-stu-id="98cb6-102">In the handshake process between the client and service, the Windows Communication Foundation (WCF) infrastructure will ensure that the identity of the expected service matches the values of this element, and thus can be authenticated.</span></span> <span data-ttu-id="98cb6-103">Pour plus d’informations, consultez [identité du service et authentification](../../../wcf/feature-details/service-identity-and-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="98cb6-103">For more information, see [Service Identity and Authentication](../../../wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<identity>**  
  
## <a name="syntax"></a><span data-ttu-id="98cb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98cb6-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98cb6-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="98cb6-105">Attributes and Elements</span></span>  
 <span data-ttu-id="98cb6-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="98cb6-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98cb6-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="98cb6-107">Attributes</span></span>  
 <span data-ttu-id="98cb6-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="98cb6-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="98cb6-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="98cb6-109">Child Elements</span></span>  
  
|<span data-ttu-id="98cb6-110">Élément</span><span class="sxs-lookup"><span data-stu-id="98cb6-110">Element</span></span>|<span data-ttu-id="98cb6-111">Description</span><span class="sxs-lookup"><span data-stu-id="98cb6-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="98cb6-112">certificat</span><span class="sxs-lookup"><span data-stu-id="98cb6-112">certificate</span></span>|<span data-ttu-id="98cb6-113">Spécifie les paramètres d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="98cb6-113">Specifies settings of an X.509 certificate.</span></span> <span data-ttu-id="98cb6-114">Cet élément est de type <xref:System.ServiceModel.Configuration.CertificateElement>.</span><span class="sxs-lookup"><span data-stu-id="98cb6-114">This element is of type <xref:System.ServiceModel.Configuration.CertificateElement>.</span></span> <span data-ttu-id="98cb6-115">Il contient un `encodedValue` d'attribut qui est une chaîne indiquant la valeur encodée par ce certificat.</span><span class="sxs-lookup"><span data-stu-id="98cb6-115">It contains an attribute `encodedValue` that is a string, which specifies the value encoded by this certificate.</span></span>|  
|<span data-ttu-id="98cb6-116">certificateReference</span><span class="sxs-lookup"><span data-stu-id="98cb6-116">certificateReference</span></span>|<span data-ttu-id="98cb6-117">Spécifie les paramètres de validation du certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="98cb6-117">Specifies settings for X.509 certificate validation.</span></span> <span data-ttu-id="98cb6-118">Cet élément est de type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span><span class="sxs-lookup"><span data-stu-id="98cb6-118">This element is of type <xref:System.ServiceModel.Configuration.CertificateReferenceElement>.</span></span>|  
|<span data-ttu-id="98cb6-119">dns</span><span class="sxs-lookup"><span data-stu-id="98cb6-119">dns</span></span>|<span data-ttu-id="98cb6-120">Spécifie le système DNS d'un certificat X.509 utilisé pour authentifier un service.</span><span class="sxs-lookup"><span data-stu-id="98cb6-120">Specifies the DNS of an X.509 certificate used to authenticate a service.</span></span> <span data-ttu-id="98cb6-121">Cet élément contient un attribut `value` qui est une chaîne et qui contient l'identité réelle.</span><span class="sxs-lookup"><span data-stu-id="98cb6-121">This element contains an attribute `value` that is a string, and contains the actual identity.</span></span>|  
|<span data-ttu-id="98cb6-122">rsa</span><span class="sxs-lookup"><span data-stu-id="98cb6-122">rsa</span></span>|<span data-ttu-id="98cb6-123">Indique la valeur du champ RSA d'un certificat X.509 utilisée pour authentifier un service au niveau d'un client.</span><span class="sxs-lookup"><span data-stu-id="98cb6-123">Specifies the value of the RSA field of an X.509 certificate used to authenticate a service to a client.</span></span> <span data-ttu-id="98cb6-124">Cet élément contient un attribut `value` qui est une chaîne et qui contient l'identité réelle.</span><span class="sxs-lookup"><span data-stu-id="98cb6-124">This element contains an attribute `value` that is a string, and contains the actual identity</span></span>|  
|<span data-ttu-id="98cb6-125">servicePrincipalName</span><span class="sxs-lookup"><span data-stu-id="98cb6-125">servicePrincipalName</span></span>|<span data-ttu-id="98cb6-126">Indique le nom SPN correspondant au nom principal utilisé par un client pour identifier de manière unique l'instance d'un service.</span><span class="sxs-lookup"><span data-stu-id="98cb6-126">Specifies a server principal name (SPN) identity, which is the principal name used by a client to uniquely identify an instance of a service.</span></span> <span data-ttu-id="98cb6-127">Cet élément contient un `value` d'attribut qui est une chaîne contenant le nom principal réel.</span><span class="sxs-lookup"><span data-stu-id="98cb6-127">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="98cb6-128">Cet élément est de type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="98cb6-128">This element is of type <xref:System.ServiceModel.Configuration.ServicePrincipalNameElement>.</span></span>|  
|<span data-ttu-id="98cb6-129">userPrincipalName</span><span class="sxs-lookup"><span data-stu-id="98cb6-129">userPrincipalName</span></span>|<span data-ttu-id="98cb6-130">Spécifie une identité UPN correspondant au type de nom de connexion d'un utilisateur sur un réseau.</span><span class="sxs-lookup"><span data-stu-id="98cb6-130">Specifies a user principal name (UPN) identity, which is the logon name type of a user on a network.</span></span> <span data-ttu-id="98cb6-131">Le nom d’utilisateur principal est constitué du nom d’objet utilisateur utilisé dans Active Directory, suivi du symbole arobase (), puis \@ , généralement, du domaine parent du système de noms de domaine.</span><span class="sxs-lookup"><span data-stu-id="98cb6-131">The user principal name consists of the user object name used in Active Directory, followed by the at symbol (\@) and then, typically, the Domain Name System parent domain.</span></span> <span data-ttu-id="98cb6-132">Par exemple, Jeff dans l’arborescence de domaine Fabrikam.com peut avoir le nom d’utilisateur principal [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com) .</span><span class="sxs-lookup"><span data-stu-id="98cb6-132">For example, Jeff in the Fabrikam.com domain tree might have the user principal name [jeff@fabrikam.com](mailto:jeffsmith@fabrikam.com).</span></span>  <span data-ttu-id="98cb6-133">Cet élément contient un `value` d'attribut qui est une chaîne contenant le nom principal réel.</span><span class="sxs-lookup"><span data-stu-id="98cb6-133">This element contains an attribute `value` that is a string, and contains the actual principal name.</span></span> <span data-ttu-id="98cb6-134">Cet élément est de type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span><span class="sxs-lookup"><span data-stu-id="98cb6-134">This element is of type <xref:System.ServiceModel.Configuration.UserPrincipalNameElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="98cb6-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="98cb6-135">Parent Elements</span></span>  
  
|<span data-ttu-id="98cb6-136">Élément</span><span class="sxs-lookup"><span data-stu-id="98cb6-136">Element</span></span>|<span data-ttu-id="98cb6-137">Description</span><span class="sxs-lookup"><span data-stu-id="98cb6-137">Description</span></span>|  
|-------------|-----------------|  
|[\<custom>](custom.md)|<span data-ttu-id="98cb6-138">Indique le programme de résolution d'homologue personnalisé pour un netPeerTcpBinding.</span><span class="sxs-lookup"><span data-stu-id="98cb6-138">Specifies a custom peer resolver for a netPeerTcpBinding.</span></span>|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="98cb6-139">Configure les points de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="98cb6-139">Configures service endpoints.</span></span>|  
|[<span data-ttu-id="98cb6-140">\<endpoint>of\<client></span><span class="sxs-lookup"><span data-stu-id="98cb6-140">\<endpoint> of \<client></span></span>](endpoint-of-client.md)|<span data-ttu-id="98cb6-141">Configure les points de terminaison de canal.</span><span class="sxs-lookup"><span data-stu-id="98cb6-141">Configures channel endpoints.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="98cb6-142">Spécifie le service STS pour le service fédéré.</span><span class="sxs-lookup"><span data-stu-id="98cb6-142">Specifies the Security Token Service (STS) for the federated service.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="98cb6-143">Spécifie le point de terminaison de métadonnées pour le service STS d'un service fédéré.</span><span class="sxs-lookup"><span data-stu-id="98cb6-143">Specifies the metadata endpoint for the Security Token Service (STS) of a federated service.</span></span>|  
|[\<issuedTokenParameters>](issuedtokenparameters.md)|<span data-ttu-id="98cb6-144">Définit des paramètres correspondant à un jeton émis dans une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="98cb6-144">Defines parameters for an issued token in a custom binding.</span></span>|  
|[\<localIssuer>](localissuer.md)|<span data-ttu-id="98cb6-145">Spécifie un service STS local.</span><span class="sxs-lookup"><span data-stu-id="98cb6-145">Specifies a local Security Token Service (STS).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98cb6-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98cb6-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- [<span data-ttu-id="98cb6-147">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="98cb6-147">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="98cb6-148">Points de terminaison : adresses, liaisons et contrats</span><span class="sxs-lookup"><span data-stu-id="98cb6-148">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)

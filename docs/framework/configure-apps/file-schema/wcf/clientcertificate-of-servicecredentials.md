---
title: <clientCertificate> de <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 90ad03aa-2317-43dd-8a72-6d24cdcad15c
ms.openlocfilehash: a8a78bbfcd9dfbf6975503a845d5bb4e2d24b13d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398134"
---
# <a name="clientcertificate-of-servicecredentials"></a><span data-ttu-id="f0e2b-102">\<clientCertificate> de \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="f0e2b-102">\<clientCertificate> of \<serviceCredentials></span></span>
<span data-ttu-id="f0e2b-103">Définit un certificat X.509 permettant de signer et de chiffrer des messages destinés à un client et envoyés à partir d'un service selon un modèle de communication duplex.</span><span class="sxs-lookup"><span data-stu-id="f0e2b-103">Defines an X.509 certificate used to sign and encrypt messages to a client form a service in a duplex communication pattern.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="f0e2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0e2b-104">Syntax</span></span>  
  
```xml  
<clientCertificate>
  <certificate />
  <authentication />
</clientCertificate>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0e2b-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f0e2b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f0e2b-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f0e2b-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0e2b-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="f0e2b-107">Attributes</span></span>  
 <span data-ttu-id="f0e2b-108">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f0e2b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f0e2b-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f0e2b-109">Child Elements</span></span>  
  
|<span data-ttu-id="f0e2b-110">Élément</span><span class="sxs-lookup"><span data-stu-id="f0e2b-110">Element</span></span>|<span data-ttu-id="f0e2b-111">Description</span><span class="sxs-lookup"><span data-stu-id="f0e2b-111">Description</span></span>|  
|-------------|-----------------|  
|[\<authentication>](authentication-of-clientcertificate-element.md)|<span data-ttu-id="f0e2b-112">Spécifie des options d'authentification pour le certificat client.</span><span class="sxs-lookup"><span data-stu-id="f0e2b-112">Specifies authentication options for the client certificate.</span></span>|  
|[\<certificate>](certificate-of-clientcertificate-element.md)|<span data-ttu-id="f0e2b-113">Spécifie le certificat à utiliser.</span><span class="sxs-lookup"><span data-stu-id="f0e2b-113">Specifies the certificate to use.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0e2b-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f0e2b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f0e2b-115">Élément</span><span class="sxs-lookup"><span data-stu-id="f0e2b-115">Element</span></span>|<span data-ttu-id="f0e2b-116">Description</span><span class="sxs-lookup"><span data-stu-id="f0e2b-116">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="f0e2b-117">Spécifie les informations d’identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d’identification du client.</span><span class="sxs-lookup"><span data-stu-id="f0e2b-117">Specifies the credentials to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0e2b-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="f0e2b-118">Remarks</span></span>  
 <span data-ttu-id="f0e2b-119">Cet élément est utilisé lorsque le service doit disposer du certificat du client à l'avance afin de communiquer de manière sécurisée avec le client.</span><span class="sxs-lookup"><span data-stu-id="f0e2b-119">This element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="f0e2b-120">Cela se produit lors de l'utilisation du modèle de communication duplex.</span><span class="sxs-lookup"><span data-stu-id="f0e2b-120">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="f0e2b-121">Dans le modèle demande-réponse classique, le client inclut son certificat dans la demande que le service utilise pour sécuriser à nouveau sa réponse au client.</span><span class="sxs-lookup"><span data-stu-id="f0e2b-121">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="f0e2b-122">Dans le modèle de communication duplex, toutefois, le service ne dispose pas de demande du client et, par conséquent, requiert le certificat du client à l'avance pour sécuriser l'envoi du message au client.</span><span class="sxs-lookup"><span data-stu-id="f0e2b-122">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="f0e2b-123">C'est pourquoi vous devez obtenir le certificat du client dans une négociation hors bande et l'indiquer à l'aide de cet élément.</span><span class="sxs-lookup"><span data-stu-id="f0e2b-123">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="f0e2b-124">Pour plus d’informations sur les services duplex, consultez [Comment : créer un contrat duplex](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="f0e2b-124">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
 <span data-ttu-id="f0e2b-125">Le certificat défini dans cet élément est utilisé pour chiffrer les messages au client uniquement pour les liaisons configurées avec le mode d’authentification de sécurité des messages `MutualCertificateDuplex`.</span><span class="sxs-lookup"><span data-stu-id="f0e2b-125">The certificate set in this element is used to encrypt messages to the client only for bindings that are configured with `MutualCertificateDuplex` message security authentication mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0e2b-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0e2b-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ClientCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.ClientCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>
- [<span data-ttu-id="f0e2b-127">Comment : créer un contrat duplex</span><span class="sxs-lookup"><span data-stu-id="f0e2b-127">How to: Create a Duplex Contract</span></span>](../../../wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="f0e2b-128">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="f0e2b-128">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="f0e2b-129">Working with Certificates</span><span class="sxs-lookup"><span data-stu-id="f0e2b-129">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)

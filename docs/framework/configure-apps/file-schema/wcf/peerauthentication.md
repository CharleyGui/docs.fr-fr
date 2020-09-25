---
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: a88a3c0bbbd36d2372520f70b3c5692757b35ade
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181555"
---
# \<peerAuthentication>

<span data-ttu-id="f9fe6-101">Spécifie des paramètres d'authentification pour un certificat d'homologue utilisé par un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-101">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="f9fe6-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9fe6-102">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9fe6-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="f9fe6-103">Attributes and Elements</span></span>  

 <span data-ttu-id="f9fe6-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9fe6-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="f9fe6-105">Attributes</span></span>  
  
|<span data-ttu-id="f9fe6-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="f9fe6-106">Attribute</span></span>|<span data-ttu-id="f9fe6-107">Description</span><span class="sxs-lookup"><span data-stu-id="f9fe6-107">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="f9fe6-108">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-108">Optional enumeration.</span></span> <span data-ttu-id="f9fe6-109">Spécifie l'un de trois modes utilisés pour valider des informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-109">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="f9fe6-110">Cet attribut est de type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-110">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="f9fe6-111">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-111">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="f9fe6-112">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-112">Optional string.</span></span> <span data-ttu-id="f9fe6-113">Spécifie un type et un assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-113">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="f9fe6-114">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="f9fe6-115">Cet attribut est de type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-115">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="f9fe6-116">Windows Communication Foundation (WCF) fournit un validateur de certificat homologue par défaut qui vérifie le certificat homologue par rapport au magasin de personnes autorisées.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-116">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="f9fe6-117">Il vérifie également que le certificat remonte jusqu'à une racine valide.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-117">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="f9fe6-118">Vous pouvez implémenter un validateur personnalisé pour spécifier un comportement différent et utiliser cet attribut pour pointer vers ce validateur.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-118">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="f9fe6-119">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-119">Optional enumeration.</span></span> <span data-ttu-id="f9fe6-120">Spécifie le mode de révocation de certificat.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-120">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="f9fe6-121">Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-121">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="f9fe6-122">Le système vérifie que le certificat homologue n'a pas été révoqué en le recherchant dans la liste des certificats révoqués.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-122">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="f9fe6-123">Cette vérification peut être effectuée en ligne ou par rapport à une liste de révocations mise en cache.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-123">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="f9fe6-124">La vérification de la révocation peut être désactivée en affectant la valeur NoCheck à cet attribut.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-124">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="f9fe6-125">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-125">Optional enumeration.</span></span> <span data-ttu-id="f9fe6-126">Spécifie l’emplacement du magasin de confiance dans lequel le certificat homologue est validé par le système de sécurité WCF.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-126">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="f9fe6-127">Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9fe6-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="f9fe6-128">Child Elements</span></span>  

 <span data-ttu-id="f9fe6-129">Aucun.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9fe6-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="f9fe6-130">Parent Elements</span></span>  
  
|<span data-ttu-id="f9fe6-131">Élément</span><span class="sxs-lookup"><span data-stu-id="f9fe6-131">Element</span></span>|<span data-ttu-id="f9fe6-132">Description</span><span class="sxs-lookup"><span data-stu-id="f9fe6-132">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="f9fe6-133">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-133">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9fe6-134">Notes</span><span class="sxs-lookup"><span data-stu-id="f9fe6-134">Remarks</span></span>  

 <span data-ttu-id="f9fe6-135">L'élément `<authentication>` correspond à la classe <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-135">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="f9fe6-136">Cet élément spécifie un validateur, appelé pendant l'authentification de voisins dans la maille.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-136">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="f9fe6-137">Lorsqu'un nouvel homologue essaie d'établir une connexion avec un voisin, il transmet ses propres informations d'identification à l'homologue répondant.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-137">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="f9fe6-138">Le validateur du répondeur est appelé pour vérifier les informations d'identification du tiers distant.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-138">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="f9fe6-139">Chaque fois qu'une connexion est établie avec un homologue de la maille, les deux homologues sont authentifiés mutuellement, ce qui signifie que des validateurs sont appelés à chaque extrémité.</span><span class="sxs-lookup"><span data-stu-id="f9fe6-139">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9fe6-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9fe6-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="f9fe6-141">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="f9fe6-141">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="f9fe6-142">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="f9fe6-142">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="f9fe6-143">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f9fe6-143">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="f9fe6-144">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f9fe6-144">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="f9fe6-145">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="f9fe6-145">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)

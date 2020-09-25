---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: e7888d01838312aa51397ca39133edb9318fac80
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204773"
---
# \<messageSenderAuthentication>

<span data-ttu-id="de427-101">Spécifie les paramètres d'authentification pour le certificat homologue utilisé par l'expéditeur d'un message.</span><span class="sxs-lookup"><span data-stu-id="de427-101">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="de427-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="de427-102">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="de427-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="de427-103">Attributes and Elements</span></span>  

 <span data-ttu-id="de427-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="de427-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="de427-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="de427-105">Attributes</span></span>  
  
|<span data-ttu-id="de427-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="de427-106">Attribute</span></span>|<span data-ttu-id="de427-107">Description</span><span class="sxs-lookup"><span data-stu-id="de427-107">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="de427-108">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="de427-108">Optional enumeration.</span></span> <span data-ttu-id="de427-109">Spécifie l'un des cinq modes utilisés pour valider les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="de427-109">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="de427-110">Cet attribut est de type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="de427-110">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="de427-111">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="de427-111">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="de427-112">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="de427-112">Optional string.</span></span> <span data-ttu-id="de427-113">Spécifie un type et un assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="de427-113">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="de427-114">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="de427-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="de427-115">Cet attribut est de type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="de427-115">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="de427-116">Windows Communication Foundation (WCF) fournit un validateur de certificat homologue par défaut qui vérifie le certificat homologue par rapport au magasin de personnes autorisées.</span><span class="sxs-lookup"><span data-stu-id="de427-116">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="de427-117">Il vérifie également que le certificat remonte jusqu'à une racine valide.</span><span class="sxs-lookup"><span data-stu-id="de427-117">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="de427-118">Vous pouvez implémenter un validateur personnalisé pour spécifier un comportement différent et utiliser cet attribut pour pointer vers ce validateur.</span><span class="sxs-lookup"><span data-stu-id="de427-118">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="de427-119">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="de427-119">Optional enumeration.</span></span> <span data-ttu-id="de427-120">Spécifie le mode de révocation de certificat.</span><span class="sxs-lookup"><span data-stu-id="de427-120">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="de427-121">Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="de427-121">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="de427-122">Le système vérifie que le certificat homologue n'a pas été révoqué en le recherchant dans la liste des certificats révoqués.</span><span class="sxs-lookup"><span data-stu-id="de427-122">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="de427-123">Cette vérification peut être effectuée en ligne ou par rapport à une liste de révocations mise en cache.</span><span class="sxs-lookup"><span data-stu-id="de427-123">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="de427-124">La vérification de la révocation peut être désactivée en affectant la valeur NoCheck à cet attribut.</span><span class="sxs-lookup"><span data-stu-id="de427-124">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="de427-125">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="de427-125">Optional enumeration.</span></span> <span data-ttu-id="de427-126">Spécifie l’emplacement du magasin de confiance dans lequel le certificat homologue est validé par le système de sécurité WCF.</span><span class="sxs-lookup"><span data-stu-id="de427-126">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="de427-127">Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="de427-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="de427-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="de427-128">Child Elements</span></span>  

 <span data-ttu-id="de427-129">Aucun.</span><span class="sxs-lookup"><span data-stu-id="de427-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="de427-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="de427-130">Parent Elements</span></span>  
  
|<span data-ttu-id="de427-131">Élément</span><span class="sxs-lookup"><span data-stu-id="de427-131">Element</span></span>|<span data-ttu-id="de427-132">Description</span><span class="sxs-lookup"><span data-stu-id="de427-132">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="de427-133">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="de427-133">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de427-134">Notes</span><span class="sxs-lookup"><span data-stu-id="de427-134">Remarks</span></span>  

 <span data-ttu-id="de427-135">Cet élément doit être configuré si l'authentification des messages est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="de427-135">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="de427-136">Pour les canaux de sortie, chaque message est signé à l’aide du certificat fourni par [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="de427-136">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="de427-137">Avant d'être remis à l'application, tous les messages sont vérifiés par rapport aux informations d'identification de message à l'aide du validateur spécifié par l'attribut `customCertificateValidatorType` de cet élément.</span><span class="sxs-lookup"><span data-stu-id="de427-137">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="de427-138">Le validateur peut accepter ou rejeter les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="de427-138">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de427-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="de427-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [<span data-ttu-id="de427-140">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="de427-140">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="de427-141">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="de427-141">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="de427-142">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="de427-142">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="de427-143">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="de427-143">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="de427-144">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="de427-144">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)

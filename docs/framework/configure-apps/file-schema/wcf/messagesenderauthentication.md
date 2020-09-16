---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: 035f3c95fc876f0d451e6b2146e754cfe0959a85
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546983"
---
# \<messageSenderAuthentication>
<span data-ttu-id="399a5-101">Spécifie les paramètres d'authentification pour le certificat homologue utilisé par l'expéditeur d'un message.</span><span class="sxs-lookup"><span data-stu-id="399a5-101">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="399a5-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="399a5-102">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="399a5-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="399a5-103">Attributes and Elements</span></span>  
 <span data-ttu-id="399a5-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="399a5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="399a5-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="399a5-105">Attributes</span></span>  
  
|<span data-ttu-id="399a5-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="399a5-106">Attribute</span></span>|<span data-ttu-id="399a5-107">Description</span><span class="sxs-lookup"><span data-stu-id="399a5-107">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="399a5-108">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="399a5-108">Optional enumeration.</span></span> <span data-ttu-id="399a5-109">Spécifie l'un des cinq modes utilisés pour valider les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="399a5-109">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="399a5-110">Cet attribut est de type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="399a5-110">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="399a5-111">S'il est défini à `Custom`, un `customCertificateValidator` doit également être fourni.</span><span class="sxs-lookup"><span data-stu-id="399a5-111">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="399a5-112">Chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="399a5-112">Optional string.</span></span> <span data-ttu-id="399a5-113">Spécifie un type et un assembly utilisés pour valider un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="399a5-113">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="399a5-114">Cet attribut doit être défini lorsque `certificateValidationMode` a la valeur `Custom`.</span><span class="sxs-lookup"><span data-stu-id="399a5-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="399a5-115">Cet attribut est de type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="399a5-115">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="399a5-116">Windows Communication Foundation (WCF) fournit un validateur de certificat homologue par défaut qui vérifie le certificat homologue par rapport au magasin de personnes autorisées.</span><span class="sxs-lookup"><span data-stu-id="399a5-116">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="399a5-117">Il vérifie également que le certificat remonte jusqu'à une racine valide.</span><span class="sxs-lookup"><span data-stu-id="399a5-117">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="399a5-118">Vous pouvez implémenter un validateur personnalisé pour spécifier un comportement différent et utiliser cet attribut pour pointer vers ce validateur.</span><span class="sxs-lookup"><span data-stu-id="399a5-118">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="399a5-119">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="399a5-119">Optional enumeration.</span></span> <span data-ttu-id="399a5-120">Spécifie le mode de révocation de certificat.</span><span class="sxs-lookup"><span data-stu-id="399a5-120">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="399a5-121">Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="399a5-121">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="399a5-122">Le système vérifie que le certificat homologue n'a pas été révoqué en le recherchant dans la liste des certificats révoqués.</span><span class="sxs-lookup"><span data-stu-id="399a5-122">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="399a5-123">Cette vérification peut être effectuée en ligne ou par rapport à une liste de révocations mise en cache.</span><span class="sxs-lookup"><span data-stu-id="399a5-123">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="399a5-124">La vérification de la révocation peut être désactivée en affectant la valeur NoCheck à cet attribut.</span><span class="sxs-lookup"><span data-stu-id="399a5-124">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="399a5-125">Énumération facultative.</span><span class="sxs-lookup"><span data-stu-id="399a5-125">Optional enumeration.</span></span> <span data-ttu-id="399a5-126">Spécifie l’emplacement du magasin de confiance dans lequel le certificat homologue est validé par le système de sécurité WCF.</span><span class="sxs-lookup"><span data-stu-id="399a5-126">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="399a5-127">Cet attribut est de type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="399a5-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="399a5-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="399a5-128">Child Elements</span></span>  
 <span data-ttu-id="399a5-129">Aucun.</span><span class="sxs-lookup"><span data-stu-id="399a5-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="399a5-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="399a5-130">Parent Elements</span></span>  
  
|<span data-ttu-id="399a5-131">Élément</span><span class="sxs-lookup"><span data-stu-id="399a5-131">Element</span></span>|<span data-ttu-id="399a5-132">Description</span><span class="sxs-lookup"><span data-stu-id="399a5-132">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="399a5-133">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="399a5-133">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="399a5-134">Notes</span><span class="sxs-lookup"><span data-stu-id="399a5-134">Remarks</span></span>  
 <span data-ttu-id="399a5-135">Cet élément doit être configuré si l'authentification des messages est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="399a5-135">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="399a5-136">Pour les canaux de sortie, chaque message est signé à l’aide du certificat fourni par [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="399a5-136">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="399a5-137">Avant d'être remis à l'application, tous les messages sont vérifiés par rapport aux informations d'identification de message à l'aide du validateur spécifié par l'attribut `customCertificateValidatorType` de cet élément.</span><span class="sxs-lookup"><span data-stu-id="399a5-137">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="399a5-138">Le validateur peut accepter ou rejeter les informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="399a5-138">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="399a5-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="399a5-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [<span data-ttu-id="399a5-140">Utilisation des certificats</span><span class="sxs-lookup"><span data-stu-id="399a5-140">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="399a5-141">Réseaux homologues</span><span class="sxs-lookup"><span data-stu-id="399a5-141">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="399a5-142">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="399a5-142">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="399a5-143">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="399a5-143">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="399a5-144">Sécurisation des applications de canal homologue</span><span class="sxs-lookup"><span data-stu-id="399a5-144">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)

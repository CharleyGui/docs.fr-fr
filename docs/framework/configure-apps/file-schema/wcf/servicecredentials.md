---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 63368355027856118546bc70183b41864eddb0e6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172877"
---
# \<serviceCredentials>

<span data-ttu-id="07b47-101">Spécifie l'information d'identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="07b47-101">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="07b47-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="07b47-102">Syntax</span></span>  
  
```xml  
<serviceCredentials type="String">
  <clientCertificate>
  </clientCertificate>
  <issuedTokenAuthentication>
  </issuedTokenAuthentication>
  <peer>
  </peer>
  <secureConversationAuthentication>
  </secureConversationAuthentication>
  <serviceCertificate>
  </serviceCertificate>
  <userNameAuthentication>
  </userNameAuthentication>
  <windowsAuthentication>
  </windowsAuthentication>
</serviceCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07b47-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="07b47-103">Attributes and Elements</span></span>  

 <span data-ttu-id="07b47-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="07b47-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07b47-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="07b47-105">Attributes</span></span>  
  
|<span data-ttu-id="07b47-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="07b47-106">Attribute</span></span>|<span data-ttu-id="07b47-107">Description</span><span class="sxs-lookup"><span data-stu-id="07b47-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="07b47-108">Chaîne qui spécifie le type de cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="07b47-108">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="07b47-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="07b47-109">Child Elements</span></span>  
  
|<span data-ttu-id="07b47-110">Élément</span><span class="sxs-lookup"><span data-stu-id="07b47-110">Element</span></span>|<span data-ttu-id="07b47-111">Description</span><span class="sxs-lookup"><span data-stu-id="07b47-111">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="07b47-112">Spécifie le certificat à utiliser lorsque le certificat client est disponible hors bande.</span><span class="sxs-lookup"><span data-stu-id="07b47-112">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="07b47-113">Cet élément spécifie également les paramètres de validation du certificat client.</span><span class="sxs-lookup"><span data-stu-id="07b47-113">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="07b47-114">Cet élément est de type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="07b47-114">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="07b47-115">Spécifie le jeton émis actuellement pour ce service.</span><span class="sxs-lookup"><span data-stu-id="07b47-115">Specifies the current issued token for this service.</span></span> <span data-ttu-id="07b47-116">Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="07b47-116">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="07b47-117">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="07b47-117">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="07b47-118">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="07b47-118">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<secureConversationAuthentication>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="07b47-119">Spécifie les informations d'identification actuelles pour une conversation sécurisée.</span><span class="sxs-lookup"><span data-stu-id="07b47-119">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="07b47-120">Cet élément est de type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="07b47-120">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="07b47-121">Spécifie un certificat utilisé par un service pour s'identifier.</span><span class="sxs-lookup"><span data-stu-id="07b47-121">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="07b47-122">Cet élément est de type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="07b47-122">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[\<userNameAuthentication>](usernameauthentication.md)|<span data-ttu-id="07b47-123">Spécifie les paramètres pour la validation du mot de passe du nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="07b47-123">Specifies the settings for username password validation.</span></span> <span data-ttu-id="07b47-124">Cet élément est de type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="07b47-124">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[\<windowsAuthentication>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="07b47-125">Spécifie les paramètres de validation des informations d’identification Windows.</span><span class="sxs-lookup"><span data-stu-id="07b47-125">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="07b47-126">Cet élément est de type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="07b47-126">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="07b47-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="07b47-127">Parent Elements</span></span>  
  
|<span data-ttu-id="07b47-128">Élément</span><span class="sxs-lookup"><span data-stu-id="07b47-128">Element</span></span>|<span data-ttu-id="07b47-129">Description</span><span class="sxs-lookup"><span data-stu-id="07b47-129">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="07b47-130">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="07b47-130">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07b47-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07b47-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="07b47-132">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="07b47-132">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)

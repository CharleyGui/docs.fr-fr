---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: 90a34a4a52b4c7a2e67d733fecba132818cac4fc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399652"
---
# <a name="servicecredentials"></a><span data-ttu-id="2f851-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="2f851-101">\<serviceCredentials></span></span>
<span data-ttu-id="2f851-102">Spécifie l'information d'identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="2f851-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
<span data-ttu-id="2f851-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2f851-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2f851-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2f851-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2f851-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2f851-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="2f851-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2f851-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="2f851-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2f851-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="2f851-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceCredentials >**</span><span class="sxs-lookup"><span data-stu-id="2f851-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCredentials>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f851-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f851-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f851-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2f851-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2f851-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2f851-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f851-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="2f851-112">Attributes</span></span>  
  
|<span data-ttu-id="2f851-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="2f851-113">Attribute</span></span>|<span data-ttu-id="2f851-114">Description</span><span class="sxs-lookup"><span data-stu-id="2f851-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="2f851-115">Chaîne qui spécifie le type de cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="2f851-115">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f851-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2f851-116">Child Elements</span></span>  
  
|<span data-ttu-id="2f851-117">Élément</span><span class="sxs-lookup"><span data-stu-id="2f851-117">Element</span></span>|<span data-ttu-id="2f851-118">Description</span><span class="sxs-lookup"><span data-stu-id="2f851-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f851-119">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="2f851-119">\<clientCertificate></span></span>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="2f851-120">Spécifie le certificat à utiliser lorsque le certificat client est disponible hors bande.</span><span class="sxs-lookup"><span data-stu-id="2f851-120">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="2f851-121">Cet élément spécifie également les paramètres de validation du certificat client.</span><span class="sxs-lookup"><span data-stu-id="2f851-121">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="2f851-122">Cet élément est de type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2f851-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="2f851-123">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="2f851-123">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="2f851-124">Spécifie le jeton émis actuellement pour ce service.</span><span class="sxs-lookup"><span data-stu-id="2f851-124">Specifies the current issued token for this service.</span></span> <span data-ttu-id="2f851-125">Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2f851-125">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="2f851-126">\<peer></span><span class="sxs-lookup"><span data-stu-id="2f851-126">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="2f851-127">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="2f851-127">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="2f851-128">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="2f851-128">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="2f851-129">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="2f851-129">\<secureConversationAuthentication></span></span>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="2f851-130">Spécifie les informations d'identification actuelles pour une conversation sécurisée.</span><span class="sxs-lookup"><span data-stu-id="2f851-130">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="2f851-131">Cet élément est de type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2f851-131">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="2f851-132">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="2f851-132">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="2f851-133">Spécifie un certificat utilisé par un service pour s'identifier.</span><span class="sxs-lookup"><span data-stu-id="2f851-133">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="2f851-134">Cet élément est de type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2f851-134">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="2f851-135">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="2f851-135">\<userNameAuthentication></span></span>](usernameauthentication.md)|<span data-ttu-id="2f851-136">Spécifie les paramètres pour la validation du mot de passe du nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="2f851-136">Specifies the settings for username password validation.</span></span> <span data-ttu-id="2f851-137">Cet élément est de type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2f851-137">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="2f851-138">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="2f851-138">\<windowsAuthentication></span></span>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="2f851-139">Spécifie les paramètres de validation des informations d’identification Windows.</span><span class="sxs-lookup"><span data-stu-id="2f851-139">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="2f851-140">Cet élément est de type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="2f851-140">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2f851-141">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2f851-141">Parent Elements</span></span>  
  
|<span data-ttu-id="2f851-142">Élément</span><span class="sxs-lookup"><span data-stu-id="2f851-142">Element</span></span>|<span data-ttu-id="2f851-143">Description</span><span class="sxs-lookup"><span data-stu-id="2f851-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f851-144">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2f851-144">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="2f851-145">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="2f851-145">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f851-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f851-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="2f851-147">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="2f851-147">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)

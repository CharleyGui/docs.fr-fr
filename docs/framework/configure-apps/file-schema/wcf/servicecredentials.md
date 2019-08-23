---
title: <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 96db336c-4f7a-4193-81a5-910b8ffd804f
ms.openlocfilehash: b5d257b3082717ba94b9a4517ed5ccd4bd325c06
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936299"
---
# <a name="servicecredentials"></a><span data-ttu-id="ae4bc-101">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="ae4bc-101">\<serviceCredentials></span></span>
<span data-ttu-id="ae4bc-102">Spécifie l'information d'identification à utiliser pour authentifier le service, ainsi que les paramètres liés à la validation des informations d'identification du client.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-102">Specifies the credential to be used in authenticating the service and the client credential validation-related settings.</span></span>  
  
 <span data-ttu-id="ae4bc-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ae4bc-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ae4bc-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="ae4bc-104">\<behaviors></span></span>  
<span data-ttu-id="ae4bc-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="ae4bc-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="ae4bc-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="ae4bc-106">\<behavior></span></span>  
<span data-ttu-id="ae4bc-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="ae4bc-107">\<serviceCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae4bc-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae4bc-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae4bc-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ae4bc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ae4bc-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae4bc-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="ae4bc-111">Attributes</span></span>  
  
|<span data-ttu-id="ae4bc-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="ae4bc-112">Attribute</span></span>|<span data-ttu-id="ae4bc-113">Description</span><span class="sxs-lookup"><span data-stu-id="ae4bc-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="ae4bc-114">Chaîne qui spécifie le type de cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-114">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae4bc-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ae4bc-115">Child Elements</span></span>  
  
|<span data-ttu-id="ae4bc-116">Élément</span><span class="sxs-lookup"><span data-stu-id="ae4bc-116">Element</span></span>|<span data-ttu-id="ae4bc-117">Description</span><span class="sxs-lookup"><span data-stu-id="ae4bc-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae4bc-118">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="ae4bc-118">\<clientCertificate></span></span>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="ae4bc-119">Spécifie le certificat à utiliser lorsque le certificat client est disponible hors bande.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-119">Specifies the certificate to be used when the client certificate is available out-of-band.</span></span> <span data-ttu-id="ae4bc-120">Cet élément spécifie également les paramètres de validation du certificat client.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-120">This element also specifies client certificate validation settings.</span></span> <span data-ttu-id="ae4bc-121">Cet élément est de type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-121">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="ae4bc-122">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="ae4bc-122">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="ae4bc-123">Spécifie le jeton émis actuellement pour ce service.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-123">Specifies the current issued token for this service.</span></span> <span data-ttu-id="ae4bc-124">Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-124">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement>.</span></span>|  
|[<span data-ttu-id="ae4bc-125">\<peer></span><span class="sxs-lookup"><span data-stu-id="ae4bc-125">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="ae4bc-126">Spécifie les informations d'identification actuelles d'un nœud homologue.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-126">Specifies the current credentials for a peer node.</span></span> <span data-ttu-id="ae4bc-127">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-127">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="ae4bc-128">\<secureConversationAuthentication></span><span class="sxs-lookup"><span data-stu-id="ae4bc-128">\<secureConversationAuthentication></span></span>](secureconversationauthentication-of-servicecredential.md)|<span data-ttu-id="ae4bc-129">Spécifie les informations d'identification actuelles pour une conversation sécurisée.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-129">Specifies the current credentials for a secure conversation.</span></span> <span data-ttu-id="ae4bc-130">Cet élément est de type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-130">This element is of type <xref:System.ServiceModel.Configuration.SecureConversationServiceElement>.</span></span>|  
|[<span data-ttu-id="ae4bc-131">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="ae4bc-131">\<serviceCertificate></span></span>](servicecertificate-of-servicecredentials.md)|<span data-ttu-id="ae4bc-132">Spécifie un certificat utilisé par un service pour s'identifier.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-132">Specifies a certificate used by a service to identify itself.</span></span> <span data-ttu-id="ae4bc-133">Cet élément est de type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-133">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>.</span></span>|  
|[<span data-ttu-id="ae4bc-134">\<userNameAuthentication></span><span class="sxs-lookup"><span data-stu-id="ae4bc-134">\<userNameAuthentication></span></span>](usernameauthentication.md)|<span data-ttu-id="ae4bc-135">Spécifie les paramètres pour la validation du mot de passe du nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-135">Specifies the settings for username password validation.</span></span> <span data-ttu-id="ae4bc-136">Cet élément est de type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-136">This element is of type <xref:System.ServiceModel.Configuration.UserNameServiceElement>.</span></span>|  
|[<span data-ttu-id="ae4bc-137">\<windowsAuthentication></span><span class="sxs-lookup"><span data-stu-id="ae4bc-137">\<windowsAuthentication></span></span>](windowsauthentication-of-servicecredentials.md)|<span data-ttu-id="ae4bc-138">Spécifie les paramètres de validation des informations d’identification Windows.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-138">Specifies the settings for Windows credential validation.</span></span> <span data-ttu-id="ae4bc-139">Cet élément est de type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsServiceElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ae4bc-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ae4bc-140">Parent Elements</span></span>  
  
|<span data-ttu-id="ae4bc-141">Élément</span><span class="sxs-lookup"><span data-stu-id="ae4bc-141">Element</span></span>|<span data-ttu-id="ae4bc-142">Description</span><span class="sxs-lookup"><span data-stu-id="ae4bc-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae4bc-143">\<behavior></span><span class="sxs-lookup"><span data-stu-id="ae4bc-143">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ae4bc-144">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="ae4bc-144">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ae4bc-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae4bc-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- [<span data-ttu-id="ae4bc-146">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="ae4bc-146">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)

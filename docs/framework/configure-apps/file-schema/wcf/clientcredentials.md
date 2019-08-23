---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: c3e756f49b7054d6553eb6c3f1850f0fbce14943
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926105"
---
# <a name="clientcredentials"></a><span data-ttu-id="a903f-101">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="a903f-101">\<clientCredentials></span></span>
<span data-ttu-id="a903f-102">Indique les informations d'identification utilisées pour authentifier le client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="a903f-102">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
 <span data-ttu-id="a903f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a903f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a903f-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="a903f-104">\<behaviors></span></span>  
<span data-ttu-id="a903f-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="a903f-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="a903f-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="a903f-106">\<behavior></span></span>  
<span data-ttu-id="a903f-107">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="a903f-107">\<clientCredentials></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a903f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a903f-108">Syntax</span></span>  
  
```xml  
<clientCredentials type="String"
                   supportInteractive="Boolean" >
  <clientCertificate>
  </clientCertificate>
  <digest>
  </digest>
  <isuedToken>
  </isuedToken>
  <peer>
  </peer>
  <serviceCertificate>
  </serviceCertificate>
  <windowsAuthentication>
  </windowsAuthentication>
</clientCredentials>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a903f-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a903f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a903f-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a903f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a903f-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="a903f-111">Attributes</span></span>  
  
|<span data-ttu-id="a903f-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="a903f-112">Attribute</span></span>|<span data-ttu-id="a903f-113">Description</span><span class="sxs-lookup"><span data-stu-id="a903f-113">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="a903f-114">Valeur booléenne indiquant si un utilisateur interactif peut sélectionner les informations d'identification d'un client pendant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="a903f-114">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="a903f-115">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="a903f-115">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="a903f-116">Chaîne qui spécifie le type de cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="a903f-116">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a903f-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a903f-117">Child Elements</span></span>  
  
|<span data-ttu-id="a903f-118">Élément</span><span class="sxs-lookup"><span data-stu-id="a903f-118">Element</span></span>|<span data-ttu-id="a903f-119">Description</span><span class="sxs-lookup"><span data-stu-id="a903f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a903f-120">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="a903f-120">\<clientCertificate></span></span>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="a903f-121">Indique le certificat utilisé pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="a903f-121">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="a903f-122">Cet élément est de type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a903f-122">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="a903f-123">\<httpDigest></span><span class="sxs-lookup"><span data-stu-id="a903f-123">\<httpDigest></span></span>](httpdigest-element.md)|<span data-ttu-id="a903f-124">Indique un condensat utilisé pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="a903f-124">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="a903f-125">Cet élément est de type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a903f-125">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[<span data-ttu-id="a903f-126">\<issuedToken></span><span class="sxs-lookup"><span data-stu-id="a903f-126">\<issuedToken></span></span>](issuedtoken.md)|<span data-ttu-id="a903f-127">Spécifie un type de jeton personnalisé utilisé pour authentifier le client à un service STS.</span><span class="sxs-lookup"><span data-stu-id="a903f-127">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="a903f-128">Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a903f-128">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[<span data-ttu-id="a903f-129">\<peer></span><span class="sxs-lookup"><span data-stu-id="a903f-129">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="a903f-130">Spécifie des informations d'identification d'homologue actuelles.</span><span class="sxs-lookup"><span data-stu-id="a903f-130">Specifies a current peer credential.</span></span> <span data-ttu-id="a903f-131">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="a903f-131">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[<span data-ttu-id="a903f-132">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="a903f-132">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="a903f-133">Spécifie le certificat utilisé pour authentifier le service auprès du client et fournit une structure permettant de définir des options de certificat.</span><span class="sxs-lookup"><span data-stu-id="a903f-133">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="a903f-134">Ce certificat doit être fourni au client hors bande, à partir du service.</span><span class="sxs-lookup"><span data-stu-id="a903f-134">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="a903f-135">Cet élément est de type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a903f-135">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[<span data-ttu-id="a903f-136">\<windows></span><span class="sxs-lookup"><span data-stu-id="a903f-136">\<windows></span></span>](windows-of-clientcredentials-element.md)|<span data-ttu-id="a903f-137">Indique des informations d'identification Windows.</span><span class="sxs-lookup"><span data-stu-id="a903f-137">Specifies a Windows credential.</span></span> <span data-ttu-id="a903f-138">La valeur par défaut correspond aux informations d'identification du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="a903f-138">The default is the credential of the current thread.</span></span> <span data-ttu-id="a903f-139">Cet élément est de type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="a903f-139">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a903f-140">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a903f-140">Parent Elements</span></span>  
  
|<span data-ttu-id="a903f-141">Élément</span><span class="sxs-lookup"><span data-stu-id="a903f-141">Element</span></span>|<span data-ttu-id="a903f-142">Description</span><span class="sxs-lookup"><span data-stu-id="a903f-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a903f-143">\<behavior></span><span class="sxs-lookup"><span data-stu-id="a903f-143">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="a903f-144">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="a903f-144">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a903f-145">Notes</span><span class="sxs-lookup"><span data-stu-id="a903f-145">Remarks</span></span>  
 <span data-ttu-id="a903f-146">Les informations d'identification du client permettent d'authentifier le client auprès des services dans les cas où l'authentification mutuelle est requise.</span><span class="sxs-lookup"><span data-stu-id="a903f-146">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="a903f-147">Cette section de configuration peut également servir à spécifier des certificats de service pour les scénarios dans lesquels le client doit sécuriser des messages auprès d'un service à l'aide du certificat de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="a903f-147">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a903f-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a903f-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="a903f-149">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="a903f-149">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a903f-150">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="a903f-150">Securing Clients</span></span>](../../../wcf/securing-clients.md)

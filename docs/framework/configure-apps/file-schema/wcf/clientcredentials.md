---
title: <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 1e6eef0d-a34e-4d74-b0f7-f65d2181858d
ms.openlocfilehash: 6094006df24ee824c419a783ab29d7604757577c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201458"
---
# \<clientCredentials>

<span data-ttu-id="84e89-101">Indique les informations d'identification utilisées pour authentifier le client auprès d'un service.</span><span class="sxs-lookup"><span data-stu-id="84e89-101">Specifies the credentials used to authenticate the client to a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clientCredentials>**  
  
## <a name="syntax"></a><span data-ttu-id="84e89-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84e89-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84e89-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="84e89-103">Attributes and Elements</span></span>  

 <span data-ttu-id="84e89-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="84e89-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84e89-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="84e89-105">Attributes</span></span>  
  
|<span data-ttu-id="84e89-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="84e89-106">Attribute</span></span>|<span data-ttu-id="84e89-107">Description</span><span class="sxs-lookup"><span data-stu-id="84e89-107">Description</span></span>|  
|---------------|-----------------|  
|`supportInteractive`|<span data-ttu-id="84e89-108">Valeur booléenne indiquant si un utilisateur interactif peut sélectionner les informations d'identification d'un client pendant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="84e89-108">A Boolean value that specifies whether an interactive user can be involved in selecting a client credential at runtime.</span></span> <span data-ttu-id="84e89-109">La valeur par défaut est `true`.</span><span class="sxs-lookup"><span data-stu-id="84e89-109">The default value is `true`.</span></span>|  
|`type`|<span data-ttu-id="84e89-110">Chaîne qui spécifie le type de cet élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="84e89-110">A string that specifies the type of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="84e89-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="84e89-111">Child Elements</span></span>  
  
|<span data-ttu-id="84e89-112">Élément</span><span class="sxs-lookup"><span data-stu-id="84e89-112">Element</span></span>|<span data-ttu-id="84e89-113">Description</span><span class="sxs-lookup"><span data-stu-id="84e89-113">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-clientcredentials-element.md)|<span data-ttu-id="84e89-114">Indique le certificat utilisé pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="84e89-114">Specifies the certificate used to authenticate the client to the service.</span></span> <span data-ttu-id="84e89-115">Cet élément est de type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="84e89-115">This element is of type <xref:System.ServiceModel.Configuration.X509InitiatorCertificateClientElement>.</span></span>|  
|[\<httpDigest>](httpdigest-element.md)|<span data-ttu-id="84e89-116">Indique un condensat utilisé pour authentifier le client auprès du service.</span><span class="sxs-lookup"><span data-stu-id="84e89-116">Specifies a digest used to authenticate the client to the service.</span></span> <span data-ttu-id="84e89-117">Cet élément est de type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span><span class="sxs-lookup"><span data-stu-id="84e89-117">This element is of type <xref:System.ServiceModel.Configuration.HttpDigestClientElement>.</span></span>|  
|[\<issuedToken>](issuedtoken.md)|<span data-ttu-id="84e89-118">Spécifie un type de jeton personnalisé utilisé pour authentifier le client à un service STS.</span><span class="sxs-lookup"><span data-stu-id="84e89-118">Specifies a custom token type used to authenticate the client to a Secure Token Service (STS).</span></span> <span data-ttu-id="84e89-119">Cet élément est de type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span><span class="sxs-lookup"><span data-stu-id="84e89-119">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenClientElement>.</span></span>|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="84e89-120">Spécifie des informations d'identification d'homologue actuelles.</span><span class="sxs-lookup"><span data-stu-id="84e89-120">Specifies a current peer credential.</span></span> <span data-ttu-id="84e89-121">Cet élément est de type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span><span class="sxs-lookup"><span data-stu-id="84e89-121">This element is of type <xref:System.ServiceModel.Configuration.PeerCredentialElement>.</span></span>|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="84e89-122">Spécifie le certificat utilisé pour authentifier le service auprès du client et fournit une structure permettant de définir des options de certificat.</span><span class="sxs-lookup"><span data-stu-id="84e89-122">Specifies the certificate used to authenticate the service to the client and provides a structure for setting certificate options.</span></span> <span data-ttu-id="84e89-123">Ce certificat doit être fourni au client hors bande, à partir du service.</span><span class="sxs-lookup"><span data-stu-id="84e89-123">This certificate must be supplied out-of-band from the service to the client.</span></span> <span data-ttu-id="84e89-124">Cet élément est de type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span><span class="sxs-lookup"><span data-stu-id="84e89-124">This element is of type <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>.</span></span>|  
|[\<windows>](windows-of-clientcredentials-element.md)|<span data-ttu-id="84e89-125">Indique des informations d'identification Windows.</span><span class="sxs-lookup"><span data-stu-id="84e89-125">Specifies a Windows credential.</span></span> <span data-ttu-id="84e89-126">La valeur par défaut correspond aux informations d'identification du thread actuel.</span><span class="sxs-lookup"><span data-stu-id="84e89-126">The default is the credential of the current thread.</span></span> <span data-ttu-id="84e89-127">Cet élément est de type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span><span class="sxs-lookup"><span data-stu-id="84e89-127">This element is of type <xref:System.ServiceModel.Configuration.WindowsClientElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84e89-128">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="84e89-128">Parent Elements</span></span>  
  
|<span data-ttu-id="84e89-129">Élément</span><span class="sxs-lookup"><span data-stu-id="84e89-129">Element</span></span>|<span data-ttu-id="84e89-130">Description</span><span class="sxs-lookup"><span data-stu-id="84e89-130">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="84e89-131">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="84e89-131">Specifies an endpoint behavior.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84e89-132">Notes</span><span class="sxs-lookup"><span data-stu-id="84e89-132">Remarks</span></span>  

 <span data-ttu-id="84e89-133">Les informations d'identification du client permettent d'authentifier le client auprès des services dans les cas où l'authentification mutuelle est requise.</span><span class="sxs-lookup"><span data-stu-id="84e89-133">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="84e89-134">Cette section de configuration peut également servir à spécifier des certificats de service pour les scénarios dans lesquels le client doit sécuriser des messages auprès d'un service à l'aide du certificat de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="84e89-134">This configuration section can also be used to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e89-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84e89-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- [<span data-ttu-id="84e89-136">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="84e89-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="84e89-137">Sécurisation des clients</span><span class="sxs-lookup"><span data-stu-id="84e89-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)

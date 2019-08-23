---
title: <transport> de <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 837d01540fa63579877ab4085bd8034c78f2fbe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915560"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="d1bd7-102">\<> de transport \<de NetPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="d1bd7-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="d1bd7-103">Spécifie les paramètres de sécurité au niveau du transport lors de l’utilisation du [ \<> NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d1bd7-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="d1bd7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d1bd7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d1bd7-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d1bd7-105">\<bindings></span></span>  
<span data-ttu-id="d1bd7-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="d1bd7-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="d1bd7-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="d1bd7-107">\<binding></span></span>  
<span data-ttu-id="d1bd7-108">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="d1bd7-108">\<security></span></span>  
<span data-ttu-id="d1bd7-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="d1bd7-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1bd7-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1bd7-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1bd7-111">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d1bd7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d1bd7-112">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d1bd7-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1bd7-113">Attributs</span><span class="sxs-lookup"><span data-stu-id="d1bd7-113">Attributes</span></span>  
  
|<span data-ttu-id="d1bd7-114">Attribut</span><span class="sxs-lookup"><span data-stu-id="d1bd7-114">Attribute</span></span>|<span data-ttu-id="d1bd7-115">Description</span><span class="sxs-lookup"><span data-stu-id="d1bd7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1bd7-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="d1bd7-116">credentialType</span></span>|<span data-ttu-id="d1bd7-117">facultatif.</span><span class="sxs-lookup"><span data-stu-id="d1bd7-117">Optional.</span></span> <span data-ttu-id="d1bd7-118">Spécifie le type d'informations d'identification utilisé pour vérifier les messages envoyés avec le transport d'homologues.</span><span class="sxs-lookup"><span data-stu-id="d1bd7-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="d1bd7-119">Cet attribut est de type <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d1bd7-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="d1bd7-120">Attribut credentialType</span><span class="sxs-lookup"><span data-stu-id="d1bd7-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="d1bd7-121">Valeur</span><span class="sxs-lookup"><span data-stu-id="d1bd7-121">Value</span></span>|<span data-ttu-id="d1bd7-122">Description</span><span class="sxs-lookup"><span data-stu-id="d1bd7-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d1bd7-123">Certificat</span><span class="sxs-lookup"><span data-stu-id="d1bd7-123">Certificate</span></span>|<span data-ttu-id="d1bd7-124">L'authentification du transport de canal homologue requiert un certificat X509.</span><span class="sxs-lookup"><span data-stu-id="d1bd7-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="d1bd7-125">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="d1bd7-125">Password</span></span>|<span data-ttu-id="d1bd7-126">L'authentification du transport de canal homologue requiert un mot de passe correct.</span><span class="sxs-lookup"><span data-stu-id="d1bd7-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1bd7-127">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d1bd7-127">Child Elements</span></span>  
 <span data-ttu-id="d1bd7-128">Aucun</span><span class="sxs-lookup"><span data-stu-id="d1bd7-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1bd7-129">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d1bd7-129">Parent Elements</span></span>  
  
|<span data-ttu-id="d1bd7-130">Élément</span><span class="sxs-lookup"><span data-stu-id="d1bd7-130">Element</span></span>|<span data-ttu-id="d1bd7-131">Description</span><span class="sxs-lookup"><span data-stu-id="d1bd7-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1bd7-132">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="d1bd7-132">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="d1bd7-133">Définit les paramètres de sécurité pour le [ \<> NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d1bd7-133">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1bd7-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d1bd7-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="d1bd7-135">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="d1bd7-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d1bd7-136">Liaisons</span><span class="sxs-lookup"><span data-stu-id="d1bd7-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d1bd7-137">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="d1bd7-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d1bd7-138">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="d1bd7-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d1bd7-139">\<binding></span><span class="sxs-lookup"><span data-stu-id="d1bd7-139">\<binding></span></span>](../../../misc/binding.md)

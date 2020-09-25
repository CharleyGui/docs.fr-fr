---
title: <transport> de <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 5df47b1bfc149b524fc9b90eacffa832817f653c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172864"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="500dc-102">\<transport> de \<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="500dc-102">\<transport> of \<netPeerTcpBinding></span></span>

<span data-ttu-id="500dc-103">Spécifie les paramètres de sécurité au niveau du transport lors de l’utilisation de [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="500dc-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="500dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="500dc-104">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="500dc-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="500dc-105">Attributes and Elements</span></span>  

 <span data-ttu-id="500dc-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="500dc-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="500dc-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="500dc-107">Attributes</span></span>  
  
|<span data-ttu-id="500dc-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="500dc-108">Attribute</span></span>|<span data-ttu-id="500dc-109">Description</span><span class="sxs-lookup"><span data-stu-id="500dc-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="500dc-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="500dc-110">credentialType</span></span>|<span data-ttu-id="500dc-111">Optionnel.</span><span class="sxs-lookup"><span data-stu-id="500dc-111">Optional.</span></span> <span data-ttu-id="500dc-112">Spécifie le type d'informations d'identification utilisé pour vérifier les messages envoyés avec le transport d'homologues.</span><span class="sxs-lookup"><span data-stu-id="500dc-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="500dc-113">Cet attribut est de type <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="500dc-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="500dc-114">Attribut credentialType</span><span class="sxs-lookup"><span data-stu-id="500dc-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="500dc-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="500dc-115">Value</span></span>|<span data-ttu-id="500dc-116">Description</span><span class="sxs-lookup"><span data-stu-id="500dc-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="500dc-117">Certificat</span><span class="sxs-lookup"><span data-stu-id="500dc-117">Certificate</span></span>|<span data-ttu-id="500dc-118">L'authentification du transport de canal homologue requiert un certificat X509.</span><span class="sxs-lookup"><span data-stu-id="500dc-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="500dc-119">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="500dc-119">Password</span></span>|<span data-ttu-id="500dc-120">L'authentification du transport de canal homologue requiert un mot de passe correct.</span><span class="sxs-lookup"><span data-stu-id="500dc-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="500dc-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="500dc-121">Child Elements</span></span>  

 <span data-ttu-id="500dc-122">None</span><span class="sxs-lookup"><span data-stu-id="500dc-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="500dc-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="500dc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="500dc-124">Élément</span><span class="sxs-lookup"><span data-stu-id="500dc-124">Element</span></span>|<span data-ttu-id="500dc-125">Description</span><span class="sxs-lookup"><span data-stu-id="500dc-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="500dc-126">Définit les paramètres de sécurité pour [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="500dc-126">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="500dc-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="500dc-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="500dc-128">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="500dc-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="500dc-129">Liaisons</span><span class="sxs-lookup"><span data-stu-id="500dc-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="500dc-130">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="500dc-130">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="500dc-131">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="500dc-131">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)

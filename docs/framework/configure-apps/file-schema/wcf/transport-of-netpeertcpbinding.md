---
title: <transport> de <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 08be5d752f8422ebe6442b295195f21b16a274c0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399307"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="267ea-102">\<> de transport \<de NetPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="267ea-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="267ea-103">Spécifie les paramètres de sécurité au niveau du transport lors de l’utilisation du [ \<> NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="267ea-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
<span data-ttu-id="267ea-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="267ea-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="267ea-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="267ea-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="267ea-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="267ea-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="267ea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="267ea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="267ea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="267ea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="267ea-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-netpeerbinding.md)</span><span class="sxs-lookup"><span data-stu-id="267ea-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)</span></span>\
<span data-ttu-id="267ea-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de transport**</span><span class="sxs-lookup"><span data-stu-id="267ea-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="267ea-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="267ea-111">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="267ea-112">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="267ea-112">Attributes and Elements</span></span>  
 <span data-ttu-id="267ea-113">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="267ea-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="267ea-114">Attributs</span><span class="sxs-lookup"><span data-stu-id="267ea-114">Attributes</span></span>  
  
|<span data-ttu-id="267ea-115">Attribut</span><span class="sxs-lookup"><span data-stu-id="267ea-115">Attribute</span></span>|<span data-ttu-id="267ea-116">Description</span><span class="sxs-lookup"><span data-stu-id="267ea-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="267ea-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="267ea-117">credentialType</span></span>|<span data-ttu-id="267ea-118">facultatif.</span><span class="sxs-lookup"><span data-stu-id="267ea-118">Optional.</span></span> <span data-ttu-id="267ea-119">Spécifie le type d'informations d'identification utilisé pour vérifier les messages envoyés avec le transport d'homologues.</span><span class="sxs-lookup"><span data-stu-id="267ea-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="267ea-120">Cet attribut est de type <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="267ea-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="267ea-121">Attribut credentialType</span><span class="sxs-lookup"><span data-stu-id="267ea-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="267ea-122">Valeur</span><span class="sxs-lookup"><span data-stu-id="267ea-122">Value</span></span>|<span data-ttu-id="267ea-123">Description</span><span class="sxs-lookup"><span data-stu-id="267ea-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="267ea-124">Certificat</span><span class="sxs-lookup"><span data-stu-id="267ea-124">Certificate</span></span>|<span data-ttu-id="267ea-125">L'authentification du transport de canal homologue requiert un certificat X509.</span><span class="sxs-lookup"><span data-stu-id="267ea-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="267ea-126">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="267ea-126">Password</span></span>|<span data-ttu-id="267ea-127">L'authentification du transport de canal homologue requiert un mot de passe correct.</span><span class="sxs-lookup"><span data-stu-id="267ea-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="267ea-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="267ea-128">Child Elements</span></span>  
 <span data-ttu-id="267ea-129">Aucun</span><span class="sxs-lookup"><span data-stu-id="267ea-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="267ea-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="267ea-130">Parent Elements</span></span>  
  
|<span data-ttu-id="267ea-131">Élément</span><span class="sxs-lookup"><span data-stu-id="267ea-131">Element</span></span>|<span data-ttu-id="267ea-132">Description</span><span class="sxs-lookup"><span data-stu-id="267ea-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="267ea-133">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="267ea-133">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="267ea-134">Définit les paramètres de sécurité pour le [ \<> NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="267ea-134">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="267ea-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="267ea-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="267ea-136">Sécurisation des services et des clients</span><span class="sxs-lookup"><span data-stu-id="267ea-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="267ea-137">Liaisons</span><span class="sxs-lookup"><span data-stu-id="267ea-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="267ea-138">Configuration des liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="267ea-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="267ea-139">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="267ea-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="267ea-140">\<binding></span><span class="sxs-lookup"><span data-stu-id="267ea-140">\<binding></span></span>](../../../misc/binding.md)

---
title: <transport> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3b2c7716727f58abb81bf4d58b13189ac170cf7c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399290"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="75089-102">\<> de transport \<de peerTransport ></span><span class="sxs-lookup"><span data-stu-id="75089-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="75089-103">Indique le type de transport correspondant aux messages sécurisés envoyés par des homologues configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="75089-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
<span data-ttu-id="75089-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="75089-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="75089-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="75089-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="75089-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="75089-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="75089-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="75089-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="75089-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="75089-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="75089-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<peerTransport >** ](peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="75089-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)</span></span>\
<span data-ttu-id="75089-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de sécurité**](security-of-peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="75089-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)</span></span>\
<span data-ttu-id="75089-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de transport**</span><span class="sxs-lookup"><span data-stu-id="75089-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75089-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75089-112">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75089-113">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="75089-113">Attributes and Elements</span></span>  
 <span data-ttu-id="75089-114">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="75089-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75089-115">Attributs</span><span class="sxs-lookup"><span data-stu-id="75089-115">Attributes</span></span>  
  
|<span data-ttu-id="75089-116">Attribut</span><span class="sxs-lookup"><span data-stu-id="75089-116">Attribute</span></span>|<span data-ttu-id="75089-117">Description</span><span class="sxs-lookup"><span data-stu-id="75089-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75089-118">credentialType</span><span class="sxs-lookup"><span data-stu-id="75089-118">credentialType</span></span>|<span data-ttu-id="75089-119">facultatif.</span><span class="sxs-lookup"><span data-stu-id="75089-119">Optional.</span></span> <span data-ttu-id="75089-120">Spécifie le type d'informations d'identification utilisé pour vérifier les messages envoyés avec le transport d'homologues.</span><span class="sxs-lookup"><span data-stu-id="75089-120">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="75089-121">Cet attribut est de type <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="75089-121">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="75089-122">Attribut credentialType</span><span class="sxs-lookup"><span data-stu-id="75089-122">credentialType Attribute</span></span>  
  
|<span data-ttu-id="75089-123">Valeur</span><span class="sxs-lookup"><span data-stu-id="75089-123">Value</span></span>|<span data-ttu-id="75089-124">Description</span><span class="sxs-lookup"><span data-stu-id="75089-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="75089-125">Certificat</span><span class="sxs-lookup"><span data-stu-id="75089-125">Certificate</span></span>|<span data-ttu-id="75089-126">L'authentification du transport de canal homologue requiert un certificat X509.</span><span class="sxs-lookup"><span data-stu-id="75089-126">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="75089-127">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="75089-127">Password</span></span>|<span data-ttu-id="75089-128">L'authentification du transport de canal homologue requiert un mot de passe correct.</span><span class="sxs-lookup"><span data-stu-id="75089-128">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75089-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="75089-129">Child Elements</span></span>  
 <span data-ttu-id="75089-130">Aucun</span><span class="sxs-lookup"><span data-stu-id="75089-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75089-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="75089-131">Parent Elements</span></span>  
  
|<span data-ttu-id="75089-132">Élément</span><span class="sxs-lookup"><span data-stu-id="75089-132">Element</span></span>|<span data-ttu-id="75089-133">Description</span><span class="sxs-lookup"><span data-stu-id="75089-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75089-134">\<> de sécurité</span><span class="sxs-lookup"><span data-stu-id="75089-134">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="75089-135">Définit les paramètres de sécurité pour un transport d'homologue.</span><span class="sxs-lookup"><span data-stu-id="75089-135">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75089-136">Notes</span><span class="sxs-lookup"><span data-stu-id="75089-136">Remarks</span></span>  
 <span data-ttu-id="75089-137">Cet élément est défini uniquement si l’attribut mode de la [ \<> de sécurité](security-of-peertransport.md) a la valeur `Transport` ou `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="75089-137">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75089-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75089-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="75089-139">Sécurité de transport</span><span class="sxs-lookup"><span data-stu-id="75089-139">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="75089-140">Transports</span><span class="sxs-lookup"><span data-stu-id="75089-140">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="75089-141">Choix d’un transport</span><span class="sxs-lookup"><span data-stu-id="75089-141">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="75089-142">Liaisons</span><span class="sxs-lookup"><span data-stu-id="75089-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="75089-143">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="75089-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="75089-144">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="75089-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="75089-145">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="75089-145">\<customBinding></span></span>](custombinding.md)

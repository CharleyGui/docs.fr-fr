---
title: <transport> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3b2c7716727f58abb81bf4d58b13189ac170cf7c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399290"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="45d48-102">\<transport> de \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="45d48-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="45d48-103">Indique le type de transport correspondant aux messages sécurisés envoyés par des homologues configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="45d48-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="45d48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45d48-104">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45d48-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="45d48-105">Attributes and Elements</span></span>  
 <span data-ttu-id="45d48-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="45d48-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45d48-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="45d48-107">Attributes</span></span>  
  
|<span data-ttu-id="45d48-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="45d48-108">Attribute</span></span>|<span data-ttu-id="45d48-109">Description</span><span class="sxs-lookup"><span data-stu-id="45d48-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="45d48-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="45d48-110">credentialType</span></span>|<span data-ttu-id="45d48-111">facultatif.</span><span class="sxs-lookup"><span data-stu-id="45d48-111">Optional.</span></span> <span data-ttu-id="45d48-112">Spécifie le type d'informations d'identification utilisé pour vérifier les messages envoyés avec le transport d'homologues.</span><span class="sxs-lookup"><span data-stu-id="45d48-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="45d48-113">Cet attribut est de type <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="45d48-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="45d48-114">Attribut credentialType</span><span class="sxs-lookup"><span data-stu-id="45d48-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="45d48-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="45d48-115">Value</span></span>|<span data-ttu-id="45d48-116">Description</span><span class="sxs-lookup"><span data-stu-id="45d48-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="45d48-117">Certificat</span><span class="sxs-lookup"><span data-stu-id="45d48-117">Certificate</span></span>|<span data-ttu-id="45d48-118">L'authentification du transport de canal homologue requiert un certificat X509.</span><span class="sxs-lookup"><span data-stu-id="45d48-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="45d48-119">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="45d48-119">Password</span></span>|<span data-ttu-id="45d48-120">L'authentification du transport de canal homologue requiert un mot de passe correct.</span><span class="sxs-lookup"><span data-stu-id="45d48-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45d48-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="45d48-121">Child Elements</span></span>  
 <span data-ttu-id="45d48-122">Aucune</span><span class="sxs-lookup"><span data-stu-id="45d48-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45d48-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="45d48-123">Parent Elements</span></span>  
  
|<span data-ttu-id="45d48-124">Élément</span><span class="sxs-lookup"><span data-stu-id="45d48-124">Element</span></span>|<span data-ttu-id="45d48-125">Description</span><span class="sxs-lookup"><span data-stu-id="45d48-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="45d48-126">Définit les paramètres de sécurité pour un transport d'homologue.</span><span class="sxs-lookup"><span data-stu-id="45d48-126">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45d48-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="45d48-127">Remarks</span></span>  
 <span data-ttu-id="45d48-128">Cet élément est défini uniquement si l’attribut mode de [\<security>](security-of-peertransport.md) a la valeur `Transport` ou `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="45d48-128">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d48-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="45d48-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="45d48-130">Sécurité de transport</span><span class="sxs-lookup"><span data-stu-id="45d48-130">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="45d48-131">Transports</span><span class="sxs-lookup"><span data-stu-id="45d48-131">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="45d48-132">Choix d'un transport</span><span class="sxs-lookup"><span data-stu-id="45d48-132">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="45d48-133">Liaisons</span><span class="sxs-lookup"><span data-stu-id="45d48-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="45d48-134">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="45d48-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="45d48-135">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="45d48-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

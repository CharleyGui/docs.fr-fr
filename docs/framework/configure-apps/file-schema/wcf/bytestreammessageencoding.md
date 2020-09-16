---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: e2b92b88c3e2a8abb14f58af90aab6e2e58ce14a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557292"
---
# \<byteStreamMessageEncoding>
<span data-ttu-id="350df-101">Spécifie l'encodage de message sous forme de flux d'octets, avec l'option permettant de spécifier l'encodage de caractères.</span><span class="sxs-lookup"><span data-stu-id="350df-101">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="350df-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="350df-102">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="350df-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="350df-103">Attributes and Elements</span></span>  
 <span data-ttu-id="350df-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="350df-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="350df-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="350df-105">Attributes</span></span>  
  
|<span data-ttu-id="350df-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="350df-106">Attribute</span></span>|<span data-ttu-id="350df-107">Description</span><span class="sxs-lookup"><span data-stu-id="350df-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="350df-108">messageVersion</span><span class="sxs-lookup"><span data-stu-id="350df-108">messageVersion</span></span>|<span data-ttu-id="350df-109">Spécifie la version SOAP des messages envoyés à l'aide de la liaison.</span><span class="sxs-lookup"><span data-stu-id="350df-109">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="350df-110">Cette propriété ne peut être affectée que de la valeur de version de message <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="350df-110">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="350df-111">L'encodeur de message en flux d'octets ne prend pas en charge d'autres versions de message.</span><span class="sxs-lookup"><span data-stu-id="350df-111">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="350df-112">Cet attribut est de type <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="350df-112">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="350df-113">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="350df-113">Child Elements</span></span>  
  
|<span data-ttu-id="350df-114">Élément</span><span class="sxs-lookup"><span data-stu-id="350df-114">Element</span></span>|<span data-ttu-id="350df-115">Description</span><span class="sxs-lookup"><span data-stu-id="350df-115">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="350df-116">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="350df-116">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="350df-117">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="350df-117">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="350df-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="350df-118">Parent Elements</span></span>  
  
|<span data-ttu-id="350df-119">Élément</span><span class="sxs-lookup"><span data-stu-id="350df-119">Element</span></span>|<span data-ttu-id="350df-120">Description</span><span class="sxs-lookup"><span data-stu-id="350df-120">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="350df-121">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="350df-121">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="350df-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="350df-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="350df-123">Encodage de message</span><span class="sxs-lookup"><span data-stu-id="350df-123">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="350df-124">Sélection d'un encodeur de message</span><span class="sxs-lookup"><span data-stu-id="350df-124">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="350df-125">Liaisons</span><span class="sxs-lookup"><span data-stu-id="350df-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="350df-126">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="350df-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="350df-127">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="350df-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

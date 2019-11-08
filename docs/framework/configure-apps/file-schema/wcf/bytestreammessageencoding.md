---
title: <byteStreamMessageEncoding>
ms.date: 03/30/2017
ms.assetid: bbadd8dd-60a2-4007-b959-89373a8a7d60
ms.openlocfilehash: 1d4109bde9c1668bc0832689b05e5d1dc3b198e9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739061"
---
# <a name="bytestreammessageencoding"></a><span data-ttu-id="a7fdd-101">\<byteStreamMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="a7fdd-101">\<byteStreamMessageEncoding></span></span>
<span data-ttu-id="a7fdd-102">Spécifie l'encodage de message sous forme de flux d'octets, avec l'option permettant de spécifier l'encodage de caractères.</span><span class="sxs-lookup"><span data-stu-id="a7fdd-102">Specifies the message encoding as a stream of bytes, with the option to specify the character encoding.</span></span>  
  
<span data-ttu-id="a7fdd-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a7fdd-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a7fdd-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="a7fdd-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a7fdd-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="a7fdd-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="a7fdd-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="a7fdd-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="a7fdd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="a7fdd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="a7fdd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**byteStreamMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="a7fdd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<byteStreamMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7fdd-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7fdd-109">Syntax</span></span>  
  
```xml  
<byteStreamMessageEncoding />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7fdd-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="a7fdd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a7fdd-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="a7fdd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7fdd-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="a7fdd-112">Attributes</span></span>  
  
|<span data-ttu-id="a7fdd-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="a7fdd-113">Attribute</span></span>|<span data-ttu-id="a7fdd-114">Description</span><span class="sxs-lookup"><span data-stu-id="a7fdd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7fdd-115">messageVersion</span><span class="sxs-lookup"><span data-stu-id="a7fdd-115">messageVersion</span></span>|<span data-ttu-id="a7fdd-116">Spécifie la version SOAP des messages envoyés à l'aide de la liaison.</span><span class="sxs-lookup"><span data-stu-id="a7fdd-116">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="a7fdd-117">Cette propriété ne peut être affectée que de la valeur de version de message <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="a7fdd-117">This property can only be set to the message version value of <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span> <span data-ttu-id="a7fdd-118">L'encodeur de message en flux d'octets ne prend pas en charge d'autres versions de message.</span><span class="sxs-lookup"><span data-stu-id="a7fdd-118">The byte stream message encoder does not support any other message versions.</span></span><br /><br /> <span data-ttu-id="a7fdd-119">Cet attribut est de type <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="a7fdd-119">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7fdd-120">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="a7fdd-120">Child Elements</span></span>  
  
|<span data-ttu-id="a7fdd-121">Élément</span><span class="sxs-lookup"><span data-stu-id="a7fdd-121">Element</span></span>|<span data-ttu-id="a7fdd-122">Description</span><span class="sxs-lookup"><span data-stu-id="a7fdd-122">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7fdd-123">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a7fdd-123">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="a7fdd-124">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="a7fdd-124">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="a7fdd-125">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="a7fdd-125">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7fdd-126">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="a7fdd-126">Parent Elements</span></span>  
  
|<span data-ttu-id="a7fdd-127">Élément</span><span class="sxs-lookup"><span data-stu-id="a7fdd-127">Element</span></span>|<span data-ttu-id="a7fdd-128">Description</span><span class="sxs-lookup"><span data-stu-id="a7fdd-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7fdd-129">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="a7fdd-129">\<binding></span></span>](bindings.md)|<span data-ttu-id="a7fdd-130">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a7fdd-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7fdd-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7fdd-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.ByteStreamMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>
- [<span data-ttu-id="a7fdd-132">Encodage de message</span><span class="sxs-lookup"><span data-stu-id="a7fdd-132">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="a7fdd-133">Sélection d’un encodeur de message</span><span class="sxs-lookup"><span data-stu-id="a7fdd-133">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="a7fdd-134">Liaisons</span><span class="sxs-lookup"><span data-stu-id="a7fdd-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a7fdd-135">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="a7fdd-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a7fdd-136">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="a7fdd-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a7fdd-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="a7fdd-137">\<customBinding></span></span>](custombinding.md)

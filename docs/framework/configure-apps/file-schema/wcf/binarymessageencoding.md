---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: afe0479d9cbf6d754b309c18e23d3a479870177c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739075"
---
# \<binaryMessageEncoding>
<span data-ttu-id="579b6-101">Définit un encodeur de message binaire qui encode des messages de Windows Communication Foundation (WCF) en binaire sur le câble.</span><span class="sxs-lookup"><span data-stu-id="579b6-101">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="579b6-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="579b6-102">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="579b6-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="579b6-103">Attributes and Elements</span></span>  
 <span data-ttu-id="579b6-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="579b6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="579b6-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="579b6-105">Attributes</span></span>  
  
|<span data-ttu-id="579b6-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="579b6-106">Attribute</span></span>|<span data-ttu-id="579b6-107">Description</span><span class="sxs-lookup"><span data-stu-id="579b6-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="579b6-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="579b6-108">maxReadPoolSize</span></span>|<span data-ttu-id="579b6-109">Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="579b6-109">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="579b6-110">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="579b6-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="579b6-111">La valeur par défaut est 64.</span><span class="sxs-lookup"><span data-stu-id="579b6-111">The default is 64.</span></span>|  
|<span data-ttu-id="579b6-112">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="579b6-112">maxSessionSize</span></span>|<span data-ttu-id="579b6-113">Entier positif qui définit la taille, en octets, de la mémoire tampon utilisée pour l'encodage.</span><span class="sxs-lookup"><span data-stu-id="579b6-113">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="579b6-114">Une mémoire tampon plus importante augmente la vitesse d'encodage aux dépens de la taille de la plage de travail.</span><span class="sxs-lookup"><span data-stu-id="579b6-114">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="579b6-115">La valeur par défaut est 2048.</span><span class="sxs-lookup"><span data-stu-id="579b6-115">The default is 2048.</span></span>|  
|<span data-ttu-id="579b6-116">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="579b6-116">maxWritePoolSize</span></span>|<span data-ttu-id="579b6-117">Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="579b6-117">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="579b6-118">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="579b6-118">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="579b6-119">La valeur par défaut est 16.</span><span class="sxs-lookup"><span data-stu-id="579b6-119">The default is 16.</span></span>|  
|<span data-ttu-id="579b6-120">messageVersion</span><span class="sxs-lookup"><span data-stu-id="579b6-120">messageVersion</span></span>|<span data-ttu-id="579b6-121">Spécifie le message SOAP et les versions WS-Addressing qui sont utilisées ou attendues.</span><span class="sxs-lookup"><span data-stu-id="579b6-121">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="579b6-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="579b6-122">Child Elements</span></span>  
  
|<span data-ttu-id="579b6-123">Élément</span><span class="sxs-lookup"><span data-stu-id="579b6-123">Element</span></span>|<span data-ttu-id="579b6-124">Description</span><span class="sxs-lookup"><span data-stu-id="579b6-124">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="579b6-125">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="579b6-125">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="579b6-126">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="579b6-126">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="579b6-127">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="579b6-127">Parent Elements</span></span>  
  
|<span data-ttu-id="579b6-128">Élément</span><span class="sxs-lookup"><span data-stu-id="579b6-128">Element</span></span>|<span data-ttu-id="579b6-129">Description</span><span class="sxs-lookup"><span data-stu-id="579b6-129">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="579b6-130">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="579b6-130">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="579b6-131">Remarques</span><span class="sxs-lookup"><span data-stu-id="579b6-131">Remarks</span></span>  
 <span data-ttu-id="579b6-132">L'encodage est le processus de transformation d'un message en une séquence d'octets.</span><span class="sxs-lookup"><span data-stu-id="579b6-132">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="579b6-133">Le décodage est le processus inverse.</span><span class="sxs-lookup"><span data-stu-id="579b6-133">Decoding is the reverse process.</span></span> <span data-ttu-id="579b6-134">Windows Communication Foundation (WCF) inclut trois types d'encodage des messages SOAP : Texte, Binaire et MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="579b6-134">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="579b6-135">L'élément `binaryMessageEncoding` spécifie le format binaire .NET pour le code XML et propose des options permettant de spécifier l'encodage de caractères et la version SOAP et WS-Addressing à utiliser.</span><span class="sxs-lookup"><span data-stu-id="579b6-135">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="579b6-136">L'encodeur de message binaire encode des messages de Windows Communication Foundation (WCF) en binaire sur le câble.</span><span class="sxs-lookup"><span data-stu-id="579b6-136">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="579b6-137">Même si cet encodage permet une transmission très rapide des messages, l'interopérabilité basée sur les normes WS-\* est perdue.</span><span class="sxs-lookup"><span data-stu-id="579b6-137">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="579b6-138">Exemple</span><span class="sxs-lookup"><span data-stu-id="579b6-138">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="579b6-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="579b6-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="579b6-140">Encodage de message</span><span class="sxs-lookup"><span data-stu-id="579b6-140">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="579b6-141">Sélection d'un encodeur de message</span><span class="sxs-lookup"><span data-stu-id="579b6-141">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="579b6-142">Liaisons</span><span class="sxs-lookup"><span data-stu-id="579b6-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="579b6-143">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="579b6-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="579b6-144">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="579b6-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

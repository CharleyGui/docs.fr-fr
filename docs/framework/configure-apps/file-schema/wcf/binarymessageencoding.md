---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: feefd7fe73363b5fe1ec5658c5dc339c3d6bac57
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398208"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="2a721-101">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="2a721-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="2a721-102">Définit un encodeur de message binaire qui encode des messages de Windows Communication Foundation (WCF) en binaire sur le câble.</span><span class="sxs-lookup"><span data-stu-id="2a721-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
<span data-ttu-id="2a721-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2a721-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2a721-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2a721-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2a721-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="2a721-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="2a721-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="2a721-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="2a721-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="2a721-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="2a721-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<binaryMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="2a721-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binaryMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a721-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a721-109">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a721-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2a721-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2a721-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2a721-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a721-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="2a721-112">Attributes</span></span>  
  
|<span data-ttu-id="2a721-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="2a721-113">Attribute</span></span>|<span data-ttu-id="2a721-114">Description</span><span class="sxs-lookup"><span data-stu-id="2a721-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a721-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="2a721-115">maxReadPoolSize</span></span>|<span data-ttu-id="2a721-116">Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="2a721-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="2a721-117">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="2a721-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="2a721-118">La valeur par défaut est 64.</span><span class="sxs-lookup"><span data-stu-id="2a721-118">The default is 64.</span></span>|  
|<span data-ttu-id="2a721-119">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="2a721-119">maxSessionSize</span></span>|<span data-ttu-id="2a721-120">Entier positif qui définit la taille, en octets, de la mémoire tampon utilisée pour l'encodage.</span><span class="sxs-lookup"><span data-stu-id="2a721-120">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="2a721-121">Une mémoire tampon plus importante augmente la vitesse d'encodage aux dépens de la taille de la plage de travail.</span><span class="sxs-lookup"><span data-stu-id="2a721-121">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="2a721-122">La valeur par défaut est 2048.</span><span class="sxs-lookup"><span data-stu-id="2a721-122">The default is 2048.</span></span>|  
|<span data-ttu-id="2a721-123">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="2a721-123">maxWritePoolSize</span></span>|<span data-ttu-id="2a721-124">Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="2a721-124">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="2a721-125">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="2a721-125">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="2a721-126">La valeur par défaut est 16.</span><span class="sxs-lookup"><span data-stu-id="2a721-126">The default is 16.</span></span>|  
|<span data-ttu-id="2a721-127">messageVersion</span><span class="sxs-lookup"><span data-stu-id="2a721-127">messageVersion</span></span>|<span data-ttu-id="2a721-128">Spécifie le message SOAP et les versions WS-Addressing qui sont utilisées ou attendues.</span><span class="sxs-lookup"><span data-stu-id="2a721-128">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a721-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2a721-129">Child Elements</span></span>  
  
|<span data-ttu-id="2a721-130">Élément</span><span class="sxs-lookup"><span data-stu-id="2a721-130">Element</span></span>|<span data-ttu-id="2a721-131">Description</span><span class="sxs-lookup"><span data-stu-id="2a721-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2a721-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2a721-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="2a721-133">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="2a721-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="2a721-134">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="2a721-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2a721-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2a721-135">Parent Elements</span></span>  
  
|<span data-ttu-id="2a721-136">Élément</span><span class="sxs-lookup"><span data-stu-id="2a721-136">Element</span></span>|<span data-ttu-id="2a721-137">Description</span><span class="sxs-lookup"><span data-stu-id="2a721-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a721-138">\<binding></span><span class="sxs-lookup"><span data-stu-id="2a721-138">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="2a721-139">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="2a721-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a721-140">Notes</span><span class="sxs-lookup"><span data-stu-id="2a721-140">Remarks</span></span>  
 <span data-ttu-id="2a721-141">L'encodage est le processus de transformation d'un message en une séquence d'octets.</span><span class="sxs-lookup"><span data-stu-id="2a721-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="2a721-142">Le décodage est le processus inverse.</span><span class="sxs-lookup"><span data-stu-id="2a721-142">Decoding is the reverse process.</span></span> <span data-ttu-id="2a721-143">Windows Communication Foundation (WCF) comprend trois types d’encodage pour les messages SOAP : Texte, binaire et MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="2a721-143">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="2a721-144">L'élément `binaryMessageEncoding` spécifie le format binaire .NET pour le code XML et propose des options permettant de spécifier l'encodage de caractères et la version SOAP et WS-Addressing à utiliser.</span><span class="sxs-lookup"><span data-stu-id="2a721-144">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="2a721-145">L'encodeur de message binaire encode des messages de Windows Communication Foundation (WCF) en binaire sur le câble.</span><span class="sxs-lookup"><span data-stu-id="2a721-145">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="2a721-146">Même si cet encodage permet une transmission très rapide des messages, l'interopérabilité basée sur les normes WS-\* est perdue.</span><span class="sxs-lookup"><span data-stu-id="2a721-146">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a721-147">Exemples</span><span class="sxs-lookup"><span data-stu-id="2a721-147">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="2a721-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2a721-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="2a721-149">Encodage de message</span><span class="sxs-lookup"><span data-stu-id="2a721-149">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="2a721-150">Sélection d’un encodeur de message</span><span class="sxs-lookup"><span data-stu-id="2a721-150">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="2a721-151">Liaisons</span><span class="sxs-lookup"><span data-stu-id="2a721-151">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2a721-152">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="2a721-152">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2a721-153">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="2a721-153">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2a721-154">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2a721-154">\<customBinding></span></span>](custombinding.md)

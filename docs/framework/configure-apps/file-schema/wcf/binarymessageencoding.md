---
title: <binaryMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e4ae3cd4-6b67-4ce1-af4b-9400e0a38dba
ms.openlocfilehash: 9b6b74200c807e6523ed3f7250945040bd12658d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919794"
---
# <a name="binarymessageencoding"></a><span data-ttu-id="02d72-101">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="02d72-101">\<binaryMessageEncoding></span></span>
<span data-ttu-id="02d72-102">Définit un encodeur de message binaire qui encode des messages de Windows Communication Foundation (WCF) en binaire sur le câble.</span><span class="sxs-lookup"><span data-stu-id="02d72-102">Defines a binary message encoder that encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span>  
  
 <span data-ttu-id="02d72-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="02d72-103">\<system.serviceModel></span></span>  
<span data-ttu-id="02d72-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="02d72-104">\<bindings></span></span>  
<span data-ttu-id="02d72-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="02d72-105">\<customBinding></span></span>  
<span data-ttu-id="02d72-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="02d72-106">\<binding></span></span>  
<span data-ttu-id="02d72-107">\<binaryMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="02d72-107">\<binaryMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02d72-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02d72-108">Syntax</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="Integer"
                       maxSessionSize="Integer"
                       maxWritePoolSize="Integer"
                       messageVersion="Soap11Addressing10/Soap12Addressing10" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02d72-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="02d72-109">Attributes and Elements</span></span>  
 <span data-ttu-id="02d72-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="02d72-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02d72-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="02d72-111">Attributes</span></span>  
  
|<span data-ttu-id="02d72-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="02d72-112">Attribute</span></span>|<span data-ttu-id="02d72-113">Description</span><span class="sxs-lookup"><span data-stu-id="02d72-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02d72-114">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="02d72-114">maxReadPoolSize</span></span>|<span data-ttu-id="02d72-115">Entier qui définit combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="02d72-115">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="02d72-116">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="02d72-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="02d72-117">La valeur par défaut est 64.</span><span class="sxs-lookup"><span data-stu-id="02d72-117">The default is 64.</span></span>|  
|<span data-ttu-id="02d72-118">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="02d72-118">maxSessionSize</span></span>|<span data-ttu-id="02d72-119">Entier positif qui définit la taille, en octets, de la mémoire tampon utilisée pour l'encodage.</span><span class="sxs-lookup"><span data-stu-id="02d72-119">A positive integer that sets the size, in bytes, of the buffer used for encoding.</span></span> <span data-ttu-id="02d72-120">Une mémoire tampon plus importante augmente la vitesse d'encodage aux dépens de la taille de la plage de travail.</span><span class="sxs-lookup"><span data-stu-id="02d72-120">A larger buffer increases encoding speed at the expense of the size of the working set.</span></span> <span data-ttu-id="02d72-121">La valeur par défaut est 2048.</span><span class="sxs-lookup"><span data-stu-id="02d72-121">The default is 2048.</span></span>|  
|<span data-ttu-id="02d72-122">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="02d72-122">maxWritePoolSize</span></span>|<span data-ttu-id="02d72-123">Entier qui définit combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="02d72-123">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="02d72-124">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="02d72-124">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="02d72-125">La valeur par défaut est 16.</span><span class="sxs-lookup"><span data-stu-id="02d72-125">The default is 16.</span></span>|  
|<span data-ttu-id="02d72-126">messageVersion</span><span class="sxs-lookup"><span data-stu-id="02d72-126">messageVersion</span></span>|<span data-ttu-id="02d72-127">Spécifie le message SOAP et les versions WS-Addressing qui sont utilisées ou attendues.</span><span class="sxs-lookup"><span data-stu-id="02d72-127">Specifies the SOAP message and WS-Addressing versions that are used or expected.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02d72-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="02d72-128">Child Elements</span></span>  
  
|<span data-ttu-id="02d72-129">Élément</span><span class="sxs-lookup"><span data-stu-id="02d72-129">Element</span></span>|<span data-ttu-id="02d72-130">Description</span><span class="sxs-lookup"><span data-stu-id="02d72-130">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="02d72-131">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="02d72-131">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="02d72-132">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="02d72-132">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="02d72-133">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="02d72-133">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02d72-134">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="02d72-134">Parent Elements</span></span>  
  
|<span data-ttu-id="02d72-135">Élément</span><span class="sxs-lookup"><span data-stu-id="02d72-135">Element</span></span>|<span data-ttu-id="02d72-136">Description</span><span class="sxs-lookup"><span data-stu-id="02d72-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02d72-137">\<binding></span><span class="sxs-lookup"><span data-stu-id="02d72-137">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="02d72-138">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="02d72-138">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02d72-139">Notes</span><span class="sxs-lookup"><span data-stu-id="02d72-139">Remarks</span></span>  
 <span data-ttu-id="02d72-140">L'encodage est le processus de transformation d'un message en une séquence d'octets.</span><span class="sxs-lookup"><span data-stu-id="02d72-140">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="02d72-141">Le décodage est le processus inverse.</span><span class="sxs-lookup"><span data-stu-id="02d72-141">Decoding is the reverse process.</span></span> <span data-ttu-id="02d72-142">Windows Communication Foundation (WCF) comprend trois types d’encodage pour les messages SOAP: Texte, binaire et MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="02d72-142">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="02d72-143">L'élément `binaryMessageEncoding` spécifie le format binaire .NET pour le code XML et propose des options permettant de spécifier l'encodage de caractères et la version SOAP et WS-Addressing à utiliser.</span><span class="sxs-lookup"><span data-stu-id="02d72-143">The `binaryMessageEncoding` element specifies the .NET Binary Format for XML and has options to specify the character encoding and the SOAP and WS-Addressing version to be used.</span></span> <span data-ttu-id="02d72-144">L'encodeur de message binaire encode des messages de Windows Communication Foundation (WCF) en binaire sur le câble.</span><span class="sxs-lookup"><span data-stu-id="02d72-144">The binary message encoder encodes Windows Communication Foundation (WCF) messages in binary on the wire.</span></span> <span data-ttu-id="02d72-145">Même si cet encodage permet une transmission très rapide des messages, l'interopérabilité basée sur les normes WS-\* est perdue.</span><span class="sxs-lookup"><span data-stu-id="02d72-145">While this encoding results in very fast transmission of messages, interoperability based on the WS-\* standards is lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02d72-146">Exemple</span><span class="sxs-lookup"><span data-stu-id="02d72-146">Example</span></span>  
  
```xml  
<binaryMessageEncoding maxReadPoolSize="211"
                       maxWritePoolSize="2132"
                       maxSessionSize="3141" />
```  
  
## <a name="see-also"></a><span data-ttu-id="02d72-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02d72-147">See also</span></span>

- <xref:System.ServiceModel.Configuration.BinaryMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>
- [<span data-ttu-id="02d72-148">Encodage de message</span><span class="sxs-lookup"><span data-stu-id="02d72-148">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="02d72-149">Sélection d’un encodeur de message</span><span class="sxs-lookup"><span data-stu-id="02d72-149">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="02d72-150">Liaisons</span><span class="sxs-lookup"><span data-stu-id="02d72-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="02d72-151">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="02d72-151">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="02d72-152">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="02d72-152">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="02d72-153">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="02d72-153">\<customBinding></span></span>](custombinding.md)

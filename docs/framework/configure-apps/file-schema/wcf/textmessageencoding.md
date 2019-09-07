---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: 1494cee0e412bebc6637ad73354f7c91dc636e15
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399430"
---
# <a name="textmessageencoding"></a><span data-ttu-id="4b820-101">\<textMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="4b820-101">\<textMessageEncoding></span></span>
<span data-ttu-id="4b820-102">Spécifie l'encodage de caractères et le suivi des versions de message utilisés pour les messages XML textuels.</span><span class="sxs-lookup"><span data-stu-id="4b820-102">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
<span data-ttu-id="4b820-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4b820-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4b820-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4b820-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4b820-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4b820-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="4b820-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="4b820-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="4b820-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="4b820-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="4b820-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<textMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="4b820-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b820-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b820-109">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b820-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4b820-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4b820-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4b820-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b820-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="4b820-112">Attributes</span></span>  
  
|<span data-ttu-id="4b820-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="4b820-113">Attribute</span></span>|<span data-ttu-id="4b820-114">Description</span><span class="sxs-lookup"><span data-stu-id="4b820-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4b820-115">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="4b820-115">maxReadPoolSize</span></span>|<span data-ttu-id="4b820-116">Entier qui spécifie combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="4b820-116">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="4b820-117">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="4b820-117">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4b820-118">La valeur par défaut est 64.</span><span class="sxs-lookup"><span data-stu-id="4b820-118">The default is 64.</span></span>|  
|<span data-ttu-id="4b820-119">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="4b820-119">maxWritePoolSize</span></span>|<span data-ttu-id="4b820-120">Entier qui spécifie combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="4b820-120">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="4b820-121">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="4b820-121">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4b820-122">La valeur par défaut est 16.</span><span class="sxs-lookup"><span data-stu-id="4b820-122">The default is 16.</span></span>|  
|<span data-ttu-id="4b820-123">messageVersion</span><span class="sxs-lookup"><span data-stu-id="4b820-123">messageVersion</span></span>|<span data-ttu-id="4b820-124">Spécifie la version SOAP des messages envoyés à l'aide de la liaison.</span><span class="sxs-lookup"><span data-stu-id="4b820-124">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="4b820-125">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="4b820-125">Valid values are</span></span><br /><br /> <span data-ttu-id="4b820-126">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="4b820-126">-   Soap11Addressing10</span></span><br /><span data-ttu-id="4b820-127">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="4b820-127">-   Soap12Addressing10</span></span><br /><span data-ttu-id="4b820-128">- Soap11</span><span class="sxs-lookup"><span data-stu-id="4b820-128">-   Soap11</span></span><br /><span data-ttu-id="4b820-129">-Soap12</span><span class="sxs-lookup"><span data-stu-id="4b820-129">-  Soap12</span></span><br /><br /><span data-ttu-id="4b820-130">La valeur par défaut est Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="4b820-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="4b820-131">Cet attribut est de type <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="4b820-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="4b820-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="4b820-132">writeEncoding</span></span>|<span data-ttu-id="4b820-133">Spécifie l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="4b820-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4b820-134">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="4b820-134">Valid values are</span></span><br /><br /> <span data-ttu-id="4b820-135">UnicodeFffeTextEncoding Encodage BigEndian Unicode</span><span class="sxs-lookup"><span data-stu-id="4b820-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="4b820-136">Utf16TextEncoding Encodage Unicode</span><span class="sxs-lookup"><span data-stu-id="4b820-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="4b820-137">Utf8TextEncoding encodage 8 bits</span><span class="sxs-lookup"><span data-stu-id="4b820-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="4b820-138">La valeur par défaut est Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="4b820-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="4b820-139">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="4b820-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4b820-140">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4b820-140">Child Elements</span></span>  
  
|<span data-ttu-id="4b820-141">Élément</span><span class="sxs-lookup"><span data-stu-id="4b820-141">Element</span></span>|<span data-ttu-id="4b820-142">Description</span><span class="sxs-lookup"><span data-stu-id="4b820-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b820-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4b820-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="4b820-144">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="4b820-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4b820-145">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="4b820-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b820-146">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4b820-146">Parent Elements</span></span>  
  
|<span data-ttu-id="4b820-147">Élément</span><span class="sxs-lookup"><span data-stu-id="4b820-147">Element</span></span>|<span data-ttu-id="4b820-148">Description</span><span class="sxs-lookup"><span data-stu-id="4b820-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4b820-149">\<binding></span><span class="sxs-lookup"><span data-stu-id="4b820-149">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="4b820-150">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="4b820-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b820-151">Notes</span><span class="sxs-lookup"><span data-stu-id="4b820-151">Remarks</span></span>  
 <span data-ttu-id="4b820-152">L'encodage est le processus de transformation d'un message en une séquence d'octets.</span><span class="sxs-lookup"><span data-stu-id="4b820-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="4b820-153">Le décodage est le processus inverse.</span><span class="sxs-lookup"><span data-stu-id="4b820-153">Decoding is the reverse process.</span></span> <span data-ttu-id="4b820-154">Windows Communication Foundation (WCF) comprend trois types d’encodage pour les messages SOAP : Texte, binaire et MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="4b820-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="4b820-155">L'encodage de texte représenté par l'élément `textMessageEncoding` est l'encodeur le plus interopérable, mais le moins efficace pour les messages XML.</span><span class="sxs-lookup"><span data-stu-id="4b820-155">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="4b820-156">L'encodeur de texte crée des messages textuels sur le câble.</span><span class="sxs-lookup"><span data-stu-id="4b820-156">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="4b820-157">Les messages produits par cet encodeur sont adaptés à l'interopérabilité basée sur WS-\*.</span><span class="sxs-lookup"><span data-stu-id="4b820-157">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="4b820-158">Les services Web ou les clients de ces services comprennent généralement le XML textuel.</span><span class="sxs-lookup"><span data-stu-id="4b820-158">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="4b820-159">Toutefois, la transmission de grands blocs de données binaires sous forme de texte est la méthode d'encodage de messages XML la moins efficace.</span><span class="sxs-lookup"><span data-stu-id="4b820-159">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b820-160">Exemples</span><span class="sxs-lookup"><span data-stu-id="4b820-160">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="4b820-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b820-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="4b820-162">Sélection d’un encodeur de message</span><span class="sxs-lookup"><span data-stu-id="4b820-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="4b820-163">Encodage de message</span><span class="sxs-lookup"><span data-stu-id="4b820-163">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="4b820-164">Liaisons</span><span class="sxs-lookup"><span data-stu-id="4b820-164">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4b820-165">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="4b820-165">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4b820-166">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="4b820-166">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4b820-167">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4b820-167">\<customBinding></span></span>](custombinding.md)

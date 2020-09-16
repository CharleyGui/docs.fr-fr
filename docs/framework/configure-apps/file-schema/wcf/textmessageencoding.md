---
title: <textMessageEncoding>
ms.date: 03/30/2017
ms.assetid: e6d834d0-356e-45eb-b530-bbefbb9ec3f0
ms.openlocfilehash: c5cd8e9e2002f44fd9feebdc6bb7ede023de459a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556445"
---
# \<textMessageEncoding>
<span data-ttu-id="d272f-101">Spécifie l'encodage de caractères et le suivi des versions de message utilisés pour les messages XML textuels.</span><span class="sxs-lookup"><span data-stu-id="d272f-101">Specifies the character encoding and message versioning used for text-based XML messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<textMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="d272f-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d272f-102">Syntax</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing10/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d272f-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="d272f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d272f-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="d272f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d272f-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="d272f-105">Attributes</span></span>  
  
|<span data-ttu-id="d272f-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="d272f-106">Attribute</span></span>|<span data-ttu-id="d272f-107">Description</span><span class="sxs-lookup"><span data-stu-id="d272f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d272f-108">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="d272f-108">maxReadPoolSize</span></span>|<span data-ttu-id="d272f-109">Entier qui spécifie combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="d272f-109">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="d272f-110">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="d272f-110">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="d272f-111">La valeur par défaut est 64.</span><span class="sxs-lookup"><span data-stu-id="d272f-111">The default is 64.</span></span>|  
|<span data-ttu-id="d272f-112">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="d272f-112">maxWritePoolSize</span></span>|<span data-ttu-id="d272f-113">Entier qui spécifie combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="d272f-113">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="d272f-114">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="d272f-114">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="d272f-115">La valeur par défaut est 16.</span><span class="sxs-lookup"><span data-stu-id="d272f-115">The default is 16.</span></span>|  
|<span data-ttu-id="d272f-116">messageVersion</span><span class="sxs-lookup"><span data-stu-id="d272f-116">messageVersion</span></span>|<span data-ttu-id="d272f-117">Spécifie la version SOAP des messages envoyés à l'aide de la liaison.</span><span class="sxs-lookup"><span data-stu-id="d272f-117">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="d272f-118">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d272f-118">Valid values are</span></span><br /><br /> <span data-ttu-id="d272f-119">- Soap11Addressing10</span><span class="sxs-lookup"><span data-stu-id="d272f-119">-   Soap11Addressing10</span></span><br /><span data-ttu-id="d272f-120">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="d272f-120">-   Soap12Addressing10</span></span><br /><span data-ttu-id="d272f-121">- Soap11</span><span class="sxs-lookup"><span data-stu-id="d272f-121">-   Soap11</span></span><br /><span data-ttu-id="d272f-122">-Soap12</span><span class="sxs-lookup"><span data-stu-id="d272f-122">-  Soap12</span></span><br /><br /><span data-ttu-id="d272f-123">La valeur par défaut est Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="d272f-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="d272f-124">Cet attribut est de type <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="d272f-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="d272f-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="d272f-125">writeEncoding</span></span>|<span data-ttu-id="d272f-126">Spécifie l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="d272f-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="d272f-127">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="d272f-127">Valid values are</span></span><br /><br /> <span data-ttu-id="d272f-128">-UnicodeFffeTextEncoding : encodage BigEndian Unicode</span><span class="sxs-lookup"><span data-stu-id="d272f-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="d272f-129">-Utf16TextEncoding : encodage Unicode</span><span class="sxs-lookup"><span data-stu-id="d272f-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="d272f-130">-Utf8TextEncoding : encodage 8 bits</span><span class="sxs-lookup"><span data-stu-id="d272f-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="d272f-131">La valeur par défaut est Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="d272f-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="d272f-132">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="d272f-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d272f-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="d272f-133">Child Elements</span></span>  
  
|<span data-ttu-id="d272f-134">Élément</span><span class="sxs-lookup"><span data-stu-id="d272f-134">Element</span></span>|<span data-ttu-id="d272f-135">Description</span><span class="sxs-lookup"><span data-stu-id="d272f-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="d272f-136">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="d272f-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="d272f-137">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="d272f-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d272f-138">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="d272f-138">Parent Elements</span></span>  
  
|<span data-ttu-id="d272f-139">Élément</span><span class="sxs-lookup"><span data-stu-id="d272f-139">Element</span></span>|<span data-ttu-id="d272f-140">Description</span><span class="sxs-lookup"><span data-stu-id="d272f-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="d272f-141">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="d272f-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d272f-142">Notes</span><span class="sxs-lookup"><span data-stu-id="d272f-142">Remarks</span></span>  
 <span data-ttu-id="d272f-143">L'encodage est le processus de transformation d'un message en une séquence d'octets.</span><span class="sxs-lookup"><span data-stu-id="d272f-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="d272f-144">Le décodage est le processus inverse.</span><span class="sxs-lookup"><span data-stu-id="d272f-144">Decoding is the reverse process.</span></span> <span data-ttu-id="d272f-145">Windows Communication Foundation (WCF) inclut trois types d'encodage des messages SOAP : Texte, Binaire et MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="d272f-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="d272f-146">L'encodage de texte représenté par l'élément `textMessageEncoding` est l'encodeur le plus interopérable, mais le moins efficace pour les messages XML.</span><span class="sxs-lookup"><span data-stu-id="d272f-146">The text encoding represented by the `textMessageEncoding` element is the most interoperable, but the least efficient encoder for XML messages.</span></span>  <span data-ttu-id="d272f-147">L'encodeur de texte crée des messages textuels sur le câble.</span><span class="sxs-lookup"><span data-stu-id="d272f-147">The text encoder creates text-based messages on the wire.</span></span> <span data-ttu-id="d272f-148">Les messages produits par cet encodeur sont adaptés à l'interopérabilité basée sur WS-\*.</span><span class="sxs-lookup"><span data-stu-id="d272f-148">Messages produced by this encoder are suitable for WS-\* based interop.</span></span> <span data-ttu-id="d272f-149">Les services Web ou les clients de ces services comprennent généralement le XML textuel.</span><span class="sxs-lookup"><span data-stu-id="d272f-149">Web service or Web service client can generally understand textual XML.</span></span> <span data-ttu-id="d272f-150">Toutefois, la transmission de grands blocs de données binaires sous forme de texte est la méthode d'encodage de messages XML la moins efficace.</span><span class="sxs-lookup"><span data-stu-id="d272f-150">However, transmitting large blocks of binary data as text is the least efficient method for encoding XML messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d272f-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="d272f-151">Example</span></span>  
  
```xml  
<textMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap12Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="d272f-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d272f-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.TextMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- [<span data-ttu-id="d272f-153">Sélection d'un encodeur de message</span><span class="sxs-lookup"><span data-stu-id="d272f-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="d272f-154">Encodage de message</span><span class="sxs-lookup"><span data-stu-id="d272f-154">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="d272f-155">Liaisons</span><span class="sxs-lookup"><span data-stu-id="d272f-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d272f-156">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="d272f-156">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d272f-157">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="d272f-157">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

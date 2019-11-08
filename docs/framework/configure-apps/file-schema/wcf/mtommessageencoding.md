---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: bd38bf812e6d8d9e57d99bf1a5b77ebb776193a5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738841"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="2b314-101">\<mtomMessageEncoding ></span><span class="sxs-lookup"><span data-stu-id="2b314-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="2b314-102">Spécifie l'encodage et le suivi des versions de message utilisés pour les messages basés sur MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="2b314-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
<span data-ttu-id="2b314-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b314-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2b314-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="2b314-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2b314-105">&nbsp;&nbsp;&nbsp;&nbsp;[**liaisons**](bindings.md)\<</span><span class="sxs-lookup"><span data-stu-id="2b314-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\</span></span>
<span data-ttu-id="2b314-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="2b314-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="2b314-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\< \**\**</span><span class="sxs-lookup"><span data-stu-id="2b314-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\</span></span>
<span data-ttu-id="2b314-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**mtomMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="2b314-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b314-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b314-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b314-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2b314-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2b314-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2b314-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b314-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="2b314-112">Attributes</span></span>  
  
|<span data-ttu-id="2b314-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="2b314-113">Attribute</span></span>|<span data-ttu-id="2b314-114">Description</span><span class="sxs-lookup"><span data-stu-id="2b314-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b314-115">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="2b314-115">maxBufferSize</span></span>|<span data-ttu-id="2b314-116">Entier qui spécifie la taille maximale de la mémoire tampon qui peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="2b314-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="2b314-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="2b314-117">maxReadPoolSize</span></span>|<span data-ttu-id="2b314-118">Entier qui spécifie combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="2b314-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="2b314-119">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="2b314-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="2b314-120">La valeur par défaut est 64.</span><span class="sxs-lookup"><span data-stu-id="2b314-120">The default is 64.</span></span>|  
|<span data-ttu-id="2b314-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="2b314-121">maxWritePoolSize</span></span>|<span data-ttu-id="2b314-122">Entier qui spécifie combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="2b314-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="2b314-123">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="2b314-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="2b314-124">La valeur par défaut est 16.</span><span class="sxs-lookup"><span data-stu-id="2b314-124">The default is 16.</span></span>|  
|<span data-ttu-id="2b314-125">messageVersion</span><span class="sxs-lookup"><span data-stu-id="2b314-125">messageVersion</span></span>|<span data-ttu-id="2b314-126">Spécifie la version SOAP des messages envoyés à l'aide de la liaison.</span><span class="sxs-lookup"><span data-stu-id="2b314-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="2b314-127">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="2b314-127">Valid values are</span></span><br /><br /> <span data-ttu-id="2b314-128">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="2b314-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="2b314-129">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="2b314-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="2b314-130">La valeur par défaut est Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="2b314-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="2b314-131">Cet attribut est de type <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="2b314-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="2b314-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="2b314-132">writeEncoding</span></span>|<span data-ttu-id="2b314-133">Spécifie l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="2b314-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="2b314-134">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="2b314-134">Valid values are</span></span><br /><br /> <span data-ttu-id="2b314-135">-UnicodeFffeTextEncoding : encodage BigEndian Unicode</span><span class="sxs-lookup"><span data-stu-id="2b314-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="2b314-136">-Utf16TextEncoding : encodage Unicode</span><span class="sxs-lookup"><span data-stu-id="2b314-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="2b314-137">-Utf8TextEncoding : encodage 8 bits</span><span class="sxs-lookup"><span data-stu-id="2b314-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="2b314-138">La valeur par défaut est Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="2b314-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="2b314-139">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="2b314-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b314-140">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2b314-140">Child Elements</span></span>  
  
|<span data-ttu-id="2b314-141">Élément</span><span class="sxs-lookup"><span data-stu-id="2b314-141">Element</span></span>|<span data-ttu-id="2b314-142">Description</span><span class="sxs-lookup"><span data-stu-id="2b314-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2b314-143">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2b314-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="2b314-144">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="2b314-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="2b314-145">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="2b314-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b314-146">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2b314-146">Parent Elements</span></span>  
  
|<span data-ttu-id="2b314-147">Élément</span><span class="sxs-lookup"><span data-stu-id="2b314-147">Element</span></span>|<span data-ttu-id="2b314-148">Description</span><span class="sxs-lookup"><span data-stu-id="2b314-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b314-149">liaison de \<</span><span class="sxs-lookup"><span data-stu-id="2b314-149">\<binding></span></span>](bindings.md)|<span data-ttu-id="2b314-150">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="2b314-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b314-151">Notes</span><span class="sxs-lookup"><span data-stu-id="2b314-151">Remarks</span></span>  
 <span data-ttu-id="2b314-152">L'encodage est le processus de transformation d'un message en une séquence d'octets.</span><span class="sxs-lookup"><span data-stu-id="2b314-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="2b314-153">Le décodage est le processus inverse.</span><span class="sxs-lookup"><span data-stu-id="2b314-153">Decoding is the reverse process.</span></span> <span data-ttu-id="2b314-154">Windows Communication Foundation (WCF) inclut trois types d'encodage des messages SOAP : Texte, Binaire et MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="2b314-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="2b314-155">L'élément `MtomMessageEncoding` spécifie l'encodage de caractères et le contrôle de version de message, ainsi que d'autres paramètres utilisés pour un message encodé avec MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="2b314-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="2b314-156">MTOM est une technologie efficace de transmission de données binaires dans les messages WCF.</span><span class="sxs-lookup"><span data-stu-id="2b314-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="2b314-157">L'encodeur MTOM tente de créer un équilibre entre rendement et interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="2b314-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="2b314-158">L'encodage MTOM transmet la plupart des données XML sous forme textuelle, mais optimise les blocs de données binaires volumineux en les transmettant tels quels, sans conversion au format base64 encodé.</span><span class="sxs-lookup"><span data-stu-id="2b314-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b314-159">Exemple</span><span class="sxs-lookup"><span data-stu-id="2b314-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="2b314-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b314-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="2b314-161">Encodage de message</span><span class="sxs-lookup"><span data-stu-id="2b314-161">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="2b314-162">Sélection d’un encodeur de message</span><span class="sxs-lookup"><span data-stu-id="2b314-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="2b314-163">Liaisons</span><span class="sxs-lookup"><span data-stu-id="2b314-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2b314-164">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="2b314-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="2b314-165">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="2b314-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="2b314-166">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2b314-166">\<customBinding></span></span>](custombinding.md)

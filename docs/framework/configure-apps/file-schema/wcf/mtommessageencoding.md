---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: 538591c85d91960eb4d4fa04caa945954ee5a997
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397700"
---
# <a name="mtommessageencoding"></a><span data-ttu-id="b6d15-101">\<mtomMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="b6d15-101">\<mtomMessageEncoding></span></span>
<span data-ttu-id="b6d15-102">Spécifie l'encodage et le suivi des versions de message utilisés pour les messages basés sur MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="b6d15-102">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
<span data-ttu-id="b6d15-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b6d15-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b6d15-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b6d15-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b6d15-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<liaisons >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b6d15-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b6d15-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="b6d15-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="b6d15-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de liaison**</span><span class="sxs-lookup"><span data-stu-id="b6d15-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b6d15-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mtomMessageEncoding >**</span><span class="sxs-lookup"><span data-stu-id="b6d15-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6d15-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6d15-109">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6d15-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="b6d15-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b6d15-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="b6d15-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6d15-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="b6d15-112">Attributes</span></span>  
  
|<span data-ttu-id="b6d15-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="b6d15-113">Attribute</span></span>|<span data-ttu-id="b6d15-114">Description</span><span class="sxs-lookup"><span data-stu-id="b6d15-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6d15-115">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="b6d15-115">maxBufferSize</span></span>|<span data-ttu-id="b6d15-116">Entier qui spécifie la taille maximale de la mémoire tampon qui peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="b6d15-116">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="b6d15-117">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="b6d15-117">maxReadPoolSize</span></span>|<span data-ttu-id="b6d15-118">Entier qui spécifie combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="b6d15-118">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="b6d15-119">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="b6d15-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="b6d15-120">La valeur par défaut est 64.</span><span class="sxs-lookup"><span data-stu-id="b6d15-120">The default is 64.</span></span>|  
|<span data-ttu-id="b6d15-121">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="b6d15-121">maxWritePoolSize</span></span>|<span data-ttu-id="b6d15-122">Entier qui spécifie combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="b6d15-122">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="b6d15-123">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="b6d15-123">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="b6d15-124">La valeur par défaut est 16.</span><span class="sxs-lookup"><span data-stu-id="b6d15-124">The default is 16.</span></span>|  
|<span data-ttu-id="b6d15-125">messageVersion</span><span class="sxs-lookup"><span data-stu-id="b6d15-125">messageVersion</span></span>|<span data-ttu-id="b6d15-126">Spécifie la version SOAP des messages envoyés à l'aide de la liaison.</span><span class="sxs-lookup"><span data-stu-id="b6d15-126">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="b6d15-127">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b6d15-127">Valid values are</span></span><br /><br /> <span data-ttu-id="b6d15-128">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="b6d15-128">-   Soap11Addressing1</span></span><br /><span data-ttu-id="b6d15-129">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="b6d15-129">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="b6d15-130">La valeur par défaut est Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="b6d15-130">The default is Soap12Addressing10.</span></span> <span data-ttu-id="b6d15-131">Cet attribut est de type <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="b6d15-131">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="b6d15-132">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="b6d15-132">writeEncoding</span></span>|<span data-ttu-id="b6d15-133">Spécifie l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="b6d15-133">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="b6d15-134">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b6d15-134">Valid values are</span></span><br /><br /> <span data-ttu-id="b6d15-135">UnicodeFffeTextEncoding Encodage BigEndian Unicode</span><span class="sxs-lookup"><span data-stu-id="b6d15-135">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="b6d15-136">Utf16TextEncoding Encodage Unicode</span><span class="sxs-lookup"><span data-stu-id="b6d15-136">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="b6d15-137">Utf8TextEncoding encodage 8 bits</span><span class="sxs-lookup"><span data-stu-id="b6d15-137">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="b6d15-138">La valeur par défaut est Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="b6d15-138">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="b6d15-139">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="b6d15-139">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6d15-140">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="b6d15-140">Child Elements</span></span>  
  
|<span data-ttu-id="b6d15-141">Élément</span><span class="sxs-lookup"><span data-stu-id="b6d15-141">Element</span></span>|<span data-ttu-id="b6d15-142">Description</span><span class="sxs-lookup"><span data-stu-id="b6d15-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b6d15-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b6d15-143">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="b6d15-144">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="b6d15-144">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b6d15-145">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="b6d15-145">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6d15-146">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="b6d15-146">Parent Elements</span></span>  
  
|<span data-ttu-id="b6d15-147">Élément</span><span class="sxs-lookup"><span data-stu-id="b6d15-147">Element</span></span>|<span data-ttu-id="b6d15-148">Description</span><span class="sxs-lookup"><span data-stu-id="b6d15-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6d15-149">\<binding></span><span class="sxs-lookup"><span data-stu-id="b6d15-149">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="b6d15-150">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="b6d15-150">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6d15-151">Notes</span><span class="sxs-lookup"><span data-stu-id="b6d15-151">Remarks</span></span>  
 <span data-ttu-id="b6d15-152">L'encodage est le processus de transformation d'un message en une séquence d'octets.</span><span class="sxs-lookup"><span data-stu-id="b6d15-152">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="b6d15-153">Le décodage est le processus inverse.</span><span class="sxs-lookup"><span data-stu-id="b6d15-153">Decoding is the reverse process.</span></span> <span data-ttu-id="b6d15-154">Windows Communication Foundation (WCF) comprend trois types d’encodage pour les messages SOAP : Texte, binaire et MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="b6d15-154">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="b6d15-155">L'élément `MtomMessageEncoding` spécifie l'encodage de caractères et le contrôle de version de message, ainsi que d'autres paramètres utilisés pour un message encodé avec MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="b6d15-155">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="b6d15-156">MTOM est une technologie efficace de transmission de données binaires dans les messages WCF.</span><span class="sxs-lookup"><span data-stu-id="b6d15-156">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="b6d15-157">L'encodeur MTOM tente de créer un équilibre entre rendement et interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="b6d15-157">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="b6d15-158">L'encodage MTOM transmet la plupart des données XML sous forme textuelle, mais optimise les blocs de données binaires volumineux en les transmettant tels quels, sans conversion au format base64 encodé.</span><span class="sxs-lookup"><span data-stu-id="b6d15-158">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6d15-159">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6d15-159">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="b6d15-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6d15-160">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="b6d15-161">Encodage de message</span><span class="sxs-lookup"><span data-stu-id="b6d15-161">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="b6d15-162">Sélection d’un encodeur de message</span><span class="sxs-lookup"><span data-stu-id="b6d15-162">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="b6d15-163">Liaisons</span><span class="sxs-lookup"><span data-stu-id="b6d15-163">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b6d15-164">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="b6d15-164">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b6d15-165">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="b6d15-165">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="b6d15-166">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="b6d15-166">\<customBinding></span></span>](custombinding.md)

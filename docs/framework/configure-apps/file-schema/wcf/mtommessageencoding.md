---
title: <mtomMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 7865d171-cd1e-430a-8421-39cc13541d1b
ms.openlocfilehash: cffde19c8fd06836eaaedb5c4fc8687b97ae0afe
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556178"
---
# \<mtomMessageEncoding>
<span data-ttu-id="29362-101">Spécifie l'encodage et le suivi des versions de message utilisés pour les messages basés sur MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="29362-101">Specifies the encoding and message versioning used for SOAP Message Transmission Optimization Mechanism (MTOM) based messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mtomMessageEncoding>**  
  
## <a name="syntax"></a><span data-ttu-id="29362-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29362-102">Syntax</span></span>  
  
```xml  
<mtomMessageEncoding maxBufferSize="Integer"
                     maxReadPoolSize="Integer"
                     maxWritePoolSize="Integer"
                     messageVersion="Soap11Addressing1/Soap12Addressing10"
                     writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29362-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="29362-103">Attributes and Elements</span></span>  
 <span data-ttu-id="29362-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="29362-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29362-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="29362-105">Attributes</span></span>  
  
|<span data-ttu-id="29362-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="29362-106">Attribute</span></span>|<span data-ttu-id="29362-107">Description</span><span class="sxs-lookup"><span data-stu-id="29362-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29362-108">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="29362-108">maxBufferSize</span></span>|<span data-ttu-id="29362-109">Entier qui spécifie la taille maximale de la mémoire tampon qui peut être utilisée.</span><span class="sxs-lookup"><span data-stu-id="29362-109">An integer that specifies the maximum size of the buffer that can be used.</span></span>|  
|<span data-ttu-id="29362-110">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="29362-110">maxReadPoolSize</span></span>|<span data-ttu-id="29362-111">Entier qui spécifie combien de messages peuvent être lus de manière simultanée sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="29362-111">An integer that specifies how many messages can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="29362-112">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="29362-112">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="29362-113">La valeur par défaut est 64.</span><span class="sxs-lookup"><span data-stu-id="29362-113">The default is 64.</span></span>|  
|<span data-ttu-id="29362-114">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="29362-114">maxWritePoolSize</span></span>|<span data-ttu-id="29362-115">Entier qui spécifie combien de messages peuvent être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="29362-115">An integer that specifies how many messages can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="29362-116">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="29362-116">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="29362-117">La valeur par défaut est 16.</span><span class="sxs-lookup"><span data-stu-id="29362-117">The default is 16.</span></span>|  
|<span data-ttu-id="29362-118">messageVersion</span><span class="sxs-lookup"><span data-stu-id="29362-118">messageVersion</span></span>|<span data-ttu-id="29362-119">Spécifie la version SOAP des messages envoyés à l'aide de la liaison.</span><span class="sxs-lookup"><span data-stu-id="29362-119">Specifies the SOAP version of the messages sent using the binding.</span></span> <span data-ttu-id="29362-120">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="29362-120">Valid values are</span></span><br /><br /> <span data-ttu-id="29362-121">- Soap11Addressing1</span><span class="sxs-lookup"><span data-stu-id="29362-121">-   Soap11Addressing1</span></span><br /><span data-ttu-id="29362-122">- Soap12Addressing10</span><span class="sxs-lookup"><span data-stu-id="29362-122">-   Soap12Addressing10</span></span><br /><br /> <span data-ttu-id="29362-123">La valeur par défaut est Soap12Addressing10.</span><span class="sxs-lookup"><span data-stu-id="29362-123">The default is Soap12Addressing10.</span></span> <span data-ttu-id="29362-124">Cet attribut est de type <xref:System.ServiceModel.Channels.MessageVersion>.</span><span class="sxs-lookup"><span data-stu-id="29362-124">This attribute is of type <xref:System.ServiceModel.Channels.MessageVersion>.</span></span>|  
|<span data-ttu-id="29362-125">writeEncoding</span><span class="sxs-lookup"><span data-stu-id="29362-125">writeEncoding</span></span>|<span data-ttu-id="29362-126">Spécifie l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="29362-126">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="29362-127">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="29362-127">Valid values are</span></span><br /><br /> <span data-ttu-id="29362-128">-UnicodeFffeTextEncoding : encodage BigEndian Unicode</span><span class="sxs-lookup"><span data-stu-id="29362-128">-   UnicodeFffeTextEncoding: Unicode BigEndian encoding</span></span><br /><span data-ttu-id="29362-129">-Utf16TextEncoding : encodage Unicode</span><span class="sxs-lookup"><span data-stu-id="29362-129">-   Utf16TextEncoding: Unicode encoding</span></span><br /><span data-ttu-id="29362-130">-Utf8TextEncoding : encodage 8 bits</span><span class="sxs-lookup"><span data-stu-id="29362-130">-   Utf8TextEncoding: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="29362-131">La valeur par défaut est Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="29362-131">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="29362-132">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="29362-132">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29362-133">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="29362-133">Child Elements</span></span>  
  
|<span data-ttu-id="29362-134">Élément</span><span class="sxs-lookup"><span data-stu-id="29362-134">Element</span></span>|<span data-ttu-id="29362-135">Description</span><span class="sxs-lookup"><span data-stu-id="29362-135">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="29362-136">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="29362-136">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="29362-137">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="29362-137">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29362-138">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="29362-138">Parent Elements</span></span>  
  
|<span data-ttu-id="29362-139">Élément</span><span class="sxs-lookup"><span data-stu-id="29362-139">Element</span></span>|<span data-ttu-id="29362-140">Description</span><span class="sxs-lookup"><span data-stu-id="29362-140">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="29362-141">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="29362-141">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29362-142">Notes</span><span class="sxs-lookup"><span data-stu-id="29362-142">Remarks</span></span>  
 <span data-ttu-id="29362-143">L'encodage est le processus de transformation d'un message en une séquence d'octets.</span><span class="sxs-lookup"><span data-stu-id="29362-143">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="29362-144">Le décodage est le processus inverse.</span><span class="sxs-lookup"><span data-stu-id="29362-144">Decoding is the reverse process.</span></span> <span data-ttu-id="29362-145">Windows Communication Foundation (WCF) inclut trois types d'encodage des messages SOAP : Texte, Binaire et MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="29362-145">Windows Communication Foundation (WCF) includes three types of encoding for SOAP messages: Text, Binary and Message Transmission Optimization Mechanism (MTOM).</span></span>  
  
 <span data-ttu-id="29362-146">L'élément `MtomMessageEncoding` spécifie l'encodage de caractères et le contrôle de version de message, ainsi que d'autres paramètres utilisés pour un message encodé avec MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="29362-146">The `MtomMessageEncoding` element specifies the character encoding and message versioning and other settings used for messages using a Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="29362-147">MTOM est une technologie efficace de transmission de données binaires dans les messages WCF.</span><span class="sxs-lookup"><span data-stu-id="29362-147">MTOM is an efficient technology for transmitting binary data in WCF messages.</span></span> <span data-ttu-id="29362-148">L'encodeur MTOM tente de créer un équilibre entre rendement et interopérabilité.</span><span class="sxs-lookup"><span data-stu-id="29362-148">The MTOM encoder attempts to create a balance between efficiency and interoperability.</span></span> <span data-ttu-id="29362-149">L'encodage MTOM transmet la plupart des données XML sous forme textuelle, mais optimise les blocs de données binaires volumineux en les transmettant tels quels, sans conversion au format base64 encodé.</span><span class="sxs-lookup"><span data-stu-id="29362-149">The MTOM encoding transmits most XML in textual form, but optimizes large blocks of binary data by transmitting them as-is, without conversion to their base64 encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29362-150">Exemple</span><span class="sxs-lookup"><span data-stu-id="29362-150">Example</span></span>  
  
```xml  
<mtomMessageEncoding maxReadPoolSize="211"
                     maxWritePoolSize="2132"
                     messageVersion="Soap11Addressing10"
                     textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="29362-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29362-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.MtomMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
- [<span data-ttu-id="29362-152">Encodage de message</span><span class="sxs-lookup"><span data-stu-id="29362-152">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="29362-153">Sélection d'un encodeur de message</span><span class="sxs-lookup"><span data-stu-id="29362-153">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="29362-154">Liaisons</span><span class="sxs-lookup"><span data-stu-id="29362-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="29362-155">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="29362-155">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="29362-156">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="29362-156">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)

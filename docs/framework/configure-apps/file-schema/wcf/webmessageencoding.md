---
title: <webMessageEncoding>
ms.date: 03/30/2017
ms.assetid: 892ca485-e21a-4a44-8e40-633161ef6796
ms.openlocfilehash: a1d776730053cd6af3c930a33e13582a8906c4d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940397"
---
# <a name="webmessageencoding"></a><span data-ttu-id="4a981-101">\<webMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="4a981-101">\<webMessageEncoding></span></span>
<span data-ttu-id="4a981-102">Permet de lire et d’écrire du contenu XML en texte brut, les encodages de message JSON (JavaScript Objet Notation) et du contenu binaire brut dans une liaison Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4a981-102">Enables plain-text XML, JavaScript Object Notation (JSON) message encodings and "raw" binary content to be read and written when used in a Windows Communication Foundation (WCF) binding.</span></span>  
  
 <span data-ttu-id="4a981-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="4a981-103">\<system.serviceModel></span></span>  
<span data-ttu-id="4a981-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="4a981-104">\<bindings></span></span>  
<span data-ttu-id="4a981-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4a981-105">\<customBinding></span></span>  
<span data-ttu-id="4a981-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="4a981-106">\<binding></span></span>  
<span data-ttu-id="4a981-107">\<webMessageEncoding></span><span class="sxs-lookup"><span data-stu-id="4a981-107">\<webMessageEncoding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a981-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a981-108">Syntax</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="Integer"
                    maxWritePoolSize="Integer"
                    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a981-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="4a981-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4a981-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="4a981-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a981-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="4a981-111">Attributes</span></span>  
  
|<span data-ttu-id="4a981-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="4a981-112">Attribute</span></span>|<span data-ttu-id="4a981-113">Description</span><span class="sxs-lookup"><span data-stu-id="4a981-113">Description</span></span>|  
|---------------|-----------------|  
|`maxReadPoolSize`|<span data-ttu-id="4a981-114">Quantité maximale de messages pouvant être consultés simultanément sans allouer de nouveaux lecteurs.</span><span class="sxs-lookup"><span data-stu-id="4a981-114">The amount of messages that can be read simultaneously without allocating new readers.</span></span> <span data-ttu-id="4a981-115">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="4a981-115">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4a981-116">La valeur par défaut est de 64 lecteurs par encodeur interne (texte, JSON, et « brut »).</span><span class="sxs-lookup"><span data-stu-id="4a981-116">The default is 64 readers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="4a981-117">L'augmentation de ce nombre entraîne celle de la consommation de mémoire, mais prépare l'encodeur afin de traiter les rafales soudaines de messages entrants. En effet, il peut ainsi utiliser les lecteurs existants du pool au lieu d'en créer.</span><span class="sxs-lookup"><span data-stu-id="4a981-117">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of incoming messages because it is able to use readers from the pool that are already created instead of creating new ones.</span></span>|  
|`maxWritePoolSize`|<span data-ttu-id="4a981-118">Quantité maximale de messages pouvant être envoyés simultanément sans allouer de nouveaux enregistreurs.</span><span class="sxs-lookup"><span data-stu-id="4a981-118">The amount of messages that can be sent simultaneously without allocating new writers.</span></span> <span data-ttu-id="4a981-119">Des pools plus volumineux permettent au système d'être plus tolérant aux pics d'activité au prix d'une plage de travail plus volumineuse.</span><span class="sxs-lookup"><span data-stu-id="4a981-119">Larger pool sizes make the system more tolerant to activity spikes at the cost of a larger working set.</span></span> <span data-ttu-id="4a981-120">La valeur par défaut est de 16 enregistreurs par encodeur interne (texte, JSON, et « brut »).</span><span class="sxs-lookup"><span data-stu-id="4a981-120">The default is 16 writers for each of the inner encoders (text, JSON, and "raw").</span></span><br /><br /> <span data-ttu-id="4a981-121">L'augmentation de ce nombre entraîne celle de la consommation de mémoire, mais prépare l'encodeur afin de traiter les rafales soudaines de messages sortants. En effet, il peut ainsi utiliser les writers existants du pool au lieu d'en créer.</span><span class="sxs-lookup"><span data-stu-id="4a981-121">Increasing this number increases memory consumption, but prepares the encoder to deal with sudden bursts of outgoing messages because it is able to use writers from the pool that are already created instead of creating new ones.</span></span>|  
|`writeEncoding`|<span data-ttu-id="4a981-122">Spécifie l'encodage de jeu de caractères à utiliser pour l'émission de messages sur la liaison.</span><span class="sxs-lookup"><span data-stu-id="4a981-122">Specifies the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="4a981-123">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="4a981-123">Valid values are:</span></span><br /><br /> <span data-ttu-id="4a981-124">UnicodeFffeTextEncoding Encodage Unicode Big endian.</span><span class="sxs-lookup"><span data-stu-id="4a981-124">-   UnicodeFffeTextEncoding: Unicode Big Endian encoding.</span></span><br /><span data-ttu-id="4a981-125">Utf16TextEncoding Encodage Unicode.</span><span class="sxs-lookup"><span data-stu-id="4a981-125">-   Utf16TextEncoding: Unicode encoding.</span></span><br /><span data-ttu-id="4a981-126">Utf8TextEncoding encodage 8 bits.</span><span class="sxs-lookup"><span data-stu-id="4a981-126">-   Utf8TextEncoding: 8-bit encoding.</span></span><br /><br /> <span data-ttu-id="4a981-127">La valeur par défaut est Utf8TextEncoding.</span><span class="sxs-lookup"><span data-stu-id="4a981-127">The default is Utf8TextEncoding.</span></span> <span data-ttu-id="4a981-128">Cet attribut est de type <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="4a981-128">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a981-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="4a981-129">Child Elements</span></span>  
  
|<span data-ttu-id="4a981-130">Élément</span><span class="sxs-lookup"><span data-stu-id="4a981-130">Element</span></span>|<span data-ttu-id="4a981-131">Description</span><span class="sxs-lookup"><span data-stu-id="4a981-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a981-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4a981-132">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="4a981-133">Définit les contraintes sur la complexité des messages SOAP pouvant être traités par les points de terminaison configurés avec cette liaison.</span><span class="sxs-lookup"><span data-stu-id="4a981-133">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4a981-134">Cet élément est de type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="4a981-134">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a981-135">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="4a981-135">Parent Elements</span></span>  
  
|<span data-ttu-id="4a981-136">Élément</span><span class="sxs-lookup"><span data-stu-id="4a981-136">Element</span></span>|<span data-ttu-id="4a981-137">Description</span><span class="sxs-lookup"><span data-stu-id="4a981-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a981-138">\<binding></span><span class="sxs-lookup"><span data-stu-id="4a981-138">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="4a981-139">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="4a981-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a981-140">Notes</span><span class="sxs-lookup"><span data-stu-id="4a981-140">Remarks</span></span>  
 <span data-ttu-id="4a981-141">L'encodage est le processus de transformation d'un message en une séquence d'octets.</span><span class="sxs-lookup"><span data-stu-id="4a981-141">Encoding is the process of transforming a message into a sequence of bytes.</span></span> <span data-ttu-id="4a981-142">Le décodage est le processus inverse.</span><span class="sxs-lookup"><span data-stu-id="4a981-142">Decoding is the reverse process.</span></span> <span data-ttu-id="4a981-143">Ces processus nécessitent l'encodage de caractères à titre de spécification.</span><span class="sxs-lookup"><span data-stu-id="4a981-143">These processes require the specification of a character encoding.</span></span>  
  
 <span data-ttu-id="4a981-144">L'élément `webMessageEncoding` fonctionne par délégation à une série d'encodeurs internes afin de gérer les données XML de texte brut, les encodages JSON et les données binaires brutes.</span><span class="sxs-lookup"><span data-stu-id="4a981-144">The `webMessageEncoding` element works by delegating to a series of inner encoders to handle the plain-text XML and JSON encodings, and "raw" binary data.</span></span> <span data-ttu-id="4a981-145">Cette délégation a lieu par le biais d'un encodeur de message composite.</span><span class="sxs-lookup"><span data-stu-id="4a981-145">This delegation is done by a composite message encoder.</span></span>  
  
 <span data-ttu-id="4a981-146">Cet élément de liaison et son encodeur composite sont utilisés pour contrôler l’encodage dans des scénarios qui n’utilisent pas la messagerie SOAP utilisée par l’élément `webHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="4a981-146">This binding element and its composite encoder are used to control the encoding in scenarios that do not use SOAP messaging used by the `webHttpBinding` element.</span></span> <span data-ttu-id="4a981-147">Ces scénarios incluent les protocoles POX (Plain Old XML) et REST (Representational State Transfer), la syndication RSS (Really Simple Syndication) et Atom, ainsi que le protocole AJAX (Asynchronous JavaScript and XML).</span><span class="sxs-lookup"><span data-stu-id="4a981-147">These scenarios include "Plain Old XML" (POX), Representational State Transfer (REST), Really Simple Syndication (RSS) and Atom syndication, and Asynchronous JavaScript and XML (AJAX).</span></span> <span data-ttu-id="4a981-148">L'encodeur de messages composite ne prend pas en charge SOAP ni WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="4a981-148">The composite message encoder does not support SOAP or WS-Addressing.</span></span>  
  
 <span data-ttu-id="4a981-149">L'élément de liaison peut être configuré avec un encodage de caractères d'écriture à l'aide de l'attribut `writeEncoding`.</span><span class="sxs-lookup"><span data-stu-id="4a981-149">The binding element can be configured with a write character encoding by using the `writeEncoding` attribute.</span></span> <span data-ttu-id="4a981-150">La valeur <xref:System.Text.Encoding> fournie spécifie le comportement sur l'écriture pour les cas JSON et XML textuels.</span><span class="sxs-lookup"><span data-stu-id="4a981-150">The supplied <xref:System.Text.Encoding> value specifies the behavior on write for the JSON and Textual XML cases.</span></span> <span data-ttu-id="4a981-151">Lors de la lecture, tous les encodages de texte et de message valides sont maîtrisés.</span><span class="sxs-lookup"><span data-stu-id="4a981-151">On read, any valid message encoding and text encoding is understood.</span></span>  
  
 <span data-ttu-id="4a981-152">`maxReadPoolSize` et `maxWritePoolSize` peuvent également être utilisés pour définir respectivement le nombre maximal de lecteurs et de writers à allouer.</span><span class="sxs-lookup"><span data-stu-id="4a981-152">`maxReadPoolSize` and `maxWritePoolSize` can also be used to set the maximum number of readers and writers to be allocated respectively.</span></span> <span data-ttu-id="4a981-153">Par défaut, 64 lecteurs et 16 writers sont alloués.</span><span class="sxs-lookup"><span data-stu-id="4a981-153">By default 64 readers and 16 writers are allocated.</span></span>  
  
 <span data-ttu-id="4a981-154">Les contraintes de complexité par défaut sont également définies à l’aide de l' [ \<élément readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) pour se protéger contre une classe d’attaques par déni de service (dos) qui tentent d’utiliser la complexité des messages pour bloquer les ressources de traitement des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="4a981-154">Default complexity constraints are also set using the [\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100)) element to protect against a class of denial of service (DOS) attacks that attempt to use message complexity to tie up endpoint processing resources.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a981-155">Exemple</span><span class="sxs-lookup"><span data-stu-id="4a981-155">Example</span></span>  
  
```xml  
<webMessageEncoding maxReadPoolSize="256"
                    maxWritePoolSize="128"
                    messageVersion="None"
                    textEncoding="utf-8" />
```  
  
## <a name="see-also"></a><span data-ttu-id="4a981-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a981-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebMessageEncodingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [<span data-ttu-id="4a981-157">Encodage de message</span><span class="sxs-lookup"><span data-stu-id="4a981-157">Message Encoding</span></span>](message-encoding.md)
- [<span data-ttu-id="4a981-158">Sélection d’un encodeur de message</span><span class="sxs-lookup"><span data-stu-id="4a981-158">Choosing a Message Encoder</span></span>](../../../wcf/feature-details/choosing-a-message-encoder.md)
- [<span data-ttu-id="4a981-159">Liaisons</span><span class="sxs-lookup"><span data-stu-id="4a981-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4a981-160">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="4a981-160">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4a981-161">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="4a981-161">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="4a981-162">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="4a981-162">\<customBinding></span></span>](custombinding.md)

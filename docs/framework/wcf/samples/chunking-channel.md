---
title: Canal de segmentation
ms.date: 03/30/2017
ms.assetid: e4d53379-b37c-4b19-8726-9cc914d5d39f
ms.openlocfilehash: 7a5e5292bcb37e83de21458716e34887a0557d91
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585543"
---
# <a name="chunking-channel"></a><span data-ttu-id="c65f1-102">Canal de segmentation</span><span class="sxs-lookup"><span data-stu-id="c65f1-102">Chunking Channel</span></span>

<span data-ttu-id="c65f1-103">Lors de l’envoi de messages volumineux à l’aide d’Windows Communication Foundation (WCF), il est souvent préférable de limiter la quantité de mémoire utilisée pour mettre ces messages en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c65f1-103">When sending large messages using Windows Communication Foundation (WCF), it is often desirable to limit the amount of memory used to buffer those messages.</span></span> <span data-ttu-id="c65f1-104">L'une des solutions pour ce faire consiste à transmettre en continu le corps de ces messages (possible à condition que la plus grande partie des données figurent dans le corps des messages concernés).</span><span class="sxs-lookup"><span data-stu-id="c65f1-104">One possible solution is to stream the message body (assuming the bulk of the data is in the body).</span></span> <span data-ttu-id="c65f1-105">Certains protocoles, cependant, nécessitent la mise en mémoire tampon de l'intégralité des messages.</span><span class="sxs-lookup"><span data-stu-id="c65f1-105">However some protocols require buffering of the entire message.</span></span> <span data-ttu-id="c65f1-106">Parmi ces protocoles figurent notamment ceux de la messagerie fiable et de la sécurité.</span><span class="sxs-lookup"><span data-stu-id="c65f1-106">Reliable messaging and security are two such examples.</span></span> <span data-ttu-id="c65f1-107">L'une des autres solutions consiste à diviser les messages de grande taille en messages plus petits appelés segments, à envoyer ces segment un par un, puis à reconstituer les grands messages initiaux à partir de ces segments, côté destinataire.</span><span class="sxs-lookup"><span data-stu-id="c65f1-107">Another possible solution is to divide up the large message into smaller messages called chunks, send those chunks one chunk at a time, and reconstitute the large message on the receiving side.</span></span> <span data-ttu-id="c65f1-108">L'application peut effectuer ces opérations de segmentation et désegmentation elle-même ou utiliser un canal personnalisé pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="c65f1-108">The application itself could do this chunking and de-chunking or it could use a custom channel to do it.</span></span> <span data-ttu-id="c65f1-109">L'exemple de canal de segmentation suivant illustre la manière dont un protocole personnalisé ou un canal superposé peuvent être utilisés afin de segmenter ou désegmenter des messages de grande taille.</span><span class="sxs-lookup"><span data-stu-id="c65f1-109">The chunking channel sample shows how a custom protocol or layered channel can be used to do chunking and de-chunking of arbitrarily large messages.</span></span>

<span data-ttu-id="c65f1-110">La segmentation doit toujours être employée uniquement une fois le message à envoyer entièrement construit.</span><span class="sxs-lookup"><span data-stu-id="c65f1-110">Chunking should always be employed only after the entire message to be sent has been constructed.</span></span> <span data-ttu-id="c65f1-111">Un canal de segmentation doit toujours être disposé en couche sous un canal de sécurité et un canal de session fiable.</span><span class="sxs-lookup"><span data-stu-id="c65f1-111">A chunking channel should always be layered below a security channel and a reliable session channel.</span></span>

> [!NOTE]
> <span data-ttu-id="c65f1-112">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c65f1-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c65f1-113">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c65f1-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c65f1-114">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c65f1-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c65f1-115">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c65f1-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c65f1-116">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="c65f1-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\ChunkingChannel`

## <a name="chunking-channel-assumptions-and-limitations"></a><span data-ttu-id="c65f1-117">Hypothèses et limites concernant les canaux de segmentation</span><span class="sxs-lookup"><span data-stu-id="c65f1-117">Chunking Channel Assumptions and Limitations</span></span>

### <a name="message-structure"></a><span data-ttu-id="c65f1-118">Structure de message</span><span class="sxs-lookup"><span data-stu-id="c65f1-118">Message Structure</span></span>

<span data-ttu-id="c65f1-119">Les canaux de segmentation partent de l'hypothèse que la structure des messages est la suivante pour permettre leur segmentation :</span><span class="sxs-lookup"><span data-stu-id="c65f1-119">The chunking channel assumes the following message structure for messages to be chunked:</span></span>

```xml
<soap:Envelope>
  <!-- headers -->
  <soap:Body>
    <operationElement>
      <paramElement>data to be chunked</paramElement>
    </operationElement>
  </soap:Body>
</soap:Envelope>
```

<span data-ttu-id="c65f1-120">Lorsque ServiceModel est utilisé, les opérations de contrat disposant d'un paramètre d'entrée appliquent cette forme de message à leur message d'entrée.</span><span class="sxs-lookup"><span data-stu-id="c65f1-120">When using the ServiceModel, contract operations that have 1 input parameter comply with this shape of message for their input message.</span></span> <span data-ttu-id="c65f1-121">De la même façon, les opérations de contrat disposant d'un paramètre de sortie ou d'une valeur de retour applique cette forme de message à leur message de sortie.</span><span class="sxs-lookup"><span data-stu-id="c65f1-121">Similarly, contract operations that have 1 output parameter or return value comply with this shape of message for their output message.</span></span> <span data-ttu-id="c65f1-122">Le code suivant donne des exemples de ce genre d'opérations :</span><span class="sxs-lookup"><span data-stu-id="c65f1-122">The following are examples of such operations:</span></span>

```csharp
[ServiceContract]
interface ITestService
{
    [OperationContract]
    Stream EchoStream(Stream stream);

    [OperationContract]
    Stream DownloadStream();

    [OperationContract(IsOneWay = true)]
    void UploadStream(Stream stream);
}
```

### <a name="sessions"></a><span data-ttu-id="c65f1-123">Sessions</span><span class="sxs-lookup"><span data-stu-id="c65f1-123">Sessions</span></span>

<span data-ttu-id="c65f1-124">Les canaux de segmentation nécessitent que les messages soient remis exactement une seule fois, en respectant l'ordre de remise des messages, c'est-à-dire des segments.</span><span class="sxs-lookup"><span data-stu-id="c65f1-124">The chunking channel requires messages to be delivered exactly once, in ordered delivery of messages (chunks).</span></span> <span data-ttu-id="c65f1-125">Cela signifie que la pile des canaux sous-jacente doit correspondre à une pile de session.</span><span class="sxs-lookup"><span data-stu-id="c65f1-125">This means the underlying channel stack must be sessionful.</span></span> <span data-ttu-id="c65f1-126">Les sessions peuvent être fournies par le transport (par exemple, par le transport TCP) ou par un canal de protocole de session (par exemple, par un canal ReliableSession).</span><span class="sxs-lookup"><span data-stu-id="c65f1-126">Sessions can be provided by the transport (for example, TCP transport) or by a sessionful protocol channel (for example, ReliableSession channel).</span></span>

### <a name="asynchronous-send-and-receive"></a><span data-ttu-id="c65f1-127">Méthodes Send et Receive asynchrones</span><span class="sxs-lookup"><span data-stu-id="c65f1-127">Asynchronous Send and Receive</span></span>

<span data-ttu-id="c65f1-128">Les méthodes Send et de Receive asynchrones ne sont pas implémentées dans cette version de l'exemple de canal de segmentation.</span><span class="sxs-lookup"><span data-stu-id="c65f1-128">Asynchronous send and receive methods are not implemented in this version of the chunking channel sample.</span></span>

## <a name="chunking-protocol"></a><span data-ttu-id="c65f1-129">Protocole de segmentation</span><span class="sxs-lookup"><span data-stu-id="c65f1-129">Chunking Protocol</span></span>

<span data-ttu-id="c65f1-130">Le canal de segmentation définit un protocole marquant le début et la fin d'une série de segments et définissant également le numéro de séquence de chaque segment.</span><span class="sxs-lookup"><span data-stu-id="c65f1-130">The chunking channel defines a protocol that indicates the start and end of a series of chunks as well as the sequence number of each chunk.</span></span> <span data-ttu-id="c65f1-131">Les trois exemples de messages suivants correspondent à des messages de début, de segment et de fin. Ces exemples comportent également des explications présentant les principaux aspects de chacun d'entre eux.</span><span class="sxs-lookup"><span data-stu-id="c65f1-131">The following three example messages demonstrate the start, chunk and end messages with comments that describe the key aspects of each.</span></span>

### <a name="start-message"></a><span data-ttu-id="c65f1-132">Message de début</span><span class="sxs-lookup"><span data-stu-id="c65f1-132">Start Message</span></span>

```xml
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">
  <s:Header>
<!--Original message action is replaced with a chunking-specific action. -->
    <a:Action s:mustUnderstand="1">http://samples.microsoft.com/chunkingAction</a:Action>
<!--
Original message is assigned a unique id that is transmitted
in a MessageId header. Note that this is different from the WS-Addressing MessageId header.
-->
    <MessageId s:mustUnderstand="1" xmlns="http://samples.microsoft.com/chunking">
53f183ee-04aa-44a0-b8d3-e45224563109
</MessageId>
<!--
ChunkingStart header signals the start of a chunked message.
-->
    <ChunkingStart s:mustUnderstand="1" i:nil="true" xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://samples.microsoft.com/chunking" />
<!--
Original message action is transmitted in OriginalAction.
This is required to re-create the original message on the other side.
-->
    <OriginalAction xmlns="http://samples.microsoft.com/chunking">
http://tempuri.org/ITestService/EchoStream
    </OriginalAction>
   <!--
    All original message headers are included here.
   -->
  </s:Header>
  <s:Body>
<!--
Chunking assumes this structure of Body content:
<element>
  <childelement>large data to be chunked<childelement>
</element>
The start message contains just <element> and <childelement> without
the data to be chunked.
-->
    <EchoStream xmlns="http://tempuri.org/">
      <stream />
    </EchoStream>
  </s:Body>
</s:Envelope>
```

### <a name="chunk-message"></a><span data-ttu-id="c65f1-133">Message de segment</span><span class="sxs-lookup"><span data-stu-id="c65f1-133">Chunk Message</span></span>

```xml
<s:Envelope
  xmlns:a="http://www.w3.org/2005/08/addressing"
  xmlns:s="http://www.w3.org/2003/05/soap-envelope">
  <s:Header>
   <!--
    All chunking protocol messages have this action.
   -->
    <a:Action s:mustUnderstand="1">
      http://samples.microsoft.com/chunkingAction
    </a:Action>
<!--
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.
-->
    <MessageId s:mustUnderstand="1"
               xmlns="http://samples.microsoft.com/chunking">
      53f183ee-04aa-44a0-b8d3-e45224563109
    </MessageId>
<!--
The sequence number of the chunk.
This number restarts at 1 with each new sequence of chunks.
-->
    <ChunkNumber s:mustUnderstand="1"
                 xmlns="http://samples.microsoft.com/chunking">
      1096
    </ChunkNumber>
  </s:Header>
  <s:Body>
<!--
The chunked data is wrapped in a chunk element.
The encoding of this data (and the entire message)
depends on the encoder used. The chunking channel does not mandate an encoding.
-->
    <chunk xmlns="http://samples.microsoft.com/chunking">
kfSr2QcBlkHTvQ==
    </chunk>
  </s:Body>
</s:Envelope>
```

### <a name="end-message"></a><span data-ttu-id="c65f1-134">Message de fin</span><span class="sxs-lookup"><span data-stu-id="c65f1-134">End Message</span></span>

```xml
<s:Envelope xmlns:a="http://www.w3.org/2005/08/addressing"
            xmlns:s="http://www.w3.org/2003/05/soap-envelope">
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://samples.microsoft.com/chunkingAction
    </a:Action>
<!--
Same as MessageId in the start message. The GUID indicates which original message this chunk belongs to.
-->
    <MessageId s:mustUnderstand="1"
               xmlns="http://samples.microsoft.com/chunking">
      53f183ee-04aa-44a0-b8d3-e45224563109
    </MessageId>
<!--
ChunkingEnd header signals the end of a chunk sequence.
-->
    <ChunkingEnd s:mustUnderstand="1" i:nil="true"
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance"
                 xmlns="http://samples.microsoft.com/chunking" />
<!--
ChunkingEnd messages have a sequence number.
-->
    <ChunkNumber s:mustUnderstand="1"
                 xmlns="http://samples.microsoft.com/chunking">
      79
    </ChunkNumber>
  </s:Header>
  <s:Body>
<!--
The ChunkingEnd message has the same <element><childelement> structure
as the ChunkingStart message.
-->
    <EchoStream xmlns="http://tempuri.org/">
      <stream />
    </EchoStream>
  </s:Body>
</s:Envelope>
```

## <a name="chunking-channel-architecture"></a><span data-ttu-id="c65f1-135">Architecture des canaux de segmentation</span><span class="sxs-lookup"><span data-stu-id="c65f1-135">Chunking Channel Architecture</span></span>

<span data-ttu-id="c65f1-136">Les canaux de segmentation sont des canaux `IDuplexSessionChannel` dont l'architecture, au plus haut niveau, s'apparente à celle des canaux standard.</span><span class="sxs-lookup"><span data-stu-id="c65f1-136">The chunking channel is an `IDuplexSessionChannel` that, at a high level, follows the typical channel architecture.</span></span> <span data-ttu-id="c65f1-137">Il existe en effet un élément `ChunkingBindingElement` capable de générer une fabrication `ChunkingChannelFactory` ainsi qu'un écouteur `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-137">There is a `ChunkingBindingElement` that can build a `ChunkingChannelFactory` and a `ChunkingChannelListener`.</span></span> <span data-ttu-id="c65f1-138">La fabrication `ChunkingChannelFactory` crée des instances de `ChunkingChannel` lorsqu'elle en reçoit la demande.</span><span class="sxs-lookup"><span data-stu-id="c65f1-138">The `ChunkingChannelFactory` creates instances of `ChunkingChannel` when it is asked to.</span></span> <span data-ttu-id="c65f1-139">L'écouteur `ChunkingChannelListener` crée des instances de `ChunkingChannel` lorsqu'un nouveau canal interne est accepté.</span><span class="sxs-lookup"><span data-stu-id="c65f1-139">The `ChunkingChannelListener` creates instances of `ChunkingChannel` when a new inner channel is accepted.</span></span> <span data-ttu-id="c65f1-140">Le `ChunkingChannel` est lui-même chargé d'envoyer et de recevoir des messages.</span><span class="sxs-lookup"><span data-stu-id="c65f1-140">The `ChunkingChannel` itself is responsible for sending and receiving messages.</span></span>

<span data-ttu-id="c65f1-141">Au niveau inférieur suivant, le canal `ChunkingChannel` s'appuie sur plusieurs composants afin d'implémenter le protocole de segmentation.</span><span class="sxs-lookup"><span data-stu-id="c65f1-141">At the next level down, `ChunkingChannel` relies on several components to implement the chunking protocol.</span></span> <span data-ttu-id="c65f1-142">Du côté expéditeur, ce canal utilise un <xref:System.Xml.XmlDictionaryWriter> personnalisé appelé `ChunkingWriter` qui procède à la segmentation effective des messages.</span><span class="sxs-lookup"><span data-stu-id="c65f1-142">On the send side, the channel uses a custom <xref:System.Xml.XmlDictionaryWriter> called `ChunkingWriter` that does the actual chunking.</span></span> <span data-ttu-id="c65f1-143">`ChunkingWriter` utilise directement le canal interne pour envoyer les segments.</span><span class="sxs-lookup"><span data-stu-id="c65f1-143">`ChunkingWriter` uses the inner channel directly to send chunks.</span></span> <span data-ttu-id="c65f1-144">L'utilisation d'un `XmlDictionaryWriter` personnalisé nous permet d'envoyer les segments pendant l'écriture du corps des messages initiaux de grande taille.</span><span class="sxs-lookup"><span data-stu-id="c65f1-144">Using a custom `XmlDictionaryWriter` allows us to send out chunks as the large body of the original message is being written.</span></span> <span data-ttu-id="c65f1-145">Cela signifie que nous ne mettons pas en mémoire tampon l'intégralité des messages initiaux.</span><span class="sxs-lookup"><span data-stu-id="c65f1-145">This means we do not buffer the entire original message.</span></span>

![Diagramme qui montre l’architecture d’envoi du canal de segmentation.](./media/chunking-channel/chunking-channel-send.gif)

<span data-ttu-id="c65f1-147">Côté destinataire, `ChunkingChannel` extrait les messages du canal interne, puis les remet à un <xref:System.Xml.XmlDictionaryReader> personnalisé appelé `ChunkingReader`, qui reconstitue les messages initiaux à partir des segments entrants.</span><span class="sxs-lookup"><span data-stu-id="c65f1-147">On the receive side, `ChunkingChannel` pulls messages from the inner channel and hands them to a custom <xref:System.Xml.XmlDictionaryReader> called `ChunkingReader`, which reconstitutes the original message from the incoming chunks.</span></span> <span data-ttu-id="c65f1-148">`ChunkingChannel` encapsule ce `ChunkingReader` dans une implémentation de `Message` personnalisée appelée `ChunkingMessage` et retourne ce message à la couche supérieure.</span><span class="sxs-lookup"><span data-stu-id="c65f1-148">`ChunkingChannel` wraps this `ChunkingReader` in a custom `Message` implementation called `ChunkingMessage` and returns this message to the layer above.</span></span> <span data-ttu-id="c65f1-149">Cette combinaison de `ChunkingReader` et `ChunkingMessage` nous permet de désegmenter le corps des messages initiaux pendant leur lecture par la couche supérieure, nous évitant ainsi d'avoir à mettre la totalité de leur corps en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c65f1-149">This combination of `ChunkingReader` and `ChunkingMessage` allows us to de-chunk the original message body as it is being read by the layer above instead of having to buffer the entire original message body.</span></span> <span data-ttu-id="c65f1-150">`ChunkingReader` met en mémoire tampon un certain nombre de segments entrants, ce nombre étant configurable.</span><span class="sxs-lookup"><span data-stu-id="c65f1-150">`ChunkingReader` has a queue where it buffers incoming chunks up to a maximum configurable number of buffered chunks.</span></span> <span data-ttu-id="c65f1-151">Cette limite atteinte, le lecteur patiente jusqu'à ce que les messages soient extraits de la file d'attente par la couche supérieure (c'est-à-dire par simple lecture de leur corps) ou jusqu'à ce que le délai de réception arrive à échéance.</span><span class="sxs-lookup"><span data-stu-id="c65f1-151">When this maximum limit is reached, the reader waits for messages to be drained from the queue by the layer above (that is, by just reading from the original message body) or until the maximum receive timeout is reached.</span></span>

![Diagramme qui montre l’architecture de réception du canal de segmentation.](./media/chunking-channel/chunking-channel-receive.gif)

## <a name="chunking-programming-model"></a><span data-ttu-id="c65f1-153">Modèle de programmation de segmentation</span><span class="sxs-lookup"><span data-stu-id="c65f1-153">Chunking Programming Model</span></span>

<span data-ttu-id="c65f1-154">Les développeurs de service peuvent spécifier quels messages doivent être segmentés en appliquant l'attribut `ChunkingBehavior` aux opérations du contrat.</span><span class="sxs-lookup"><span data-stu-id="c65f1-154">Service developers can specify which messages are to be chunked by applying the `ChunkingBehavior` attribute to operations within the contract.</span></span> <span data-ttu-id="c65f1-155">Cet attribut expose une propriété `AppliesTo` qui permet aux développeurs de préciser si la segmentation doit être appliquée aux messages entrants, aux messages sortants ou aux deux.</span><span class="sxs-lookup"><span data-stu-id="c65f1-155">The attribute exposes an `AppliesTo` property that allows the developer to specify whether chunking applies to the input message, the output message or both.</span></span> <span data-ttu-id="c65f1-156">L'exemple suivant illustre la manière dont l'attribut `ChunkingBehavior` est utilisé :</span><span class="sxs-lookup"><span data-stu-id="c65f1-156">The following example shows the usage of `ChunkingBehavior` attribute:</span></span>

```csharp
[ServiceContract]
interface ITestService
{
    [OperationContract]
    [ChunkingBehavior(ChunkingAppliesTo.Both)]
    Stream EchoStream(Stream stream);

    [OperationContract]
    [ChunkingBehavior(ChunkingAppliesTo.OutMessage)]
    Stream DownloadStream();

    [OperationContract(IsOneWay=true)]
    [ChunkingBehavior(ChunkingAppliesTo.InMessage)]
    void UploadStream(Stream stream);

}
```

<span data-ttu-id="c65f1-157">À partir de ce modèle de programmation, le `ChunkingBindingElement` compile une liste d'URI d'action qui identifient les messages qui doivent être segmentés.</span><span class="sxs-lookup"><span data-stu-id="c65f1-157">From this programming model, the `ChunkingBindingElement` compiles a list of action URIs that identify messages to be chunked.</span></span> <span data-ttu-id="c65f1-158">L'action de chaque message sortant est comparée à celles figurant dans cette liste afin de déterminer si les messages doivent être segmentés ou envoyés directement.</span><span class="sxs-lookup"><span data-stu-id="c65f1-158">The action of each outgoing message is compared against this list to determine if the message should be chunked or sent directly.</span></span>

## <a name="implementing-the-send-operation"></a><span data-ttu-id="c65f1-159">Implémentation de l'opération d'envoi</span><span class="sxs-lookup"><span data-stu-id="c65f1-159">Implementing the Send Operation</span></span>

<span data-ttu-id="c65f1-160">Au niveau le plus élevé, l'opération d'envoi vérifie d'abord si le message sortant doit être segmenté, lorsque ce n'est pas le cas, elle l'envoie directement à l'aide du canal interne.</span><span class="sxs-lookup"><span data-stu-id="c65f1-160">At a high level, the Send operation first checks whether the outgoing message must be chunked and, if not, sends the message directly using the inner channel.</span></span>

<span data-ttu-id="c65f1-161">Si le message doit être segmenté, elle crée un nouveau `ChunkingWriter`, puis appelle `WriteBodyContents` sur ce message auquel elle passe ce `ChunkingWriter`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-161">If the message must be chunked, Send creates a new `ChunkingWriter` and calls `WriteBodyContents` on the outgoing message passing it this `ChunkingWriter`.</span></span> <span data-ttu-id="c65f1-162">Le `ChunkingWriter` procède ensuite à la segmentation du message (notamment en copiant ses en-têtes dans le message de début), puis envoie les segments à l'aide du canal interne.</span><span class="sxs-lookup"><span data-stu-id="c65f1-162">The `ChunkingWriter` then does the message chunking (including copying original message headers to the start chunk message) and sends chunks using the inner channel.</span></span>

<span data-ttu-id="c65f1-163">Autres informations dignes d'intérêt :</span><span class="sxs-lookup"><span data-stu-id="c65f1-163">A few details worth noting:</span></span>

- <span data-ttu-id="c65f1-164">La méthode Send appelle d'abord `ThrowIfDisposedOrNotOpened` afin de s'assurer que `CommunicationState` est ouvert.</span><span class="sxs-lookup"><span data-stu-id="c65f1-164">Send first calls `ThrowIfDisposedOrNotOpened` to ensure the `CommunicationState` is opened.</span></span>

- <span data-ttu-id="c65f1-165">L'envoi est synchronisé afin qu'un seul message puisse être envoyé à la fois pour chaque session.</span><span class="sxs-lookup"><span data-stu-id="c65f1-165">Sending is synchronized so that only one message can be sent at a time for each session.</span></span> <span data-ttu-id="c65f1-166">Lors de l'envoi d'un message segmenté, un événement `ManualResetEvent` appelé `sendingDone` est réinitialisé.</span><span class="sxs-lookup"><span data-stu-id="c65f1-166">There is a `ManualResetEvent` named `sendingDone` that is reset when a chunked message is being sent.</span></span> <span data-ttu-id="c65f1-167">Cet événement est défini, une fois le segment de fin envoyé.</span><span class="sxs-lookup"><span data-stu-id="c65f1-167">Once the end chunk message is sent, this event is set.</span></span> <span data-ttu-id="c65f1-168">La méthode Send patiente jusqu'à la définition de cet événement avant d'essayer d'envoyer le message sortant.</span><span class="sxs-lookup"><span data-stu-id="c65f1-168">The Send method waits for this event to be set before it tries to send the outgoing message.</span></span>

- <span data-ttu-id="c65f1-169">La méthode Send verrouille `CommunicationObject.ThisLock` pour empêcher la modification des états synchronisés lors de l’envoi.</span><span class="sxs-lookup"><span data-stu-id="c65f1-169">Send locks the `CommunicationObject.ThisLock` to prevent synchronized state changes while sending.</span></span> <span data-ttu-id="c65f1-170">Consultez la documentation <xref:System.ServiceModel.Channels.CommunicationObject> pour plus d'informations sur les états et l'ordinateur d'état <xref:System.ServiceModel.Channels.CommunicationObject>.</span><span class="sxs-lookup"><span data-stu-id="c65f1-170">See the <xref:System.ServiceModel.Channels.CommunicationObject> documentation for more information about <xref:System.ServiceModel.Channels.CommunicationObject> states and state machine.</span></span>

- <span data-ttu-id="c65f1-171">Le délai passé à la méthode Send correspond au délai appliqué à l'intégralité de l'opération d'envoi, notamment à l'envoi de tous les segments.</span><span class="sxs-lookup"><span data-stu-id="c65f1-171">The timeout passed to Send is used as the timeout for the entire send operation which includes sending all of the chunks.</span></span>

- <span data-ttu-id="c65f1-172">Le <xref:System.Xml.XmlDictionaryWriter> a été spécialement conçu pour éviter la mise en mémoire tampon de la totalité du corps des messages initiaux.</span><span class="sxs-lookup"><span data-stu-id="c65f1-172">The custom <xref:System.Xml.XmlDictionaryWriter> design was chosen to avoid buffering the entire original message body.</span></span> <span data-ttu-id="c65f1-173">Si le <xref:System.Xml.XmlDictionaryReader> du corps des messages était obtenu à l'aide de `message.GetReaderAtBodyContents`, tout leur corps serait mis en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c65f1-173">If we were to get an <xref:System.Xml.XmlDictionaryReader> on the body using `message.GetReaderAtBodyContents` the entire body would be buffered.</span></span> <span data-ttu-id="c65f1-174">Au lieu de cela, nous avons un personnalisé <xref:System.Xml.XmlDictionaryWriter> qui est passé à `message.WriteBodyContents` .</span><span class="sxs-lookup"><span data-stu-id="c65f1-174">Instead, we have a custom  <xref:System.Xml.XmlDictionaryWriter> that is passed to `message.WriteBodyContents`.</span></span> <span data-ttu-id="c65f1-175">Les messages appelant WriteBase64 sur l'enregistreur, ce dernier emballe les segments dans des messages, puis les envoie à l'aide du canal interne.</span><span class="sxs-lookup"><span data-stu-id="c65f1-175">As the message calls WriteBase64 on the writer, the writer packages up chunks into messages and sends them using the inner channel.</span></span> <span data-ttu-id="c65f1-176">WriteBase64 est verrouillé jusqu'à l'envoi des segments.</span><span class="sxs-lookup"><span data-stu-id="c65f1-176">WriteBase64 blocks until the chunk is sent.</span></span>

## <a name="implementing-the-receive-operation"></a><span data-ttu-id="c65f1-177">Implémentation de l'opération de réception</span><span class="sxs-lookup"><span data-stu-id="c65f1-177">Implementing the Receive Operation</span></span>

<span data-ttu-id="c65f1-178">Au plus haut niveau, l'opération de réception s'assure d'abord que les deux conditions suivantes sont réunies : le message entrant n'est pas `null` et son action correspond à `ChunkingAction`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-178">At a high level, the Receive operation first checks that the incoming message is not `null` and that its action is the `ChunkingAction`.</span></span> <span data-ttu-id="c65f1-179">Si l'une ou l'autre de ces conditions n'est pas respectée, la méthode Receive retourne le message sans le modifier.</span><span class="sxs-lookup"><span data-stu-id="c65f1-179">If it does not meet both criteria, the message is returned unchanged from Receive.</span></span> <span data-ttu-id="c65f1-180">En revanche, si ces deux conditions sont réunies, la méthode Receive crée un nouveau `ChunkingReader` ainsi qu'un nouveau `ChunkingMessage` encapsulé autour du premier (en appelant `GetNewChunkingMessage`).</span><span class="sxs-lookup"><span data-stu-id="c65f1-180">Otherwise, Receive creates a new `ChunkingReader` and a new `ChunkingMessage` wrapped around it (by calling `GetNewChunkingMessage`).</span></span> <span data-ttu-id="c65f1-181">Avant de retourner ce nouveau `ChunkingMessage`, la méthode Receive utilise un thread Threadpool pour exécuter une `ReceiveChunkLoop` qui appelle la méthode `innerChannel.Receive` dans une boucle, puis remet les segments au `ChunkingReader` jusqu'à réception du segment de fin ou échéance du délai de réception.</span><span class="sxs-lookup"><span data-stu-id="c65f1-181">Before returning that new `ChunkingMessage`, Receive uses a threadpool thread to execute `ReceiveChunkLoop`, which calls `innerChannel.Receive` in a loop and hands off chunks to the `ChunkingReader` until the end chunk message is received or the receive timeout is hit.</span></span>

<span data-ttu-id="c65f1-182">Autres informations dignes d'intérêt :</span><span class="sxs-lookup"><span data-stu-id="c65f1-182">A few details worth noting:</span></span>

- <span data-ttu-id="c65f1-183">À l'instar de la méthode Send, la méthode Receive appelle d'abord `ThrowIfDisposedOrNotOepned` afin de s'assurer que `CommunicationState` est ouvert.</span><span class="sxs-lookup"><span data-stu-id="c65f1-183">Like Send, Receive first calls `ThrowIfDisposedOrNotOepned` to ensure the `CommunicationState` is Opened.</span></span>

- <span data-ttu-id="c65f1-184">La méthode Receive est également synchronisée afin qu’un seul message puisse être reçu à la fois pour chaque session.</span><span class="sxs-lookup"><span data-stu-id="c65f1-184">Receive is also synchronized so that only one message can be received at a time from the session.</span></span> <span data-ttu-id="c65f1-185">Il s'agit d'une spécification particulièrement importante. En effet, une fois le segment de début reçu, tous les messages suivants sont censés correspondre à des segments appartenant à la nouvelle séquence de segments démarrée par ce segment de début, et ce jusqu'à réception du segment de fin.</span><span class="sxs-lookup"><span data-stu-id="c65f1-185">This is especially important because once a start chunk message is received, all subsequent received messages are expected to be chunks within this new chunk sequence until an end chunk message is received.</span></span> <span data-ttu-id="c65f1-186">La méthode Receive ne peut extraire les segments du message en cours de désegmentation du canal interne qu'une fois tous ces segments reçus.</span><span class="sxs-lookup"><span data-stu-id="c65f1-186">Receive cannot pull messages from the inner channel until all chunks that belong to the message currently being de-chunked are received.</span></span> <span data-ttu-id="c65f1-187">À cette fin, la méthode Receive utilise un événement `ManualResetEvent` appelé `currentMessageCompleted` qui est défini à réception du segment de fin et réinitialisé à réception d'un nouveau segment de début.</span><span class="sxs-lookup"><span data-stu-id="c65f1-187">To accomplish this, Receive uses a `ManualResetEvent` named `currentMessageCompleted`, which is set when the end chunk message is received and reset when a new start chunk message is received.</span></span>

- <span data-ttu-id="c65f1-188">À la différence de la méthode Send, la méthode Receive n’empêche pas les transitions entre états synchronisés pendant la réception.</span><span class="sxs-lookup"><span data-stu-id="c65f1-188">Unlike Send, Receive does not prevent synchronized state transitions while receiving.</span></span> <span data-ttu-id="c65f1-189">Par exemple, la méthode Close, laquelle patiente alors jusqu'au terme de la réception en attente du message initial ou jusqu'à l'arrivée à échéance du délai spécifié, peut être appelée pendant la réception.</span><span class="sxs-lookup"><span data-stu-id="c65f1-189">For example, Close can be called while receiving and waits until the pending receive of the original message is completed or the specified timeout value is reached.</span></span>

- <span data-ttu-id="c65f1-190">Le délai passé à la méthode Receive correspond au délai appliqué à l'intégralité de l'opération de réception, notamment à la réception de tous les segments.</span><span class="sxs-lookup"><span data-stu-id="c65f1-190">The timeout passed to Receive is used as the timeout for the entire receive operation, which includes receiving all of the chunks.</span></span>

- <span data-ttu-id="c65f1-191">Lorsque la couche absorbe le corps des messages à une vitesse inférieure à la vitesse d'arrivée des segments entrants, le `ChunkingReader` met en mémoire tampon ces segments jusqu'à ce que la limite spécifiée par `ChunkingBindingElement.MaxBufferedChunks` soit atteinte.</span><span class="sxs-lookup"><span data-stu-id="c65f1-191">If the layer that consumes the message is consuming the message body at a rate lower than the rate of incoming chunk messages, the `ChunkingReader` buffers those incoming chunks up to the limit specified by `ChunkingBindingElement.MaxBufferedChunks`.</span></span> <span data-ttu-id="c65f1-192">Cette limite atteinte, plus aucun segment n’est tiré de la couche inférieure jusqu’à absorption d’un des segments en mémoire tampon ou jusqu’à l’arrivée à échéance du délai de réception.</span><span class="sxs-lookup"><span data-stu-id="c65f1-192">Once that limit is reached, no more chunks are pulled from the lower layer until either a buffered chunk is consumed or the receive timeout is reached.</span></span>

## <a name="communicationobject-overrides"></a><span data-ttu-id="c65f1-193">Substitutions CommunicationObject</span><span class="sxs-lookup"><span data-stu-id="c65f1-193">CommunicationObject Overrides</span></span>

### <a name="onopen"></a><span data-ttu-id="c65f1-194">OnOpen</span><span class="sxs-lookup"><span data-stu-id="c65f1-194">OnOpen</span></span>

<span data-ttu-id="c65f1-195">`OnOpen` appelle la méthode `innerChannel.Open` afin d'ouvrir le canal interne.</span><span class="sxs-lookup"><span data-stu-id="c65f1-195">`OnOpen` calls `innerChannel.Open` to open the inner channel.</span></span>

### <a name="onclose"></a><span data-ttu-id="c65f1-196">OnClose</span><span class="sxs-lookup"><span data-stu-id="c65f1-196">OnClose</span></span>

<span data-ttu-id="c65f1-197">`OnClose` affecte d'abord à `stopReceive` la valeur `true` pour arrêter l'exécution de la boucle `ReceiveChunkLoop` en attente.</span><span class="sxs-lookup"><span data-stu-id="c65f1-197">`OnClose` first sets `stopReceive` to `true` to signal the pending `ReceiveChunkLoop` to stop.</span></span> <span data-ttu-id="c65f1-198">Il attend ensuite le `receiveStopped` <xref:System.Threading.ManualResetEvent> , qui est défini quand `ReceiveChunkLoop` s’arrête.</span><span class="sxs-lookup"><span data-stu-id="c65f1-198">It then waits for the `receiveStopped` <xref:System.Threading.ManualResetEvent>, which is set when `ReceiveChunkLoop` stops.</span></span> <span data-ttu-id="c65f1-199">En partant de l'hypothèse que la boucle `ReceiveChunkLoop` s'arrête avant l'expiration du délai spécifié, la méthode `OnClose` appelle alors `innerChannel.Close` dans le temps encore imparti.</span><span class="sxs-lookup"><span data-stu-id="c65f1-199">Assuming the `ReceiveChunkLoop` stops within the specified timeout, `OnClose` calls `innerChannel.Close` with the remaining timeout.</span></span>

### <a name="onabort"></a><span data-ttu-id="c65f1-200">OnAbort</span><span class="sxs-lookup"><span data-stu-id="c65f1-200">OnAbort</span></span>

<span data-ttu-id="c65f1-201">`OnAbort` appelle la méthode `innerChannel.Abort` afin d'annuler le canal interne.</span><span class="sxs-lookup"><span data-stu-id="c65f1-201">`OnAbort` calls `innerChannel.Abort` to abort the inner channel.</span></span> <span data-ttu-id="c65f1-202">Lorsqu'une boucle `ReceiveChunkLoop` est en attente, une exception est levée depuis l'appel de `innerChannel.Receive` en attente.</span><span class="sxs-lookup"><span data-stu-id="c65f1-202">If there is a pending `ReceiveChunkLoop` it gets an exception from the pending `innerChannel.Receive` call.</span></span>

### <a name="onfaulted"></a><span data-ttu-id="c65f1-203">OnFaulted</span><span class="sxs-lookup"><span data-stu-id="c65f1-203">OnFaulted</span></span>

<span data-ttu-id="c65f1-204">Le `ChunkingChannel` ne requiert pas de comportement spécial lorsqu'il est rendu défaillant afin d'empêcher la substitution de `OnFaulted`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-204">The `ChunkingChannel` does not require special behavior when the channel is faulted so `OnFaulted` is not overridden.</span></span>

## <a name="implementing-channel-factory"></a><span data-ttu-id="c65f1-205">Implémentation de la fabrication de canal</span><span class="sxs-lookup"><span data-stu-id="c65f1-205">Implementing Channel Factory</span></span>

<span data-ttu-id="c65f1-206">La fabrication `ChunkingChannelFactory` est chargée de créer des instances de `ChunkingDuplexSessionChannel` et de mettre en cascade les transitions d'état au niveau de la fabrication de canal interne.</span><span class="sxs-lookup"><span data-stu-id="c65f1-206">The `ChunkingChannelFactory` is responsible for creating instances of `ChunkingDuplexSessionChannel` and for cascading state transitions to the inner channel factory.</span></span>

<span data-ttu-id="c65f1-207">`OnCreateChannel` utilise la fabrication de canal interne pour créer un canal interne `IDuplexSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-207">`OnCreateChannel` uses the inner channel factory to create an `IDuplexSessionChannel` inner channel.</span></span> <span data-ttu-id="c65f1-208">Cette méthode crée ensuite un nouveau canal `ChunkingDuplexSessionChannel` auquel elle passe ce canal interne, la liste des actions de message à segmenter et le nombre maximal de segments pouvant être mis en mémoire tampon à réception.</span><span class="sxs-lookup"><span data-stu-id="c65f1-208">It then creates a new `ChunkingDuplexSessionChannel` passing it this inner channel along with the list of message actions to be chunked and the maximum number of chunks to buffer upon receive.</span></span> <span data-ttu-id="c65f1-209">Cette liste et ce nombre correspondent à deux paramètres passés à `ChunkingChannelFactory` par l'intermédiaire de son constructeur.</span><span class="sxs-lookup"><span data-stu-id="c65f1-209">The list of message actions to be chunked and the maximum number of chunks to buffer are two parameters passed to `ChunkingChannelFactory` in its constructor.</span></span> <span data-ttu-id="c65f1-210">La section consacrée à `ChunkingBindingElement` contient des explications sur l'origine de ces deux valeurs.</span><span class="sxs-lookup"><span data-stu-id="c65f1-210">The section on `ChunkingBindingElement` describes where these values come from.</span></span>

<span data-ttu-id="c65f1-211">Les méthodes `OnOpen`, `OnClose`, `OnAbort` et leurs équivalents asynchrones appellent la méthode de transition d'état correspondante sur la fabrication de canal interne.</span><span class="sxs-lookup"><span data-stu-id="c65f1-211">The `OnOpen`, `OnClose`, `OnAbort` and their asynchronous equivalents call the corresponding state transition method on the inner channel factory.</span></span>

## <a name="implementing-channel-listener"></a><span data-ttu-id="c65f1-212">Implémentation de l'écouteur de canal</span><span class="sxs-lookup"><span data-stu-id="c65f1-212">Implementing Channel Listener</span></span>

<span data-ttu-id="c65f1-213">L'écouteur `ChunkingChannelListener` correspond à un wrapper autour d'un écouteur de canal interne.</span><span class="sxs-lookup"><span data-stu-id="c65f1-213">The `ChunkingChannelListener` is a wrapper around an inner channel listener.</span></span> <span data-ttu-id="c65f1-214">Sa fonction principale, outre déléguer les appels à l'écouteur de canal interne, consiste à encapsuler les nouveaux canaux `ChunkingDuplexSessionChannels` autour des canaux acceptés depuis l'écouteur de canal interne.</span><span class="sxs-lookup"><span data-stu-id="c65f1-214">Its main function, besides delegate calls to that inner channel listener, is to wrap new `ChunkingDuplexSessionChannels` around channels accepted from the inner channel listener.</span></span> <span data-ttu-id="c65f1-215">Ce processus s'effectue dans `OnAcceptChannel` et `OnEndAcceptChannel`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-215">This is done in `OnAcceptChannel` and `OnEndAcceptChannel`.</span></span> <span data-ttu-id="c65f1-216">Le canal interne ainsi que les autres paramètres décrits précédemment sont passés au nouveau canal `ChunkingDuplexSessionChannel` créé.</span><span class="sxs-lookup"><span data-stu-id="c65f1-216">The newly created `ChunkingDuplexSessionChannel` is passed the inner channel along with the other parameters previously described.</span></span>

## <a name="implementing-binding-element-and-binding"></a><span data-ttu-id="c65f1-217">Implémentation de l'élément de liaison et de la liaison</span><span class="sxs-lookup"><span data-stu-id="c65f1-217">Implementing Binding Element and Binding</span></span>

<span data-ttu-id="c65f1-218">L'élément `ChunkingBindingElement` est chargé de créer la fabrication `ChunkingChannelFactory` et l'écouteur `ChunkingChannelListener`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-218">`ChunkingBindingElement` is responsible for creating the `ChunkingChannelFactory` and `ChunkingChannelListener`.</span></span> <span data-ttu-id="c65f1-219">`ChunkingBindingElement`Vérifie si T dans `CanBuildChannelFactory` \<T> et `CanBuildChannelListener` \<T> est de type `IDuplexSessionChannel` (le seul canal pris en charge par le canal de segmentation) et que les autres éléments de liaison de la liaison prennent en charge ce type de canal.</span><span class="sxs-lookup"><span data-stu-id="c65f1-219">The `ChunkingBindingElement` checks whether T in `CanBuildChannelFactory`\<T> and `CanBuildChannelListener`\<T> is of type `IDuplexSessionChannel` (the only channel supported by the chunking channel) and that the other binding elements in the binding support this channel type.</span></span>

<span data-ttu-id="c65f1-220">`BuildChannelFactory`\<T>vérifie d’abord que le type de canal demandé peut être généré, puis obtient une liste d’actions de message à segmenter.</span><span class="sxs-lookup"><span data-stu-id="c65f1-220">`BuildChannelFactory`\<T> first checks that the requested channel type can be built and then gets a list of message actions to be chunked.</span></span> <span data-ttu-id="c65f1-221">Pour plus d’informations, consultez la section suivante :</span><span class="sxs-lookup"><span data-stu-id="c65f1-221">For more information, see the following section.</span></span> <span data-ttu-id="c65f1-222">Cette méthode crée alors une nouvelle fabrication `ChunkingChannelFactory` à laquelle elle passe la fabrication de canal interne (telle que retournée depuis `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), la liste d'actions de message et le nombre maximal de segments pouvant être mise en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="c65f1-222">It then creates a new `ChunkingChannelFactory` passing it the inner channel factory (as returned from `context.BuildInnerChannelFactory<IDuplexSessionChannel>`), the list of message actions, and the maximum number of chunks to buffer.</span></span> <span data-ttu-id="c65f1-223">Ce nombre maximal est issu de la propriété appelée `MaxBufferedChunks`, laquelle est exposée par l'élément `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-223">The maximum number of chunks comes from a property called `MaxBufferedChunks` exposed by the `ChunkingBindingElement`.</span></span>

<span data-ttu-id="c65f1-224">`BuildChannelListener<T>` utilise une implémentation similaire pour créer `ChunkingChannelListener` et lui passer l'écouteur de canal interne.</span><span class="sxs-lookup"><span data-stu-id="c65f1-224">`BuildChannelListener<T>` has a similar implementation for creating `ChunkingChannelListener` and passing it the inner channel listener.</span></span>

<span data-ttu-id="c65f1-225">Cet exemple de code contient une liaison appelée `TcpChunkingBinding`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-225">There is an example binding included in this sample named `TcpChunkingBinding`.</span></span> <span data-ttu-id="c65f1-226">Cette liaison se compose de deux éléments de liaison : `TcpTransportBindingElement` et `ChunkingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-226">This binding consists of two binding elements: `TcpTransportBindingElement` and `ChunkingBindingElement`.</span></span> <span data-ttu-id="c65f1-227">En plus d’exposer la propriété `MaxBufferedChunks`, cette liaison définit également quelques-unes des propriétés `TcpTransportBindingElement` telles que `MaxReceivedMessageSize` (elle affecte à cette dernière la valeur `ChunkingUtils.ChunkSize` + 100 Ko pour les en-têtes).</span><span class="sxs-lookup"><span data-stu-id="c65f1-227">In addition to exposing the `MaxBufferedChunks` property, the binding also sets some of the `TcpTransportBindingElement` properties such as `MaxReceivedMessageSize` (sets it to `ChunkingUtils.ChunkSize` + 100KB bytes for headers).</span></span>

<span data-ttu-id="c65f1-228">`TcpChunkingBinding` implémente également `IBindingRuntimePreferences` et retourne la valeur true depuis la méthode `ReceiveSynchronously`, indiquant que seuls les appels Receive synchrones sont implémentés.</span><span class="sxs-lookup"><span data-stu-id="c65f1-228">`TcpChunkingBinding` also implements `IBindingRuntimePreferences` and returns true from the `ReceiveSynchronously` method indicating that only the synchronous Receive calls are implemented.</span></span>

### <a name="determining-which-messages-to-chunk"></a><span data-ttu-id="c65f1-229">Identification des messages à segmenter</span><span class="sxs-lookup"><span data-stu-id="c65f1-229">Determining Which Messages To Chunk</span></span>

<span data-ttu-id="c65f1-230">Les canaux de segmentation segmentent uniquement les messages identifiés à l'aide de l'attribut `ChunkingBehavior`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-230">The chunking channel chunks only the messages identified through the `ChunkingBehavior` attribute.</span></span> <span data-ttu-id="c65f1-231">La classe `ChunkingBehavior` implémente `IOperationBehavior` et est elle-même implémentée par l'appel de la méthode `AddBindingParameter`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-231">The `ChunkingBehavior` class implements `IOperationBehavior` and is implemented by calling the `AddBindingParameter` method.</span></span> <span data-ttu-id="c65f1-232">Dans cette méthode, la classe `ChunkingBehavior` examine la valeur de sa propriété `AppliesTo` (`InMessage` ou `OutMessage` ou encore les deux) afin d'identifier les messages à segmenter.</span><span class="sxs-lookup"><span data-stu-id="c65f1-232">In this method, the `ChunkingBehavior` examines the value of its `AppliesTo` property (`InMessage`, `OutMessage` or both) to determine which messages should be chunked.</span></span> <span data-ttu-id="c65f1-233">Elle obtient ensuite l’action correspondant à chacun de ces messages (depuis la collection Messages sur `OperationDescription`), puis ajoute chacune de ces actions aux collections de chaînes contenue dans les instances de `ChunkingBindingParameter`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-233">It then gets the action of each of those messages (from the Messages collection on `OperationDescription`) and adds it to a string collection contained within an instance of `ChunkingBindingParameter`.</span></span> <span data-ttu-id="c65f1-234">Elle ajoute enfin ce `ChunkingBindingParameter` à la collection `BindingParameterCollection`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-234">It then adds this `ChunkingBindingParameter` to the provided `BindingParameterCollection`.</span></span>

<span data-ttu-id="c65f1-235">Cette `BindingParameterCollection` est passée à l’intérieur du `BindingContext` à chaque élément de la liaison lorsque ces éléments génèrent la fabrication de canal ou l’écouteur de canal.</span><span class="sxs-lookup"><span data-stu-id="c65f1-235">This `BindingParameterCollection` is passed inside the `BindingContext` to each binding element in the binding when that binding element builds the channel factory or the channel listener.</span></span> <span data-ttu-id="c65f1-236">L' `ChunkingBindingElement` implémentation de `BuildChannelFactory<T>` et `BuildChannelListener<T>` extrayez `ChunkingBindingParameter` - `BindingContext’` la de `BindingParameterCollection` .</span><span class="sxs-lookup"><span data-stu-id="c65f1-236">The `ChunkingBindingElement`'s implementation of `BuildChannelFactory<T>` and `BuildChannelListener<T>` pull this `ChunkingBindingParameter` out of the `BindingContext’`s `BindingParameterCollection`.</span></span> <span data-ttu-id="c65f1-237">La collection d'actions contenue dans le `ChunkingBindingParameter` est passée à `ChunkingChannelFactory` ou à `ChunkingChannelListener`, qui la passe ensuite au `ChunkingDuplexSessionChannel`.</span><span class="sxs-lookup"><span data-stu-id="c65f1-237">The collection of actions contained within the `ChunkingBindingParameter` is then passed to the `ChunkingChannelFactory` or `ChunkingChannelListener`, which in turn passes it to the `ChunkingDuplexSessionChannel`.</span></span>

## <a name="running-the-sample"></a><span data-ttu-id="c65f1-238">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="c65f1-238">Running the Sample</span></span>

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c65f1-239">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="c65f1-239">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c65f1-240">Installez ASP.NET 4,0 à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="c65f1-240">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="c65f1-241">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c65f1-241">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="c65f1-242">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c65f1-242">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="c65f1-243">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c65f1-243">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="c65f1-244">Exécutez en premier Service.exe, puis Client.exe. Regardez ensuite leurs fenêtres de console respectives pour connaître leur résultat.</span><span class="sxs-lookup"><span data-stu-id="c65f1-244">Run Service.exe first, then run Client.exe and watch both console windows for output.</span></span>

<span data-ttu-id="c65f1-245">L'exécution de l'exemple est censée donner le résultat suivant.</span><span class="sxs-lookup"><span data-stu-id="c65f1-245">When running the sample, the following output is expected.</span></span>

<span data-ttu-id="c65f1-246">Client :</span><span class="sxs-lookup"><span data-stu-id="c65f1-246">Client:</span></span>

```console
Press enter when service is available

 > Sent chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 < Received chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd
```

<span data-ttu-id="c65f1-247">Serveur : </span><span class="sxs-lookup"><span data-stu-id="c65f1-247">Server:</span></span>

```console
Service started, press enter to exit
 < Received chunk 1 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 2 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 3 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 4 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 5 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 6 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 7 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 8 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 9 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 < Received chunk 10 of message 867c1fd1-d39e-4be1-bc7b-32066d7ced10
 > Sent chunk 1 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 2 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 3 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 4 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 5 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 6 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 7 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 8 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 9 of message 5b226ad5-c088-4988-b737-6a565e0563dd
 > Sent chunk 10 of message 5b226ad5-c088-4988-b737-6a565e0563dd
```

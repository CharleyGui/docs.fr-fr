---
title: Protocole de messagerie fiable version 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: 6fceb49d107e4268a4b9fad6197335ff9e2af9ab
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662793"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="66f23-102">Protocole de messagerie fiable version 1.0</span><span class="sxs-lookup"><span data-stu-id="66f23-102">Reliable Messaging Protocol version 1.0</span></span>

<span data-ttu-id="66f23-103">Cette rubrique traite des détails d’implémentation de Windows Communication Foundation (WCF) pour WS-Reliable Messaging protocol de février 2005 (version 1.0) nécessaire pour l’interopérabilité utilisant le transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="66f23-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="66f23-104">WCF suit la spécification WS-Reliable Messaging avec les contraintes et les éclaircissements présentés dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="66f23-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="66f23-105">Notez que le protocole de la version 1.0 WS-ReliableMessaging est implémenté en commençant par le WinFX.</span><span class="sxs-lookup"><span data-stu-id="66f23-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the WinFX.</span></span>

<span data-ttu-id="66f23-106">La messagerie WS-Reliable février 2005 protocole est implémenté dans WCF par le <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="66f23-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="66f23-107">Pour plus de simplicité, la rubrique utilise les rôles suivants :</span><span class="sxs-lookup"><span data-stu-id="66f23-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="66f23-108">Initiateur : client qui initialise la création de la séquence de message WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="66f23-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>

- <span data-ttu-id="66f23-109">Répondeur : service qui reçoit les demandes de l'initiateur.</span><span class="sxs-lookup"><span data-stu-id="66f23-109">Responder: the service that receives the initiator's requests</span></span>

<span data-ttu-id="66f23-110">Ce document utilise les préfixes et les espaces de noms répertoriés dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="66f23-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="66f23-111">Préfixe</span><span class="sxs-lookup"><span data-stu-id="66f23-111">Prefix</span></span>|<span data-ttu-id="66f23-112">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="66f23-112">Namespace</span></span>|
|------------|---------------|
|<span data-ttu-id="66f23-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="66f23-113">wsrm</span></span>|http://schemas.xmlsoap.org/ws/2005/02/rm|
|<span data-ttu-id="66f23-114">netrm</span><span class="sxs-lookup"><span data-stu-id="66f23-114">netrm</span></span>|http://schemas.microsoft.com/ws/2006/05/rm|
|<span data-ttu-id="66f23-115">s</span><span class="sxs-lookup"><span data-stu-id="66f23-115">s</span></span>|http://www.w3.org/2003/05/soap-envelope|
|<span data-ttu-id="66f23-116">wsa</span><span class="sxs-lookup"><span data-stu-id="66f23-116">wsa</span></span>|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|<span data-ttu-id="66f23-117">wsse</span><span class="sxs-lookup"><span data-stu-id="66f23-117">wsse</span></span>|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|

## <a name="messaging"></a><span data-ttu-id="66f23-118">Messagerie</span><span class="sxs-lookup"><span data-stu-id="66f23-118">Messaging</span></span>

### <a name="sequence-establishment-messages"></a><span data-ttu-id="66f23-119">Messages d'établissement de séquence</span><span class="sxs-lookup"><span data-stu-id="66f23-119">Sequence Establishment Messages</span></span>

<span data-ttu-id="66f23-120">WCF implémente `CreateSequence` et `CreateSequenceResponse` messages pour établir une séquence de message fiable.</span><span class="sxs-lookup"><span data-stu-id="66f23-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="66f23-121">Les contraintes suivantes s'appliquent :</span><span class="sxs-lookup"><span data-stu-id="66f23-121">The following constraints apply:</span></span>

- <span data-ttu-id="66f23-122">B1101 : L’initiateur WCF ne génère pas de l’élément Expires facultatif dans le `CreateSequence` message ou, dans le cas lorsque le `CreateSequence` message contient un `Offer` élément, le paramètre facultatif `Expires` élément dans le `Offer` élément.</span><span class="sxs-lookup"><span data-stu-id="66f23-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>

- <span data-ttu-id="66f23-123">B1102 : Lorsque vous accédez à la `CreateSequence` du message, WCF`Responder` envoie et reçoit les deux `Expires` éléments s’ils existent, mais n’utilisent pas leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="66f23-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>

<span data-ttu-id="66f23-124">La messagerie WS-Reliable introduit le mécanisme `Offer` pour établir deux séquences corrélées réciproques qui forment une session.</span><span class="sxs-lookup"><span data-stu-id="66f23-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="66f23-125">R1103 : Si `CreateSequence` contient un `Offer` élément, le répondeur de messagerie fiable doit soit accepter la séquence et répondre avec `CreateSequenceResponse` qui contient un `wsrm:Accept` élément, formant deux corrélées séquences réciproques ou rejeter le `CreateSequence`demande.</span><span class="sxs-lookup"><span data-stu-id="66f23-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>

- <span data-ttu-id="66f23-126">R1104 : l'`SequenceAcknowledgement` et les messages d'application qui passent sur la séquence réciproque doivent être envoyés à la référence de point de terminaison `ReplyTo` de `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="66f23-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="66f23-127">R1105 : les références de point de terminaison `AcksTo` et `ReplyTo` dans `CreateSequence` doivent avoir des valeurs d'adresse qui correspondent au niveau des octets.</span><span class="sxs-lookup"><span data-stu-id="66f23-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>

  <span data-ttu-id="66f23-128">Le répondeur WCF vérifie que la portion d’URI de la `AcksTo` et `ReplyTo` EPR est identiques avant de créer une séquence.</span><span class="sxs-lookup"><span data-stu-id="66f23-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>

- <span data-ttu-id="66f23-129">R1106 : les références de point de terminaison `AcksTo` et `ReplyTo` dans `CreateSequence` doivent avoir le même jeu de paramètres de référence.</span><span class="sxs-lookup"><span data-stu-id="66f23-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>

  <span data-ttu-id="66f23-130">WCF n’applique pas, mais part du principe que [paramètres de référence] de `AcksTo` et `ReplyTo` sur `CreateSequence` sont identiques et utilise [paramètres de référence] à partir de `ReplyTo` référence de point de terminaison pour les accusés de réception et les messages de séquence réciproque.</span><span class="sxs-lookup"><span data-stu-id="66f23-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="66f23-131">R1107 : Lorsque deux séquences réciproques sont établies à l’aide de la `Offer` mécanisme, `SequenceAcknowledgement` et messages d’application traversent les séquences réciproques doivent être envoyés à la `ReplyTo` référence de point de terminaison de la `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="66f23-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="66f23-132">R1108 : Lorsque deux séquences réciproques sont établies à l’aide du mécanisme Offer, la `[address]` propriété de la `wsrm:AcksTo` élément enfant de référence de point de terminaison de la `wsrm:Accept` élément de la `CreateSequenceResponse` doit correspondre octet par octet l’URI de destination de la `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="66f23-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>

- <span data-ttu-id="66f23-133">R1109 : Lorsque deux séquences réciproques sont établies à l’aide de la `Offer` mécanisme, les messages envoyés par l’initiateur et les accusés de réception des messages par le répondeur doivent être envoyés à la même référence de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="66f23-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>

  <span data-ttu-id="66f23-134">WCF utilise la messagerie WS-Reliable pour établir des sessions fiables entre l’initiateur et le répondeur.</span><span class="sxs-lookup"><span data-stu-id="66f23-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="66f23-135">Implémentation de la messagerie WS-Reliable de WCF fournit une session fiable pour intégral demande-réponse et unidirectionnels, modèles de messagerie en duplex.</span><span class="sxs-lookup"><span data-stu-id="66f23-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="66f23-136">La messagerie WS-Reliable `Offer` mécanisme sur `CreateSequence` / `CreateSequenceResponse` vous permet d’établir deux séquences réciproques corrélées et fournit un protocole de session qui convient à tous les points de terminaison de message.</span><span class="sxs-lookup"><span data-stu-id="66f23-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="66f23-137">Étant donné que WCF fournit une garantie de sécurité pour une telle session, y compris la protection de bout en bout pour l’intégrité de session, il est pratique de s’assurer de messages destinés au même correspondant arrivent à la même destination.</span><span class="sxs-lookup"><span data-stu-id="66f23-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="66f23-138">Cela permet également la superposition des accusés de réception de séquence sur les messages d'application.</span><span class="sxs-lookup"><span data-stu-id="66f23-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="66f23-139">Par conséquent, les contraintes R1104, R1105 et R1108 s’appliquent à WCF.</span><span class="sxs-lookup"><span data-stu-id="66f23-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>

<span data-ttu-id="66f23-140">Exemple de message `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="66f23-140">An example of a `CreateSequence` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence
    </a:Action>
    <a:ReplyTo>
      <a:Address>
         http://Business456.com/clientA
      </a:Address>
    </a:ReplyTo>
    <a:MessageID>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </a:MessageID>
    <a:To s:mustUnderstand="1">
      http://Business456.com/clientA
    </a:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
       <wsa:Address>
         http://Business456.com/clientA
       </wsa:Address>
     </wsrm:AcksTo>
     <wsrm:Offer>
      <wsrm:Identifier>
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496
      </wsrm:Identifier>
     </wsrm:Offer>
   </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

 <span data-ttu-id="66f23-141">Exemple de message `CreateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="66f23-141">An example of a `CreateSequenceResponse` message.</span></span>

```xml
<s:Envelope>
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse
    </a:Action>
    <a:RelatesTo>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </a:RelatesTo>
    <a:To s:mustUnderstand="1">
      http://Business456.com/clientA
    </a:To>
  </s:Header>
  <s:Body>
   <wsrm:CreateSequenceResponse>
    <Identifier>
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386
    </Identifier>
    <Accept>
    <AcksTo>
      <a:Address>
        http://BusinessABC.com/serviceA
      </a:Address>
    </AcksTo>
    </Accept>
   </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence"></a><span data-ttu-id="66f23-142">Séquence</span><span class="sxs-lookup"><span data-stu-id="66f23-142">Sequence</span></span>

<span data-ttu-id="66f23-143">Voici une liste des contraintes qui s'appliquent aux séquences :</span><span class="sxs-lookup"><span data-stu-id="66f23-143">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="66f23-144">B1201:WCF génère et ne dépassant pas de numéros de séquence d’accès `xs:long`de valeur maximale, 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="66f23-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

- <span data-ttu-id="66f23-145">B1202:WCF génère toujours un message dernier vide avec l’URI d’action de `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span><span class="sxs-lookup"><span data-stu-id="66f23-145">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

- <span data-ttu-id="66f23-146">B1203 : WCF reçoit et remet un message avec un en-tête de séquence qui contient un `LastMessage` élément tant que l’URI action n’est pas `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span><span class="sxs-lookup"><span data-stu-id="66f23-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

<span data-ttu-id="66f23-147">Exemple d'en-tête Sequence.</span><span class="sxs-lookup"><span data-stu-id="66f23-147">An example of a Sequence Header.</span></span>

```xml
<wsrm:Sequence>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
  <wsrm:MessageNumber>
    10
  </wsrm:MessageNumber>
  <wsrm:LastMessage/>
 </wsrm:Sequence>
```

### <a name="ackrequested-header"></a><span data-ttu-id="66f23-148">En-tête AckRequested</span><span class="sxs-lookup"><span data-stu-id="66f23-148">AckRequested Header</span></span>

<span data-ttu-id="66f23-149">WCF utilise `AckRequested` en-tête comme un mécanisme keep-alive.</span><span class="sxs-lookup"><span data-stu-id="66f23-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="66f23-150">WCF ne génère pas le paramètre facultatif `MessageNumber` élément.</span><span class="sxs-lookup"><span data-stu-id="66f23-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="66f23-151">Lors de la réception d’un message avec un `AckRequested` en-tête qui contient le `MessageNumber` élément, WCF ignore le `MessageNumber` valeur de l’élément, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="66f23-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="66f23-152">En-tête SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="66f23-152">SequenceAcknowledgement Header</span></span>

<span data-ttu-id="66f23-153">WCF utilise le mécanisme de superposition des accusés de réception de séquence fournis dans la messagerie WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="66f23-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>

- <span data-ttu-id="66f23-154">R1401 : Lorsque deux séquences réciproques sont établies à l’aide de la `Offer` mécanisme, le `SequenceAcknowledgement` en-tête peut être inclus dans n’importe quel message d’application transmis au destinataire prévu.</span><span class="sxs-lookup"><span data-stu-id="66f23-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>

- <span data-ttu-id="66f23-155">B1402 : Lorsque WCF doit générer un accusé de réception avant de recevoir un message de séquence (par exemple, pour satisfaire un `AckRequested` message), WCF génère un `SequenceAcknowledgement` en-tête qui contient la plage 0-0, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="66f23-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="66f23-156">B1403 : WCF ne génère pas `SequenceAcknowledgement` en-têtes qui contiennent un `Nack` élément mais prend en charge `Nack` éléments.</span><span class="sxs-lookup"><span data-stu-id="66f23-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="66f23-157">Erreurs de la messagerie WS-Reliable</span><span class="sxs-lookup"><span data-stu-id="66f23-157">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="66f23-158">Voici une liste de contraintes qui s’appliquent à l’implémentation de WCF des erreurs WS-Reliable Messaging :</span><span class="sxs-lookup"><span data-stu-id="66f23-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>

- <span data-ttu-id="66f23-159">B1501 : WCF ne génère pas `MessageNumberRollover` erreurs.</span><span class="sxs-lookup"><span data-stu-id="66f23-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="66f23-160">Point de terminaison B1502:WCF peut générer `CreateSequenceRefused` comme décrit dans la spécification des erreurs.</span><span class="sxs-lookup"><span data-stu-id="66f23-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>

- <span data-ttu-id="66f23-161">B1503:when le point de terminaison de service atteint sa limite de connexion et ne peut pas traiter de nouvelles connexions, WCF génère un autre `CreateSequenceRefused` sous-code, d’erreur `netrm:ConnectionLimitReached`, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="66f23-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

  ```xml
  <s:Envelope>
    <s:Header>
      <wsa:Action>
        http://schemas.xmlsoap.org/ws/2005/08/addressing/fault
      </wsa:Action>
    </s:Header>
    <s:Body>
      <s:Fault>
        <s:Code>
          <s:Value>
            s:Receiver
          </s:Value>
          <s:Subcode>
            <s:Value>
              wsrm:CreateSequenceRefused
            </s:Value>
            <s:Subcode>
              <s:Value>
                netrm:ConnectionLimitReached
              </s:Value>
            </s:Subcode>
          </s:Subcode>
        </s:Code>
        <s:Reason>
          <s:Text xml:lang="en">
            [Reason]
          </s:Text>
        </s:Reason>
      </s:Fault>
    </s:Body>
  </s:Envelope>
  ```

### <a name="ws-addressing-faults"></a><span data-ttu-id="66f23-162">Erreurs WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="66f23-162">WS-Addressing Faults</span></span>

<span data-ttu-id="66f23-163">Étant donné que la messagerie WS-Reliable utilise WS-Addressing, implémentation de la messagerie WS-Reliable WCF peut générer des erreurs WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="66f23-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="66f23-164">Cette section décrit les erreurs WS-Addressing, WCF génère explicitement au niveau de la couche de messagerie WS-Reliable :</span><span class="sxs-lookup"><span data-stu-id="66f23-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>

- <span data-ttu-id="66f23-165">B1601:WCF génère l’erreur Message Addressing Header Required lorsqu’une des opérations suivantes est vraie :</span><span class="sxs-lookup"><span data-stu-id="66f23-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>

  - <span data-ttu-id="66f23-166">Un message n'a pas d'en-tête `Sequence` ni d'en-tête `Action`.</span><span class="sxs-lookup"><span data-stu-id="66f23-166">A message is missing a `Sequence` header and an `Action` header.</span></span>

  - <span data-ttu-id="66f23-167">Un message `CreateSequence` n'a pas d'en-tête `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="66f23-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="66f23-168">Un message `CreateSequence` n'a pas d'en-tête `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="66f23-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>

- <span data-ttu-id="66f23-169">B1602:WCF génère l’erreur pas pris en charge par Action en réponse à un message qui manque un `Sequence` en-tête et a une `Action` en-tête n’est pas reconnue dans la spécification WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="66f23-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>

- <span data-ttu-id="66f23-170">B1603:WCF génère l’erreur Endpoint Unavailable pour indiquer que le point de terminaison ne traite pas de la séquence basée sur l’examen de la `CreateSequence` en-têtes d’adressage du message.</span><span class="sxs-lookup"><span data-stu-id="66f23-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="66f23-171">Composition du protocole</span><span class="sxs-lookup"><span data-stu-id="66f23-171">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="66f23-172">Composition avec WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="66f23-172">Composition with WS-Addressing</span></span>

<span data-ttu-id="66f23-173">WCF prend en charge deux versions de WS-Addressing : WS-Addressing 2004/08 [WS-ADDR] et W3C WS-Addressing 1.0 recommandations [WS-ADDR-CORE] et [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="66f23-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="66f23-174">Bien que la spécification de la messagerie WS-Reliable mentionne WS-Addressing 2004/08 uniquement, cela ne constitue pas une restriction en ce qui concerne la version WS-Addressing à utiliser.</span><span class="sxs-lookup"><span data-stu-id="66f23-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="66f23-175">Voici une liste de contraintes qui s’appliquent à WCF :</span><span class="sxs-lookup"><span data-stu-id="66f23-175">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="66f23-176">R2101 : les deux WS-Addressing 2004/08 et WS-Addressing 1.0 peuvent être utilisé avec la messagerie WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="66f23-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="66f23-177">R2102:A une seule version de WS-Addressing doit être utilisée tout au long d’une séquence de messagerie WS-Reliable donnée ou une paire de séquences réciproques corrélées à l’aide de la `wsrm:Offer` mécanisme.</span><span class="sxs-lookup"><span data-stu-id="66f23-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="66f23-178">Composition avec SOAP</span><span class="sxs-lookup"><span data-stu-id="66f23-178">Composition with SOAP</span></span>

<span data-ttu-id="66f23-179">WCF prend en charge l’utilisation de SOAP 1.1 et SOAP 1.2 avec WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="66f23-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="66f23-180">Composition avec WS-Security et WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="66f23-180">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="66f23-181">WCF fournit une protection pour les séquences WS-Reliable Messaging à l’aide de sécurisé de Transport (HTTPS), de composition avec WS-Security et de composition avec WS-Secure Conversation.</span><span class="sxs-lookup"><span data-stu-id="66f23-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="66f23-182">Voici une liste de contraintes qui s’appliquent à WCF :</span><span class="sxs-lookup"><span data-stu-id="66f23-182">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="66f23-183">R2301 : pour protéger l’intégrité d’une séquence de messagerie WS-Reliable en plus de l’intégrité et la confidentialité des messages individuels, WCF requiert que WS-Secure Conversation doit être utilisée.</span><span class="sxs-lookup"><span data-stu-id="66f23-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="66f23-184">R2302:AWS-session Secure Conversation doit être établie avant l’établissement ou les séquences de messagerie WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="66f23-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>

- <span data-ttu-id="66f23-185">R2303 : Si la durée de vie séquence WS-Reliable Messaging dépasse WS-Secure Conversation durée de vie de session, le `SecurityContextToken` établi à l’aide de WS-Secure Conversation doit être renouvelée à l’aide de la liaison WS-Secure Conversation Renewal correspondante.</span><span class="sxs-lookup"><span data-stu-id="66f23-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="66f23-186">B2304:ws-séquence de messagerie fiable ou une paire de séquences réciproques corrélées est toujours liée à une seule session WS-SecureConversation.</span><span class="sxs-lookup"><span data-stu-id="66f23-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

  <span data-ttu-id="66f23-187">La source WCF génère le `wsse:SecurityTokenReference` élément dans la section d’extensibilité d’élément le `CreateSequence` message.</span><span class="sxs-lookup"><span data-stu-id="66f23-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>

- <span data-ttu-id="66f23-188">R2305:when composé avec WS-Secure Conversation, un `CreateSequence` message doit contenir le `wsse:SecurityTokenReference` élément.</span><span class="sxs-lookup"><span data-stu-id="66f23-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>

## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="66f23-189">Assertion WS-Policy de la messagerie WS-Reliable</span><span class="sxs-lookup"><span data-stu-id="66f23-189">WS-Reliable Messaging WS-Policy Assertion</span></span>

<span data-ttu-id="66f23-190">WCF utilise l’Assertion WS-Policy de la messagerie WS-Reliable `wsrm:RMAssertion` pour décrire les capacités de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="66f23-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="66f23-191">Voici une liste de contraintes qui s’appliquent à WCF :</span><span class="sxs-lookup"><span data-stu-id="66f23-191">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="66f23-192">B3001 : WCF attache `wsrm:RMAssertion` WS-Policy Assertion aux `wsdl:binding` éléments.</span><span class="sxs-lookup"><span data-stu-id="66f23-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="66f23-193">WCF prend en charge des pièces jointes aux `wsdl:binding` et `wsdl:port` éléments.</span><span class="sxs-lookup"><span data-stu-id="66f23-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="66f23-194">B3002 : WCF prend en charge les propriétés facultatives suivantes d’assertion WS-Reliable Messaging et assure leur contrôle sur WCF`ReliableMessagingBindingElement`:</span><span class="sxs-lookup"><span data-stu-id="66f23-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  <span data-ttu-id="66f23-195">Voici un exemple.</span><span class="sxs-lookup"><span data-stu-id="66f23-195">The following is an example.</span></span>

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="66f23-196">Extension de messagerie WS-Reliable pour le contrôle de flux</span><span class="sxs-lookup"><span data-stu-id="66f23-196">Flow Control WS-Reliable Messaging Extension</span></span>

<span data-ttu-id="66f23-197">WCF utilise extensibilité de la messagerie WS-Reliable pour renforcer le contrôle facultatif sur le flux de message de séquence.</span><span class="sxs-lookup"><span data-stu-id="66f23-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="66f23-198">Contrôle de flux est activé en définissant le <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="66f23-198">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="66f23-199">Voici une liste de contraintes qui s’appliquent à WCF :</span><span class="sxs-lookup"><span data-stu-id="66f23-199">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="66f23-200">B4001 : Lorsque le contrôle de flux de messagerie fiable est activé, WCF génère un `netrm:BufferRemaining` élément dans l’élément d’extensibilité de la `SequenceAcknowledgement` en-tête.</span><span class="sxs-lookup"><span data-stu-id="66f23-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="66f23-201">B4002 : Lorsque le contrôle de flux de messagerie fiable est activé, WCF ne nécessite pas un `netrm:BufferRemaining` élément soit présent dans `SequenceAcknowledgement` en-tête, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="66f23-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      http://fabrikam123.com/abc
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>
      8
    </netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="66f23-202">B4003 : WCF utilise `netrm:BufferRemaining` pour indiquer combien de nouveaux messages la Destination de messagerie fiable peut mettre en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="66f23-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>

- <span data-ttu-id="66f23-203">B4004 : le Service de messagerie fiable WCF limite le nombre de messages transmis lorsque l’application de destination de messagerie fiable ne peut pas recevoir les messages rapidement.</span><span class="sxs-lookup"><span data-stu-id="66f23-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="66f23-204">La destination de la messagerie fiable met en mémoire tampon les messages et la valeur de l’élément tombe à 0.</span><span class="sxs-lookup"><span data-stu-id="66f23-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>

- <span data-ttu-id="66f23-205">B4005 : WCF génère `netrm:BufferRemaining` entier des valeurs comprises entre 0 et inclusif de 4096 et lit les valeurs de nombre entier compris entre 0 et `xs:int`de `maxInclusive` valeur 214748364 inclusif.</span><span class="sxs-lookup"><span data-stu-id="66f23-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="66f23-206">Modèles d’échange de messages</span><span class="sxs-lookup"><span data-stu-id="66f23-206">Message Exchange Patterns</span></span>

<span data-ttu-id="66f23-207">Cette section décrit le comportement de WCF lors de la messagerie WS-Reliable est utilisée pour différents modèles d’échange de Message.</span><span class="sxs-lookup"><span data-stu-id="66f23-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="66f23-208">Pour chaque modèle d'échange de messages, les deux scénarios de déploiements suivants sont considérés :</span><span class="sxs-lookup"><span data-stu-id="66f23-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="66f23-209">Initiateur non adressable : L’initiateur est derrière un pare-feu ; Répondeur peut remettre des messages à l’initiateur uniquement sur les réponses HTTP.</span><span class="sxs-lookup"><span data-stu-id="66f23-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="66f23-210">Initiateur adressable : Initiateur et le répondeur peuvent recevoir des requêtes HTTP ; en d’autres termes, les deux connexions HTTP réciproques peuvent être établies.</span><span class="sxs-lookup"><span data-stu-id="66f23-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="66f23-211">Initiateur unidirectionnel, non adressable</span><span class="sxs-lookup"><span data-stu-id="66f23-211">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="66f23-212">Liaison</span><span class="sxs-lookup"><span data-stu-id="66f23-212">Binding</span></span>

<span data-ttu-id="66f23-213">WCF fournit un modèle d’échange de messages unidirectionnel à l’aide d’une séquence sur un canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="66f23-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="66f23-214">WCF utilise les requêtes HTTP pour transmettre tous les messages à partir du RMS au RMD et la réponse HTTP pour transmettre les messages du RMD au RMS.</span><span class="sxs-lookup"><span data-stu-id="66f23-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="66f23-215">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="66f23-215">CreateSequence Exchange</span></span>

<span data-ttu-id="66f23-216">L’initiateur WCF génère un `CreateSequence` message sans offre.</span><span class="sxs-lookup"><span data-stu-id="66f23-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="66f23-217">Le répondeur de WCF garantit la `CreateSequence` n’a aucune offre avant de créer une séquence.</span><span class="sxs-lookup"><span data-stu-id="66f23-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="66f23-218">Le répondeur WCF répond à la `CreateSequence` demande avec un `CreateSequenceResponse` message.</span><span class="sxs-lookup"><span data-stu-id="66f23-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="66f23-219">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="66f23-219">SequenceAcknowledgement</span></span>

<span data-ttu-id="66f23-220">L’initiateur WCF traite les accusés de réception sur la réponse de tous les messages sauf le `CreateSequence` message et les messages d’erreur.</span><span class="sxs-lookup"><span data-stu-id="66f23-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="66f23-221">Le répondeur WCF génère toujours un accusé de réception autonome dans la réponse à ces deux séquence et `AckRequested` messages.</span><span class="sxs-lookup"><span data-stu-id="66f23-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>

#### <a name="terminatesequence-message"></a><span data-ttu-id="66f23-222">Message TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="66f23-222">TerminateSequence message</span></span>

<span data-ttu-id="66f23-223">WCF traite `TerminateSequence` comme une opération unidirectionnelle, ce qui signifie que la réponse HTTP a un corps vide et le code d’état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="66f23-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="66f23-224">Initiateur unidirectionnel, adressable</span><span class="sxs-lookup"><span data-stu-id="66f23-224">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="66f23-225">Liaison</span><span class="sxs-lookup"><span data-stu-id="66f23-225">Binding</span></span>

<span data-ttu-id="66f23-226">WCF fournit un modèle d’échange de messages unidirectionnel à l’aide d’une séquence sur un trafic entrant et un canal Http sortant.</span><span class="sxs-lookup"><span data-stu-id="66f23-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="66f23-227">WCF utilise les requêtes HTTP pour transmettre tous les messages.</span><span class="sxs-lookup"><span data-stu-id="66f23-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="66f23-228">Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="66f23-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="66f23-229">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="66f23-229">CreateSequence Exchange</span></span>

<span data-ttu-id="66f23-230">L’initiateur WCF génère un `CreateSequence` message sans offre.</span><span class="sxs-lookup"><span data-stu-id="66f23-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="66f23-231">Le répondeur de WCF garantit que le `CreateSequence` n’a aucune offre avant de créer une séquence.</span><span class="sxs-lookup"><span data-stu-id="66f23-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="66f23-232">Le répondeur de WCF transmet le `CreateSequenceResponse` message sur une requête HTTP adressée avec la `ReplyTo` référence de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="66f23-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="66f23-233">Initiateur duplex, adressable</span><span class="sxs-lookup"><span data-stu-id="66f23-233">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="66f23-234">Liaison</span><span class="sxs-lookup"><span data-stu-id="66f23-234">Binding</span></span>

<span data-ttu-id="66f23-235">WCF fournit un modèle d’échange de messages bidirectionnel entièrement asynchrone à l’aide de deux séquences sur un trafic entrant et un canal HTTP sortant.</span><span class="sxs-lookup"><span data-stu-id="66f23-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="66f23-236">WCF utilise les requêtes HTTP pour transmettre tous les messages.</span><span class="sxs-lookup"><span data-stu-id="66f23-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="66f23-237">Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="66f23-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="66f23-238">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="66f23-238">CreateSequence Exchange</span></span>

<span data-ttu-id="66f23-239">L’initiateur WCF génère un `CreateSequence` message avec une offre.</span><span class="sxs-lookup"><span data-stu-id="66f23-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="66f23-240">Le répondeur de WCF garantit que le `CreateSequence` a une offre avant de créer une séquence.</span><span class="sxs-lookup"><span data-stu-id="66f23-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="66f23-241">WCF envoie le `CreateSequenceResponse` sur la requête HTTP adressée à la `CreateSequence`de `ReplyTo` référence de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="66f23-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="66f23-242">Durée de vie de séquence</span><span class="sxs-lookup"><span data-stu-id="66f23-242">Sequence Lifetime</span></span>

<span data-ttu-id="66f23-243">WCF traite les deux séquences comme une session duplex complète.</span><span class="sxs-lookup"><span data-stu-id="66f23-243">WCF treats the two sequences as one fully duplex session.</span></span>

<span data-ttu-id="66f23-244">Lors de la génération d’une erreur qui fait échouer une séquence, WCF attend le point de terminaison distant d’erreur les deux séquences.</span><span class="sxs-lookup"><span data-stu-id="66f23-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="66f23-245">À la lecture d’une erreur qui fait échouer une séquence, WCF provoque des erreurs les deux séquences.</span><span class="sxs-lookup"><span data-stu-id="66f23-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="66f23-246">WCF peut fermer sa séquence sortante et continuer à traiter les messages sur sa séquence entrante.</span><span class="sxs-lookup"><span data-stu-id="66f23-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="66f23-247">À l’inverse, WCF peut traiter la fermeture de la séquence entrante et continuer à envoyer des messages sur sa séquence sortante.</span><span class="sxs-lookup"><span data-stu-id="66f23-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="66f23-248">Initiateur demande-réponse, non adressable</span><span class="sxs-lookup"><span data-stu-id="66f23-248">Request-Reply, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="66f23-249">Liaison</span><span class="sxs-lookup"><span data-stu-id="66f23-249">Binding</span></span>

<span data-ttu-id="66f23-250">WCF fournit un unidirectionnel et modèle d’échange de message demande-réponse à l’aide de deux séquences sur un canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="66f23-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="66f23-251">WCF utilise les requêtes HTTP pour transmettre les messages de séquence de demande et utilise les réponses HTTP pour transmettre des messages de la séquence de réponse.</span><span class="sxs-lookup"><span data-stu-id="66f23-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="66f23-252">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="66f23-252">CreateSequence Exchange</span></span>

<span data-ttu-id="66f23-253">L’initiateur WCF génère un `CreateSequence` message avec une offre.</span><span class="sxs-lookup"><span data-stu-id="66f23-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="66f23-254">Le répondeur de WCF garantit que le `CreateSequence` a une offre avant de créer une séquence.</span><span class="sxs-lookup"><span data-stu-id="66f23-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="66f23-255">Le répondeur WCF répond à la `CreateSequence` demande avec un `CreateSequenceResponse` message.</span><span class="sxs-lookup"><span data-stu-id="66f23-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="66f23-256">Message unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="66f23-256">One-way Message</span></span>

<span data-ttu-id="66f23-257">Pour terminer avec succès un protocole d’échange de messages unidirectionnel, l’initiateur de WCF transmet un message de séquence de demande sur la requête HTTP et reçoit un autonome `SequenceAcknowledgement` message sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="66f23-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="66f23-258">`SequenceAcknowledgement` doit accepter le message transmis.</span><span class="sxs-lookup"><span data-stu-id="66f23-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="66f23-259">Le répondeur WCF peut répondre à la demande avec un accusé de réception, une erreur ou une réponse avec un corps vide et le code d’état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="66f23-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="66f23-260">Messages bidirectionnels</span><span class="sxs-lookup"><span data-stu-id="66f23-260">Two Way Messages</span></span>

<span data-ttu-id="66f23-261">Pour terminer avec succès un protocole d’échange de messages bidirectionnel, l’initiateur de WCF transmet un message de séquence de demande sur la requête HTTP et reçoit un message de séquence de réponse sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="66f23-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="66f23-262">La réponse doit contenir un `SequenceAcknowledgement` qui accuse réception du message de séquence de demande transmis.</span><span class="sxs-lookup"><span data-stu-id="66f23-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="66f23-263">Le répondeur WCF peut répondre à la demande avec une réponse d’application, une erreur ou une réponse avec un corps vide et le code d’état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="66f23-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="66f23-264">En raison de la présence de messages unidirectionnels et du délai d'attente des réponses d'application, le numéro de séquence du message de séquence de demande et le numéro de séquence du message de réponse n'ont aucune corrélation.</span><span class="sxs-lookup"><span data-stu-id="66f23-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="66f23-265">Nouvelles tentatives de réponses</span><span class="sxs-lookup"><span data-stu-id="66f23-265">Retrying Replies</span></span>

<span data-ttu-id="66f23-266">WCF s’appuie sur une corrélation demande-réponse HTTP pour la corrélation protocole d’échange de messages bidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="66f23-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="66f23-267">Pour cette raison, l’initiateur de WCF n’arrête pas une nouvelle tentative d’un message de séquence de demande lorsque le message de séquence de demande est accepté, mais lors de la réponse HTTP contient un accusé de réception, un message de l’utilisateur ou une erreur.</span><span class="sxs-lookup"><span data-stu-id="66f23-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="66f23-268">Le répondeur WCF réessaie des réponses sur le tronçon HTTP de la demande à laquelle la réponse est corrélée.</span><span class="sxs-lookup"><span data-stu-id="66f23-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>

#### <a name="lastmessage-exchange"></a><span data-ttu-id="66f23-269">Échange LastMessage</span><span class="sxs-lookup"><span data-stu-id="66f23-269">LastMessage Exchange</span></span>

<span data-ttu-id="66f23-270">L’initiateur WCF génère et transmet un dernier message vide sur le tronçon de demande HTTP.</span><span class="sxs-lookup"><span data-stu-id="66f23-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="66f23-271">WCF requiert une réponse mais ignore le message de réponse réelle.</span><span class="sxs-lookup"><span data-stu-id="66f23-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="66f23-272">Le répondeur WCF répond à dernier message vide de la séquence de demande avec vide dernier message la séquence de réponse.</span><span class="sxs-lookup"><span data-stu-id="66f23-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>

<span data-ttu-id="66f23-273">Si le répondeur WCF reçoit un dernier message dans lequel l’URI action n’est pas `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, les réponses WCF avec un dernier message.</span><span class="sxs-lookup"><span data-stu-id="66f23-273">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="66f23-274">Dans le cas d'un protocole d'échange de messages bidirectionnel, le dernier message contient le message d'application ; dans le cas d'un protocole d'échange de messages unidirectionnel, le dernier message est vide.</span><span class="sxs-lookup"><span data-stu-id="66f23-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>

<span data-ttu-id="66f23-275">Le répondeur WCF ne nécessite pas d’accusé de réception pour le dernier message de la séquence de réponse vide.</span><span class="sxs-lookup"><span data-stu-id="66f23-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="66f23-276">Échange TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="66f23-276">TerminateSequence Exchange</span></span>

<span data-ttu-id="66f23-277">Lorsque toutes les demandes ont reçu une réponse valide, l’initiateur WCF génère et transmet la séquence de demande `TerminateSequence` message sur le tronçon de demande HTTP.</span><span class="sxs-lookup"><span data-stu-id="66f23-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="66f23-278">WCF requiert une réponse mais ignore le message de réponse réelle.</span><span class="sxs-lookup"><span data-stu-id="66f23-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="66f23-279">Le répondeur WCF répond à la séquence de demande `TerminateSequence` message avec la séquence de réponse `TerminateSequence` message.</span><span class="sxs-lookup"><span data-stu-id="66f23-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>

<span data-ttu-id="66f23-280">Dans une séquence d'arrêt normale, les deux messages `TerminateSequence` incluent un `SequenceAcknowledgement` complet.</span><span class="sxs-lookup"><span data-stu-id="66f23-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="66f23-281">Initiateur demande/réponse, adressable</span><span class="sxs-lookup"><span data-stu-id="66f23-281">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="66f23-282">Liaison</span><span class="sxs-lookup"><span data-stu-id="66f23-282">Binding</span></span>

<span data-ttu-id="66f23-283">WCF fournit un modèle d’échange de message demande-réponse à l’aide de deux séquences sur un trafic entrant et un canal HTTP sortant.</span><span class="sxs-lookup"><span data-stu-id="66f23-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="66f23-284">WCF utilise les requêtes HTTP pour transmettre tous les messages.</span><span class="sxs-lookup"><span data-stu-id="66f23-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="66f23-285">Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="66f23-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="66f23-286">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="66f23-286">CreateSequence Exchange</span></span>

<span data-ttu-id="66f23-287">L’initiateur WCF génère un `CreateSequence` message avec une offre.</span><span class="sxs-lookup"><span data-stu-id="66f23-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="66f23-288">Le répondeur de WCF garantit que le `CreateSequence` a une offre avant de créer une séquence.</span><span class="sxs-lookup"><span data-stu-id="66f23-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="66f23-289">WCF envoie le `CreateSequenceResponse` sur la requête HTTP adressée à la `CreateSequence`de `ReplyTo` référence de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="66f23-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="66f23-290">Corrélation demande/réponse</span><span class="sxs-lookup"><span data-stu-id="66f23-290">Request/Reply Correlation</span></span>

<span data-ttu-id="66f23-291">L’initiateur de WCF garantit que tous les ours de messages de demande application un `MessageId` et un `ReplyTo` référence de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="66f23-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="66f23-292">L’initiateur de WCF s’applique le `CreateSequence` du message `ReplyTo` référence de point de terminaison sur chaque message de demande d’application.</span><span class="sxs-lookup"><span data-stu-id="66f23-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="66f23-293">Le répondeur WCF requiert que demande entrante messages portent un `MessageId` et un `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="66f23-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="66f23-294">Le répondeur de WCF garantit que les URI de la référence de point de terminaison des deux le `CreateSequence` et tous les messages de demande d’application sont identiques.</span><span class="sxs-lookup"><span data-stu-id="66f23-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>

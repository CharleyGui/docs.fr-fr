---
title: Protocole de messagerie fiable version 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: 8d192afcffca52136d6d71de49770c5a5ad13895
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202304"
---
# <a name="reliable-messaging-protocol-version-10"></a><span data-ttu-id="efe5a-102">Protocole de messagerie fiable version 1.0</span><span class="sxs-lookup"><span data-stu-id="efe5a-102">Reliable Messaging Protocol version 1.0</span></span>

<span data-ttu-id="efe5a-103">Cette rubrique couvre les détails de l’implémentation de Windows Communication Foundation (WCF) pour le protocole WS-Reliable Messaging 2005 (version 1,0) nécessaire pour l’interopérabilité à l’aide du transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="efe5a-103">This topic covers Windows Communication Foundation (WCF) implementation details for the WS-Reliable Messaging February 2005 (version 1.0) protocol necessary for interoperation using the HTTP transport.</span></span> <span data-ttu-id="efe5a-104">WCF suit la spécification de la messagerie WS-Reliable avec les contraintes et les clarifications décrites dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="efe5a-104">WCF follows the WS-Reliable Messaging specification with the constraints and clarifications explained in this topic.</span></span> <span data-ttu-id="efe5a-105">Notez que le protocole WS-ReliableMessaging version 1,0 est implémenté à partir de WinFX.</span><span class="sxs-lookup"><span data-stu-id="efe5a-105">Note that the WS-ReliableMessaging version 1.0 protocol is implemented starting with the WinFX.</span></span>

<span data-ttu-id="efe5a-106">Le protocole de la messagerie WS-Reliable de février 2005 est implémenté dans WCF par le <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="efe5a-106">The WS-Reliable Messaging February 2005 protocol is implemented in WCF by the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.</span></span>

<span data-ttu-id="efe5a-107">Pour plus de simplicité, la rubrique utilise les rôles suivants :</span><span class="sxs-lookup"><span data-stu-id="efe5a-107">For convenience, the topic uses the following roles:</span></span>

- <span data-ttu-id="efe5a-108">Initiateur : client qui initialise la création de la séquence de message WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="efe5a-108">Initiator: the client that initiates WS-Reliable Message sequence creation</span></span>

- <span data-ttu-id="efe5a-109">Répondeur : service qui reçoit les demandes de l'initiateur.</span><span class="sxs-lookup"><span data-stu-id="efe5a-109">Responder: the service that receives the initiator's requests</span></span>

<span data-ttu-id="efe5a-110">Ce document utilise les préfixes et les espaces de noms répertoriés dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="efe5a-110">This document uses the prefixes and namespaces in the following table.</span></span>

|<span data-ttu-id="efe5a-111">Préfixe</span><span class="sxs-lookup"><span data-stu-id="efe5a-111">Prefix</span></span>|<span data-ttu-id="efe5a-112">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="efe5a-112">Namespace</span></span>|
|------------|---------------|
|<span data-ttu-id="efe5a-113">wsrm</span><span class="sxs-lookup"><span data-stu-id="efe5a-113">wsrm</span></span>|`http://schemas.xmlsoap.org/ws/2005/02/rm`|
|<span data-ttu-id="efe5a-114">netrm</span><span class="sxs-lookup"><span data-stu-id="efe5a-114">netrm</span></span>|`http://schemas.microsoft.com/ws/2006/05/rm`|
|<span data-ttu-id="efe5a-115">s</span><span class="sxs-lookup"><span data-stu-id="efe5a-115">s</span></span>|`http://www.w3.org/2003/05/soap-envelope`|
|<span data-ttu-id="efe5a-116">wsa</span><span class="sxs-lookup"><span data-stu-id="efe5a-116">wsa</span></span>|`http://schemas.xmlsoap.org/ws/2005/08/addressing`|
|<span data-ttu-id="efe5a-117">wsse</span><span class="sxs-lookup"><span data-stu-id="efe5a-117">wsse</span></span>|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|

## <a name="messaging"></a><span data-ttu-id="efe5a-118">Messagerie</span><span class="sxs-lookup"><span data-stu-id="efe5a-118">Messaging</span></span>

### <a name="sequence-establishment-messages"></a><span data-ttu-id="efe5a-119">Messages d'établissement de séquence</span><span class="sxs-lookup"><span data-stu-id="efe5a-119">Sequence Establishment Messages</span></span>

<span data-ttu-id="efe5a-120">WCF implémente `CreateSequence` les `CreateSequenceResponse` messages et pour établir une séquence de message fiable.</span><span class="sxs-lookup"><span data-stu-id="efe5a-120">WCF implements `CreateSequence` and `CreateSequenceResponse` messages to establish a reliable message sequence.</span></span> <span data-ttu-id="efe5a-121">Les contraintes suivantes s'appliquent :</span><span class="sxs-lookup"><span data-stu-id="efe5a-121">The following constraints apply:</span></span>

- <span data-ttu-id="efe5a-122">B1101 : l’initiateur WCF ne génère pas l’élément Expires facultatif dans le `CreateSequence` message ou, dans le cas où le `CreateSequence` message contient un `Offer` élément, l' `Expires` élément facultatif dans l' `Offer` élément.</span><span class="sxs-lookup"><span data-stu-id="efe5a-122">B1101: The WCF Initiator does not generate the optional Expires element in the `CreateSequence` message or, in the cases when the `CreateSequence` message contains an `Offer` element, the optional `Expires` element in the `Offer` element.</span></span>

- <span data-ttu-id="efe5a-123">B1102 : lors de l’accès au `CreateSequence` message, WCF `Responder` envoie et reçoit les deux `Expires` éléments s’ils existent, mais n’utilise pas leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="efe5a-123">B1102: When accessing the `CreateSequence` message, the WCF`Responder` sends and receives both `Expires` elements if they exist, but does not use their values.</span></span>

<span data-ttu-id="efe5a-124">La messagerie WS-Reliable introduit le mécanisme `Offer` pour établir deux séquences corrélées réciproques qui forment une session.</span><span class="sxs-lookup"><span data-stu-id="efe5a-124">WS-Reliable Messaging introduces the `Offer` mechanism to establish the two converse correlated sequences that form a session.</span></span>

- <span data-ttu-id="efe5a-125">R1103 : si `CreateSequence` contient un élément `Offer`, le répondeur de messagerie fiable doit soit accepter la séquence et répondre avec `CreateSequenceResponse` contenant un élément `wsrm:Accept`, formant deux séquences réciproques corrélées, soit rejeter la demande `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="efe5a-125">R1103: If `CreateSequence` contains an `Offer` element, the Reliable Messaging Responder must either accept the sequence and respond with `CreateSequenceResponse` that contains a `wsrm:Accept` element, forming two correlated converse sequences or reject the `CreateSequence` request.</span></span>

- <span data-ttu-id="efe5a-126">R1104 : l'`SequenceAcknowledgement` et les messages d'application qui passent sur la séquence réciproque doivent être envoyés à la référence de point de terminaison `ReplyTo` de `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="efe5a-126">R1104: `SequenceAcknowledgement` and application messages flowing on converse sequence must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="efe5a-127">R1105 : les références de point de terminaison `AcksTo` et `ReplyTo` dans `CreateSequence` doivent avoir des valeurs d'adresse qui correspondent au niveau des octets.</span><span class="sxs-lookup"><span data-stu-id="efe5a-127">R1105: `AcksTo` and `ReplyTo` endpoint references in the `CreateSequence` must have address values that match the octet-wise.</span></span>

  <span data-ttu-id="efe5a-128">Le répondeur WCF vérifie que la partie URI des `AcksTo` `ReplyTo` ERP et est identique avant de créer une séquence.</span><span class="sxs-lookup"><span data-stu-id="efe5a-128">The WCF Responder verifies that the URI portion of the `AcksTo` and `ReplyTo` EPRs are identical before creating a sequence.</span></span>

- <span data-ttu-id="efe5a-129">R1106 : les références de point de terminaison `AcksTo` et `ReplyTo` dans `CreateSequence` doivent avoir le même jeu de paramètres de référence.</span><span class="sxs-lookup"><span data-stu-id="efe5a-129">R1106: `AcksTo` and `ReplyTo` Endpoint References in the `CreateSequence` should have the same set of reference parameters.</span></span>

  <span data-ttu-id="efe5a-130">WCF n’applique pas, mais suppose que les [paramètres de référence] de `AcksTo` et `ReplyTo` sur `CreateSequence` sont identiques et utilise les [paramètres de référence] de la `ReplyTo` référence de point de terminaison pour les accusés de réception et les messages de séquence réciproque.</span><span class="sxs-lookup"><span data-stu-id="efe5a-130">WCF does not enforce but assumes that [reference parameters] of `AcksTo` and `ReplyTo` on `CreateSequence` are identical and uses [reference parameters] from `ReplyTo` endpoint reference for acknowledgements and converse sequence messages.</span></span>

- <span data-ttu-id="efe5a-131">R1107 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme `Offer`, l'`SequenceAcknowledgement` et les messages d'application qui traversent les séquences réciproques doivent être envoyés à la référence de point de terminaison `ReplyTo` de `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="efe5a-131">R1107: When two converse sequences are established using the `Offer` mechanism, `SequenceAcknowledgement` and application messages flowing on converse sequences must be sent to the `ReplyTo` endpoint reference of the `CreateSequence`.</span></span>

- <span data-ttu-id="efe5a-132">R1108 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme Offer, la propriété `[address]` de l'élément enfant `wsrm:AcksTo` de la référence de point de terminaison de l'élément `wsrm:Accept` de la `CreateSequenceResponse` doit correspondre octet par octet à l'URI de destination de `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="efe5a-132">R1108: When two converse sequences are established using the Offer mechanism, the `[address]` property of the `wsrm:AcksTo` Endpoint Reference child element of the `wsrm:Accept` element of the `CreateSequenceResponse` must match byte-wise the destination URI of the `CreateSequence`.</span></span>

- <span data-ttu-id="efe5a-133">R1109 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme `Offer`, les messages envoyés par l'initiateur et les accusés de réception des messages envoyés par le répondeur doivent être envoyés à la même référence de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="efe5a-133">R1109: When two converse sequences are established using the `Offer` mechanism, messages sent by initiator and acknowledgements to messages by responder must be sent to the same Endpoint Reference.</span></span>

  <span data-ttu-id="efe5a-134">WCF utilise la messagerie WS-Reliable pour établir des sessions fiables entre l’initiateur et le répondeur.</span><span class="sxs-lookup"><span data-stu-id="efe5a-134">WCF uses WS-Reliable Messaging to establish reliable sessions between the Initiator and Responder.</span></span> <span data-ttu-id="efe5a-135">L’implémentation de la messagerie WS-Reliable de WCF fournit une session fiable pour les modèles de messagerie à sens unique, demande-réponse et duplex intégral.</span><span class="sxs-lookup"><span data-stu-id="efe5a-135">WCF's WS-Reliable Messaging implementation provides reliable session for one-way, request-reply and full duplex messaging patterns.</span></span> <span data-ttu-id="efe5a-136">Le mécanisme de messagerie WS-Reliable `Offer` sur `CreateSequence` / `CreateSequenceResponse` vous permet d’établir deux séquences réciproques corrélées et fournit un protocole de session qui convient à tous les points de terminaison de message.</span><span class="sxs-lookup"><span data-stu-id="efe5a-136">The WS-Reliable Messaging `Offer` mechanism on `CreateSequence`/`CreateSequenceResponse` lets you establish two correlated converse sequences, and provides a session protocol that is suitable for all message endpoints.</span></span> <span data-ttu-id="efe5a-137">Étant donné que WCF offre une garantie de sécurité pour une telle session, y compris une protection de bout en bout pour l’intégrité de la session, il est pratique de s’assurer que les messages destinés au même tiers arrivent à la même destination.</span><span class="sxs-lookup"><span data-stu-id="efe5a-137">Because WCF provides a security guarantee for such a session including end-to-end protection for session integrity, it is practical to ensure messages intended to the same party are arriving at the same destination.</span></span> <span data-ttu-id="efe5a-138">Cela permet également la superposition des accusés de réception de séquence sur les messages d'application.</span><span class="sxs-lookup"><span data-stu-id="efe5a-138">This also allows piggy-backing of sequence acknowledgements on application messages.</span></span> <span data-ttu-id="efe5a-139">Par conséquent, les contraintes R1104, R1105 et R1108 s’appliquent à WCF.</span><span class="sxs-lookup"><span data-stu-id="efe5a-139">Therefore, constraints R1104, R1105, and R1108 apply to WCF.</span></span>

<span data-ttu-id="efe5a-140">Exemple de message `CreateSequence`.</span><span class="sxs-lookup"><span data-stu-id="efe5a-140">An example of a `CreateSequence` message.</span></span>

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

 <span data-ttu-id="efe5a-141">Exemple de message `CreateSequenceResponse`.</span><span class="sxs-lookup"><span data-stu-id="efe5a-141">An example of a `CreateSequenceResponse` message.</span></span>

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

### <a name="sequence"></a><span data-ttu-id="efe5a-142">Séquence</span><span class="sxs-lookup"><span data-stu-id="efe5a-142">Sequence</span></span>

<span data-ttu-id="efe5a-143">Voici une liste des contraintes qui s'appliquent aux séquences :</span><span class="sxs-lookup"><span data-stu-id="efe5a-143">The following is a list of constraints that apply to sequences:</span></span>

- <span data-ttu-id="efe5a-144">B1201 : WCF génère et accède aux numéros de séquence qui ne sont pas plus élevés que `xs:long` la valeur inclusive maximale de 9223372036854775807.</span><span class="sxs-lookup"><span data-stu-id="efe5a-144">B1201:WCF generates and accesses sequence numbers no higher than `xs:long`’s maximum inclusive value, 9223372036854775807.</span></span>

- <span data-ttu-id="efe5a-145">B1202 : WCF génère toujours un dernier message vide avec l’URI d’action de `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .</span><span class="sxs-lookup"><span data-stu-id="efe5a-145">B1202:WCF always generates an empty-bodied last message with the action URI of `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

- <span data-ttu-id="efe5a-146">B1203 : WCF reçoit et remet un message avec un en-tête de séquence qui contient un `LastMessage` élément tant que l’URI d’action n’a pas la valeur `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .</span><span class="sxs-lookup"><span data-stu-id="efe5a-146">B1203: WCF receives and delivers a message with a Sequence header that contains a `LastMessage` element as long as the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.</span></span>

<span data-ttu-id="efe5a-147">Exemple d'en-tête Sequence.</span><span class="sxs-lookup"><span data-stu-id="efe5a-147">An example of a Sequence Header.</span></span>

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

### <a name="ackrequested-header"></a><span data-ttu-id="efe5a-148">En-tête AckRequested</span><span class="sxs-lookup"><span data-stu-id="efe5a-148">AckRequested Header</span></span>

<span data-ttu-id="efe5a-149">WCF utilise l' `AckRequested` en-tête comme un mécanisme Keep-Alive.</span><span class="sxs-lookup"><span data-stu-id="efe5a-149">WCF uses `AckRequested` Header as a keep-alive mechanism.</span></span> <span data-ttu-id="efe5a-150">WCF ne génère pas l' `MessageNumber` élément facultatif.</span><span class="sxs-lookup"><span data-stu-id="efe5a-150">WCF does not generate the optional `MessageNumber` element.</span></span> <span data-ttu-id="efe5a-151">Lors de la réception d’un message avec un `AckRequested` en-tête contenant l' `MessageNumber` élément, WCF ignore la `MessageNumber` valeur de l’élément, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="efe5a-151">Upon receiving a message with an `AckRequested` header that contains the `MessageNumber` element, WCF ignores the `MessageNumber` element’s value, as shown in the following example.</span></span>

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a><span data-ttu-id="efe5a-152">En-tête SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="efe5a-152">SequenceAcknowledgement Header</span></span>

<span data-ttu-id="efe5a-153">WCF utilise un mécanisme de superposition pour les accusés de réception de séquence fournis dans WS-Reliable Messaging.</span><span class="sxs-lookup"><span data-stu-id="efe5a-153">WCF uses piggy-back mechanism for sequence acknowledgements provided in WS-Reliable Messaging.</span></span>

- <span data-ttu-id="efe5a-154">R1401 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme `Offer`, l'en-tête `SequenceAcknowledgement` peut être inclus dans tout message d'application transmis au destinataire souhaité.</span><span class="sxs-lookup"><span data-stu-id="efe5a-154">R1401: When two converse sequences are established using the `Offer` mechanism, the `SequenceAcknowledgement` header may be included in any application message transmitted to the intended recipient.</span></span>

- <span data-ttu-id="efe5a-155">B1402 : lorsque WCF doit générer un accusé de réception avant de recevoir des messages de séquence (par exemple, pour répondre à un `AckRequested` message), WCF génère un `SequenceAcknowledgement` en-tête qui contient la plage 0-0, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="efe5a-155">B1402: When WCF must generate an acknowledgement prior to receiving any sequence messages (for example, to satisfy an `AckRequested` message), WCF generates a `SequenceAcknowledgement` header that contains the range 0-0, as shown in the following example.</span></span>

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- <span data-ttu-id="efe5a-156">B1403 : WCF ne génère pas `SequenceAcknowledgement` d’en-têtes contenant un `Nack` élément, mais prend en charge les `Nack` éléments.</span><span class="sxs-lookup"><span data-stu-id="efe5a-156">B1403: WCF does not generate `SequenceAcknowledgement` headers that contain a `Nack` element but supports `Nack` elements.</span></span>

### <a name="ws-reliablemessaging-faults"></a><span data-ttu-id="efe5a-157">Erreurs de la messagerie WS-Reliable</span><span class="sxs-lookup"><span data-stu-id="efe5a-157">WS-ReliableMessaging Faults</span></span>

<span data-ttu-id="efe5a-158">La liste suivante répertorie les contraintes qui s’appliquent à l’implémentation WCF des erreurs de messagerie WS-Reliable :</span><span class="sxs-lookup"><span data-stu-id="efe5a-158">The following is a list of constraints that apply to the WCF implementation of WS-Reliable Messaging faults:</span></span>

- <span data-ttu-id="efe5a-159">B1501 : WCF ne génère pas d' `MessageNumberRollover` Erreurs.</span><span class="sxs-lookup"><span data-stu-id="efe5a-159">B1501: WCF does not generate `MessageNumberRollover` faults.</span></span>

- <span data-ttu-id="efe5a-160">B1502 : le point de terminaison WCF peut générer `CreateSequenceRefused` des erreurs, comme décrit dans la spécification.</span><span class="sxs-lookup"><span data-stu-id="efe5a-160">B1502:WCF endpoint may generate `CreateSequenceRefused` faults as described in the specification.</span></span>

- <span data-ttu-id="efe5a-161">B1503 : lorsque le point de terminaison de service atteint sa limite de connexion et ne peut pas traiter de nouvelles connexions, WCF génère un `CreateSequenceRefused` sous-code d’erreur supplémentaire, `netrm:ConnectionLimitReached` , comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="efe5a-161">B1503:When the service endpoint reaches its connection limit and cannot process new connections, WCF generates an additional `CreateSequenceRefused` fault subcode, `netrm:ConnectionLimitReached`, as shown in the following example.</span></span>

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

### <a name="ws-addressing-faults"></a><span data-ttu-id="efe5a-162">Erreurs WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="efe5a-162">WS-Addressing Faults</span></span>

<span data-ttu-id="efe5a-163">Étant donné que la messagerie WS-Reliable utilise WS-Addressing, l’implémentation de la messagerie WS-Reliable WCF peut générer des erreurs WS-Addressing.</span><span class="sxs-lookup"><span data-stu-id="efe5a-163">Because WS-Reliable Messaging uses WS-Addressing, WCF WS-Reliable Messaging implementation may generate WS-Addressing faults.</span></span> <span data-ttu-id="efe5a-164">Cette section traite des erreurs WS-Addressing que WCF génère explicitement au niveau de la couche de messagerie WS-Reliable :</span><span class="sxs-lookup"><span data-stu-id="efe5a-164">This section covers the WS-Addressing faults that WCF explicitly generates at the WS-Reliable Messaging layer:</span></span>

- <span data-ttu-id="efe5a-165">B1601 : WCF génère l’en-tête d’adressage de message d’erreur requis lorsque l’une des conditions suivantes est remplie :</span><span class="sxs-lookup"><span data-stu-id="efe5a-165">B1601:WCF generates the fault Message Addressing Header Required when one of the following is true:</span></span>

  - <span data-ttu-id="efe5a-166">Un message n'a pas d'en-tête `Sequence` ni d'en-tête `Action`.</span><span class="sxs-lookup"><span data-stu-id="efe5a-166">A message is missing a `Sequence` header and an `Action` header.</span></span>

  - <span data-ttu-id="efe5a-167">Un message `CreateSequence` n'a pas d'en-tête `MessageId`.</span><span class="sxs-lookup"><span data-stu-id="efe5a-167">A `CreateSequence` message is missing a `MessageId` header.</span></span>

  - <span data-ttu-id="efe5a-168">Un message `CreateSequence` n'a pas d'en-tête `ReplyTo`.</span><span class="sxs-lookup"><span data-stu-id="efe5a-168">A `CreateSequence` message is missing a `ReplyTo` header.</span></span>

- <span data-ttu-id="efe5a-169">B1602 : WCF génère l’action d’erreur non prise en charge en réponse à un message dont `Sequence` l’en-tête est manquant et dont `Action` l’en-tête n’est pas reconnu dans la spécification de la messagerie WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="efe5a-169">B1602:WCF generates the fault Action Not Supported in reply to a message that is missing a `Sequence` header and has an `Action` header that is not a recognized in the WS-Reliable Messaging specification.</span></span>

- <span data-ttu-id="efe5a-170">B1603 : WCF génère le point de terminaison d’erreur non disponible pour indiquer que le point de terminaison ne traite pas la séquence en fonction de l’examen des `CreateSequence` en-têtes d’adressage du message.</span><span class="sxs-lookup"><span data-stu-id="efe5a-170">B1603:WCF generates the fault Endpoint Unavailable to indicate that the endpoint does not process the sequence based upon examination of the `CreateSequence` message’s addressing headers.</span></span>

## <a name="protocol-composition"></a><span data-ttu-id="efe5a-171">Composition du protocole</span><span class="sxs-lookup"><span data-stu-id="efe5a-171">Protocol Composition</span></span>

### <a name="composition-with-ws-addressing"></a><span data-ttu-id="efe5a-172">Composition avec WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="efe5a-172">Composition with WS-Addressing</span></span>

<span data-ttu-id="efe5a-173">WCF prend en charge deux versions de WS-Addressing : WS-Addressing 2004/08 [WS-ADDR] et W3C WS-Addressing 1,0 Recommendations [WS-ADDR-CORE] et [WS-ADDR-SOAP].</span><span class="sxs-lookup"><span data-stu-id="efe5a-173">WCF supports two versions of WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] and W3C WS-Addressing 1.0 Recommendations [WS-ADDR-CORE] and [WS-ADDR-SOAP].</span></span>

<span data-ttu-id="efe5a-174">Bien que la spécification de la messagerie WS-Reliable mentionne WS-Addressing 2004/08 uniquement, cela ne constitue pas une restriction en ce qui concerne la version WS-Addressing à utiliser.</span><span class="sxs-lookup"><span data-stu-id="efe5a-174">While the WS-Reliable Messaging specification mentions only WS-Addressing 2004/08, it does not restrict the WS-Addressing version to be used.</span></span> <span data-ttu-id="efe5a-175">Voici une liste des contraintes qui s’appliquent à WCF :</span><span class="sxs-lookup"><span data-stu-id="efe5a-175">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="efe5a-176">R2101 : aussi bien WS-Addressing 2004/08 que WS-Addressing 1.0 peuvent être utilisés avec la messagerie WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="efe5a-176">R2101:Both WS-Addressing 2004/08 and WS-Addressing 1.0 can be used with WS-Reliable Messaging.</span></span>

- <span data-ttu-id="efe5a-177">R2102 : une seule version de WS-Addressing doit être utilisée dans une séquence de messagerie WS-Reliable donnée ou une paire de séquences réciproques corrélées à l’aide du `wsrm:Offer` mécanisme.</span><span class="sxs-lookup"><span data-stu-id="efe5a-177">R2102:A single version of WS-Addressing must be used throughout a given WS-Reliable Messaging sequence or a pair of converse sequences correlated by using the `wsrm:Offer` mechanism.</span></span>

### <a name="composition-with-soap"></a><span data-ttu-id="efe5a-178">Composition avec SOAP</span><span class="sxs-lookup"><span data-stu-id="efe5a-178">Composition with SOAP</span></span>

<span data-ttu-id="efe5a-179">WCF prend en charge l’utilisation de SOAP 1,1 et SOAP 1,2 avec la messagerie WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="efe5a-179">WCF supports use of both SOAP 1.1 and SOAP 1.2 with WS-Reliable Messaging.</span></span>

### <a name="composition-with-ws-security-and-ws-secureconversation"></a><span data-ttu-id="efe5a-180">Composition avec WS-Security et WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="efe5a-180">Composition with WS-Security and WS-SecureConversation</span></span>

<span data-ttu-id="efe5a-181">WCF fournit une protection pour les séquences de messagerie WS-Reliable en utilisant le transport sécurisé (HTTPs), la composition avec WS-Security et la composition avec WS-Secure conversation.</span><span class="sxs-lookup"><span data-stu-id="efe5a-181">WCF provides protection for WS-Reliable Messaging sequences by using secure Transport (HTTPS), composition with WS-Security, and composition with WS-Secure Conversation.</span></span> <span data-ttu-id="efe5a-182">Voici une liste des contraintes qui s’appliquent à WCF :</span><span class="sxs-lookup"><span data-stu-id="efe5a-182">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="efe5a-183">R2301 : pour protéger l’intégrité d’une séquence de messagerie WS-Reliable en plus de l’intégrité et de la confidentialité des messages individuels, WCF requiert l’utilisation de la conversation WS-Secure.</span><span class="sxs-lookup"><span data-stu-id="efe5a-183">R2301:To protect the integrity of a WS-Reliable Messaging sequence in addition to the integrity and confidentiality of individual messages, WCF requires that WS-Secure Conversation must be used.</span></span>

- <span data-ttu-id="efe5a-184">R2302 :unesession WS-Secure Conversation doit être établie avant d'établir la ou les séquences de messagerie WS-Reliable.</span><span class="sxs-lookup"><span data-stu-id="efe5a-184">R2302:AWS-Secure Conversation session must be established prior to establishing WS-Reliable Messaging sequence(s).</span></span>

- <span data-ttu-id="efe5a-185">R2303 : si la durée de vie de la séquence de messagerie WS-Reliable dépasse celle de la session WS-Secure Conversation, le `SecurityContextToken` établi à l'aide de WS-Secure Conversation doit être renouvelé par le biais de la liaison WS-Secure Conversation Renewal correspondante.</span><span class="sxs-lookup"><span data-stu-id="efe5a-185">R2303: If the WS-Reliable Messaging sequence lifetime exceeds the WS-Secure Conversation session’s lifetime, the `SecurityContextToken` established by using WS-Secure Conversation must be renewed by using the corresponding WS-Secure Conversation Renewal binding.</span></span>

- <span data-ttu-id="efe5a-186">B2304 :la séquence de messagerie WS-Reliable ou une paire de séquences réciproques corrélées est toujours liée à une session WS-SecureConversation unique.</span><span class="sxs-lookup"><span data-stu-id="efe5a-186">B2304:WS-Reliable Messaging sequence or a pair of correlated converse sequences are always bound to a single WS-SecureConversation session.</span></span>

  <span data-ttu-id="efe5a-187">La source WCF génère l' `wsse:SecurityTokenReference` élément dans la section d’extensibilité d’élément du `CreateSequence` message.</span><span class="sxs-lookup"><span data-stu-id="efe5a-187">The WCF source generates the `wsse:SecurityTokenReference` element in the element extensibility section of the `CreateSequence` message.</span></span>

- <span data-ttu-id="efe5a-188">R2305 : lorsqu’il est composé avec WS-Secure conversation, un `CreateSequence` message doit contenir l' `wsse:SecurityTokenReference` élément.</span><span class="sxs-lookup"><span data-stu-id="efe5a-188">R2305:When composed with WS-Secure Conversation, a `CreateSequence` message must contain the `wsse:SecurityTokenReference` element.</span></span>

## <a name="ws-reliable-messaging-ws-policy-assertion"></a><span data-ttu-id="efe5a-189">Assertion WS-Policy de la messagerie WS-Reliable</span><span class="sxs-lookup"><span data-stu-id="efe5a-189">WS-Reliable Messaging WS-Policy Assertion</span></span>

<span data-ttu-id="efe5a-190">WCF utilise l’assertion WS-Policy de la messagerie WS-Reliable `wsrm:RMAssertion` pour décrire les fonctionnalités des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="efe5a-190">WCF uses WS-Reliable Messaging WS-Policy Assertion `wsrm:RMAssertion` to describe endpoints capabilities.</span></span> <span data-ttu-id="efe5a-191">Voici une liste des contraintes qui s’appliquent à WCF :</span><span class="sxs-lookup"><span data-stu-id="efe5a-191">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="efe5a-192">B3001 : WCF attache l' `wsrm:RMAssertion` assertion WS-Policy à des `wsdl:binding` éléments.</span><span class="sxs-lookup"><span data-stu-id="efe5a-192">B3001: WCF attaches `wsrm:RMAssertion` WS-Policy Assertion to `wsdl:binding` elements.</span></span> <span data-ttu-id="efe5a-193">WCF prend en charge les deux pièces jointes aux `wsdl:binding` `wsdl:port` éléments et.</span><span class="sxs-lookup"><span data-stu-id="efe5a-193">WCF supports both attachments to `wsdl:binding` and `wsdl:port` elements.</span></span>

- <span data-ttu-id="efe5a-194">B3002 : WCF prend en charge les propriétés facultatives suivantes de l’assertion de messagerie WS-Reliable et en assure le contrôle sur WCF `ReliableMessagingBindingElement` :</span><span class="sxs-lookup"><span data-stu-id="efe5a-194">B3002: WCF supports the following optional properties of WS-Reliable Messaging assertion and provides control over them on the WCF`ReliableMessagingBindingElement`:</span></span>

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  <span data-ttu-id="efe5a-195">Voici un exemple.</span><span class="sxs-lookup"><span data-stu-id="efe5a-195">The following is an example.</span></span>

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a><span data-ttu-id="efe5a-196">Extension de messagerie WS-Reliable pour le contrôle de flux</span><span class="sxs-lookup"><span data-stu-id="efe5a-196">Flow Control WS-Reliable Messaging Extension</span></span>

<span data-ttu-id="efe5a-197">WCF utilise l’extensibilité de la messagerie WS-Reliable pour fournir un contrôle plus strict facultatif sur le déroulement du message de séquence.</span><span class="sxs-lookup"><span data-stu-id="efe5a-197">WCF uses WS-Reliable Messaging extensibility to provide optional additional tighter control over sequence message flow.</span></span>

<span data-ttu-id="efe5a-198">Le contrôle de Flow est activé en affectant à la propriété la valeur <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> `true` .</span><span class="sxs-lookup"><span data-stu-id="efe5a-198">Flow control is enabled by setting the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="efe5a-199">Voici une liste des contraintes qui s’appliquent à WCF :</span><span class="sxs-lookup"><span data-stu-id="efe5a-199">The following is a list of constraints that apply to WCF:</span></span>

- <span data-ttu-id="efe5a-200">B4001 : lorsque le contrôle de workflow de messagerie fiable est activé, WCF génère un `netrm:BufferRemaining` élément dans l’extensibilité d’élément de l' `SequenceAcknowledgement` en-tête.</span><span class="sxs-lookup"><span data-stu-id="efe5a-200">B4001: When Reliable Messaging Flow Control is enabled, WCF generates a `netrm:BufferRemaining` element in the element extensibility of the `SequenceAcknowledgement` header.</span></span>

- <span data-ttu-id="efe5a-201">B4002 : lorsque le contrôle de workflow de messagerie fiable est activé, WCF ne nécessite pas la présence d’un `netrm:BufferRemaining` élément dans `SequenceAcknowledgement` l’en-tête, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="efe5a-201">B4002: When Reliable Messaging Flow Control is enabled, WCF does not require a `netrm:BufferRemaining` element to be present in `SequenceAcknowledgement` header, as shown in the following example.</span></span>

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

- <span data-ttu-id="efe5a-202">B4003 : WCF utilise `netrm:BufferRemaining` pour indiquer le nombre de nouveaux messages que la destination de messagerie fiable peut mettre en mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="efe5a-202">B4003: WCF uses `netrm:BufferRemaining` to indicate how many new messages the Reliable Messaging Destination can buffer.</span></span>

- <span data-ttu-id="efe5a-203">B4004 : le service de messagerie fiable WCF limite le nombre de messages transmis lorsque l’application de destination de la messagerie fiable ne peut pas recevoir des messages rapidement.</span><span class="sxs-lookup"><span data-stu-id="efe5a-203">B4004:The WCF Reliable Messaging Service throttles the number of messages transmitted when the Reliable Messaging destination application cannot receive messages quickly.</span></span> <span data-ttu-id="efe5a-204">La destination de la messagerie fiable met en mémoire tampon les messages et la valeur de l’élément tombe à 0.</span><span class="sxs-lookup"><span data-stu-id="efe5a-204">The Reliable Messaging destination buffers messages and the element’s value drops to 0.</span></span>

- <span data-ttu-id="efe5a-205">B4005 : WCF génère `netrm:BufferRemaining` des valeurs entières comprises entre 0 et 4096 inclus, et lit les valeurs entières comprises entre 0 et `xs:int` la `maxInclusive` valeur 214748364 inclusives.</span><span class="sxs-lookup"><span data-stu-id="efe5a-205">B4005: WCF generates `netrm:BufferRemaining` integer values between 0 and 4096 inclusive, and reads integer values between 0 and `xs:int`’s `maxInclusive` value 214748364 inclusive.</span></span>

## <a name="message-exchange-patterns"></a><span data-ttu-id="efe5a-206">Modèles d’échange de messages</span><span class="sxs-lookup"><span data-stu-id="efe5a-206">Message Exchange Patterns</span></span>

<span data-ttu-id="efe5a-207">Cette section décrit le comportement de WCF lorsque la messagerie WS-Reliable est utilisée pour différents modèles d’échange de messages.</span><span class="sxs-lookup"><span data-stu-id="efe5a-207">This section describes WCF's behavior when WS-Reliable Messaging is used for different Message Exchange Patterns.</span></span> <span data-ttu-id="efe5a-208">Pour chaque modèle d'échange de messages, les deux scénarios de déploiements suivants sont considérés :</span><span class="sxs-lookup"><span data-stu-id="efe5a-208">For each Message Exchange Pattern the following two deployments scenarios are considered:</span></span>

- <span data-ttu-id="efe5a-209">Initiateur non adressable : l'initiateur est derrière un pare-feu ; le répondeur peut remettre des messages à celui-ci uniquement sur les réponses HTTP.</span><span class="sxs-lookup"><span data-stu-id="efe5a-209">Non-Addressable Initiator: Initiator is behind firewall; Responder can deliver messages to Initiator only on HTTP responses.</span></span>

- <span data-ttu-id="efe5a-210">Initiateur adressable : l'initiateur et le répondeur peuvent tous les deux recevoir des requêtes HTTP ; en d'autres termes, deux connexions HTTP réciproques peuvent être établies.</span><span class="sxs-lookup"><span data-stu-id="efe5a-210">Addressable Initiator: Initiator and Responder both can be sent HTTP requests; in other words, two converse HTTP connections can be established.</span></span>

### <a name="one-way-non-addressable-initiator"></a><span data-ttu-id="efe5a-211">Initiateur unidirectionnel, non adressable</span><span class="sxs-lookup"><span data-stu-id="efe5a-211">One-way, Non-addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="efe5a-212">Liaison</span><span class="sxs-lookup"><span data-stu-id="efe5a-212">Binding</span></span>

<span data-ttu-id="efe5a-213">WCF fournit un modèle d’échange de messages unidirectionnel qui utilise une séquence sur un canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="efe5a-213">WCF provides a one-way message exchange pattern using one sequence over one HTTP channel.</span></span> <span data-ttu-id="efe5a-214">WCF utilise les requêtes HTTP pour transmettre tous les messages du RMS au RMD et la réponse HTTP pour transmettre tous les messages du RMD au RMS.</span><span class="sxs-lookup"><span data-stu-id="efe5a-214">WCF uses the HTTP requests to transmit all messages from the RMS to the RMD and the HTTP response to transmit all messages from the RMD to the RMS.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="efe5a-215">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="efe5a-215">CreateSequence Exchange</span></span>

<span data-ttu-id="efe5a-216">L’initiateur WCF génère un `CreateSequence` message sans offre.</span><span class="sxs-lookup"><span data-stu-id="efe5a-216">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="efe5a-217">Le répondeur WCF garantit que le n' `CreateSequence` a pas d’offre avant de créer une séquence.</span><span class="sxs-lookup"><span data-stu-id="efe5a-217">The WCF Responder ensures the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="efe5a-218">Le répondeur WCF répond à la `CreateSequence` demande à l’aide d’un `CreateSequenceResponse` message.</span><span class="sxs-lookup"><span data-stu-id="efe5a-218">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="sequenceacknowledgement"></a><span data-ttu-id="efe5a-219">SequenceAcknowledgement</span><span class="sxs-lookup"><span data-stu-id="efe5a-219">SequenceAcknowledgement</span></span>

<span data-ttu-id="efe5a-220">L’initiateur WCF traite les accusés de réception de la réponse de tous les messages, à l’exception des `CreateSequence` messages de message et d’erreur.</span><span class="sxs-lookup"><span data-stu-id="efe5a-220">The WCF Initiator processes acknowledgements on the reply of all messages except the `CreateSequence` message and fault messages.</span></span> <span data-ttu-id="efe5a-221">Le répondeur WCF génère toujours un accusé de réception autonome dans la réponse à la séquence et aux `AckRequested` messages.</span><span class="sxs-lookup"><span data-stu-id="efe5a-221">The WCF Responder always generates a stand-alone acknowledgement in the response to both sequence and `AckRequested` messages.</span></span>

#### <a name="terminatesequence-message"></a><span data-ttu-id="efe5a-222">Message TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="efe5a-222">TerminateSequence message</span></span>

<span data-ttu-id="efe5a-223">WCF traite `TerminateSequence` comme une opération unidirectionnelle, ce qui signifie que la réponse http a un corps vide et un code d’état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="efe5a-223">WCF treats `TerminateSequence` as a one-way operation, meaning the HTTP response has an empty body and HTTP 202 status code.</span></span>

### <a name="one-way-addressable-initiator"></a><span data-ttu-id="efe5a-224">Initiateur unidirectionnel, adressable</span><span class="sxs-lookup"><span data-stu-id="efe5a-224">One Way, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="efe5a-225">Liaison</span><span class="sxs-lookup"><span data-stu-id="efe5a-225">Binding</span></span>

<span data-ttu-id="efe5a-226">WCF fournit un modèle d’échange de messages unidirectionnel qui utilise une séquence sur un canal http entrant et sortant.</span><span class="sxs-lookup"><span data-stu-id="efe5a-226">WCF provides a one-way message exchange pattern using one sequence over an inbound and an outbound Http channel.</span></span> <span data-ttu-id="efe5a-227">WCF utilise les requêtes HTTP pour transmettre tous les messages.</span><span class="sxs-lookup"><span data-stu-id="efe5a-227">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="efe5a-228">Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="efe5a-228">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="efe5a-229">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="efe5a-229">CreateSequence Exchange</span></span>

<span data-ttu-id="efe5a-230">L’initiateur WCF génère un `CreateSequence` message sans offre.</span><span class="sxs-lookup"><span data-stu-id="efe5a-230">The WCF Initiator generates a `CreateSequence` message with no offer.</span></span> <span data-ttu-id="efe5a-231">Le répondeur WCF s’assure que le `CreateSequence` n’a pas d’offre avant de créer une séquence.</span><span class="sxs-lookup"><span data-stu-id="efe5a-231">The WCF Responder ensures that the `CreateSequence` has no offer before creating a sequence.</span></span> <span data-ttu-id="efe5a-232">Le répondeur WCF transmet le `CreateSequenceResponse` message sur une requête HTTP adressée à la `ReplyTo` référence de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="efe5a-232">The WCF Responder transmits the `CreateSequenceResponse` message on an HTTP request addressed with the `ReplyTo` endpoint reference.</span></span>

### <a name="duplex-addressable-initiator"></a><span data-ttu-id="efe5a-233">Initiateur duplex, adressable</span><span class="sxs-lookup"><span data-stu-id="efe5a-233">Duplex, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="efe5a-234">Liaison</span><span class="sxs-lookup"><span data-stu-id="efe5a-234">Binding</span></span>

<span data-ttu-id="efe5a-235">WCF fournit un modèle d’échange de messages bidirectionnel entièrement asynchrone à l’aide de deux séquences sur un canal HTTP entrant et sortant.</span><span class="sxs-lookup"><span data-stu-id="efe5a-235">WCF provides a fully asynchronous two-way message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="efe5a-236">WCF utilise les requêtes HTTP pour transmettre tous les messages.</span><span class="sxs-lookup"><span data-stu-id="efe5a-236">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="efe5a-237">Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="efe5a-237">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="efe5a-238">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="efe5a-238">CreateSequence Exchange</span></span>

<span data-ttu-id="efe5a-239">L’initiateur WCF génère un `CreateSequence` message avec une offre.</span><span class="sxs-lookup"><span data-stu-id="efe5a-239">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="efe5a-240">Le répondeur WCF s’assure que `CreateSequence` a une offre avant de créer une séquence.</span><span class="sxs-lookup"><span data-stu-id="efe5a-240">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="efe5a-241">WCF envoie le `CreateSequenceResponse` sur la requête HTTP adressée à la `CreateSequence` `ReplyTo` référence de point de terminaison de.</span><span class="sxs-lookup"><span data-stu-id="efe5a-241">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="sequence-lifetime"></a><span data-ttu-id="efe5a-242">Durée de vie de séquence</span><span class="sxs-lookup"><span data-stu-id="efe5a-242">Sequence Lifetime</span></span>

<span data-ttu-id="efe5a-243">WCF traite les deux séquences comme une seule session duplex intégrale.</span><span class="sxs-lookup"><span data-stu-id="efe5a-243">WCF treats the two sequences as one fully duplex session.</span></span>

<span data-ttu-id="efe5a-244">Lors de la génération d’une erreur qui provoque une séquence, WCF s’attend à ce que le point de terminaison distant cause les deux séquences.</span><span class="sxs-lookup"><span data-stu-id="efe5a-244">Upon generating a fault that faults one sequence, WCF expects the remote endpoint to fault both sequences.</span></span> <span data-ttu-id="efe5a-245">Lors de la lecture d’une erreur qui provoque une séquence, les deux séquences sont des erreurs WCF.</span><span class="sxs-lookup"><span data-stu-id="efe5a-245">Upon reading a fault that faults one sequence, WCF faults both sequences.</span></span>

<span data-ttu-id="efe5a-246">WCF peut fermer sa séquence sortante et continuer à traiter les messages sur sa séquence entrante.</span><span class="sxs-lookup"><span data-stu-id="efe5a-246">WCF can close its outbound sequence and continue to process messages on its inbound sequence.</span></span> <span data-ttu-id="efe5a-247">À l’inverse, WCF peut traiter la fermeture de la séquence entrante et continuer à envoyer des messages sur sa séquence sortante.</span><span class="sxs-lookup"><span data-stu-id="efe5a-247">Conversely, WCF can process the close of the inbound sequence and continue to send messages on its outbound sequence.</span></span>

### <a name="request-reply-non-addressable-initiator"></a><span data-ttu-id="efe5a-248">Initiateur demande-réponse, non adressable</span><span class="sxs-lookup"><span data-stu-id="efe5a-248">Request-Reply, Non-Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="efe5a-249">Liaison</span><span class="sxs-lookup"><span data-stu-id="efe5a-249">Binding</span></span>

<span data-ttu-id="efe5a-250">WCF fournit un modèle d’échange de messages unidirectionnel et demande-réponse à l’aide de deux séquences sur un canal HTTP.</span><span class="sxs-lookup"><span data-stu-id="efe5a-250">WCF provides a one-way and request-reply message exchange pattern using two sequences over one HTTP channel.</span></span> <span data-ttu-id="efe5a-251">WCF utilise les requêtes HTTP pour transmettre les messages de la séquence de demande et utilise les réponses HTTP pour transmettre les messages de la séquence de réponse.</span><span class="sxs-lookup"><span data-stu-id="efe5a-251">WCF uses the HTTP requests to transmit the request sequence’s messages and uses the HTTP responses to transmit the reply sequence’s messages.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="efe5a-252">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="efe5a-252">CreateSequence Exchange</span></span>

<span data-ttu-id="efe5a-253">L’initiateur WCF génère un `CreateSequence` message avec une offre.</span><span class="sxs-lookup"><span data-stu-id="efe5a-253">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="efe5a-254">Le répondeur WCF s’assure que `CreateSequence` a une offre avant de créer une séquence.</span><span class="sxs-lookup"><span data-stu-id="efe5a-254">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="efe5a-255">Le répondeur WCF répond à la `CreateSequence` demande à l’aide d’un `CreateSequenceResponse` message.</span><span class="sxs-lookup"><span data-stu-id="efe5a-255">The WCF Responder replies to the `CreateSequence` request with a `CreateSequenceResponse` message.</span></span>

#### <a name="one-way-message"></a><span data-ttu-id="efe5a-256">Message unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="efe5a-256">One-way Message</span></span>

<span data-ttu-id="efe5a-257">Pour réussir un protocole d’échange de messages unidirectionnel, l’initiateur WCF transmet un message de séquence de demande sur la requête HTTP et reçoit un `SequenceAcknowledgement` message autonome sur la réponse http.</span><span class="sxs-lookup"><span data-stu-id="efe5a-257">To complete a one-way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a standalone `SequenceAcknowledgement` message on the HTTP response.</span></span> <span data-ttu-id="efe5a-258">`SequenceAcknowledgement` doit accepter le message transmis.</span><span class="sxs-lookup"><span data-stu-id="efe5a-258">The `SequenceAcknowledgement` must acknowledge the message transmitted.</span></span>

<span data-ttu-id="efe5a-259">Le répondeur WCF peut répondre à la demande avec un accusé de réception, une erreur ou une réponse avec un corps vide et un code d’état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="efe5a-259">The WCF Responder can reply to the request with an acknowledgement, a fault, or a response with an empty body and HTTP 202 status code.</span></span>

#### <a name="two-way-messages"></a><span data-ttu-id="efe5a-260">Messages bidirectionnels</span><span class="sxs-lookup"><span data-stu-id="efe5a-260">Two Way Messages</span></span>

<span data-ttu-id="efe5a-261">Pour réussir un protocole d’échange de messages bidirectionnel, l’initiateur WCF transmet un message de séquence de demande sur la requête HTTP et reçoit un message de séquence de réponse sur la réponse HTTP.</span><span class="sxs-lookup"><span data-stu-id="efe5a-261">To complete a two way message exchange protocol successfully, the WCF Initiator transmits a request sequence message on the HTTP request and receives a reply sequence message on the HTTP response.</span></span> <span data-ttu-id="efe5a-262">La réponse doit contenir un `SequenceAcknowledgement` qui accuse réception du message de séquence de demande transmis.</span><span class="sxs-lookup"><span data-stu-id="efe5a-262">The response must carry a `SequenceAcknowledgement` acknowledging the request sequence message transmitted.</span></span>

<span data-ttu-id="efe5a-263">Le répondeur WCF peut répondre à la demande avec une réponse d’application, une erreur ou une réponse avec un corps vide et un code d’état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="efe5a-263">The WCF Responder can reply to the request with an application reply, a fault or a response with an empty body and HTTP 202 status code.</span></span>

<span data-ttu-id="efe5a-264">En raison de la présence de messages unidirectionnels et du délai d'attente des réponses d'application, le numéro de séquence du message de séquence de demande et le numéro de séquence du message de réponse n'ont aucune corrélation.</span><span class="sxs-lookup"><span data-stu-id="efe5a-264">Because of the presence of one-way messages and the timing of application replies, the request sequence message’s sequence number and the response message’s sequence number have no correlation.</span></span>

#### <a name="retrying-replies"></a><span data-ttu-id="efe5a-265">Nouvelles tentatives de réponses</span><span class="sxs-lookup"><span data-stu-id="efe5a-265">Retrying Replies</span></span>

<span data-ttu-id="efe5a-266">WCF s’appuie sur la corrélation de requête-réponse HTTP pour la corrélation de protocole d’échange de messages bidirectionnels.</span><span class="sxs-lookup"><span data-stu-id="efe5a-266">WCF relies on HTTP request-reply correlation for two-way message exchange protocol correlation.</span></span> <span data-ttu-id="efe5a-267">Pour cette raison, l’initiateur WCF n’interrompt pas la nouvelle tentative d’un message de séquence de demande lorsque le message de séquence de demande est reconnu, mais plutôt lorsque la réponse HTTP contient un accusé de réception, un message utilisateur ou une erreur.</span><span class="sxs-lookup"><span data-stu-id="efe5a-267">Because of this, the WCF Initiator does not stop retrying a request sequence message when the request sequence message is acknowledged but rather when the HTTP response carries an acknowledgement, user message, or fault.</span></span> <span data-ttu-id="efe5a-268">Le répondeur WCF réessaye les réponses sur le tronçon de requête HTTP de la demande à laquelle la réponse est corrélée.</span><span class="sxs-lookup"><span data-stu-id="efe5a-268">The WCF Responder retries replies on the HTTP request leg of the request to which the reply is correlated.</span></span>

#### <a name="lastmessage-exchange"></a><span data-ttu-id="efe5a-269">Échange LastMessage</span><span class="sxs-lookup"><span data-stu-id="efe5a-269">LastMessage Exchange</span></span>

<span data-ttu-id="efe5a-270">L’initiateur WCF génère et transmet un dernier message vide vide sur le tronçon de requête HTTP.</span><span class="sxs-lookup"><span data-stu-id="efe5a-270">The WCF Initiator generates and transmits an empty bodied last message on the HTTP request leg.</span></span> <span data-ttu-id="efe5a-271">WCF requiert une réponse mais ignore le message de réponse réel.</span><span class="sxs-lookup"><span data-stu-id="efe5a-271">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="efe5a-272">Le répondeur WCF répond au dernier message vide de la séquence de demande avec le dernier message vide de la séquence de réponse.</span><span class="sxs-lookup"><span data-stu-id="efe5a-272">The WCF Responder replies to the request sequence’s empty-bodied last message with the reply sequence’s empty-bodied last message.</span></span>

<span data-ttu-id="efe5a-273">Si le répondeur WCF reçoit un dernier message dans lequel l’URI d’action n’est pas `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` , WCF répond avec un dernier message.</span><span class="sxs-lookup"><span data-stu-id="efe5a-273">If the WCF Responder receives a last message in which the action URI is not `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF replies with a last message.</span></span> <span data-ttu-id="efe5a-274">Dans le cas d'un protocole d'échange de messages bidirectionnel, le dernier message contient le message d'application ; dans le cas d'un protocole d'échange de messages unidirectionnel, le dernier message est vide.</span><span class="sxs-lookup"><span data-stu-id="efe5a-274">In the case of a two-way message exchange protocol, the last message carries the application message; in the case of a one-way message exchange protocol, the last message is empty.</span></span>

<span data-ttu-id="efe5a-275">Le répondeur WCF ne requiert pas d’accusé de réception pour le dernier message vide de la séquence de réponse.</span><span class="sxs-lookup"><span data-stu-id="efe5a-275">The WCF Responder does not require an acknowledgement for the reply sequence’s empty-bodied last message.</span></span>

#### <a name="terminatesequence-exchange"></a><span data-ttu-id="efe5a-276">Échange TerminateSequence</span><span class="sxs-lookup"><span data-stu-id="efe5a-276">TerminateSequence Exchange</span></span>

<span data-ttu-id="efe5a-277">Lorsque toutes les demandes ont reçu une réponse valide, l’initiateur WCF génère et transmet le message de la séquence `TerminateSequence` de demande sur le tronçon de requête http.</span><span class="sxs-lookup"><span data-stu-id="efe5a-277">When all requests have received a valid reply, the WCF Initiator generates and transmits the request sequence’s `TerminateSequence` message on the HTTP request leg.</span></span> <span data-ttu-id="efe5a-278">WCF requiert une réponse mais ignore le message de réponse réel.</span><span class="sxs-lookup"><span data-stu-id="efe5a-278">WCF requires a response but ignores the actual response message.</span></span> <span data-ttu-id="efe5a-279">Le répondeur WCF répond au message de la séquence de demande `TerminateSequence` avec le message de la séquence de réponse `TerminateSequence` .</span><span class="sxs-lookup"><span data-stu-id="efe5a-279">The WCF Responder replies to the request sequence’s `TerminateSequence` message with the reply sequence’s `TerminateSequence` message.</span></span>

<span data-ttu-id="efe5a-280">Dans une séquence d'arrêt normale, les deux messages `TerminateSequence` incluent un `SequenceAcknowledgement` complet.</span><span class="sxs-lookup"><span data-stu-id="efe5a-280">In a normal shutdown sequence, both `TerminateSequence` messages carry a full range `SequenceAcknowledgement`.</span></span>

### <a name="requestreply-addressable-initiator"></a><span data-ttu-id="efe5a-281">Initiateur demande/réponse, adressable</span><span class="sxs-lookup"><span data-stu-id="efe5a-281">Request/Reply, Addressable Initiator</span></span>

#### <a name="binding"></a><span data-ttu-id="efe5a-282">Liaison</span><span class="sxs-lookup"><span data-stu-id="efe5a-282">Binding</span></span>

<span data-ttu-id="efe5a-283">WCF fournit un modèle d’échange de messages de demande-réponse utilisant deux séquences sur un canal HTTP entrant et sortant.</span><span class="sxs-lookup"><span data-stu-id="efe5a-283">WCF provides a request-reply message exchange pattern using two sequences over an inbound and an outbound HTTP channel.</span></span> <span data-ttu-id="efe5a-284">WCF utilise les requêtes HTTP pour transmettre tous les messages.</span><span class="sxs-lookup"><span data-stu-id="efe5a-284">WCF uses the HTTP requests to transmit all messages.</span></span> <span data-ttu-id="efe5a-285">Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.</span><span class="sxs-lookup"><span data-stu-id="efe5a-285">All HTTP responses have an empty body and HTTP 202 status code.</span></span>

#### <a name="createsequence-exchange"></a><span data-ttu-id="efe5a-286">Échange CreateSequence</span><span class="sxs-lookup"><span data-stu-id="efe5a-286">CreateSequence Exchange</span></span>

<span data-ttu-id="efe5a-287">L’initiateur WCF génère un `CreateSequence` message avec une offre.</span><span class="sxs-lookup"><span data-stu-id="efe5a-287">The WCF Initiator generates a `CreateSequence` message with an offer.</span></span> <span data-ttu-id="efe5a-288">Le répondeur WCF s’assure que `CreateSequence` a une offre avant de créer une séquence.</span><span class="sxs-lookup"><span data-stu-id="efe5a-288">The WCF Responder ensures that the `CreateSequence` has an offer before creating a sequence.</span></span> <span data-ttu-id="efe5a-289">WCF envoie le `CreateSequenceResponse` sur la requête HTTP adressée à la `CreateSequence` `ReplyTo` référence de point de terminaison de.</span><span class="sxs-lookup"><span data-stu-id="efe5a-289">WCF sends the `CreateSequenceResponse` on the HTTP request addressed to the `CreateSequence`’s `ReplyTo` endpoint reference.</span></span>

#### <a name="requestreply-correlation"></a><span data-ttu-id="efe5a-290">Corrélation demande/réponse</span><span class="sxs-lookup"><span data-stu-id="efe5a-290">Request/Reply Correlation</span></span>

<span data-ttu-id="efe5a-291">L’initiateur WCF garantit que tous les messages de demande d’application portent un `MessageId` et une `ReplyTo` référence de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="efe5a-291">The WCF Initiator ensures all application request messages bear a `MessageId` and a `ReplyTo` endpoint reference.</span></span> <span data-ttu-id="efe5a-292">L’initiateur WCF applique la `CreateSequence` référence de `ReplyTo` point de terminaison du message sur chaque message de demande d’application.</span><span class="sxs-lookup"><span data-stu-id="efe5a-292">The WCF Initiator applies the `CreateSequence` message’s `ReplyTo` endpoint reference on each application request message.</span></span> <span data-ttu-id="efe5a-293">Le répondeur WCF exige que les messages de demande entrants comportent un `MessageId` et un `ReplyTo` .</span><span class="sxs-lookup"><span data-stu-id="efe5a-293">The WCF Responder requires that incoming request messages bear a `MessageId` and a `ReplyTo`.</span></span> <span data-ttu-id="efe5a-294">Le répondeur WCF s’assure que l’URI de la référence de point de terminaison de `CreateSequence` et de tous les messages de demande d’application sont identiques.</span><span class="sxs-lookup"><span data-stu-id="efe5a-294">The WCF Responder ensures that the endpoint reference’s URI of both the `CreateSequence` and all application request messages are identical.</span></span>

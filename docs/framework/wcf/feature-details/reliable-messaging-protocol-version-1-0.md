---
title: Protocole de messagerie fiable version 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: ef45df0f1cae1f20cf34d07d154baee2cad34b29
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143443"
---
# <a name="reliable-messaging-protocol-version-10"></a>Protocole de messagerie fiable version 1.0

Cette rubrique couvre les détails de l’implémentation de Windows Communication Foundation (WCF) pour le protocole WS-Reliable Messaging 2005 (version 1,0) nécessaire pour l’interopérabilité à l’aide du transport HTTP. WCF suit la spécification de la messagerie WS-Reliable avec les contraintes et les clarifications décrites dans cette rubrique. Notez que le protocole WS-ReliableMessaging version 1,0 est implémenté à partir de WinFX.

Le protocole de la messagerie WS-Reliable de février 2005 est implémenté dans WCF par le <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> .

Pour plus de simplicité, la rubrique utilise les rôles suivants :

- Initiateur : client qui initialise la création de la séquence de message WS-Reliable.

- Répondeur : service qui reçoit les demandes de l'initiateur.

Ce document utilise les préfixes et les espaces de noms répertoriés dans le tableau suivant.

|Préfixe|Espace de noms|
|------------|---------------|
|wsrm|`http://schemas.xmlsoap.org/ws/2005/02/rm`|
|netrm|`http://schemas.microsoft.com/ws/2006/05/rm`|
|s|`http://www.w3.org/2003/05/soap-envelope`|
|wsa|`http://schemas.xmlsoap.org/ws/2005/08/addressing|
|wsse|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|

## <a name="messaging"></a>Messagerie

### <a name="sequence-establishment-messages"></a>Messages d'établissement de séquence

WCF implémente `CreateSequence` les `CreateSequenceResponse` messages et pour établir une séquence de message fiable. Les contraintes suivantes s'appliquent :

- B1101 : l’initiateur WCF ne génère pas l’élément Expires facultatif dans le `CreateSequence` message ou, dans le cas où le `CreateSequence` message contient un `Offer` élément, l' `Expires` élément facultatif dans l' `Offer` élément.

- B1102 : lors de l’accès au `CreateSequence` message, WCF `Responder` envoie et reçoit les deux `Expires` éléments s’ils existent, mais n’utilise pas leurs valeurs.

La messagerie WS-Reliable introduit le mécanisme `Offer` pour établir deux séquences corrélées réciproques qui forment une session.

- R1103 : si `CreateSequence` contient un élément `Offer`, le répondeur de messagerie fiable doit soit accepter la séquence et répondre avec `CreateSequenceResponse` contenant un élément `wsrm:Accept`, formant deux séquences réciproques corrélées, soit rejeter la demande `CreateSequence`.

- R1104 : l'`SequenceAcknowledgement` et les messages d'application qui passent sur la séquence réciproque doivent être envoyés à la référence de point de terminaison `ReplyTo` de `CreateSequence`.

- R1105 : les références de point de terminaison `AcksTo` et `ReplyTo` dans `CreateSequence` doivent avoir des valeurs d'adresse qui correspondent au niveau des octets.

  Le répondeur WCF vérifie que la partie URI des `AcksTo` `ReplyTo` ERP et est identique avant de créer une séquence.

- R1106 : les références de point de terminaison `AcksTo` et `ReplyTo` dans `CreateSequence` doivent avoir le même jeu de paramètres de référence.

  WCF n’applique pas, mais suppose que les [paramètres de référence] de `AcksTo` et `ReplyTo` sur `CreateSequence` sont identiques et utilise les [paramètres de référence] de la `ReplyTo` référence de point de terminaison pour les accusés de réception et les messages de séquence réciproque.

- R1107 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme `Offer`, l'`SequenceAcknowledgement` et les messages d'application qui traversent les séquences réciproques doivent être envoyés à la référence de point de terminaison `ReplyTo` de `CreateSequence`.

- R1108 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme Offer, la propriété `[address]` de l'élément enfant `wsrm:AcksTo` de la référence de point de terminaison de l'élément `wsrm:Accept` de la `CreateSequenceResponse` doit correspondre octet par octet à l'URI de destination de `CreateSequence`.

- R1109 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme `Offer`, les messages envoyés par l'initiateur et les accusés de réception des messages envoyés par le répondeur doivent être envoyés à la même référence de point de terminaison.

  WCF utilise la messagerie WS-Reliable pour établir des sessions fiables entre l’initiateur et le répondeur. L’implémentation de la messagerie WS-Reliable de WCF fournit une session fiable pour les modèles de messagerie à sens unique, demande-réponse et duplex intégral. Le mécanisme de messagerie WS-Reliable `Offer` sur `CreateSequence` / `CreateSequenceResponse` vous permet d’établir deux séquences réciproques corrélées et fournit un protocole de session qui convient à tous les points de terminaison de message. Étant donné que WCF offre une garantie de sécurité pour une telle session, y compris une protection de bout en bout pour l’intégrité de la session, il est pratique de s’assurer que les messages destinés au même tiers arrivent à la même destination. Cela permet également la superposition des accusés de réception de séquence sur les messages d'application. Par conséquent, les contraintes R1104, R1105 et R1108 s’appliquent à WCF.

Exemple de message `CreateSequence`.

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

 Exemple de message `CreateSequenceResponse`.

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

### <a name="sequence"></a>Séquence

Voici une liste des contraintes qui s'appliquent aux séquences :

- B1201 : WCF génère et accède aux numéros de séquence qui ne sont pas plus élevés que `xs:long` la valeur inclusive maximale de 9223372036854775807.

- B1202 : WCF génère toujours un dernier message vide avec l’URI d’action de `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .

- B1203 : WCF reçoit et remet un message avec un en-tête de séquence qui contient un `LastMessage` élément tant que l’URI d’action n’a pas la valeur `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .

Exemple d'en-tête Sequence.

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

### <a name="ackrequested-header"></a>En-tête AckRequested

WCF utilise l' `AckRequested` en-tête comme un mécanisme Keep-Alive. WCF ne génère pas l' `MessageNumber` élément facultatif. Lors de la réception d’un message avec un `AckRequested` en-tête contenant l' `MessageNumber` élément, WCF ignore la `MessageNumber` valeur de l’élément, comme indiqué dans l’exemple suivant.

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a>En-tête SequenceAcknowledgement

WCF utilise un mécanisme de superposition pour les accusés de réception de séquence fournis dans WS-Reliable Messaging.

- R1401 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme `Offer`, l'en-tête `SequenceAcknowledgement` peut être inclus dans tout message d'application transmis au destinataire souhaité.

- B1402 : lorsque WCF doit générer un accusé de réception avant de recevoir des messages de séquence (par exemple, pour répondre à un `AckRequested` message), WCF génère un `SequenceAcknowledgement` en-tête qui contient la plage 0-0, comme indiqué dans l’exemple suivant.

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- B1403 : WCF ne génère pas `SequenceAcknowledgement` d’en-têtes contenant un `Nack` élément, mais prend en charge les `Nack` éléments.

### <a name="ws-reliablemessaging-faults"></a>Erreurs de la messagerie WS-Reliable

La liste suivante répertorie les contraintes qui s’appliquent à l’implémentation WCF des erreurs de messagerie WS-Reliable :

- B1501 : WCF ne génère pas d' `MessageNumberRollover` Erreurs.

- B1502 : le point de terminaison WCF peut générer `CreateSequenceRefused` des erreurs, comme décrit dans la spécification.

- B1503 : lorsque le point de terminaison de service atteint sa limite de connexion et ne peut pas traiter de nouvelles connexions, WCF génère un `CreateSequenceRefused` sous-code d’erreur supplémentaire, `netrm:ConnectionLimitReached` , comme indiqué dans l’exemple suivant.

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

### <a name="ws-addressing-faults"></a>Erreurs WS-Addressing

Étant donné que la messagerie WS-Reliable utilise WS-Addressing, l’implémentation de la messagerie WS-Reliable WCF peut générer des erreurs WS-Addressing. Cette section traite des erreurs WS-Addressing que WCF génère explicitement au niveau de la couche de messagerie WS-Reliable :

- B1601 : WCF génère l’en-tête d’adressage de message d’erreur requis lorsque l’une des conditions suivantes est remplie :

  - Un message n'a pas d'en-tête `Sequence` ni d'en-tête `Action`.

  - Un message `CreateSequence` n'a pas d'en-tête `MessageId`.

  - Un message `CreateSequence` n'a pas d'en-tête `ReplyTo`.

- B1602 : WCF génère l’action d’erreur non prise en charge en réponse à un message dont `Sequence` l’en-tête est manquant et dont `Action` l’en-tête n’est pas reconnu dans la spécification de la messagerie WS-Reliable.

- B1603 : WCF génère le point de terminaison d’erreur non disponible pour indiquer que le point de terminaison ne traite pas la séquence en fonction de l’examen des `CreateSequence` en-têtes d’adressage du message.

## <a name="protocol-composition"></a>Composition du protocole

### <a name="composition-with-ws-addressing"></a>Composition avec WS-Addressing

WCF prend en charge deux versions de WS-Addressing : WS-Addressing 2004/08 [WS-ADDR] et W3C WS-Addressing 1,0 Recommendations [WS-ADDR-CORE] et [WS-ADDR-SOAP].

Bien que la spécification de la messagerie WS-Reliable mentionne WS-Addressing 2004/08 uniquement, cela ne constitue pas une restriction en ce qui concerne la version WS-Addressing à utiliser. Voici une liste des contraintes qui s’appliquent à WCF :

- R2101 : aussi bien WS-Addressing 2004/08 que WS-Addressing 1.0 peuvent être utilisés avec la messagerie WS-Reliable.

- R2102 : une seule version de WS-Addressing doit être utilisée dans une séquence de messagerie WS-Reliable donnée ou une paire de séquences réciproques corrélées à l’aide du `wsrm:Offer` mécanisme.

### <a name="composition-with-soap"></a>Composition avec SOAP

WCF prend en charge l’utilisation de SOAP 1,1 et SOAP 1,2 avec la messagerie WS-Reliable.

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Composition avec WS-Security et WS-SecureConversation

WCF fournit une protection pour les séquences de messagerie WS-Reliable en utilisant le transport sécurisé (HTTPs), la composition avec WS-Security et la composition avec WS-Secure conversation. Voici une liste des contraintes qui s’appliquent à WCF :

- R2301 : pour protéger l’intégrité d’une séquence de messagerie WS-Reliable en plus de l’intégrité et de la confidentialité des messages individuels, WCF requiert l’utilisation de la conversation WS-Secure.

- R2302 :unesession WS-Secure Conversation doit être établie avant d'établir la ou les séquences de messagerie WS-Reliable.

- R2303 : si la durée de vie de la séquence de messagerie WS-Reliable dépasse celle de la session WS-Secure Conversation, le `SecurityContextToken` établi à l'aide de WS-Secure Conversation doit être renouvelé par le biais de la liaison WS-Secure Conversation Renewal correspondante.

- B2304 :la séquence de messagerie WS-Reliable ou une paire de séquences réciproques corrélées est toujours liée à une session WS-SecureConversation unique.

  La source WCF génère l' `wsse:SecurityTokenReference` élément dans la section d’extensibilité d’élément du `CreateSequence` message.

- R2305 : lorsqu’il est composé avec WS-Secure conversation, un `CreateSequence` message doit contenir l' `wsse:SecurityTokenReference` élément.

## <a name="ws-reliable-messaging-ws-policy-assertion"></a>Assertion WS-Policy de la messagerie WS-Reliable

WCF utilise l’assertion WS-Policy de la messagerie WS-Reliable `wsrm:RMAssertion` pour décrire les fonctionnalités des points de terminaison. Voici une liste des contraintes qui s’appliquent à WCF :

- B3001 : WCF attache l' `wsrm:RMAssertion` assertion WS-Policy à des `wsdl:binding` éléments. WCF prend en charge les deux pièces jointes aux `wsdl:binding` `wsdl:port` éléments et.

- B3002 : WCF prend en charge les propriétés facultatives suivantes de l’assertion de messagerie WS-Reliable et en assure le contrôle sur WCF `ReliableMessagingBindingElement` :

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  Voici un exemple.

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a>Extension de messagerie WS-Reliable pour le contrôle de flux

WCF utilise l’extensibilité de la messagerie WS-Reliable pour fournir un contrôle plus strict facultatif sur le déroulement du message de séquence.

Le contrôle de Flow est activé en affectant à la propriété la valeur <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> `true` . Voici une liste des contraintes qui s’appliquent à WCF :

- B4001 : lorsque le contrôle de workflow de messagerie fiable est activé, WCF génère un `netrm:BufferRemaining` élément dans l’extensibilité d’élément de l' `SequenceAcknowledgement` en-tête.

- B4002 : lorsque le contrôle de workflow de messagerie fiable est activé, WCF ne nécessite pas la présence d’un `netrm:BufferRemaining` élément dans `SequenceAcknowledgement` l’en-tête, comme illustré dans l’exemple suivant.

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

- B4003 : WCF utilise `netrm:BufferRemaining` pour indiquer le nombre de nouveaux messages que la destination de messagerie fiable peut mettre en mémoire tampon.

- B4004 : le service de messagerie fiable WCF limite le nombre de messages transmis lorsque l’application de destination de la messagerie fiable ne peut pas recevoir des messages rapidement. La destination de la messagerie fiable met en mémoire tampon les messages et la valeur de l’élément tombe à 0.

- B4005 : WCF génère `netrm:BufferRemaining` des valeurs entières comprises entre 0 et 4096 inclus, et lit les valeurs entières comprises entre 0 et `xs:int` la `maxInclusive` valeur 214748364 inclusives.

## <a name="message-exchange-patterns"></a>Modèles d’échange de messages

Cette section décrit le comportement de WCF lorsque la messagerie WS-Reliable est utilisée pour différents modèles d’échange de messages. Pour chaque modèle d'échange de messages, les deux scénarios de déploiements suivants sont considérés :

- Initiateur non adressable : l'initiateur est derrière un pare-feu ; le répondeur peut remettre des messages à celui-ci uniquement sur les réponses HTTP.

- Initiateur adressable : l'initiateur et le répondeur peuvent tous les deux recevoir des requêtes HTTP ; en d'autres termes, deux connexions HTTP réciproques peuvent être établies.

### <a name="one-way-non-addressable-initiator"></a>Initiateur unidirectionnel, non adressable

#### <a name="binding"></a>Liaison

WCF fournit un modèle d’échange de messages unidirectionnel qui utilise une séquence sur un canal HTTP. WCF utilise les requêtes HTTP pour transmettre tous les messages du RMS au RMD et la réponse HTTP pour transmettre tous les messages du RMD au RMS.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF génère un `CreateSequence` message sans offre. Le répondeur WCF garantit que le n' `CreateSequence` a pas d’offre avant de créer une séquence. Le répondeur WCF répond à la `CreateSequence` demande à l’aide d’un `CreateSequenceResponse` message.

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

L’initiateur WCF traite les accusés de réception de la réponse de tous les messages, à l’exception des `CreateSequence` messages de message et d’erreur. Le répondeur WCF génère toujours un accusé de réception autonome dans la réponse à la séquence et aux `AckRequested` messages.

#### <a name="terminatesequence-message"></a>Message TerminateSequence

WCF traite `TerminateSequence` comme une opération unidirectionnelle, ce qui signifie que la réponse http a un corps vide et un code d’état HTTP 202.

### <a name="one-way-addressable-initiator"></a>Initiateur unidirectionnel, adressable

#### <a name="binding"></a>Liaison

WCF fournit un modèle d’échange de messages unidirectionnel qui utilise une séquence sur un canal http entrant et sortant. WCF utilise les requêtes HTTP pour transmettre tous les messages. Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF génère un `CreateSequence` message sans offre. Le répondeur WCF s’assure que le `CreateSequence` n’a pas d’offre avant de créer une séquence. Le répondeur WCF transmet le `CreateSequenceResponse` message sur une requête HTTP adressée à la `ReplyTo` référence de point de terminaison.

### <a name="duplex-addressable-initiator"></a>Initiateur duplex, adressable

#### <a name="binding"></a>Liaison

WCF fournit un modèle d’échange de messages bidirectionnel entièrement asynchrone à l’aide de deux séquences sur un canal HTTP entrant et sortant. WCF utilise les requêtes HTTP pour transmettre tous les messages. Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF génère un `CreateSequence` message avec une offre. Le répondeur WCF s’assure que `CreateSequence` a une offre avant de créer une séquence. WCF envoie le `CreateSequenceResponse` sur la requête HTTP adressée à la `CreateSequence` `ReplyTo` référence de point de terminaison de.

#### <a name="sequence-lifetime"></a>Durée de vie de séquence

WCF traite les deux séquences comme une seule session duplex intégrale.

Lors de la génération d’une erreur qui provoque une séquence, WCF s’attend à ce que le point de terminaison distant cause les deux séquences. Lors de la lecture d’une erreur qui provoque une séquence, les deux séquences sont des erreurs WCF.

WCF peut fermer sa séquence sortante et continuer à traiter les messages sur sa séquence entrante. À l’inverse, WCF peut traiter la fermeture de la séquence entrante et continuer à envoyer des messages sur sa séquence sortante.

### <a name="request-reply-non-addressable-initiator"></a>Initiateur demande-réponse, non adressable

#### <a name="binding"></a>Liaison

WCF fournit un modèle d’échange de messages unidirectionnel et demande-réponse à l’aide de deux séquences sur un canal HTTP. WCF utilise les requêtes HTTP pour transmettre les messages de la séquence de demande et utilise les réponses HTTP pour transmettre les messages de la séquence de réponse.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF génère un `CreateSequence` message avec une offre. Le répondeur WCF s’assure que `CreateSequence` a une offre avant de créer une séquence. Le répondeur WCF répond à la `CreateSequence` demande à l’aide d’un `CreateSequenceResponse` message.

#### <a name="one-way-message"></a>Message unidirectionnel

Pour réussir un protocole d’échange de messages unidirectionnel, l’initiateur WCF transmet un message de séquence de demande sur la requête HTTP et reçoit un `SequenceAcknowledgement` message autonome sur la réponse http. `SequenceAcknowledgement` doit accepter le message transmis.

Le répondeur WCF peut répondre à la demande avec un accusé de réception, une erreur ou une réponse avec un corps vide et un code d’état HTTP 202.

#### <a name="two-way-messages"></a>Messages bidirectionnels

Pour réussir un protocole d’échange de messages bidirectionnel, l’initiateur WCF transmet un message de séquence de demande sur la requête HTTP et reçoit un message de séquence de réponse sur la réponse HTTP. La réponse doit contenir un `SequenceAcknowledgement` qui accuse réception du message de séquence de demande transmis.

Le répondeur WCF peut répondre à la demande avec une réponse d’application, une erreur ou une réponse avec un corps vide et un code d’état HTTP 202.

En raison de la présence de messages unidirectionnels et du délai d'attente des réponses d'application, le numéro de séquence du message de séquence de demande et le numéro de séquence du message de réponse n'ont aucune corrélation.

#### <a name="retrying-replies"></a>Nouvelles tentatives de réponses

WCF s’appuie sur la corrélation de requête-réponse HTTP pour la corrélation de protocole d’échange de messages bidirectionnels. Pour cette raison, l’initiateur WCF n’interrompt pas la nouvelle tentative d’un message de séquence de demande lorsque le message de séquence de demande est reconnu, mais plutôt lorsque la réponse HTTP contient un accusé de réception, un message utilisateur ou une erreur. Le répondeur WCF réessaye les réponses sur le tronçon de requête HTTP de la demande à laquelle la réponse est corrélée.

#### <a name="lastmessage-exchange"></a>Échange LastMessage

L’initiateur WCF génère et transmet un dernier message vide vide sur le tronçon de requête HTTP. WCF requiert une réponse mais ignore le message de réponse réel. Le répondeur WCF répond au dernier message vide de la séquence de demande avec le dernier message vide de la séquence de réponse.

Si le répondeur WCF reçoit un dernier message dans lequel l’URI d’action n’est pas `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` , WCF répond avec un dernier message. Dans le cas d'un protocole d'échange de messages bidirectionnel, le dernier message contient le message d'application ; dans le cas d'un protocole d'échange de messages unidirectionnel, le dernier message est vide.

Le répondeur WCF ne requiert pas d’accusé de réception pour le dernier message vide de la séquence de réponse.

#### <a name="terminatesequence-exchange"></a>Échange TerminateSequence

Lorsque toutes les demandes ont reçu une réponse valide, l’initiateur WCF génère et transmet le message de la séquence `TerminateSequence` de demande sur le tronçon de requête http. WCF requiert une réponse mais ignore le message de réponse réel. Le répondeur WCF répond au message de la séquence de demande `TerminateSequence` avec le message de la séquence de réponse `TerminateSequence` .

Dans une séquence d'arrêt normale, les deux messages `TerminateSequence` incluent un `SequenceAcknowledgement` complet.

### <a name="requestreply-addressable-initiator"></a>Initiateur demande/réponse, adressable

#### <a name="binding"></a>Liaison

WCF fournit un modèle d’échange de messages de demande-réponse utilisant deux séquences sur un canal HTTP entrant et sortant. WCF utilise les requêtes HTTP pour transmettre tous les messages. Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF génère un `CreateSequence` message avec une offre. Le répondeur WCF s’assure que `CreateSequence` a une offre avant de créer une séquence. WCF envoie le `CreateSequenceResponse` sur la requête HTTP adressée à la `CreateSequence` `ReplyTo` référence de point de terminaison de.

#### <a name="requestreply-correlation"></a>Corrélation demande/réponse

L’initiateur WCF garantit que tous les messages de demande d’application portent un `MessageId` et une `ReplyTo` référence de point de terminaison. L’initiateur WCF applique la `CreateSequence` référence de `ReplyTo` point de terminaison du message sur chaque message de demande d’application. Le répondeur WCF exige que les messages de demande entrants comportent un `MessageId` et un `ReplyTo` . Le répondeur WCF s’assure que l’URI de la référence de point de terminaison de `CreateSequence` et de tous les messages de demande d’application sont identiques.

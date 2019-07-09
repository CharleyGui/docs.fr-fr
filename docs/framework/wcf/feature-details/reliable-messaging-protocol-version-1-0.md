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
# <a name="reliable-messaging-protocol-version-10"></a>Protocole de messagerie fiable version 1.0

Cette rubrique traite des détails d’implémentation de Windows Communication Foundation (WCF) pour WS-Reliable Messaging protocol de février 2005 (version 1.0) nécessaire pour l’interopérabilité utilisant le transport HTTP. WCF suit la spécification WS-Reliable Messaging avec les contraintes et les éclaircissements présentés dans cette rubrique. Notez que le protocole de la version 1.0 WS-ReliableMessaging est implémenté en commençant par le WinFX.

La messagerie WS-Reliable février 2005 protocole est implémenté dans WCF par le <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.

Pour plus de simplicité, la rubrique utilise les rôles suivants :

- Initiateur : client qui initialise la création de la séquence de message WS-Reliable.

- Répondeur : service qui reçoit les demandes de l'initiateur.

Ce document utilise les préfixes et les espaces de noms répertoriés dans le tableau suivant.

|Préfixe|Espace de noms|
|------------|---------------|
|wsrm|http://schemas.xmlsoap.org/ws/2005/02/rm|
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|
|s|http://www.w3.org/2003/05/soap-envelope|
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|

## <a name="messaging"></a>Messagerie

### <a name="sequence-establishment-messages"></a>Messages d'établissement de séquence

WCF implémente `CreateSequence` et `CreateSequenceResponse` messages pour établir une séquence de message fiable. Les contraintes suivantes s'appliquent :

- B1101 : L’initiateur WCF ne génère pas de l’élément Expires facultatif dans le `CreateSequence` message ou, dans le cas lorsque le `CreateSequence` message contient un `Offer` élément, le paramètre facultatif `Expires` élément dans le `Offer` élément.

- B1102 : Lorsque vous accédez à la `CreateSequence` du message, WCF`Responder` envoie et reçoit les deux `Expires` éléments s’ils existent, mais n’utilisent pas leurs valeurs.

La messagerie WS-Reliable introduit le mécanisme `Offer` pour établir deux séquences corrélées réciproques qui forment une session.

- R1103 : Si `CreateSequence` contient un `Offer` élément, le répondeur de messagerie fiable doit soit accepter la séquence et répondre avec `CreateSequenceResponse` qui contient un `wsrm:Accept` élément, formant deux corrélées séquences réciproques ou rejeter le `CreateSequence`demande.

- R1104 : l'`SequenceAcknowledgement` et les messages d'application qui passent sur la séquence réciproque doivent être envoyés à la référence de point de terminaison `ReplyTo` de `CreateSequence`.

- R1105 : les références de point de terminaison `AcksTo` et `ReplyTo` dans `CreateSequence` doivent avoir des valeurs d'adresse qui correspondent au niveau des octets.

  Le répondeur WCF vérifie que la portion d’URI de la `AcksTo` et `ReplyTo` EPR est identiques avant de créer une séquence.

- R1106 : les références de point de terminaison `AcksTo` et `ReplyTo` dans `CreateSequence` doivent avoir le même jeu de paramètres de référence.

  WCF n’applique pas, mais part du principe que [paramètres de référence] de `AcksTo` et `ReplyTo` sur `CreateSequence` sont identiques et utilise [paramètres de référence] à partir de `ReplyTo` référence de point de terminaison pour les accusés de réception et les messages de séquence réciproque.

- R1107 : Lorsque deux séquences réciproques sont établies à l’aide de la `Offer` mécanisme, `SequenceAcknowledgement` et messages d’application traversent les séquences réciproques doivent être envoyés à la `ReplyTo` référence de point de terminaison de la `CreateSequence`.

- R1108 : Lorsque deux séquences réciproques sont établies à l’aide du mécanisme Offer, la `[address]` propriété de la `wsrm:AcksTo` élément enfant de référence de point de terminaison de la `wsrm:Accept` élément de la `CreateSequenceResponse` doit correspondre octet par octet l’URI de destination de la `CreateSequence`.

- R1109 : Lorsque deux séquences réciproques sont établies à l’aide de la `Offer` mécanisme, les messages envoyés par l’initiateur et les accusés de réception des messages par le répondeur doivent être envoyés à la même référence de point de terminaison.

  WCF utilise la messagerie WS-Reliable pour établir des sessions fiables entre l’initiateur et le répondeur. Implémentation de la messagerie WS-Reliable de WCF fournit une session fiable pour intégral demande-réponse et unidirectionnels, modèles de messagerie en duplex. La messagerie WS-Reliable `Offer` mécanisme sur `CreateSequence` / `CreateSequenceResponse` vous permet d’établir deux séquences réciproques corrélées et fournit un protocole de session qui convient à tous les points de terminaison de message. Étant donné que WCF fournit une garantie de sécurité pour une telle session, y compris la protection de bout en bout pour l’intégrité de session, il est pratique de s’assurer de messages destinés au même correspondant arrivent à la même destination. Cela permet également la superposition des accusés de réception de séquence sur les messages d'application. Par conséquent, les contraintes R1104, R1105 et R1108 s’appliquent à WCF.

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

- B1201:WCF génère et ne dépassant pas de numéros de séquence d’accès `xs:long`de valeur maximale, 9223372036854775807.

- B1202:WCF génère toujours un message dernier vide avec l’URI d’action de `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.

- B1203 : WCF reçoit et remet un message avec un en-tête de séquence qui contient un `LastMessage` élément tant que l’URI action n’est pas `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.

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

WCF utilise `AckRequested` en-tête comme un mécanisme keep-alive. WCF ne génère pas le paramètre facultatif `MessageNumber` élément. Lors de la réception d’un message avec un `AckRequested` en-tête qui contient le `MessageNumber` élément, WCF ignore le `MessageNumber` valeur de l’élément, comme indiqué dans l’exemple suivant.

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a>En-tête SequenceAcknowledgement

WCF utilise le mécanisme de superposition des accusés de réception de séquence fournis dans la messagerie WS-Reliable.

- R1401 : Lorsque deux séquences réciproques sont établies à l’aide de la `Offer` mécanisme, le `SequenceAcknowledgement` en-tête peut être inclus dans n’importe quel message d’application transmis au destinataire prévu.

- B1402 : Lorsque WCF doit générer un accusé de réception avant de recevoir un message de séquence (par exemple, pour satisfaire un `AckRequested` message), WCF génère un `SequenceAcknowledgement` en-tête qui contient la plage 0-0, comme indiqué dans l’exemple suivant.

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- B1403 : WCF ne génère pas `SequenceAcknowledgement` en-têtes qui contiennent un `Nack` élément mais prend en charge `Nack` éléments.

### <a name="ws-reliablemessaging-faults"></a>Erreurs de la messagerie WS-Reliable

Voici une liste de contraintes qui s’appliquent à l’implémentation de WCF des erreurs WS-Reliable Messaging :

- B1501 : WCF ne génère pas `MessageNumberRollover` erreurs.

- Point de terminaison B1502:WCF peut générer `CreateSequenceRefused` comme décrit dans la spécification des erreurs.

- B1503:when le point de terminaison de service atteint sa limite de connexion et ne peut pas traiter de nouvelles connexions, WCF génère un autre `CreateSequenceRefused` sous-code, d’erreur `netrm:ConnectionLimitReached`, comme illustré dans l’exemple suivant.

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

Étant donné que la messagerie WS-Reliable utilise WS-Addressing, implémentation de la messagerie WS-Reliable WCF peut générer des erreurs WS-Addressing. Cette section décrit les erreurs WS-Addressing, WCF génère explicitement au niveau de la couche de messagerie WS-Reliable :

- B1601:WCF génère l’erreur Message Addressing Header Required lorsqu’une des opérations suivantes est vraie :

  - Un message n'a pas d'en-tête `Sequence` ni d'en-tête `Action`.

  - Un message `CreateSequence` n'a pas d'en-tête `MessageId`.

  - Un message `CreateSequence` n'a pas d'en-tête `ReplyTo`.

- B1602:WCF génère l’erreur pas pris en charge par Action en réponse à un message qui manque un `Sequence` en-tête et a une `Action` en-tête n’est pas reconnue dans la spécification WS-Reliable Messaging.

- B1603:WCF génère l’erreur Endpoint Unavailable pour indiquer que le point de terminaison ne traite pas de la séquence basée sur l’examen de la `CreateSequence` en-têtes d’adressage du message.

## <a name="protocol-composition"></a>Composition du protocole

### <a name="composition-with-ws-addressing"></a>Composition avec WS-Addressing

WCF prend en charge deux versions de WS-Addressing : WS-Addressing 2004/08 [WS-ADDR] et W3C WS-Addressing 1.0 recommandations [WS-ADDR-CORE] et [WS-ADDR-SOAP].

Bien que la spécification de la messagerie WS-Reliable mentionne WS-Addressing 2004/08 uniquement, cela ne constitue pas une restriction en ce qui concerne la version WS-Addressing à utiliser. Voici une liste de contraintes qui s’appliquent à WCF :

- R2101 : les deux WS-Addressing 2004/08 et WS-Addressing 1.0 peuvent être utilisé avec la messagerie WS-Reliable.

- R2102:A une seule version de WS-Addressing doit être utilisée tout au long d’une séquence de messagerie WS-Reliable donnée ou une paire de séquences réciproques corrélées à l’aide de la `wsrm:Offer` mécanisme.

### <a name="composition-with-soap"></a>Composition avec SOAP

WCF prend en charge l’utilisation de SOAP 1.1 et SOAP 1.2 avec WS-Reliable Messaging.

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Composition avec WS-Security et WS-SecureConversation

WCF fournit une protection pour les séquences WS-Reliable Messaging à l’aide de sécurisé de Transport (HTTPS), de composition avec WS-Security et de composition avec WS-Secure Conversation. Voici une liste de contraintes qui s’appliquent à WCF :

- R2301 : pour protéger l’intégrité d’une séquence de messagerie WS-Reliable en plus de l’intégrité et la confidentialité des messages individuels, WCF requiert que WS-Secure Conversation doit être utilisée.

- R2302:AWS-session Secure Conversation doit être établie avant l’établissement ou les séquences de messagerie WS-Reliable.

- R2303 : Si la durée de vie séquence WS-Reliable Messaging dépasse WS-Secure Conversation durée de vie de session, le `SecurityContextToken` établi à l’aide de WS-Secure Conversation doit être renouvelée à l’aide de la liaison WS-Secure Conversation Renewal correspondante.

- B2304:ws-séquence de messagerie fiable ou une paire de séquences réciproques corrélées est toujours liée à une seule session WS-SecureConversation.

  La source WCF génère le `wsse:SecurityTokenReference` élément dans la section d’extensibilité d’élément le `CreateSequence` message.

- R2305:when composé avec WS-Secure Conversation, un `CreateSequence` message doit contenir le `wsse:SecurityTokenReference` élément.

## <a name="ws-reliable-messaging-ws-policy-assertion"></a>Assertion WS-Policy de la messagerie WS-Reliable

WCF utilise l’Assertion WS-Policy de la messagerie WS-Reliable `wsrm:RMAssertion` pour décrire les capacités de points de terminaison. Voici une liste de contraintes qui s’appliquent à WCF :

- B3001 : WCF attache `wsrm:RMAssertion` WS-Policy Assertion aux `wsdl:binding` éléments. WCF prend en charge des pièces jointes aux `wsdl:binding` et `wsdl:port` éléments.

- B3002 : WCF prend en charge les propriétés facultatives suivantes d’assertion WS-Reliable Messaging et assure leur contrôle sur WCF`ReliableMessagingBindingElement`:

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

WCF utilise extensibilité de la messagerie WS-Reliable pour renforcer le contrôle facultatif sur le flux de message de séquence.

Contrôle de flux est activé en définissant le <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> propriété `true`. Voici une liste de contraintes qui s’appliquent à WCF :

- B4001 : Lorsque le contrôle de flux de messagerie fiable est activé, WCF génère un `netrm:BufferRemaining` élément dans l’élément d’extensibilité de la `SequenceAcknowledgement` en-tête.

- B4002 : Lorsque le contrôle de flux de messagerie fiable est activé, WCF ne nécessite pas un `netrm:BufferRemaining` élément soit présent dans `SequenceAcknowledgement` en-tête, comme indiqué dans l’exemple suivant.

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

- B4003 : WCF utilise `netrm:BufferRemaining` pour indiquer combien de nouveaux messages la Destination de messagerie fiable peut mettre en mémoire tampon.

- B4004 : le Service de messagerie fiable WCF limite le nombre de messages transmis lorsque l’application de destination de messagerie fiable ne peut pas recevoir les messages rapidement. La destination de la messagerie fiable met en mémoire tampon les messages et la valeur de l’élément tombe à 0.

- B4005 : WCF génère `netrm:BufferRemaining` entier des valeurs comprises entre 0 et inclusif de 4096 et lit les valeurs de nombre entier compris entre 0 et `xs:int`de `maxInclusive` valeur 214748364 inclusif.

## <a name="message-exchange-patterns"></a>Modèles d’échange de messages

Cette section décrit le comportement de WCF lors de la messagerie WS-Reliable est utilisée pour différents modèles d’échange de Message. Pour chaque modèle d'échange de messages, les deux scénarios de déploiements suivants sont considérés :

- Initiateur non adressable : L’initiateur est derrière un pare-feu ; Répondeur peut remettre des messages à l’initiateur uniquement sur les réponses HTTP.

- Initiateur adressable : Initiateur et le répondeur peuvent recevoir des requêtes HTTP ; en d’autres termes, les deux connexions HTTP réciproques peuvent être établies.

### <a name="one-way-non-addressable-initiator"></a>Initiateur unidirectionnel, non adressable

#### <a name="binding"></a>Liaison

WCF fournit un modèle d’échange de messages unidirectionnel à l’aide d’une séquence sur un canal HTTP. WCF utilise les requêtes HTTP pour transmettre tous les messages à partir du RMS au RMD et la réponse HTTP pour transmettre les messages du RMD au RMS.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF génère un `CreateSequence` message sans offre. Le répondeur de WCF garantit la `CreateSequence` n’a aucune offre avant de créer une séquence. Le répondeur WCF répond à la `CreateSequence` demande avec un `CreateSequenceResponse` message.

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

L’initiateur WCF traite les accusés de réception sur la réponse de tous les messages sauf le `CreateSequence` message et les messages d’erreur. Le répondeur WCF génère toujours un accusé de réception autonome dans la réponse à ces deux séquence et `AckRequested` messages.

#### <a name="terminatesequence-message"></a>Message TerminateSequence

WCF traite `TerminateSequence` comme une opération unidirectionnelle, ce qui signifie que la réponse HTTP a un corps vide et le code d’état HTTP 202.

### <a name="one-way-addressable-initiator"></a>Initiateur unidirectionnel, adressable

#### <a name="binding"></a>Liaison

WCF fournit un modèle d’échange de messages unidirectionnel à l’aide d’une séquence sur un trafic entrant et un canal Http sortant. WCF utilise les requêtes HTTP pour transmettre tous les messages. Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF génère un `CreateSequence` message sans offre. Le répondeur de WCF garantit que le `CreateSequence` n’a aucune offre avant de créer une séquence. Le répondeur de WCF transmet le `CreateSequenceResponse` message sur une requête HTTP adressée avec la `ReplyTo` référence de point de terminaison.

### <a name="duplex-addressable-initiator"></a>Initiateur duplex, adressable

#### <a name="binding"></a>Liaison

WCF fournit un modèle d’échange de messages bidirectionnel entièrement asynchrone à l’aide de deux séquences sur un trafic entrant et un canal HTTP sortant. WCF utilise les requêtes HTTP pour transmettre tous les messages. Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF génère un `CreateSequence` message avec une offre. Le répondeur de WCF garantit que le `CreateSequence` a une offre avant de créer une séquence. WCF envoie le `CreateSequenceResponse` sur la requête HTTP adressée à la `CreateSequence`de `ReplyTo` référence de point de terminaison.

#### <a name="sequence-lifetime"></a>Durée de vie de séquence

WCF traite les deux séquences comme une session duplex complète.

Lors de la génération d’une erreur qui fait échouer une séquence, WCF attend le point de terminaison distant d’erreur les deux séquences. À la lecture d’une erreur qui fait échouer une séquence, WCF provoque des erreurs les deux séquences.

WCF peut fermer sa séquence sortante et continuer à traiter les messages sur sa séquence entrante. À l’inverse, WCF peut traiter la fermeture de la séquence entrante et continuer à envoyer des messages sur sa séquence sortante.

### <a name="request-reply-non-addressable-initiator"></a>Initiateur demande-réponse, non adressable

#### <a name="binding"></a>Liaison

WCF fournit un unidirectionnel et modèle d’échange de message demande-réponse à l’aide de deux séquences sur un canal HTTP. WCF utilise les requêtes HTTP pour transmettre les messages de séquence de demande et utilise les réponses HTTP pour transmettre des messages de la séquence de réponse.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF génère un `CreateSequence` message avec une offre. Le répondeur de WCF garantit que le `CreateSequence` a une offre avant de créer une séquence. Le répondeur WCF répond à la `CreateSequence` demande avec un `CreateSequenceResponse` message.

#### <a name="one-way-message"></a>Message unidirectionnel

Pour terminer avec succès un protocole d’échange de messages unidirectionnel, l’initiateur de WCF transmet un message de séquence de demande sur la requête HTTP et reçoit un autonome `SequenceAcknowledgement` message sur la réponse HTTP. `SequenceAcknowledgement` doit accepter le message transmis.

Le répondeur WCF peut répondre à la demande avec un accusé de réception, une erreur ou une réponse avec un corps vide et le code d’état HTTP 202.

#### <a name="two-way-messages"></a>Messages bidirectionnels

Pour terminer avec succès un protocole d’échange de messages bidirectionnel, l’initiateur de WCF transmet un message de séquence de demande sur la requête HTTP et reçoit un message de séquence de réponse sur la réponse HTTP. La réponse doit contenir un `SequenceAcknowledgement` qui accuse réception du message de séquence de demande transmis.

Le répondeur WCF peut répondre à la demande avec une réponse d’application, une erreur ou une réponse avec un corps vide et le code d’état HTTP 202.

En raison de la présence de messages unidirectionnels et du délai d'attente des réponses d'application, le numéro de séquence du message de séquence de demande et le numéro de séquence du message de réponse n'ont aucune corrélation.

#### <a name="retrying-replies"></a>Nouvelles tentatives de réponses

WCF s’appuie sur une corrélation demande-réponse HTTP pour la corrélation protocole d’échange de messages bidirectionnel. Pour cette raison, l’initiateur de WCF n’arrête pas une nouvelle tentative d’un message de séquence de demande lorsque le message de séquence de demande est accepté, mais lors de la réponse HTTP contient un accusé de réception, un message de l’utilisateur ou une erreur. Le répondeur WCF réessaie des réponses sur le tronçon HTTP de la demande à laquelle la réponse est corrélée.

#### <a name="lastmessage-exchange"></a>Échange LastMessage

L’initiateur WCF génère et transmet un dernier message vide sur le tronçon de demande HTTP. WCF requiert une réponse mais ignore le message de réponse réelle. Le répondeur WCF répond à dernier message vide de la séquence de demande avec vide dernier message la séquence de réponse.

Si le répondeur WCF reçoit un dernier message dans lequel l’URI action n’est pas `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, les réponses WCF avec un dernier message. Dans le cas d'un protocole d'échange de messages bidirectionnel, le dernier message contient le message d'application ; dans le cas d'un protocole d'échange de messages unidirectionnel, le dernier message est vide.

Le répondeur WCF ne nécessite pas d’accusé de réception pour le dernier message de la séquence de réponse vide.

#### <a name="terminatesequence-exchange"></a>Échange TerminateSequence

Lorsque toutes les demandes ont reçu une réponse valide, l’initiateur WCF génère et transmet la séquence de demande `TerminateSequence` message sur le tronçon de demande HTTP. WCF requiert une réponse mais ignore le message de réponse réelle. Le répondeur WCF répond à la séquence de demande `TerminateSequence` message avec la séquence de réponse `TerminateSequence` message.

Dans une séquence d'arrêt normale, les deux messages `TerminateSequence` incluent un `SequenceAcknowledgement` complet.

### <a name="requestreply-addressable-initiator"></a>Initiateur demande/réponse, adressable

#### <a name="binding"></a>Liaison

WCF fournit un modèle d’échange de message demande-réponse à l’aide de deux séquences sur un trafic entrant et un canal HTTP sortant. WCF utilise les requêtes HTTP pour transmettre tous les messages. Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF génère un `CreateSequence` message avec une offre. Le répondeur de WCF garantit que le `CreateSequence` a une offre avant de créer une séquence. WCF envoie le `CreateSequenceResponse` sur la requête HTTP adressée à la `CreateSequence`de `ReplyTo` référence de point de terminaison.

#### <a name="requestreply-correlation"></a>Corrélation demande/réponse

L’initiateur de WCF garantit que tous les ours de messages de demande application un `MessageId` et un `ReplyTo` référence de point de terminaison. L’initiateur de WCF s’applique le `CreateSequence` du message `ReplyTo` référence de point de terminaison sur chaque message de demande d’application. Le répondeur WCF requiert que demande entrante messages portent un `MessageId` et un `ReplyTo`. Le répondeur de WCF garantit que les URI de la référence de point de terminaison des deux le `CreateSequence` et tous les messages de demande d’application sont identiques.

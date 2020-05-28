---
title: Protocole de messagerie fiable version 1,1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: ad0a77842c10965749eab4e76bb123938e07e9d5
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144719"
---
# <a name="reliable-messaging-protocol-version-11"></a>Protocole de messagerie fiable version 1,1

Cette rubrique couvre les détails de l’implémentation de Windows Communication Foundation (WCF) pour le protocole WS-ReliableMessaging 2007 (version 1,1) nécessaire à l’interopérabilité à l’aide du transport HTTP. WCF suit la spécification WS-ReliableMessaging avec les contraintes et les clarifications expliquées dans cette rubrique. Notez que le protocole WS-ReliableMessaging version 1,1 est implémenté à partir de .NET Framework 3,5.

Le protocole WS-ReliableMessaging de février 2007 est implémenté dans WCF par le <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> .

Pour plus de simplicité, la rubrique utilise les rôles suivants :

- Initiateur : client qui initialise la création de séquence de message WS-Reliable .

- Répondeur : service qui reçoit les demandes de l'initiateur.

 Ce document utilise les préfixes et les espaces de noms répertoriés dans le tableau suivant.

|Préfixe|Espace de noms|
|-|-|
|wsrm|`http://docs.oasis-open.org/ws-rx/wsrm/200702`|
|netrm|`http://schemas.microsoft.com/ws/2006/05/rm`|
|s|`http://www.w3.org/2003/05/soap-envelope`|
|wsa|`http://schemas.xmlsoap.org/ws/2005/08/addressing`|
|wsse|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|
|wsrmp|`http://docs.oasis-open.org/ws-rx/wsrmp/200702`|
|netrmp|`http://schemas.microsoft.com/ws-rx/wsrmp/200702`|
|wsp|(WS-Policy 1.2 ou WS-Policy 1.5)|

## <a name="messaging"></a>Messagerie

### <a name="sequence-creation"></a>Création de la séquence

WCF implémente `CreateSequence` les `CreateSequenceResponse` messages et pour établir une séquence de messagerie fiable. Les contraintes suivantes s'appliquent :

- B1101 : l’initiateur WCF utilise la même référence de point de terminaison que le `CreateSequence` du message `ReplyTo` , `AcksTo` et `Offer/Endpoint` .

- R1102 : les références de point de terminaison `AcksTo`, `ReplyTo` et `Offer/Endpoint` dans le message `CreateSequence` doivent avoir des valeurs d'adresse avec des représentations sous forme de chaîne identiques qui correspondent à l'octet.

  - Le répondeur WCF vérifie que la partie URI des références de `AcksTo` `ReplyTo` point de `Endpoint` terminaison et de point de terminaison est identique avant de créer une séquence.

- R1103 : les références de point de terminaison `AcksTo`, `ReplyTo` et `Offer/Endpoint` dans le message `CreateSequence` doivent avoir le même jeu de paramètres de référence.

  - WCF n’applique pas, mais suppose que les paramètres de référence du `AcksTo` `ReplyTo` et des `Offer/Endpoint` références de point de terminaison sur `CreateSequence` sont identiques et utilise des paramètres de référence à partir de la `ReplyTo` référence de point de terminaison pour les accusés de réception et les messages de séquence réciproque.

- B1104 : l’initiateur WCF ne génère pas l' `Expires` élément ou facultatif `Offer/Expires` dans le `CreateSequence` message.

- B1105 : lors de l’accès au `CreateSequence` message, le répondeur WCF utilise la `Expires` valeur de l' `CreateSequence` élément comme `Expires` valeur dans l' `CreateSequenceResponse` élément. Dans le cas contraire, le répondeur WCF lit et ignore les `Expires` `Offer/Expires` valeurs et.

- B1106 : lors de l’accès au `CreateSequenceResponse` message, l’initiateur WCF lit la `Expires` valeur facultative, mais ne l’utilise pas.

- B1107 : l’initiateur et le répondeur WCF génèrent toujours l' `IncompleteSequenceBehavior` élément facultatif dans les `CreateSequence/Offer` `CreateSequenceResponse` éléments et.

- B1108 : WCF utilise uniquement les `DiscardFollowingFirstGap` `NoDiscard` valeurs et dans l' `IncompleteSequenceBehavior` élément.

  - WS-ReliableMessaging utilise le mécanisme `Offer` pour établir deux séquences corrélées réciproques qui forment une session.

- B1109 : si `CreateSequence` contient un `Offer` élément, le répondeur WCF rejette la séquence proposée en répondant avec un `CreateSequenceResponse` sans `Accept` élément.

- B1110 : si un répondeur de messagerie fiable rejette la séquence proposée, l’initiateur WCF signale la séquence récemment établie.

- B1111 : si `CreateSequence` ne contient pas d' `Offer` élément, le répondeur WCF bidirectionnel rejette la séquence proposée en répondant à une `CreateSequenceRefused` erreur.

- R1112 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme `Offer`, la propriété `[address]` de la référence du point de terminaison `CreateSequenceResponse/Accept/AcksTo` doit correspondre à l'URI de destination du message `CreateSequence` octet par octet.

- R1113 : lorsque deux séquences réciproques sont établies à l'aide du mécanisme `Offer`, tous les messages sur les deux séquences circulant de l'initiateur au répondeur doivent être envoyés à la même référence de point de terminaison.

WCF utilise WS-ReliableMessaging pour établir des sessions fiables entre l’initiateur et le répondeur. L’implémentation WS-ReliableMessaging WCF fournit une session fiable pour les modèles de messagerie à sens unique, demande-réponse et duplex intégral. Le mécanisme WS-ReliableMessaging `Offer` sur `CreateSequence` et `CreateSequenceResponse` vous permet d'établir deux séquences réciproques corrélées et fournit un protocole de session qui convient à tous les points de terminaison de message. Étant donné que WCF offre une garantie de sécurité pour une telle session, y compris une protection de bout en bout pour l’intégrité de la session, il est pratique de s’assurer que les messages destinés au même tiers arrivent à la même destination. Cela autorise également la « superposition » des accusés de réception de séquence sur les messages d'application. Par conséquent, les contraintes R1102, R1112 et R1113 s’appliquent à WCF.

Exemple de message `CreateSequence`.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:MessageID>
    <wsa:ReplyTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
        <wsa:Address>http://Business456.com/clientA</wsa:Address>
      </wsrm:AcksTo>
      <wsrm:Offer>
        <wsrm:Identifier>urn:uuid:066b4730-fc82-458a-a5c1-210be4fb4e4e</wsrm:Identifier>
        <wsrm:Endpoint>
          <wsa:Address>http://Business456.com/clientA</wsa:Address>
        </wsrm:Endpoint>
        <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      </wsrm:Offer>
    </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

Exemple de message `CreateSequenceResponse`.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>
      <wsrm:Accept>
        <wsrm:AcksTo>
          <wsa:Address>http://BusinessABC.com/serviceA</wsa:Address>
        </wsrm:AcksTo>
      </wsrm:Accept>
    </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="closing-a-sequence"></a>Fermeture d'une séquence

WCF utilise les `CloseSequence` `CloseSequenceResponse` messages et pour un arrêt initié par la source de messagerie fiable. La destination de messagerie fiable WCF ne lance pas l’arrêt et la source de messagerie fiable WCF ne prend pas en charge un arrêt initié par la destination de la messagerie fiable. Les contraintes suivantes s'appliquent :

- B1201 : la source de messagerie fiable WCF envoie toujours un `CloseSequence` message pour arrêter la séquence.

- B1202 : la source de la messagerie fiable attend l'accusé de réception de l'ensemble complet des messages de séquence avant d'envoyer le message `CloseSequence`.

- B1203 : la source de messagerie fiable inclut toujours l'élément `LastMsgNumber` facultatif sauf si la séquence ne contient pas de messages.

- R1204 : la destination de messagerie fiable ne doit pas initier l'arrêt en envoyant un message `CloseSequence`.

- B1205 : lors de la réception d’un `CloseSequence` message, la source de messagerie fiable WCF considère la séquence comme incomplète et envoie une erreur.

 Exemple de message `CloseSequence`.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
    </wsrm:CloseSequence>
  </s:Body>
</s:Envelope>
```

Exemple de `CloseSequenceResponse` message :

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:CloseSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:CloseSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence-termination"></a>Séquence d'arrêt

WCF utilise principalement le protocole de transfert à la `TerminateSequence/TerminateSequenceResponse` fin du `CloseSequence/CloseSequenceResponse` protocole de transfert. La destination de messagerie fiable WCF ne lance pas l’arrêt et la source de messagerie fiable ne prend pas en charge l’arrêt d’une messagerie fiable. Les contraintes suivantes s'appliquent :

- B1301 : l’initiateur WCF envoie uniquement le `TerminateSequence` message une fois l’exécution de la `CloseSequence/CloseSequenceResponse` liaison terminée.

- R1302 : WCF valide le fait que l' `LastMsgNumber` élément soit cohérent sur tous les `CloseSequence` `TerminateSequence` messages et pour une séquence donnée. Cela signifie que `LastMsgNumber` est soit absent sur tous les messages `CloseSequence` et `TerminateSequence`, soit présent et identique sur tous les messages `CloseSequence` et `TerminateSequence`.

- B1303 : à la réception d'un message `TerminateSequence` après la négociation de sécurité `CloseSequence/CloseSequenceResponse`, la destination de messagerie fiable répond avec un message `TerminateSequenceResponse`. Étant donné que la source de messagerie fiable a l'accusé de réception final avant d'envoyer le message `TerminateSequence`, la destination de messagerie fiable sait sans doute que la séquence se termine, et libère immédiatement les ressources.

- B1304 : lors de la réception d’un `TerminateSequence` message avant le `CloseSequence/CloseSequenceResponse` protocole de transfert, la destination de messagerie fiable WCF répond avec un `TerminateSequenceResponse` message. Si la destination de messagerie fiable détermine que la séquence ne contient aucune incohérence, elle attend l'heure spécifiée par la destination d'une application avant de libérer des ressources afin de permettre au client de recevoir l'accusé de réception final. Sinon, la destination de messagerie fiable libère immédiatement des ressources et indique à la destination d'application que la séquence se termine en déclenchant l'événement `Faulted`.

Exemple de message `TerminateSequence`.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</wsa:Action>
    <wsa:MessageID>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:MessageID>
    <wsa:ReplyTo>
      <wsa:Address>http://Business456.com/clientA</wsa:Address>
    </wsa:ReplyTo>
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequence>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>
      </wsrm:TerminateSequence>
  </s:Body>
</s:Envelope>
```

Exemple de `TerminateSequenceResponse` message :

```xml
<s:Envelope>
  <s:Header>
    <wsrm:SequenceAcknowledgement>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>
      <wsrm:Final></wsrm:Final>
      <netrm:BufferRemaining>8</netrm:BufferRemaining>
    </wsrm:SequenceAcknowledgement>
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</wsa:Action>
    <wsa:RelatesTo>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:RelatesTo>
    <wsa:To s:mustUnderstand="1">://Business456.com/clientA</wsa:To>
  </s:Header>
  <s:Body>
    <wsrm:TerminateSequenceResponse>
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    </wsrm:TerminateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequences"></a>Séquences

Voici une liste des contraintes qui s'appliquent aux séquences :

- B1401 : WCF génère et accède aux numéros de séquence qui ne sont pas plus élevés que `xs:long` la valeur inclusive maximale de 9223372036854775807.

Exemple d'en-tête `Sequence`.

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a>Demander un accusé de réception

WCF utilise l' `AckRequested` en-tête comme un mécanisme Keep-Alive.

Exemple d'en-tête `AckRequested`.

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

WCF utilise un mécanisme de « superposition » pour les accusés de réception de séquence fournis dans WS-Reliable Messaging. Les contraintes suivantes s'appliquent :

- R1601 : lorsque deux séquences réciproques sont établies à l’aide du `Offer` mécanisme, l' `SequenceAcknowledgement` en-tête peut être inclus dans tout message d’application transmis au destinataire prévu. Le point de terminaison distant doit être en mesure d'accéder à un en-tête `SequenceAcknowledgement` superposé.

- B1602 : WCF ne génère pas d' `SequenceAcknowledgement` en-têtes qui contiennent des `Nack` éléments. WCF valide que chaque `Nack` élément contient un numéro de séquence, mais ignore sinon l' `Nack` élément et la valeur.

 Exemple d'en-tête `SequenceAcknowledgement`.

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a>Erreurs de la messagerie WS-Reliable

La liste suivante répertorie les contraintes qui s’appliquent à l’implémentation WCF des erreurs WS-ReliableMessaging. Les contraintes suivantes s'appliquent :

- B1701 : WCF ne génère pas d' `MessageNumberRollover` Erreurs.

- B1702 : sur SOAP 1,2, lorsque le point de terminaison de service atteint sa limite de connexion et ne peut pas traiter de nouvelles connexions, WCF génère un `CreateSequenceRefused` sous-code d’erreur imbriqué, `netrm:ConnectionLimitReached` , comme indiqué dans l’exemple suivant.

```xml
<s:Envelope>
  <s:Header>
    <wsa:Action>http://docs.oasis-open.org/ws-rx/wsrm/200702/fault</wsa:Action>
  </s:Header>
  <s:Body>
    <s:Fault>
      <s:Code>
        <s:Value>s:Receiver</s:Value>
        <s:Subcode>
          <s:Value>wsrm:CreateSequenceRefused</s:Value>
          <s:Subcode>
            <s:Value>netrm:ConnectionLimitReached</s:Value>
          </s:Subcode>
        </s:Subcode>
      </s:Code>
      <s:Reason>
        <s:Text xml:lang="en">Server 'http://BusinessABC.com/serviceA' is too busy to process this request. Try again later.</s:Text>
      </s:Reason>
    </s:Fault>
  </s:Body>
</s:Envelope>
```

### <a name="ws-addressing-faults"></a>Erreurs WS-Addressing

Étant donné que WS-ReliableMessaging utilise WS-Addressing, l’implémentation WS-ReliableMessaging WCF peut générer et transmettre des erreurs WS-Addressing. Cette section traite des erreurs WS-Addressing que WCF génère et transmet explicitement au niveau de la couche WS-ReliableMessaging :

- B1801 : WCF génère et transmet l' `Message Addressing Header Required` erreur lorsque l’une des conditions suivantes est vraie :

  - Il manque un en-tête `CreateSequence` à un message `CloseSequence`, `TerminateSequence` ou `MessageId`.

  - Il manque un en-tête `CreateSequence` à un message `CloseSequence`, `TerminateSequence` ou `ReplyTo`.

  - Il manque un en-tête `CreateSequenceResponse` à un message `CloseSequenceResponse`, `TerminateSequenceResponse` ou `RelatesTo`.

- B1802 : WCF génère et transmet l' `Endpoint Unavailable` erreur pour indiquer qu’il n’y a pas d’écoute de point de terminaison qui peut traiter la séquence en fonction de l’examen des en-têtes d’adressage dans le `CreateSequence` message.

## <a name="protocol-composition"></a>Composition du protocole

### <a name="composition-with-ws-addressing"></a>Composition avec WS-Addressing

WCF prend en charge deux versions de WS-Addressing : WS-Addressing 2004/08 [WS-ADDR] et W3C WS-Addressing 1,0 Recommendations [WS-ADDR-CORE] et [WS-ADDR-SOAP].

Si la spécification WS-ReliableMessaging mentionne WS-Addressing 2004/08 uniquement, elle ne limite pas la version WS-Addressing à utiliser. Voici une liste des contraintes qui s’appliquent à WCF :

- R2101 : WS-Addressing 2004/08 et WS-Addressing 1.0 peuvent être utilisés ensemble avec la messagerie WS-Reliable.

- R2102 : une version unique de WS-Addressing doit être utilisée dans l'ensemble d'une séquence WS-ReliableMessaging ou une paire de séquences réciproques corrélées à l'aide du mécanisme `Offer`.

### <a name="composition-with-soap"></a>Composition avec SOAP

WCF prend en charge l’utilisation de SOAP 1,1 et SOAP 1,2 avec la messagerie WS-Reliable.

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Composition avec WS-Security et WS-SecureConversation

WCF fournit une protection pour les séquences WS-ReliableMessaging en utilisant le transport sécurisé (HTTPs), la composition avec WS-Security et la composition avec WS-Secure conversation. Le protocole WS-ReliableMessaging 1.1, WS-Security 1.1 et le protocole WS-Secure Conversation 1.3 doivent être utilisés ensemble. Voici une liste des contraintes qui s’appliquent à WCF :

- R2301 : pour protéger l’intégrité d’une séquence WS-ReliableMessaging en plus de l’intégrité et de la confidentialité des messages individuels, WCF requiert l’utilisation de la conversation WS-Secure.

- R2302 :unesession WS-Secure Conversation doit être établie avant l'établissement de la ou des séquences WS-ReliableMessaging.

- R2303 : si la durée de vie de la séquence WS-ReliableMessaging dépasse celle de la session WS-Secure Conversation, le `SecurityContextToken` établi à l’aide de WS-Secure Conversation doit être renouvelé par le biais de la liaison de renouvellement WS-Secure Conversation correspondante.

- B2304 :la séquence WS-ReliableMessaging ou une paire de séquences réciproques corrélées est toujours liée à une session WS-SecureConversation unique.

- R2305 : lorsqu’il est composé avec WS-Secure conversation, le répondeur WCF exige que le `CreateSequence` message contienne l' `wsse:SecurityTokenReference` élément et l' `wsrm:UsesSequenceSTR` en-tête.

 Exemple d'en-tête `UsesSequenceSTR`.

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a>Composition avec les sessions SSL/TLS

WCF ne prend pas en charge la composition avec les sessions SSL/TLS :

- B2401 : WCF ne génère pas l' `wsrm:UsesSequenceSSL` en-tête.

- R2402 : un initiateur de messagerie fiable ne doit pas envoyer un `CreateSequence` message avec un `wsrm:UsesSequenceSSL` en-tête à un répondeur WCF.

### <a name="composition-with-ws-policy"></a>Composition avec WS-Policy

WCF prend en charge deux versions de WS-Policy : WS-Policy 1,2 et WS-Policy 1,5.

## <a name="ws-reliablemessaging-ws-policy-assertion"></a>Assertion WS-Policy de la messagerie WS-ReliableMessaging

WCF utilise l’assertion WS-Policy WS-ReliableMessaging `wsrm:RMAssertion` pour décrire les fonctionnalités des points de terminaison. Voici une liste des contraintes qui s’appliquent à WCF :

- B3001 : WCF attache l' `wsrmn:RMAssertion` assertion WS-Policy à des `wsdl:binding` éléments. WCF prend en charge les deux pièces jointes aux `wsdl:binding` `wsdl:port` éléments et.

- B3002 : WCF ne génère jamais la `wsp:Optional` balise.

- B3003 : lors de l’accès à l' `wsrmp:RMAssertion` assertion WS-Policy, WCF ignore la `wsp:Optional` balise et traite la stratégie WS-RM comme obligatoire.

- R3004 : étant donné que WCF ne compose pas les sessions SSL/TLS, WCF n’accepte pas la stratégie qui spécifie `wsrmp:SequenceTransportSecurity` .

- B3005 : WCF génère toujours l' `wsrmp:DeliveryAssurance` élément.

- B3006 : WCF spécifie toujours l' `wsrmp:ExactlyOnce` assurance de remise.

- B3007 : WCF génère et lit les propriétés suivantes de l’assertion WS-ReliableMessaging et en assure le contrôle sur WCF `ReliableSessionBindingElement` :

  - `netrmp:InactivityTimeout`

  - `netrmp:AcknowledgementInterval`

  Exemple de `RMAssertion`.

  ```xml
  <wsrmp:RMAssertion>
    <wsp:Policy>
      <wsrmp:SequenceSTR/>
      <wsrmp:DeliveryAssurance>
        <wsp:Policy>
          <wsrmp:ExactlyOnce/>
          <wsrmp:InOrder/>
        </wsp:Policy>
      </wsrmp:DeliveryAssurance>
    </wsp:Policy>
    <netrmp:InactivityTimeout Milliseconds="600000"/>
    <netrmp:AcknowledgementInterval Milliseconds="200"/>
  </wsrmp:RMAssertion>
  ```

## <a name="flow-control-ws-reliablemessaging-extension"></a>Extension de messagerie WS-Reliable pour le contrôle de flux

WCF utilise l’extensibilité WS-ReliableMessaging pour fournir un contrôle plus strict facultatif sur le déroulement du message de séquence.

Le contrôle de Flow est activé en affectant à la propriété la valeur <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> `true` . Voici une liste des contraintes qui s’appliquent à WCF :

- B4001 : lorsque le contrôle de workflow de messagerie fiable est activé, WCF génère un `netrm:BufferRemaining` élément dans l’extensibilité d’élément de l' `SequenceAcknowledgement` en-tête, comme indiqué dans l’exemple suivant.

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- B4002 : même lorsque le contrôle de workflow de messagerie fiable est activé, WCF ne requiert pas `netrm:BufferRemaining` d’élément dans l' `SequenceAcknowledgement` en-tête.

- B4003 : la destination de messagerie fiable WCF utilise `netrm:BufferRemaining` pour indiquer le nombre de nouveaux messages qu’elle peut mettre en mémoire tampon.

- B4004 : lorsque le contrôle de workflow de messagerie fiable est activé, la source de messagerie fiable WCF utilise la valeur de `netrm:BufferRemaining` pour limiter la transmission des messages.

- B4005 : WCF génère `netrm:BufferRemaining` des valeurs entières comprises entre 0 et 4096 inclus, et lit les valeurs entières comprises entre 0 et `xs:int` la `maxInclusive` valeur 214748364 inclusives.

## <a name="message-exchange-patterns"></a>Modèles d’échange de messages

Cette section décrit le comportement de WCF lorsque WS-ReliableMessaging est utilisé pour différents modèles d’échange de messages. Pour chaque modèle d'échange de messages, les deux scénarios de déploiements suivants sont considérés :

- Initiateur non adressable : l'initiateur est derrière un pare-feu ; le répondeur peut remettre uniquement des messages à celui-ci sur les réponses HTTP.

- Initiateur adressable : l'initiateur et le répondeur peuvent tous les deux recevoir des requêtes HTTP ; en d'autres termes, deux connexions HTTP réciproques peuvent être établies.

### <a name="one-way-non-addressable-initiator"></a>Initiateur unidirectionnel, non adressable

#### <a name="binding"></a>Liaison

WCF fournit un modèle d’échange de messages unidirectionnel qui utilise une séquence sur un canal HTTP. WCF utilise des requêtes HTTP pour transmettre tous les messages de l’initiateur au répondeur et les réponses HTTP pour transmettre tous les messages du répondeur à l’initiateur.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF transmet un `CreateSequence` message sans `Offer` élément sur une requête HTTP et attend le `CreateSequenceResponse` message sur la réponse http. Le répondeur WCF crée une séquence et transmet le `CreateSequenceResponse` message sans `Accept` élément sur la réponse http.

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

L’initiateur WCF traite les accusés de réception de la réponse de tous les messages, à l’exception des `CreateSequence` messages de message et d’erreur. Le répondeur WCF transmet toujours un accusé de réception autonome sur la réponse HTTP à l’ensemble de la séquence et des `AckRequested` messages.

#### <a name="closesequence-exchange"></a>Échange CloseSequence

L’initiateur WCF transmet un `CloseSequence` message sur une requête HTTP et attend le `CreateSequenceResponse` message sur la réponse http. Le répondeur WCF transmet le `CloseSequenceResponse` message sur la réponse http.

#### <a name="terminatesequence-exchange"></a>Échange TerminateSequence

L’initiateur WCF transmet un `TerminateSequence` message sur une requête HTTP et attend le `TerminateSequenceResponse` message sur la réponse http. Le répondeur WCF transmet le `TerminateSequenceResponse` message sur la réponse http.

### <a name="one-way-addressable-initiator"></a>Initiateur unidirectionnel, adressable

#### <a name="binding"></a>Liaison

WCF fournit un modèle d’échange de messages unidirectionnel qui utilise une séquence sur un canal HTTP entrant et un canal sortant. WCF utilise les requêtes HTTP pour transmettre tous les messages. Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF transmet un `CreateSequence` message sans `Offer` élément sur une requête http. Le répondeur WCF crée une séquence et transmet le `CreateSequenceResponse` message sans `Accept` élément sur une requête http.

### <a name="duplex-addressable-initiator"></a>Initiateur duplex, adressable

#### <a name="binding"></a>Liaison

WCF fournit un modèle d’échange de messages bidirectionnels entièrement asynchrone utilisant deux séquences sur un canal HTTP entrant et un canal HTTP sortant. Ce modèle d’échange de messages peut être combiné avec le modèle d’échange de messages initiateur `Request/Reply`, `Addressable` d’une manière limitée. WCF utilise des requêtes HTTP pour transmettre tous les messages. Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF transmet un `CreateSequence` message avec un `Offer` élément sur une requête http. Le répondeur WCF s’assure que le `CreateSequence` a un `Offer` élément, puis crée une séquence et transmet le `CreateSequenceResponse` message avec un `Accept` élément.

#### <a name="sequence-lifetime"></a>Durée de vie de séquence

WCF traite les deux séquences comme une session duplex intégrale.

Lors de la génération d’une erreur qui provoque une séquence, WCF s’attend à ce que le point de terminaison distant cause les deux séquences. Lors de la lecture d’une erreur qui provoque une séquence, les deux séquences sont des erreurs WCF.

WCF peut fermer sa séquence sortante et continuer à traiter les messages sur sa séquence entrante. À l’inverse, WCF peut traiter la fermeture de la séquence entrante et continuer à envoyer des messages sur sa séquence sortante.

### <a name="request-reply-and-one-way-non-addressable-initiator"></a>Initiateur demande-réponse, unidirectionnel et non adressable

#### <a name="binding"></a>Liaison

WCF fournit un modèle d’échange de messages unidirectionnel et demande-réponse à l’aide de deux séquences sur un canal HTTP. WCF utilise des requêtes HTTP pour transmettre tous les messages de l’initiateur au répondeur et les réponses HTTP pour transmettre tous les messages du répondeur à l’initiateur.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF transmet un `CreateSequence` message avec un `Offer` élément sur une requête HTTP et attend le `CreateSequenceResponse` message sur la réponse http. Le répondeur WCF crée une séquence et transmet le `CreateSequenceResponse` message avec un `Accept` élément sur la réponse http.

#### <a name="one-way-message"></a>Message unidirectionnel

Pour réussir un échange de messages unidirectionnel, l’initiateur WCF transmet un message de séquence de demande sur la requête HTTP et reçoit un message autonome `SequenceAcknowledgement` sur la réponse http. `SequenceAcknowledgement` doit accepter le message transmis.

Le répondeur WCF peut répondre à la demande avec un accusé de réception, une erreur ou une réponse avec un corps vide et un code d’état HTTP 202.

#### <a name="two-way-messages"></a>Messages bidirectionnels

Pour réussir un protocole d’échange de messages bidirectionnel, l’initiateur WCF transmet un message de séquence de demande sur la requête HTTP et reçoit un message de séquence de réponse sur la réponse HTTP. La réponse doit contenir un `SequenceAcknowledgement` qui accuse réception du message de séquence de demande transmis.

Le répondeur WCF peut répondre à la demande avec une réponse d’application, une erreur ou une réponse avec un corps vide et un code d’état HTTP 202.

En raison de la présence de messages unidirectionnels et du délai d'attente des réponses d'application, le numéro de séquence du message de séquence de demande et le numéro de séquence du message de réponse n'ont aucune corrélation.

#### <a name="retrying-replies"></a>Nouvelles tentatives de réponses

WCF s’appuie sur la corrélation de requête-réponse HTTP pour la corrélation de protocole d’échange de messages bidirectionnels. Pour cette raison, l’initiateur WCF n’interrompt pas la nouvelle tentative d’un message de séquence de demande lorsque le message de séquence de demande est reconnu, mais plutôt lorsque la réponse HTTP porte une `SequenceAcknowledgement` erreur, une réponse de l’application ou une erreur. Le répondeur WCF réessaye les réponses sur la réponse HTTP de la demande à laquelle la réponse est corrélée.

#### <a name="closesequence-exchange"></a>Échange CloseSequence

Après avoir reçu tous les messages de séquence de réponse et les accusés de réception de tous les messages de séquence de demande unidirectionnels, l’initiateur WCF transmet un `CloseSequence` message pour la séquence de demande sur une requête HTTP et attend le `CloseSequenceResponse` sur la réponse http.

La fermeture de la séquence de demande ferme implicitement la séquence de réponse. Cela signifie que l’initiateur WCF comprend la dernière de la séquence `SequenceAcknowledgement` de réponse sur le `CloseSequence` message et que la séquence de réponse n’a pas d' `CloseSequence` échange.

Le répondeur WCF garantit que toutes les réponses sont acceptées et transmet le `CloseSequenceResponse` message sur la réponse http.

#### <a name="terminatesequence-exchange"></a>Échange TerminateSequence

Après avoir reçu le `CloseSequenceResponse` message, l’initiateur WCF transmet un `TerminateSequence` message pour la séquence de demande sur une requête HTTP et attend le `TerminateSequenceResponse` sur la réponse http.

Comme l'échange `CloseSequence`, terminer la séquence de demande termine implicitement la séquence de réponse. Cela signifie que l’initiateur WCF comprend la dernière de la séquence `SequenceAcknowledgement` de réponse sur le `TerminateSequence` message et que la séquence de réponse n’a pas d' `TerminateSequence` échange.

Le répondeur WCF transmet le `TerminateSequenceResponse` message sur la réponse http.

### <a name="requestreply-addressable-initiator"></a>Initiateur demande/réponse, adressable

#### <a name="binding"></a>Liaison

WCF fournit un modèle d’échange de messages de demande-réponse utilisant deux séquences sur un canal HTTP entrant et un canal sortant. Ce modèle d'échange de messages peut être combiné avec le modèle d'échange de messages initiateur `Duplex, Addressable` d'une manière limitée. WCF utilise les requêtes HTTP pour transmettre tous les messages. Toutes les réponses HTTP ont un corps vide et le code d'état HTTP 202.

#### <a name="createsequence-exchange"></a>Échange CreateSequence

L’initiateur WCF transmet un `CreateSequence` message avec un `Offer` élément sur une requête http. Le répondeur WCF s’assure que le `CreateSequence` a un `Offer` élément, puis crée une séquence et transmet le `CreateSequenceResponse` message avec un `Accept` élément.

#### <a name="requestreply-correlation"></a>Corrélation demande/réponse

Les points suivants s'appliquent à toutes les demandes et réponses corrélées :

- WCF garantit que tous les messages de demande d’application comportent une `ReplyTo` référence de point de terminaison et un `MessageId` .

- WCF applique la référence de point de terminaison local à chaque message de demande d’application `ReplyTo` . La référence de point de terminaison locale est `CreateSequence` du message `ReplyTo` pour l'initiateur et `CreateSequence` du message `To` pour le répondeur.

- WCF garantit que les messages de demande entrants comportent un `MessageId` et un `ReplyTo` .

- WCF garantit `ReplyTo` que l’URI de la référence du point de terminaison de tous les messages de demande d’application correspond à la référence de point de terminaison locale définie précédemment.

- WCF s’assure que toutes les réponses portent les `RelatesTo` en-têtes et les corrections qui suivent les `To` règles de `wsa` corrélation demande/réponse.

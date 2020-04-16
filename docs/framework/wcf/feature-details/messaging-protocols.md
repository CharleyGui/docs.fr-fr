---
title: Protocoles de messagerie
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 814347c77b54c4450aabf0a4f3966df223360663
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463831"
---
# <a name="messaging-protocols"></a>Protocoles de messagerie

La pile de canaux de la Windows Communication Foundation (WCF) utilise des canaux de codage et de transport pour transformer la représentation interne des messages en format fil et l’envoyer en utilisant un transport particulier. Le transport le plus couramment utilisé pour l'interopérabilité des services Web est le HTTP, et les encodages les plus couramment utilisés par les services Web sont SOAP 1.1 basé sur XML, SOAP 1.2 et MTOM (Message Transmission Optimization Mechanism).

Ce sujet couvre les détails de mise <xref:System.ServiceModel.Channels.HttpTransportBindingElement>en œuvre WCF pour les protocoles suivants utilisés par .

Spécification/document :

- [HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)
- [SOAP 1.1 HTTP Binding](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), Section 7
- [SOAP 1.2 HTTP Liaison](https://www.w3.org/TR/soap12-part2) Article 7

Ce sujet couvre les détails de mise <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> en œuvre WCF pour les protocoles suivants qui et l’emploi.

Spécification/Document:

- [XML](https://www.w3.org/TR/REC-xml)
- [SOAP 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [SOAP 1.2 Core](https://www.w3.org/TR/soap12-part1/)
- [WS-Addressing 2004/08](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [W3C Web Services Addressing 1.0 – Éléments principaux](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [W3C Web Services Addressing 1.0 – Liaison SOAP](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [W3C Web Services Adresse 1.0 - WSDL Binding](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [W3C Web Services Addressing 1.0 - Métadonnées](https://www.w3.org/TR/ws-addr-metadata/)
- [Liaison WSDL SOAP 1.1](https://www.w3.org/TR/wsdl/)
- [Liaison WSDL SOAP 1.2](https://www.w3.org/Submission/wsdl11soap12/)

Ce sujet couvre les détails de la <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> mise en œuvre de WCF pour les protocoles suivants qui emploient.

Spécification/document :

- [Xop](https://www.w3.org/TR/xop10/)
- [Liaison MTOM + SOAP 1.2](https://www.w3.org/TR/soap12-mtom/)
- [Liaison MTOM SOAP 1.1](https://www.w3.org/Submission/soap11mtom10/)
- [Assertion de MTOM WS-Policy](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

Les espaces de noms XML suivants et les préfixes associés sont utilisés tout au long de ce sujet :

| Préfixe | URI (Uniform Resource Identifier) de l'espace de noms |
|------------|---------------------------------------------------|
| s11 | `http://schemas.xmlsoap.org/soap/envelope` |
| s12 |`http://www.w3.org/2003/05/soap-envelope` |
| wsa |`http://www.w3.org/2004/08/addressing` |
| wsam |`http://www.w3.org/2007/05/addressing/metadata` |
| wsap |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| wsa10 |`http://www.w3.org/2005/08/addressing` |
| wsaw10 |`http://www.w3.org/2006/05/addressing/wsdl` |
| xop |`http://www.w3.org/2004/08/xop/include` |
| xmime |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| Dp |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a>SOAP 1.1 et SOAP 1.2

### <a name="envelope-and-processing-model"></a>Enveloppe et modèle de traitement
WCF implémente le traitement des enveloppes SOAP 1.1 suivant le profil de base 1.1 (BP11) et le profil de base 1.0 (SSBP10). Le traitement d'enveloppe SOAP 1.2 est implémenté selon SOAP12-Part1.

Cette section explique certains choix de mise en œuvre pris par WCF en ce qui concerne BP11 et SOAP12-Part1.

#### <a name="mandatory-header-processing"></a>Traitement obligatoire des en-têtes
WCF suit les règles `mustUnderstand` de traitement des en-têtes marqués décrits dans les spécifications SOAP 1.1 et SOAP 1.2, avec les variations suivantes.

Un message qui entre dans la pile de canaux WCF est traité par des canaux individuels configurés par des éléments contraignants associés, par exemple, l’encodage des messages texte, la sécurité, la messagerie fiable et les transactions. Chaque canal reconnaît les en-têtes de l'espace de noms associé et les marque comme compris. Une fois qu'un message entre le répartiteur, le module de formatage de l'opération lit les en-têtes attendus par le contrat de message/opération correspondant et les marque comme compris. Ensuite, le répartiteur vérifie si des en-têtes restants ne sont pas compris mais marqués comme `mustUnderstand` et lève une exception. Les messages qui contiennent des en-têtes `mustUnderstand` ciblant le destinataire ne sont pas traités par le code de l'application destinataire.

Un tel traitement par couches permet de séparer les couches d'infrastructure et les couches d'application du nœud SOAP :

- B1111: Les en-têtes qui ne sont pas compris sont détectés après le traitement du message par la pile du canal d’infrastructure WCF, mais avant qu’il ne soit traité par application

     La valeur d'en-tête `mustUnderstand` diffère entre SOAP 1.1 et SOAP 1.2. Basic Profile 1.1 exige que la valeur `mustUnderstand` soit définie sur 0 ou 1 pour les messages SOAP 1.1. SOAP 1.2 accepte les valeurs 0, 1, `false` et `true`, mais recommande d'émettre une représentation canonique de valeurs `xs:boolean` (`false`, `true`).

- B1112: WCF `mustUnderstand` émet des valeurs 0 et 1 pour les deux VERSIONs SOAP 1.1 et SOAP 1.2 de l’enveloppe SOAP. WCF accepte l’espace `xs:boolean` de `mustUnderstand` valeur total de l’en-tête (0, 1, `false`, `true`)

#### <a name="soap-faults"></a>Erreurs SOAP
Ce qui suit est une liste des implémentations de défauts SOAP spécifiques à WCF.

- B2121: WCF retourne les codes de défaut `s11:mustUnderstand`SOAP `s11:Client`1.1 suivants: , et `s11:Server`.

- B2122: WCF retourne les codes de défaut `s12:MustUnderstand`SOAP `s12:Sender`1.2 suivants: , , et `s12:Receiver`.

### <a name="http-binding"></a>Liaison HTTP

#### <a name="soap-11-http-binding"></a>Liaison HTTP SOAP 1.1
WCF implémente la liaison SOAP1.1 HTTP suivant la section de spécifications 1.1 du Profil de base 1.1 avec les précisions suivantes :

- B2211 : Le service WCF ne met pas en œuvre la réorientation des demandes HTTP POST.

- B2212 : Les clients de WCF prennent en charge LES cookies HTTP conformément au 3.4.8.

#### <a name="soap-12-http-binding"></a>Liaison HTTP SOAP 1,2
WCF met en œuvre la liaison SOAP 1.2 HTTP telle que décrite dans les spécifications SOAP 1.2-partie 2 (SOAP12Part2) avec les précisions suivantes.

SOAP 1.2 a introduit un paramètre d'action facultatif pour le type de média `application/soap+xml`. Ce paramètre est utile pour optimiser la distribution du message sans que le corps du message SOAP soit analysé lorsque la spécification WS-Addressing n'est pas utilisée.

- R2221 : le paramètre d’action `application/soap+xml`, lorsqu’il est présent dans une demande SOAP 1.2, doit correspondre à l’attribut `soapAction` sur l’élément `wsoap12:operation` dans la liaison WSDL correspondante.

- R2222 : le paramètre d'action `application/soap+xml`, lorsqu'il est présent dans un message SOAP 1.2, doit correspondre à `wsa:Action` lorsque la spécification WS-Addressing 2004/08 ou WS-Addressing 1.0 est utilisée.

Lorsque la spécification WS-Addressing est désactivée et qu'une demande entrante ne contient pas de paramètre d'action, l'`Action` du message est considérée comme non spécifiée.

## <a name="ws-addressing"></a>WS-Addressing
WCF implémente 3 versions de WS-Addressing :

- WS-Addressing 2004/08

- W3C Web Services Addressing 1.0 Core (ADDR10-CORE) et liaison SOAP (ADDR10-SOAP)

- WS-Addressing 1.0 - Métadonnées

### <a name="endpoint-references"></a>Références de point de terminaison
Toutes les versions de WS-Addressing que WCF implémente utilisent des références de point de terminaison pour décrire les points de terminaison.

#### <a name="endpoint-references-and-ws-addressing-versions"></a>Références de point de terminaison et versions de WS-Addressing
WCF met en œuvre un certain nombre de protocoles `EndpointReference` d’infrastructure qui utilisent WS-Addressing et en particulier l’élément et `W3C.WsAddressing.EndpointReferenceType` la classe (par exemple, WS-ReliableMessaging, WS-SecureConversation, et WS-Trust). WCF prend en charge l’utilisation de l’une ou l’autre version de WS-Addressing avec d’autres protocoles d’infrastructure. Les critères de terminaison WCF prennent en charge une version de WS-Addressing par point de terminaison.

Pour R3111, l’espace `EndpointReference` nom pour l’élément ou le type utilisé dans les messages échangés avec un point de terminaison WCF doit correspondre à la version de WS-Addressing implémentée par ce point de terminaison.

Par exemple, si un point de terminaison WCF `AcksTo` implémente WS-ReliableMessaging, l’en-tête retourné par un tel point d’arrivée à l’intérieur `CreateSequenceResponse` utilise la version WS-Addressing que l’élément `EncodingBinding` spécifie pour ce critère d’évaluation.

#### <a name="endpoint-references-and-metadata"></a>Références de point de terminaison et métadonnées
Plusieurs scénarios nécessitent de communiquer des métadonnées ou une référence aux métadonnées pour un point de terminaison donné.

B3121 : WCF utilise des mécanismes décrits dans la section 6 de la section 6 de WS-MetadataExchange (MEX) pour inclure les métadonnées pour les références de points de terminaison par valeur ou par référence.

Considérez un scénario où un service WCF nécessite une authentification à l’aide d’un jeton Markup Language (SAML) d’affirmations de sécurité émis par l’émetteur symbolique à `http://sts.fabrikam123.com`. Le critère d’évaluation du WCF `sp:IssuedToken` décrit cette exigence `sp:Issuer` d’authentification en utilisant l’affirmation avec une affirmation imbriquée pointant vers l’émetteur symbolique. Les applications clientes qui accèdent à l'assertion `sp:Issuer` doivent savoir comment communiquer avec l'émetteur du jetons du point de terminaison. Le client a besoin de connaître les métadonnées relatives à l'émetteur de jetons. À l’aide des extensions de métadonnées de référence définies dans MEX, WCF fournit une référence aux métadonnées d’émetteurs symboliques.

```xml
<sp:IssuedToken>
  <sp:Issuer>
    <wsa10:Address>
      http://sts.fabrikam123.com
    </wsa10:Address>
    <wsa10:Metadata>
      <mex:Metadata>
        <mex:MetadataSection>
          <mex:MetadataReference>
            <wsa10:Address>
              http://sts.fabrikam123.com/mex
            </wsa10:Address>
          </mex:MetadataReference>
        </mex:MetadataSection>
      </mex:Metadata>
    </wsa10:Metadata>
  </sp:Issuer>
</sp:IssuedToken>
```

### <a name="message-addressing-headers"></a>En-têtes d'adressage des messages

#### <a name="message-headers"></a>En-têtes de message
Pour les deux versions WS-Addressing, WCF utilise les `wsa:To`en-têtes `wsa:MessageID`de `wsa:RelatesTo`message suivants comme prescrit par les spécifications , `wsa:ReplyTo`, `wsa:Action`, , , et .

B3211: Pour toutes les versions WS-Addressing, WCF honore, mais ne produit pas `wsa:FaultTo` hors `wsa:From`de la boîte, WS-Addressing en-têtes de message et .

Les applications qui interagissent avec les applications WCF peuvent ajouter ces en-têtes de message et WCF les traitera en conséquence.

#### <a name="reference-parameters-and-properties"></a>Paramètres et propriétés de référence

WCF met en œuvre le traitement des paramètres de référence des points de terminaison et des propriétés de référence conformément aux spécifications respectives.

B3221 : Lorsqu’ils sont configurés pour utiliser WS-Addressing 2004/08, les critères de terminaison WCF ne font pas de distinction entre le traitement des propriétés de référence et les paramètres de référence.

### <a name="message-exchange-patterns"></a>Modèles d’échange de messages
La séquence des messages impliqués dans l’invocation de l’opération de service Web est appelée *le modèle d’échange de messages*. WCF prend en charge les modèles d’échange de messages à sens unique, de demande et de duplex. Cette section clarifie les exigences WS-Addressing de traitement des messages en fonction du modèle d’échange de messages utilisé.

Dans cette section, le demandeur envoie le premier message et le répondeur reçoit le premier message.

#### <a name="one-way-message"></a>Message unidirectionnel
Lorsqu’un critère d’évaluation WCF est `Action` configuré pour prendre en charge les messages avec un modèle donné pour suivre un modèle à sens unique, le critère d’évaluation WCF suit les comportements et les exigences suivants. Sauf indication contraire, les comportements et les règles s’appliquent pour les deux versions de WS-Addressing prises en charge dans WCF:

- R3311 : le demandeur doit inclure `wsa:To`, `wsa:Action` et les en-têtes pour tous les paramètres de référence spécifiés par la référence de point de terminaison. Lorsque WS-Addressing 2004/08 est utilisée et que des [propriétés de référence] sont spécifiées par la référence de point de terminaison, les en-têtes correspondants doivent également être ajoutés au message.

- B3312: le demandeur peut inclure les en-têtes `MessageID`, `ReplyTo` et `FaultTo`. L'infrastructure du récepteur les ignorera, et ils seront passés à l'application.

- R3313: lorsque le HTTP est utilisé et qu'aucun message n'est envoyé sur la section de réponse HTTP, le répondeur doit envoyer une réponse HTTP avec un corps vide et un code d'état HTTP 202.

     Lorsque le transport HTTP est utilisé et que le contrat d'opération déclare un message unidirectionnel, la réponse HTTP peut encore être utilisée pour envoyer les messages d'infrastructure. Par exemple, la messagerie fiable peut envoyer un message `SequenceAcknowledgement` sur une réponse HTTP.

- B3314 : Le répondant du WCF n’envoie pas de message de défaut en réponse à un message à sens unique.

#### <a name="request-reply"></a>Demande-réponse
Lorsqu’un critère d’évaluation WCF est `Action` configuré pour un message avec un modèle de réponse préalable, le critère de terminaison WCF suit les comportements et les exigences ci-dessous. Sauf indication contraire, les comportements et les règles s’appliquent pour les deux versions de WS-Addressing prises en charge dans WCF:

- R3321: Le demandeur doit inclure `wsa:To` `wsa:Action`dans `wsa:MessageID`la demande , , et les en-têtes pour tous les paramètres de référence ou les propriétés de référence (ou les deux) spécifiés par la référence de point de terminaison.

- R3322 : lorsque WS-Addressing 2004/08 est utilisée, `ReplyTo` doit également être inclus dans la demande.

- R3323 : Lorsque WS-Addressing 1.0 est utilisé et `ReplyTo` n’est pas présent dans la `http://www.w3.org/2005/08/addressing/anonymous` demande, une référence par défaut avec la propriété [adresse] égale à elle est utilisée.

- R3324: Le demandeur `wsa:To`doit `wsa:Action`inclure, et `wsa:RelatesTo` les en-têtes dans le message de réponse, ainsi que les `ReplyTo` en-têtes pour tous les paramètres de référence ou les propriétés de référence (ou les deux) spécifiés par la référence de point de terminaison dans la demande.

### <a name="web-services-addressing-faults"></a>Erreurs d'adressage des services Web
R3411 : WCF produit les défauts suivants définis par WS-Addressing 2004/08.

| Code | Cause |
|----------|-----------|
| `wsa:DestinationUnreachable` | Le message est arrivé avec un `ReplyTo` différent de l'adresse de réponse établie pour ce canal ; il n'y a aucun point de terminaison qui écoute l'adresse spécifiée dans l'en-tête To. |
| `wsa:ActionNotSupported` | les canaux de l'infrastructure ou le répartiteur associé au point de terminaison ne reconnaissent pas l'action spécifiée dans l'en-tête `Action`. |

R3412: WCF produit les défauts suivants définis par WS-Addressing 1.0.

| Code | Cause |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | Dupliquer `wsa:To`, `wsa:ReplyTo`, `wsa:From` ou `wsa:MessageID`. Dupliquer `wsa:RelatesTo` `RelationshipType`avec le même . |
| `wsa10:MessageAddressingHeaderRequired` | L'en-tête d'adressage requis est absent. |
| `wsa10:DestinationUnreachable` | Le message est arrivé avec un `ReplyTo` différent de l'adresse de réponse établie pour ce canal. Il n'y a aucun point de terminaison qui écoute l'adresse spécifiée dans l'en-tête To. |
| `wsa10:ActionNotSupported` | Une action spécifiée dans l'en-tête `Action` n'est pas reconnue par les canaux de l'infrastructure ou le répartiteur associé au point de terminaison. |
| `wsa10:EndpointUnavailable` | Le canal RM renvoie cette erreur pour indiquer que le point de terminaison ne traitera pas la séquence suite à l'examen des en-têtes d'adressage du message `CreateSequence`. |

Le code des tables précédentes correspond à `FaultCode` dans SOAP 1.1 et `SubCode` (avec Code=Expéditeur) dans SOAP 1.2.

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>Liaison WSDL 1.1 et assertions de WS-Policy

#### <a name="indicating-use-of-ws-addressing"></a>Utilisation recommandée de WS-Addressing
WCF utilise des affirmations de politique pour indiquer le support de point final pour une version particulière de WS-Addressing.

L'assertion de stratégie suivante possède l'objet de stratégie de point de terminaison [WS-PA] et indique que les messages envoyés et reçus depuis le point de terminaison doivent utiliser WS-Addressing 2004/08.

```xml
<wsap:UsingAddressing />
```

Cette assertion de stratégie complète la spécification WS-Addressing 2004/08.

L'assertion de stratégie indique que les messages envoyés/reçus doivent utiliser WS-Addressing 1.0.

```xml
<wsam:Addressing/>
```

L'assertion de stratégie suivante possède un objet de stratégie de point de terminaison [WS-PA] et indique que les messages envoyés et reçus depuis le point de terminaison doivent utiliser WS-Addressing 2004/08.

```xml
<wsaw10:UsingAddressing />
```

L'élément `wsaw10:UsingAddressing` est emprunté à [WS-Adressage-WSDL] et est utilisé dans le contexte de WS-Policy conformément à la section 3.1.2 de cette spécification.

L’utilisation de l’adressage n’altère pas la sémantique des liaisons HTTP WSDL 1.1, SOAP 1.1 et SOAP 1.2. Par exemple, si une réponse est attendue à une demande envoyée à un point de terminaison qui utilise l’adressage et la liaison HTTP WSDL SOAP 1.x, elle doit être envoyée en utilisant la réponse HTTP.

Pour les réponses envoyées via HTTP, l'assertion WS-AM est :

```xml
<wsam:AnonymousResponses/>
```

L'assertion de stratégie complète peut ressembler à ceci :

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Toutefois, certains modèles d’échange de messages profitent du fait que deux connexions HTTP réciproques indépendantes soient établies entre le demandeur et le répondeur, par exemple dans le cas de messages unidirectionnels non sollicités envoyés par le répondeur.

WCF offre une fonctionnalité par laquelle deux canaux de transport sous-jacents peuvent former un canal Composite Duplex, où un canal est utilisé pour les messages d’entrée et l’autre est utilisé pour les messages de sortie. Dans le cas du transport HTTP, le canal duplex composite fournit deux connexions HTTP réciproques. Le demandeur utilise une connexion pour envoyer des messages au répondeur, et le répondeur utilise l'autre pour renvoyer des messages au demandeur.

Pour les réponses envoyées via des demandes HTTP distinctes, l'assertion WS-AM est :

```xml
<wsam:NonAnonymousResponses/>
```

L'assertion de stratégie complète peut ressembler à ceci :

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Pour utiliser l'assertion suivante, qui possède un objet de stratégie de point de terminaison [WS-PA] sur les points de terminaison qui utilisent des liaisons HTTP WSDL 1.1 SOAP 1.x, il est nécessaire d'utiliser deux connexions HTTP réciproques séparées pour transmettre des messages du demandeur au répondeur et du répondeur au demandeur, respectivement.

```xml
<cdp:CompositeDuplex/>
```

L’instruction précédente mène aux exigences suivantes pour l’en-tête `wsa:ReplyTo` des messages de demande :

- R3514: Les messages de demande envoyés `ReplyTo` à `[address]` un point `http://www.w3.org/2005/08/addressing/anonymous` de terminaison doivent avoir un en-tête avec la propriété n’est pas `wsap10:UsingAddressing` égal `wsap:UsingAddressing` à `cdp:CompositeDuplex` si le point final utilise un WSDL 1.1 SOAP 1.x HTTP liaison et a une alternative de politique avec un ou une affirmation couplée avec attaché.

- R3515: Les messages de demande envoyés `ReplyTo` à `[address]` un point `http://www.w3.org/2005/08/addressing/anonymous`de terminaison doivent avoir un en-tête avec la propriété égale à , ou ne pas avoir un `ReplyTo` en-tête du tout, si le point final utilise un WSDL 1.1 SOAP 1.x HTTP liaison et a une alternative de politique avec `wsap10:UsingAddressing` affirmation et aucune `cdp:CompositeDuplex` affirmation attachée.

- R3516: Les messages de demande envoyés `ReplyTo` à `[address]` un point `http://www.w3.org/2005/08/addressing/anonymous` de terminaison doivent avoir un en-tête avec une propriété égale à `wsap:UsingAddressing` si le `cdp:CompositeDuplex` point final utilise un WSDL 1.1 SOAP 1.x HTTP liaison et a une alternative de politique avec affirmation et aucune affirmation ci-jointe.

La spécification WSDL de WS-Addressing tente de décrire des liaisons de protocole semblables en présentant un élément `<wsaw:Anonymous/>` avec trois valeurs textuelles (obligatoire, facultatif et a interdit) pour indiquer des besoins sur l’en-tête `wsa:ReplyTo` (section 3.2). Malheureusement, une telle définition d’élément n’est pas particulièrement utilisable comme une assertion dans le contexte de WS-Policy, car il requiert que les extensions spécifiques au domaine prennent en charge l’intersection d’alternatives à l’aide d’un élément de ce type comme une assertion. Une telle définition d'élément indique également la valeur de l'en-tête `ReplyTo` par opposition au comportement du point de terminaison sur la transmission, ce qui le rend spécifique au transport HTTP.

#### <a name="action-definition"></a>Définition d'action
WS-Addressing 2004/08 définit un attribut `wsa:Action` pour les éléments `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]`. La liaison WS-Addressing 1.0 WSDL (WS-ADDR10-WSDL) définit un attribut semblable, `wsaw10:Action`.

La seule différence entre les deux réside dans la sémantique du modèle d’action par défaut décrite à la section 3.3.2 de WS-ADDR et à la section 4.4.4 de WS-ADDR10-WSDL, respectivement.

Il est raisonnable d’avoir deux critères `portType` d’évaluation qui partagent le même (ou le contrat, dans la terminologie WCF) mais en utilisant différentes versions de WS-Addressing. Mais étant donné que cette action est définie par le `portType` et ne doit pas pour les points de terminaison qui implémentent le `portType`, il devient impossible de prendre en charge les deux modèles d’action par défaut.

Pour résoudre cette controverse, WCF prend `Action` en charge une seule version de l’attribut.

B3521 : WCF `wsaw10:Action` utilise `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` l’attribut sur des éléments tels que définis `Action` dans WS-ADDR10-WSDL pour déterminer l’URI pour les messages correspondants indépendamment de la version WS-Addressing utilisée par le point de terminaison.

#### <a name="use-endpoint-reference-inside-wsdl-port"></a>Utilisation des références de point de terminaison à l'intérieur d'un port WSDL
La section 4.1 de WS-ADDR10-WSDL étend l'élément `wsdl:port` de manière à inclure l'élément enfant `<wsa10:EndpointReference…/>` et décrire le point de terminaison en des termes propres à WS-Addressing. WCF élargit cet utilitaire sur WS-Addressing 2004/08, permettant `<wsa:EndpointReference…/>` `wsdl:port`d’apparaître comme un élément enfant de .

- R3531 : si un point de terminaison possède une alternative de stratégie attachée avec une assertion de la stratégie `<wsaw10:UsingAddressing/>`, l'élément `wsdl:port` correspondant peut contenir un élément enfant `<wsa10:EndpointReference …/>`.

- R3532 : `wsdl:port` Si un `<wsa10:EndpointReference …/>`élément `wsa10:EndpointReference/wsa10:Address` enfant contient un élément, `@address` la valeur `wsdl:port` / `wsdl:location` de l’élément enfant doit correspondre à la valeur de l’attribut de l’élément frère ou sœur.

- R3533 : si un point de terminaison possède une alternative de stratégie attachée avec une assertion de la stratégie `<wsap:UsingAddressing/>`, l'élément `wsdl:port` correspondant peut contenir un élément enfant `<wsa:EndpointReference …/>`.

- R3534 : `wsdl:port` Si un `<wsa:EndpointReference …/>`élément `wsa:EndpointReference/wsa:Address` enfant contient un élément, `@address` la valeur `wsdl:port` / `wsdl:location` de l’élément enfant doit correspondre à la valeur de l’attribut de l’élément frère ou sœur.

### <a name="composition-with-ws-security"></a>Composition avec WS-Security
D'après les sections relatives à la sécurité de WS-ADDR et WS-ADDR10, il est recommandé que tous les en-têtes d'adressage de messages soient signés avec le corps du message afin de les lier.

Lorsque WS-Security est utilisée pour la protection de l'intégrité des messages, les en-têtes de message WS-Addressing ainsi que les en-têtes résultant des paramètres ou des propriétés de référence (ou les deux) doivent être signés avec le corps du message.

### <a name="examples"></a>Exemples

#### <a name="one-way-message"></a>Message unidirectionnel
Dans ce scénario, l'expéditeur envoie un message unidirectionnel au récepteur. SOAP 1.2, HTTP 1.1 et W3C WS-Addressing 1.0 sont utilisés.

Structure du message de demande : les en-têtes de message incluent les éléments `wsa10:To` et `wsa10:Action`. Le corps du message inclut un élément `<app:Ping>` spécifique de l'espace de noms de l'application.

TÊTES HTTP: La destination dans POST correspond `wsa10:To` à l’URI dans l’élément.

L'en-tête Content-Type a la valeur `application/soap+xml` comme l'exige SOAP 1.2. Les paramètres `charset` et `action` sont inclus. Le paramètre `action` de l'en-tête Content-Type correspond à la valeur de l'en-tête de message `wsa10:Action`.

```
POST http://fabrikam123.com/Service HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8;  
              action="http://fabrikam123.com/Service/OneWay"
Host: 131.107.72.15
Content-Length: 1501
Expect: 100-continue
Proxy-Connection: Keep-Alive
<s12:Envelope>
  <s12:Header>
    <wsa10:To s12:mustUnderstand="1">
        http://fabrikam123.com/Service
    </wsa10:To>
    <wsa10:Action s12:mustUnderstand="1">
        http://fabrikam123.com/Service/OneWay
    </wsa10:Action>
  </s12:Header>
  <s12:Body>
    <Ping xmlns="http://fabrikam123.com/Service/">
      <Text>Hello World</Text>
    </Ping>
  </s12:Body>
</s12:Envelope>
```

Le récepteur répond avec une réponse HTTP vide et l'état 202. Exemple de réponse HTTP :

```
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a>SOAP MTOM (Message Transmission Optimization Mechanism)
Cette section décrit les détails de la mise en œuvre du WCF pour le MTOM DE HTTP SOAP. La technologie MTOM est le mécanisme d’encodage des messages SOAP de la même classe que l’encodage texte/XML traditionnel ou l’encodage binaire WCF. MTOM inclut ce qui suit :

- Un mécanisme d'encodage XML et d'empaquetage décrit par [XOP] qui optimise les éléments d'information XML qui contiennent les données binaires encodées en Base64 dans des parties binaires séparées.

- Encapsulation MIME du package XOP qui sérialise l'ensemble d'informations XML et chaque partie binaire du package XOP dans une partie MIME séparée.

- Encodage XOP MIME appliqué à l'enveloppe SOAP 1.x.

- Liaison de transport HTTP.

Il est possible d’utiliser MTOM avec des transports non-HTTP avec WCF. Toutefois, nous nous concentrerons sur le HTTP dans cette rubrique.

Le format MTOM tire parti d'un grand ensemble de spécifications qui couvrent MTOM lui-même, XOP et MIME. La modularité de cet ensemble d’exigences rend quelque peu difficile la reconstruction des spécifications exactes sur le format et le traitement de la sémantique. Cette section décrit les exigences de format et de traitement pour la liaison HTTP MTOM.

### <a name="mtom-message-encoding"></a>Encodage de message MTOM

#### <a name="generating-mtom-messages"></a>Génération de messages MTOM
Le [XOP] la section 3.1 décrit le processus de l'encodage XML avec des détails d'élément qui contiennent des valeurs Base64 dans un package XOP abstraitement défini.

La séquence d'étapes suivante décrit le processus d'encodage spécifique à MTOM :

1. Assurez-vous que l’enveloppe SOAP à encoder `[namespace name]` `http://www.w3.org/2004/08/xop/include` ne `[local name]` contient `Include`aucun élément d’information avec un des et un des .

2. Créez un package MIME vide.

3. Identifiez dans l'ensemble d'informations XML d'origine les éléments à optimiser. Pour que les éléments soient optimisés, `[children]` les caractères qui composent l’élément `xs:base64Binary` d’information doivent être sous la forme canonique de (voir XSD-2, 3.2.16 base64Binary) et ne doivent pas contenir de caractères d’espace blanc précédant, en ligne avec ou suivant le contenu non-blanc-espace.

4. Créez une enveloppe SOAP XOP qui est une copie de l'enveloppe SOAP d'origine, mais en remplaçant les enfants de chaque élément d'information identifiés à l'étape précédente par un élément d'information `xop:Include` construit comme suit :

    1. Transformez les caractères remplacés en données binaires en les traitant comme des données encodées en Base64.

    2. Générez une valeur d’en-tête Content-ID unique qui satisfait aux exigences R3133 et R3134.

    3. Générez un en-tête MIME Content-Transfer-Encoding avec la valeur binaire.

    4. Si l'élément d'information qui est optimisé (le [parent] de l'élément d'information `xop:Include` inséré) a un élément d'information d'attribut `xmime:contentType`, générez un en-tête MIME Content-type avec la valeur de l'attribut `xmime:contentType`.

    5. Générez une nouvelle partie MIME binaire avec le contenu formé par les données binaires décodées des caractères remplacés traités en Base64, l'en-tête Content-ID de l'étape 4b, l'en-tête Content-Transfer-Encoding de l'étape 4c, l'en-tête Content-Type si généré à l'étape 4d.

    6. Ajoutez un attribut `href` à l'élément `xop:Include` avec la valeur cid : l'uri dérivé de la valeur d'en-tête Content-ID générée à l'étape 4b. Retirez les\<caractères d’enveloppement « » et de « > `cid:`», échappez-vous à la chaîne restante et ajoutez le préfixe. Le jeu de caractères minimum suivant est requis pour un échappement par RFC1738 et RFC2396. D'autres caractères peuvent faire l'objet d'une séquence d'échappement.

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. Créez une partie MIME racine avec l'enveloppe SOAP XOP à partir de l'étape 4.

6. Écrivez les en-têtes HTTP, y compris l'en-tête HTTP Content-Type.

7. Écrivez le package MIME.

#### <a name="processing-mtom-messages"></a>Traitement des messages MTOM
Le traitement d'un message MTOM est l'inverse exact du processus décrit dans la section précédente « Génération de messages MTOM » :

1. Vérifiez que la partie MIME racine possède le `application/xop+xml` Content-type.

2. Construisez une enveloppe SOAP en analysant la partie MIME racine du package comme un document XML. L'encodage de caractères est déterminé par le paramètre `charset` du Content-type de la partie MIME racine.

3. Pour chaque élément d'information dans l'enveloppe SOAP construite, qui a comme seul membre de sa propriété [enfant] un élément d'information `xop:Include` :

    1. Supprimez le préfixe `cid:` préfixent et annulez toutes les séquences d'échappement d'URI (RFC 2396) dans la valeur de l'attribut `@href` de l'élément `xop:Include`. Enfermer la chaîne\<de résultat dans " ", ">".

    2. Localisez la partie MIME avec la valeur d'en-tête Content-ID qui correspond à la chaîne dérivée à l'étape 3a.

    3. Remplacez l'élément d'information `xop:Include` qui apparaît dans la propriété `children` de chaque élément par les éléments d'information de caractère qui représentent l'encodage Base64 canonique (voir XSD-2, 3.2.16 base64Binary) du corps d'entité de la partie MIME identifiée à l'étape 3b (remplacez l'élément d'information `xop:Include` par les données reconstruites à partir de la partie du package).

#### <a name="http-content-type-header"></a>En-tête HTTP Content-Type
Ce qui suit est une liste de clarifications WCF pour le format de l’en-tête HTTP Content-Type d’un message SOAP 1.x MTOM-encoded dérivé des exigences énoncées dans la spécification MTOM lui-même et sont dérivés de MTOM et RFC 2387.

- R4131 : un en-tête HTTP Content-Type doit avoir la valeur de multipart/related (non sensible à la casse) et ses paramètres. Les noms des paramètres ne respectent pas la casse. L'ordre des paramètres n'est pas important.

- La forme Backus-Naur (BNF) complète de l'en-tête Content-Type pour les messages MIME est répertoriée dans RFC 2045, section 5.1.

- R4132 : un en-tête Content-Type HTTP doit avoir un paramètre de type avec la valeur `application/xop+xml` comprise entre des guillemets doubles.

Bien que l’obligation d’utiliser des marques de double citation ne soit pas explicite dans RFC 2387, le\@texte observe que tous les paramètres multipartites/types de médias connexes contiennent très probablement des caractères réservés comme « « ou «/» et ont donc besoin de doubles guillemets.

- R4133 : un en-tête HTTP Content-Type doit avoir un paramètre de début avec la valeur de l'en-tête Content-ID de la partie MIME qui contient l'enveloppe SOAP 1.x, entourée de guillemets doubles. Si le paramètre de début est omis, la première partie MIME doit contenir l'enveloppe SOAP 1.x.

- R4134 : un en-tête HTTP Content-Type pour un message SOAP 1.1 encodé en MTOM doit inclure le paramètre start-info avec la valeur de texte/xml, entouré par des guillemets doubles.

- R4135 : un en-tête Content-Type HTTP pour un message SOAP 1.2 encodé en MTOM doit inclure le paramètre start-info avec la valeur de `application/soap+xml`, entre des guillemets doubles.

- R4136 : l'en-tête HTTP Content-Type d'un message SOAP 1.x encodé en MTOM doit avoir le paramètre de limite avec la valeur (entourée par des guillemets doubles) qui correspond au BNF de limite MIME défini dans RFC 2046, section 5.1.1

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     Exemples :

     CORRECT

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     CORRECT

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     INCORRECT

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a>Partie MIME d'ensemble d'informations
L'enveloppe SOAP 1.x est encapsulée comme une partie racine du package MIME XOP et est souvent appelée la partie `infoset`.

- R4141 : l'enveloppe SOAP 1.x doit être encapsulée comme une partie racine du package MIME XOP, appelée la partie `infoset` et référencée depuis le Content-Type HTTP.

- R4142 : la partie SOAP `Infoset` doit inclure les en-têtes MIME suivants : `Content-ID`, `Content-Transfer-Encoding` et `Content-Type`.

Le format de l'en-tête Content-ID est défini par RFC 2045 comme

```
"Content-ID" ":" msg-id
```

où `msg-id` est défini dans RFC 2822 (remplace RFC 822, référencé dans RFC 2045) comme :

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

et est effectivement une adresse\<e-mail enfermée dans " et " > ". Les préfixe et suffixe `[CFWS]` ont été ajoutés dans RFC 2822 pour contenir des commentaires et ne doivent pas être utilisés pour préserver l'interopérabilité.

R4143 : la valeur de l'en-tête Content-ID pour la partie MIME de l'ensemble d'informations doit suivre la production `msg-id` de RFC 2822 avec les parties `[CFWS]` préfixe et suffixe omises.

Un certain nombre de implémentations MIME\<assoupli les exigences pour la valeur incluse `absoluteURI` dans "\<et " > " d’être une adresse e-mail et utilisé enfermé dans " , ">" en plus de l’adresse e-mail. Cette version de WCF utilise des valeurs de l’en-tête Content-ID MIME du formulaire :

```
Content-ID: <http://tempuri.org/0>
```

R4144 : les processeurs MTOM doivent accepter les valeurs d'en-tête Content-ID qui correspondent au `msg-id` assoupli suivant.

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

MIME (RFC 2045) fournit l'en-tête Content-Transfer-Encoding pour communiquer l'encodage du contenu de la partie MIME. La valeur par défaut définie pour Content-Transfer-Encoding est de 7 bits, ce qui ne convient pas à la plupart des messages SOAP ; l'en-tête Content-Transfer-Encoding est donc nécessaire pour une plus grande interopérabilité :

- R4145 : la partie de l'ensemble d'informations SOAP doit contenir l'en-tête Content-Transfer-Encoding.

- R4146 : si l'encodage de caractères de l'enveloppe SOAP est UTF-8, la valeur de l'en-tête Content-Transfer-Encoding doit être de 8 bits.

- R4147 : si l'encodage de caractères de l'enveloppe SOAP est UTF-16, la valeur de l'en-tête Content-Transfer-Encoding doit être binaire.

- D'après [XOP] section 5,

- R4148: SOAP1.1 La partie Infoset doit contenir l’en-tête content-type avec application de type multimédia/xop xml et paramètres type "texte/xml" et charset

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- R4149: La partie SOAP 1.2 Infoset doit contenir `application/xop+xml` l’en-tête`application/soap+xml`Content-Type avec type multimédia et paramètres type " et `charset`.

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     Bien que XOP définisse le paramètre `charset` de manière à ce que `application/xop+xml` soit facultatif, il est exigé pour l’interopérabilité comme l’exigence BP 1.1 sur le paramètre `charset` pour le type de média `text/xml`.

- R41410 : Les paramètres `type` et `charset` doivent être présents dans l'en-tête Content-Type de la partie de l'ensemble d'informations SOAP 1.x.

#### <a name="wcf-endpoint-support-for-mtom"></a>Prise en charge des points de terminaison WCF pour MTOM
L'objectif de MTOM est d'encoder un message SOAP pour optimiser les données encodées en Base64. Les contraintes sont répertoriées dans la liste suivante :

- R4151 : tout élément d'information qui contient des données encodées en Base64 peut être optimisé.

- B4152 : WCF optimise les éléments d’information qui contiennent des données codées de base64 et dépassent 1024 octets de longueur.

Un point de terminaison WCF configuré pour utiliser MTOM enverra toujours des messages MTOM codés. Même si aucune partie ne répond aux critères requis, le message est tout de même encodé en MTOM (sérialisé comme un package MIME avec une partie MIME unique qui contient l'enveloppe SOAP).

### <a name="ws-policy-assertion-for-mtom"></a>Assertion de WS-Policy pour MTOM
WCF utilise l’affirmation de politique suivante pour indiquer l’utilisation de MTOM par point de terminaison :

```xml
<wsoma:OptimizedMimeSerialization />
```

- R4211 : l'assertion de stratégie précédente a un objet de stratégie de point de terminaison et spécifie que tous les messages envoyés et reçus depuis le point de terminaison doivent être optimisés à l'aide de MTOM.

- B4212 : Lorsqu’il est configuré pour utiliser l’optimisation MTOM, un critère `wsdl:binding`de terminaison WCF ajoute une affirmation de la politique MTOM à la stratégie attachée à la stratégie correspondante .

### <a name="composition-with-ws-security"></a>Composition avec WS-Security
MTOM est un mécanisme d’encodage qui est similaire à `text/xml` WCF Binaire XML. MTOM offre la composition naturelle avec WS-Security et d'autre protocoles WS-* : un message sécurisé à l'aide de WS-Security peut être optimisé à l'aide de MTOM.

### <a name="examples"></a>Exemples

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>Message SOAP 1.1 WCF encodé à l'aide de MTOM

```
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"
Content-Type: multipart/related;type="application/xop+xml";
              start="<http://tempuri.org/0>";start-info="text/xml";
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
Host: 131.107.72.15
Content-Length: 1501
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">
      <array>
        <xop:Include
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </array>
    </EchoBinaryAsString>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/1/632618206521093670>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
…Binary Content..
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
```

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>Message sécurisé SOAP 1.2 WCF encodé à l'aide de MTOM
Dans cet exemple, un message est encodé à l'aide de MTOM et SOAP 1.2 et protégé à l'aide de WS-Security. Les parties binaires identifiées pour l'encodage sont les contenus du `BinarySecurityToken`, `CipherValue` des `EncryptedData` correspondant à la signature chiffrée et au corps chiffré. Notez `CipherValue` que `EncryptedKey` le de la n’a pas été identifié pour l’optimisation par WCF, parce que sa longueur est moins que 1024 octets.

```
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1
Content-Type: multipart/related; type="application/xop+xml";
              start="<http://tempuri.org/0>";
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";
              start-info="application/soap+xml";
              action="http://xmlsoap.org/echoBinaryAsString"
Host: 131.107.72.15
Content-Length: 1941
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
  <s:Header>
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>
      </u:Timestamp>
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </o:BinarySecurityToken>
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>
        </e:CipherData>
      </e:EncryptedKey>
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">
        <o:SecurityTokenReference>
          <o:Reference URI="#_1"/>
        </o:SecurityTokenReference>
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>
      </c:DerivedKeyToken>
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:DataReference URI="#_3"/>
        <e:DataReference URI="#_4"/>
      </e:ReferenceList>
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:Reference URI="#_2"/>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>
          <e:CipherValue>
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
          </e:CipherValue>
        </e:CipherData>
      </e:EncryptedData>
    </o:Security>
  </s:Header>
  <s:Body u:Id="_0">
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
          <o:Reference URI="#_2"/>
        </o:SecurityTokenReference>
      </KeyInfo>
      <e:CipherData>
        <e:CipherValue>
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
        </e:CipherValue>
      </e:CipherData>
    </e:EncryptedData>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/1/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary content of BinarySecurityToken - X509 Certificate...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/2/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted primary signature...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/3/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted Body...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--
```

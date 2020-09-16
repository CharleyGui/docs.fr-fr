---
title: Guide d’interopérabilité des protocoles de services Web
ms.date: 03/30/2017
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
ms.openlocfilehash: 4169a796311c402a97358de5d52c52562b6ed357
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553172"
---
# <a name="web-services-protocols-interoperability-guide"></a>Guide d’interopérabilité des protocoles de services Web

Windows Communication Foundation (WCF) implémente un certain nombre de protocoles de services Web. Un grand nombre de ces protocoles incluent plusieurs options et points d'extensibilité qui sont laissés à la discrétion de l'implémenteur. Cette rubrique fournit une liste des protocoles de services Web implémentés par WCF. Des détails d'implémentation pour chaque protocole pris en charge sont fournis dans les autres rubriques de cette section.

## <a name="web-services-protocols-implemented-by-wcf"></a>Protocoles de services Web implémentés par WCF

WCF prend en charge les protocoles d’infrastructure WS (Web Services) via des canaux et des protocoles d’application de services Web via la fonctionnalité de contrats. L'interopérabilité pour les protocoles d'application s'effectue à l'aide des langages XSD (XML Schema Description) 1.0 et WSDL (Web Services Description Language ) 1.1.

L'interopérabilité des protocoles d'infrastructure est fournie par la famille des spécifications WS-*. Les canaux WCF assurent la prise en charge d’un certain nombre de protocoles WS- \* infrastructure. Les canaux WCF sont configurés à l’aide d’éléments de liaison. Les tableaux suivants contiennent la liste complète des protocoles WS- \* infrastructure implémentés par différents éléments de liaison WCF.

<xref:System.ServiceModel.Channels.HttpTransportBindingElement> prend en charge les spécifications présentées dans le tableau suivant :

|Spécification/document|Lien|
|-----------------------------|----------|
|HTTP 1.1|[RFC 2616](https://www.rfc-editor.org/rfc/rfc2616.txt)|
|Liaison HTTP SOAP 1.1|[Protocole SOAP (Simple Object Access Protocol) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), section 7|
|Liaison HTTP SOAP 1,2|[SOAP Version 1,2 partie 2 : complémentaire (deuxième édition)](https://www.w3.org/TR/soap12-part2/), section 7|

<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> et <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> prennent en charge les spécifications présentées dans le tableau suivant :

|Spécification/Document|Lien|
|-----------------------------|----------|
|XML|[Langage XML 1.0 (quatrième édition)](https://www.w3.org/TR/REC-xml/)|
|SOAP 1,1|[Protocole SOAP 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)|
|SOAP 1.2 Core|[SOAP version 1.2 partie 1 : Infrastructure de messagerie (deuxième édition)](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)|
|WS-Addressing 2004/08|[Adressage des services Web (WS-Addressing)](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)|
|W3C Web Services Addressing 1.0 – Éléments principaux|[Web Services Addressing 1.0 – Core](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509/)|
|W3C Web Services Addressing 1.0 – Liaison SOAP|[Web Services Addressing 1.0 – Liaison SOAP  (page pouvant être en anglais)](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509/)|
|W3C Web Services Addressing 1.0 – Liaison WSDL*|[Web Services Addressing 1.0 – Liaison WSDL (page pouvant être en anglais)](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)|
|W3C Web Services Addressing 1.0 - Métadonnées|[Web Services Addressing 1.0 - Métadonnées (page pouvant être en anglais)](https://www.w3.org/TR/ws-addr-metadata/)|
|Liaison WSDL SOAP 1.1|[WSDL (Web Services Description Language) 1.1 (page pouvant être en anglais)](https://www.w3.org/TR/wsdl/)|
|Liaison WSDL SOAP 1.2|[Extension de liaison WSDL 1.1 pour SOAP 1.2](https://www.w3.org/Submission/wsdl11soap12/)|

<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> prend en charge les spécifications présentées dans le tableau suivant :

|Spécification/document|Lien|
|-----------------------------|----------|
|XOP|[XML-binary Optimized Packaging](https://www.w3.org/TR/xop10/)|
|Liaison MTOM + SOAP1.2|[SOAP MTOM (Message Transmission Optimization Mechanism)](https://www.w3.org/TR/soap12-mtom/)|
|Liaison MTOM SOAP 1.1|[Liaison SOAP 1.1 pour MTOM 1.0](https://www.w3.org/Submission/soap11mtom10/)|
|MTOM WS-PolicyAssertions|[Assertion de stratégie de sérialisation MTOM (WS-MTOMPolicy)](https://www.w3.org/Submission/WS-MTOMPolicy/)|

<xref:System.ServiceModel.Channels.SecurityBindingElement> prend en charge les spécifications présentées dans le tableau suivant :

|Spécification/document|Lien|
|-----------------------------|----------|
|WSS : SOAP Message Security 1,0|[Web Services Security : sécurité des messages SOAP 1,0](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)|
|WSS : Username Token Profile 1.0|[Web Services Security le profil UsernameToken 1,0](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> require Password/@Type = PasswordText (valeur par défaut)|
|WSS : X.509 Token Profile 1.0|[Web Services Security X.509 Certificate Token Profile](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)|
|WSS: SAML 1.1 Token Profile 1,0|[Web Services Security : SAML Token Profile](https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf)|
|WSS : SOAP Message Security 1.1|[Sécurité de services Web : Sécurité des messages SOAP 1.1](https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf)|
|WSS Username Token Profile 1.1|[Web Services Security UsernameToken Profile 1.1](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> n'implémentez pas la dérivation de clés basée sur mot de passe ;<br /><br /> require Password/@Type = PasswordText (valeur par défaut)|
|WSS : X509 Token Profile 1.1|[Web Services Security X.509 Certificate Token Profile 1.1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)|
|WSS: Kerberos Token Profile 1.1|[Web Services Security Kerberos Token Profile 1.1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)|
|WSS: SAML 1.1 Token Profile 1.1|[Web Services Security SAML Token Profile 1.1](https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf)|
|WS-Secure Conversation|[Langage de conversation sécurisé des services Web](https://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)|
|WS-Trust 1.4 (page pouvant être en anglais)|[Langage d'approbation des services Web](https://docs.oasis-open.org/ws-sx/ws-trust/200802)|
|WS-SecurityPolicy 2005/07|[Langage de conversation sécurisé des services Web](https://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> Selon les corrections des errata soumis au comité technique OASIS WS-SX.<br /><br /> [message ws-sx](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html)|
|WS-ReliableMessaging 1.1|[Protocole de messagerie fiable version 1,1](reliable-messaging-protocol-version-1-1.md)|

<xref:System.ServiceModel.Channels.TransactionFlowBindingElement> prend en charge les spécifications présentées dans le tableau suivant :

|Spécification/Document|Lien|
|-----------------------------|----------|
|WS-Coordination|[Coordination de services Web](/previous-versions/ms951231(v=msdn.10))|
|WS-AtomicTransaction|[Transaction atomique de services Web](https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)|

Les classes  <xref:System.ServiceModel.Description.MetadataExporter>, <xref:System.ServiceModel.Description.MetadataImporter>, <xref:System.ServiceModel.Description.WsdlExporter>, <xref:System.ServiceModel.Description.WsdlImporter> et <xref:System.ServiceModel.Description.MetadataResolver> fournissent la prise en charge des spécifications de métadonnées suivantes.

- [XML Schema Part 1: Structures Second Edition](https://www.w3.org/TR/xmlschema-1/)

- [Schéma XML Partie 2 : Types de données, seconde édition](https://www.w3.org/TR/xmlschema-2/)

- [WSDL 1.1](https://www.w3.org/TR/wsdl/)

- [WS-Policy 1,2](https://www.w3.org/Submission/2006/SUBM-WS-Policy-20060425/)

- [WS-Policy 1.5](https://www.w3.org/TR/ws-policy/)

- [WS-PolicyAttachment 1.2](https://www.w3.org/Submission/2006/SUBM-WS-PolicyAttachment-20060425/)

- [WS-MetadataExchange 1.1](https://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)

- [WS-Transfer Get pour la récupération de métadonnées](https://www.w3.org/Submission/2006/SUBM-WS-Transfer-20060315/)

En outre, les profils d’interopérabilité suivants sont implémentés dans WCF :

- [Basic Profile 1.1](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html)

- [Simple SOAP Binding 1.0](http://www.ws-i.org/Profiles/SimpleSoapBindingProfile-1.0-2004-08-24.html)

- [Basic Security Profile 1.0 document non définitif](http://www.ws-i.org/Profiles/BasicSecurityProfile-1.0-2006-03-29.html)

## <a name="see-also"></a>Voir aussi

- [Protocoles de services Web pris en charge par des liaisons d’interopérabilité fournies par le système](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [Protocoles de messagerie](messaging-protocols.md)
- [Référence des schémas de contrats de données](data-contract-schema-reference.md)
- [WSDL et stratégie](wsdl-and-policy.md)
- [Protocoles de sécurité](security-protocols.md)
- [Protocole de messagerie fiable version 1.0](reliable-messaging-protocol-version-1-0.md)
- [Protocole de messagerie fiable version 1,1](reliable-messaging-protocol-version-1-1.md)
- [Protocoles de transaction](transaction-protocols.md)
- [Protocole d'échange de contexte](context-exchange-protocol.md)

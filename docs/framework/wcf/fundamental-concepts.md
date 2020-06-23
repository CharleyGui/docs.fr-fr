---
title: Concepts fondamentaux concernant Windows Communication Foundation
description: En savoir plus sur les notions de base de l’architecture de Windows Communication Foundation (WCF) avec cette explication de haut niveau.
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], concepts
- concepts [WCF]
- fundamentals [WCF]
- Windows Communication Foundation [WCF], concepts
ms.assetid: 3e7e0afd-7913-499d-bafb-eac7caacbc7a
ms.openlocfilehash: 93e75942487a1a81a8b0e8ecd8d9d666610152dc
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244672"
---
# <a name="fundamental-windows-communication-foundation-concepts"></a>Concepts fondamentaux concernant Windows Communication Foundation

Ce document fournit une vue d’ensemble de l’architecture de Windows Communication Foundation (WCF). Il vise à vous expliquer des concepts clés et la manière dont ils se combinent. Pour obtenir un didacticiel sur la création de la version la plus simple d’un client et d’un service WCF, consultez le [didacticiel prise en main](getting-started-tutorial.md). Pour découvrir la programmation WCF, consultez la page [programmation WCF de base](basic-wcf-programming.md).

## <a name="wcf-fundamentals"></a>Principes de base de WCF

WCF est un Runtime et un ensemble d’API permettant de créer des systèmes qui envoient des messages entre les services et les clients. La même infrastructure et les mêmes API sont utilisées pour créer des applications qui communiquent avec d'autres applications sur le même système informatique ou sur un système qui réside dans une autre société et accessible sur Internet.

### <a name="messaging-and-endpoints"></a>Messagerie et points de terminaison

WCF est basé sur la notion de communication basée sur les messages, et tout ce qui peut être modélisé en tant que message (par exemple, une requête HTTP ou un message Message Queuing (également appelé MSMQ)) peut être représenté de façon uniforme dans le modèle de programmation. Cela permet d'avoir une API unifiée à travers des mécanismes de transport différents.

Le modèle fait la distinction entre les _clients_, qui sont des applications qui initient la communication, et les _services_, qui sont des applications qui attendent que les clients communiquent avec eux et répondent à cette communication. Une application peut agir à la fois comme un client et comme un service. Pour obtenir des exemples, consultez [services duplex](./feature-details/duplex-services.md) et [réseau pair à pair](./feature-details/peer-to-peer-networking.md).

Les messages sont envoyés d'un point de terminaison à un autre. Les _points de terminaison_ sont des emplacements où les messages sont envoyés ou reçus (ou les deux), et ils définissent toutes les informations requises pour l’échange de messages. Un service expose un ou plusieurs points de terminaison d'application (ainsi que zéro ou plusieurs points de terminaison d'infrastructure), et le client génère un point de terminaison compatible avec l'un des points de terminaison du service.

Un _point de terminaison_ décrit de manière standard où les messages doivent être envoyés, comment ils doivent être envoyés et à quoi ressemblent les messages. Un service peut exposer ces informations en tant que métadonnées que les clients peuvent traiter pour générer les clients WCF et les _piles_de communication appropriés.

### <a name="communication-protocols"></a>Protocoles de communication

L’un des éléments requis de la pile de communication est le _protocole de transport_. Les messages peuvent être envoyés sur des intranets et sur Internet à l'aide de transports communément utilisés, tels que le HTTP et le TCP. D'autres transports inclus prennent en charge la communication avec les applications et les nœuds Message Queuing sur une maille de réseau homologue. D’autres mécanismes de transport peuvent être ajoutés à l’aide des points d’extension intégrés de WCF.

Autre élément requis dans la pile de communication : l'encodage qui spécifie comment un message donné est mis en forme. WCF fournit les encodages suivants :

- L'encodage de texte, un encodage interopérable.

- L'encodage MTOM (Message Transmission Optimisation Mécanisme), une manière interopérable d'envoyer efficacement des données binaires non structurées à destination et en provenance d'un service.

- L'encodage binaire pour un transfert efficace.

D’autres mécanismes d’encodage (par exemple, un encodage de compression) peuvent être ajoutés à l’aide des points d’extension intégrés de WCF.

### <a name="message-patterns"></a>Modèles de messages

WCF prend en charge plusieurs modèles de messagerie, y compris la communication demande-réponse, unidirectionnelle et duplex. Les différents transports prennent en charge des modèles de messagerie différents, ce qui affecte les types d’interactions qu’ils prennent en charge. Les API et le runtime WCF vous aident également à envoyer des messages de manière sécurisée et fiable.

## <a name="wcf-terms"></a>Termes de WCF

Les autres concepts et termes utilisés dans la documentation WCF sont les suivants :

**Message**  
 Unité autonome de données qui peut se composer de plusieurs parties, y compris d'un corps et d'un en-tête.

**Service**  
 Construction qui expose un ou plusieurs points de terminaison, chacun de ces derniers exposant une ou plusieurs opérations de service.

**Point de terminaison**  
 Construction à laquelle les messages sont envoyés ou de laquelle ils sont reçus (ou les deux). Il comprend un emplacement (une adresse) qui définit où les messages peuvent être envoyés, une spécification du mécanisme de communication (une liaison) qui décrit la façon dont les messages doivent être envoyés et une définition pour un ensemble de messages qui peuvent être envoyés ou reçus (ou les deux) à cet emplacement (un contrat de service) qui décrit le message qui peut être envoyé.

Un service WCF est exposé au monde extérieur comme une collection de points de terminaison.

**Point de terminaison d’application**  
 Point de terminaison exposé par l'application et qui correspond à un contrat de service implémenté par l'application.

**Point de terminaison d’infrastructure**  
 Point de terminaison exposé par l'infrastructure pour faciliter les fonctionnalités qui sont exigées ou sont fournies par le service qui n'est pas en rapport avec un contrat de service. Par exemple, un service peut avoir un point de terminaison d'infrastructure qui fournit des informations de métadonnées.

**Adresse**  
 Spécifie l'emplacement de réception des messages. Elle est indiquée comme un URI (Uniform Resource Identifier). La partie schématique de l'URI nomme le mécanisme de transport à utiliser pour atteindre l'adresse, tel que HTTP et TCP. La partie hiérarchique de l'URI contient un emplacement unique dont le format dépend du mécanisme de transport.

L'adresse de point de terminaison vous permet de créer des adresses uniques pour chaque point de terminaison d'un service, ou dans certaines conditions, de faire partager une adresse à plusieurs points de terminaison. L'exemple suivant représente une adresse qui fait appel au protocole HTTPS avec un port non défini par défaut :

```http
HTTPS://cohowinery:8005/ServiceModelSamples/CalculatorService
```

**Liant**  
 Définit la façon dont un point de terminaison communique avec le monde. Elle est construite à l'aide d'un ensemble de composants appelés éléments de liaison qui « s'empilent » les uns sur les autres pour créer l'infrastructure de communication. Au minimum, une liaison définit le transport (HTTP ou TCP par exemple) et l'encodage utilisés (tel que texte ou binaire). Une liaison peut contenir des éléments de liaison qui spécifient des informations détaillées comme les mécanismes de sécurité utilisés pour sécuriser les messages, ou le modèle de message utilisé par un point de terminaison. Pour plus d’informations, consultez [Configuration des services](configuring-services.md).

**Élément de liaison**  
 Représente un composant particulier de la liaison, tel qu’un transport, un encodage, une implémentation d’un protocole au niveau de l’infrastructure (comme WS-ReliableMessaging) ou tout autre composant de la pile de communication.

**comportements**  
 Composant qui contrôle plusieurs aspects de l'exécution d'un service, d'un point de terminaison, d'une opération particulière ou d'un client. Les comportements sont groupés en fonction de leur portée : les comportements courants affectent tous les points de terminaison globalement, les comportements de service affectent uniquement des aspects relatifs à un service, les comportements de point de terminaison affectent uniquement des propriétés connexes à un point de terminaison, et les comportements au niveau de l'opération affectent des opérations particulières. Par exemple, le comportement de service « limitation » spécifie comment un service réagit lorsqu'un trop grand nombre de messages menace de submerger ses fonctions de traitement. Un comportement de point de terminaison, en revanche, contrôle uniquement les aspects pertinents aux points de terminaison, par exemple comment et où rechercher une information d'identification de sécurité.

**Liaisons fournies par le système**  
 WCF inclut plusieurs liaisons fournies par le système. Il s'agit de collections d'éléments de liaison optimisés pour des scénarios spécifiques. Par exemple, le <xref:System.ServiceModel.WSHttpBinding> est conçu pour l’interopérabilité avec les services qui implémentent différentes \* spécifications WS. Ces liaisons prédéfinies vous font gagner du temps en vous présentant uniquement les options qui peuvent être appliquées correctement au scénario spécifique. Si une liaison prédéfinie ne satisfait pas vos spécifications, vous pouvez créer votre propre liaison personnalisée.

**Configuration et codage**  
 Le contrôle d'une application peut être réalisé par l'encodage, par la configuration, ou par les deux. La configuration a l'avantage de permettre à quelqu'un d'autre que le développeur (par exemple, un administrateur réseau) de définir les paramètres de client et de service après que le code a été écrit et sans devoir le recompiler. La configuration vous permet non seulement de définir des valeurs comme des adresses de point de terminaison, mais aussi de procéder à un contrôle approfondi en vous permettant d'ajouter des points de terminaison, des liaisons et des comportements. L'encodage permet au développeur de conserver un contrôle étroit sur tous les composants du service ou client, et tous les paramètres définis par la configuration peuvent être inspectés et si besoin être remplacés par le code.

**Opération de service**  
 Procédure définie dans le code d'un service qui implémente les fonctionnalités d'une opération. Cette opération est exposée aux clients de la même manière que le sont les méthodes sur un client WCF. La méthode peut renvoyer une valeur et accepter un nombre facultatif d’arguments, ou n’accepter aucun argument et ne renvoyer aucune réponse. Par exemple, une opération qui fonctionne comme un simple « Bonjour » peut être utilisée comme notification de la présence d'un client et pour commencer une série d'opérations.

**Contrat de service**  
 Joint plusieurs opérations connexes dans une unité fonctionnelle unique. Il peut définir des paramètres au niveau du service, tels que l'espace de noms du service, un contrat de rappel correspondant et d'autres paramètres de ce type. Dans la plupart des cas, le contrat est défini en créant une interface dans le langage de programmation de votre choix et en appliquant l'attribut <xref:System.ServiceModel.ServiceContractAttribute> à l'interface. Le code de service réel résulte de l'implémentation de l'interface.

**Contrat d'opération**  
 Un contrat d'opération définit les paramètres et le type de retour d'une opération. Lorsque vous créez une interface qui définit le contrat de service, vous indiquez un contrat d'opération en appliquant l'attribut <xref:System.ServiceModel.OperationContractAttribute> à chaque définition de méthode qui fait partie du contrat. Les opérations peuvent être conçues de manière à prendre un message unique et à renvoyer un message unique, ou à prendre un jeu de types et à renvoyer un type. Dans ce cas, le système détermine le format des messages qui doivent être échangés pour cette opération.

**Contrat de message**  
 Décrit le format d'un message. Par exemple, il déclare si les éléments du message doivent entrer dans les en-têtes au lieu du corps, quel niveau de sécurité doit être appliqué à quels éléments du message, et ainsi de suite.

**Contrat d’erreur**  
 Peut être associé à une opération de service pour désigner des erreurs qui peuvent être renvoyées à l'appelant. Une opération peut être associée à plusieurs erreurs ou n'être associée à aucune erreur. Ces erreurs sont des erreurs SOAP modélisées comme des exceptions dans le modèle de programmation.

**Contrat de données**  
 Descriptions dans les métadonnées des types de données utilisés par un service. Cela permet à d'autres d'interagir avec le service. Les types de données peuvent être utilisés dans n’importe quelle partie d’un message, par exemple comme paramètres ou types de retour. Si le service n'utilise que des types simples, l'utilisation explicite des contrats de données est inutile.

**Hosting**  
 Un service doit être hébergé dans un processus. Un _hôte_ est une application qui contrôle la durée de vie du service. Les services peuvent être auto-hébergés ou gérés par un processus d'hébergement existant.

**Service auto-hébergé**  
 Service qui s'exécute dans une application de processus créée par le développeur. Ce dernier définit les propriétés du service, contrôle sa durée de vie, ouvre le service (ce qui le définit en mode d'écoute) et le ferme.

**Processus d’hébergement**  
 Application conçue pour héberger des services. Ces derniers incluent les services IIS (Internet Information Services), les services WAS (Windows Activation Services) et les services Windows. Dans ces scénarios hébergés, l'hôte contrôle la durée de vie du service. Par exemple, vous pouvez installer un répertoire virtuel qui contient l'assembly de service et le fichier de configuration à l'aide d'IIS. Lorsqu'un message est reçu, IIS démarre le service et contrôle sa durée de vie.

**Instancing**  
 Un service dispose d'un modèle d'instanciation. Il existe trois modèles d'instanciation : « unique », dans lequel un objet CLR unique prend en charge tous les clients ; « par appel », dans lequel un nouvel objet CLR est créé pour gérer chaque appel du client ; et « par session », dans lequel un ensemble d'objets CLR est créé, un pour chaque session. Le choix d’un modèle d’instanciation dépend des spécifications de l’application et du modèle d’utilisation attendu du service.

**Application cliente**  
 Programme qui échange des messages avec un ou plusieurs points de terminaison. L'application cliente commence par créer l'instance d'un client WCF et appelle les méthodes de ce client. Il est important de noter qu'une même application peut être à la fois un client et un service.

**Channel**  
 Implémentation concrète d'un élément de liaison. La liaison représente la configuration, et le canal est l’implémentation associée à cette configuration. Par conséquent, un canal est associé à chaque élément de liaison. Les canaux s’empilent les uns sur les autres pour créer l’implémentation concrète de la liaison : la pile de canaux.

**Client WCF (WCF client)**  
 Construction d’application cliente qui expose les opérations de service en tant que méthodes (dans le langage de programmation .NET Framework de votre choix, comme Visual Basic ou Visual C#). N'importe quelle application peut accueillir un client WCF, y compris une application hébergeant un service. Par conséquent, il est possible de créer un service qui inclut des clients WCF d'autres services.

Un client WCF peut être généré automatiquement à l’aide de l' [outil utilitaire de métadonnées ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) et en le faisant pointer sur un service en cours d’exécution qui publie des métadonnées.

**Métadonnées**  
 Dans un service, décrivent les caractéristiques du service qu'une entité externe doit comprendre pour communiquer avec ce service. Les métadonnées peuvent être consommées par l' [outil ServiceModel Metadata Utility (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer un client WCF et la configuration associée qu’une application cliente peut utiliser pour interagir avec le service.

Les métadonnées exposées par le service incluent des documents de schéma XML qui définissent le contrat de données du service, et des documents WSDL qui décrivent les méthodes du service.

En cas d'activation, les métadonnées du service sont générées automatiquement par WCF par inspection du service et de ses points de terminaison. Pour publier les métadonnées d'un service, vous devez explicitement activer le comportement des métadonnées.

**Sécurité**  
 Dans WCF, comprend la confidentialité (chiffrement des messages pour empêcher l’espionnage), l’intégrité (la détection de la falsification du message), l’authentification (la validation des serveurs et des clients) et l’autorisation (le contrôle de l’accès aux ressources). Ces fonctions sont fournies par l’utilisation de mécanismes de sécurité existants, tels que TLS sur HTTP (également appelé HTTPs), ou en implémentant une ou plusieurs des diverses spécifications WS- \* Security.

**Mode de sécurité du transport**  
 Spécifie que la confidentialité, l'intégrité et l'authentification sont assurées par les mécanismes de la couche de transport (tels que HTTPS). Lors de l'utilisation d'un transport comme le HTTPS, ce mode a l'avantage d'être efficace en termes de performances, et d'être bien compris grâce à sa prédominance sur Internet. L’inconvénient est que ce type de sécurité est appliqué séparément sur chaque saut dans la voie de communication, et rend la communication susceptible d’être victime d’une attaque de « l’homme du milieu ».

**Mode de sécurité des messages**  
 Spécifie que la sécurité est fournie en implémentant une ou plusieurs des spécifications de sécurité, telles que la spécification nommée [Web Services Security : sécurité des messages SOAP](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf). Chaque message contient les mécanismes nécessaires pour assurer la sécurité pendant son transit et permettre aux récepteurs de détecter la falsification et de déchiffrer le message. En ce sens, la sécurité est encapsulée dans chaque message, en assurant la sécurité de bout en bout sur des sauts multiples. Étant donné que les informations de sécurité deviennent une partie du message, il est également possible d’inclure plusieurs types d’informations d’identification avec le message (ils sont appelés « _revendications_»). Cette approche a également l'avantage de permettre au message de voyager en toute sécurité sur n'importe quel transport, y compris les transports multiples, entre son origine et sa destination. L'inconvénient de cette approche réside dans la complexité des mécanismes de chiffrement employés, ce qui affecte les performances.

**Transport avec le mode de sécurité des informations d’identification de message**  
 Spécifie l'utilisation de la couche de transport pour assurer la confidentialité, l'authentification et l'intégrité des messages, tandis que chacun des messages peut contenir plusieurs informations d'identification (revendications) requises par les récepteurs du message.

**Web\***  
 Abrégé pour l'ensemble croissant des spécifications de services Web (WS), telles que WS-Security, WS-ReliableMessaging et ainsi de suite, implémentées dans WCF.

## <a name="see-also"></a>Voir aussi

- [Présentation de Windows Communication Foundation](whats-wcf.md)
- [Architecture Windows Communication Foundation](architecture.md)

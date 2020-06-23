---
title: Présentation de Windows Communication Foundation
description: En savoir plus sur le Windows Communication Foundation, qui est une infrastructure pour la création d’applications orientées service.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: 84cb45d62409769a79fa6a401fdb1aa6934c4099
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245607"
---
# <a name="what-is-windows-communication-foundation"></a>Présentation de Windows Communication Foundation
Windows Communication Foundation (WCF) est une infrastructure permettant de créer des applications orientées service. À l’aide de WCF, vous pouvez envoyer des données sous forme de messages asynchrones d’un point de terminaison de service à un autre. Un point de terminaison de service peut faire partie d'un service disponible en continu et hébergé par IIS, ou il peut s'agir d'un service hébergé dans une application. Un point de terminaison peut être un client d'un service qui demande des données auprès d'un point de terminaison de service. Les messages peuvent être simplement constitués d'un caractère ou d'un mot unique envoyé au format XML, ou se présenter sous la forme d'un flux de données binaires plus complexe. Voici quelques exemples de scénarios :

- Service sécurisé pour traiter des transactions commerciales.

- Service qui fournit des données actuelles à d'autres services, comme un rapport sur le trafic ou tout autre service de surveillance.

- Service de conversation qui permet à deux personnes de communiquer ou d'échanger des données en temps réel.

- Application de tableau de bord qui interroge les données d'un ou de plusieurs services et les présente de manière logique.

- Exposition d'un workflow implémenté à l'aide de Windows Workflow Foundation en tant que service WCF.

- Application Silverlight pour interroger un service afin d'obtenir les flux de données les plus récents.

Alors que la création d’applications de ce type était possible avant l’existence de WCF, WCF rend le développement des points de terminaison plus facile que jamais. En résumé, WCF est conçu pour offrir une approche gérable pour la création de services Web et de clients de service Web.

## <a name="features-of-wcf"></a>Fonctions de WCF

WCF comprend l’ensemble de fonctionnalités suivant. Pour plus d’informations, consultez [Détails des fonctionnalités WCF](./feature-details/index.md).

- **Orientation services**

     L’une des conséquences de l’utilisation des normes WS est que WCF vous permet de créer des applications *orientées service* . L'architecture orientée services (SOA, Service-Oriented Architecture) dépend de services Web pour envoyer et recevoir des données. Les services présentent l'avantage d'être faiblement couplés, au lieu d'être encodés de manière irréversible d'une application à une autre. Une relation faiblement couplée implique que tout client créé sur une plate-forme peut se connecter à n'importe quel service, dans la mesure où les contrats essentiels sont respectés.

- **Interopérabilité**

     WCF implémente des normes industrielles modernes pour l’interopérabilité des services Web. Pour plus d’informations sur les normes prises en charge, consultez [interopérabilité et intégration](./feature-details/interoperability-and-integration.md).

- **Modèles de messages variés**

     Les messages sont échangés selon l'un des différents modèles disponibles. Le modèle le plus courant est de type demande/réponse, dans lequel un point de terminaison demande des données auprès d'un second point de terminaison. Le second point de terminaison répond. Il existe d'autres modèles, comme un message unidirectionnel dans lequel un seul point de terminaison envoie un message sans attendre de réponse. Le modèle d'échange en duplex constitue un modèle plus complexe dans la mesure où deux points de terminaison établissent une connexion et envoient des données de part et d'autre, à la manière d'un programme de messagerie instantanée. Pour plus d’informations sur la façon d’implémenter différents modèles d’échange de messages à l’aide de WCF, consultez [contrats](./feature-details/contracts.md).

- **Métadonnées de service**

     WCF prend en charge la publication de métadonnées de service à l’aide de formats spécifiés dans les normes du secteur telles que WSDL, le schéma XML et WS-Policy. Ces métadonnées peuvent être utilisées pour générer et configurer automatiquement des clients pour l’accès aux services WCF. Les métadonnées peuvent être publiées via HTTP et HTTPS ou à l'aide de la norme d'échange de métadonnées de service Web. Pour plus d’informations, consultez [métadonnées](./feature-details/metadata.md).

- **Contrats de données**

     Étant donné que WCF est construit à l’aide de la .NET Framework, il comprend également des méthodes conviviales de code pour fournir les contrats que vous souhaitez appliquer. Le contrat de données représente l'un des types universels de contrats. Par nature, lorsque vous codez votre service à l'aide de Visual C# ou de Visual Basic, la méthode la plus simple de gérer les données consiste à créer des classes qui représentent une entité de données dotée de propriétés. WCF comprend un système complet permettant d’utiliser les données de cette manière simple. Une fois que vous avez créé les classes qui représentent les données, votre service génère automatiquement les métadonnées qui permettent aux clients de se conformer aux types de données que vous avez conçus. Pour plus d’informations, consultez [utilisation de contrats de données](feature-details/using-data-contracts.md).

- **Sécurité**

     Les messages peuvent être chiffrés afin de protéger la confidentialité. Par ailleurs, vous pouvez demander aux utilisateurs de s'authentifier avant de pouvoir recevoir des messages. La sécurité peut être implémentée à l'aide de normes célèbres, telles que SSL ou WS-SecureConversation. Pour plus d’informations, consultez [Sécurité](./feature-details/security.md).

- **Transports et encodages variés**

     Les messages peuvent être envoyés via l'un des différents encodages et protocoles de transport intégrés. Le protocole et l’encodage les plus courants consiste à envoyer des messages SOAP encodés en texte à l’aide du protocole HTTP (HyperText Transfer Protocol) pour une utilisation sur le World Wide Web. WCF vous permet également d’envoyer des messages via TCP, les canaux nommés ou MSMQ. Ces messages peuvent être encodés en tant que texte ou à l'aide d'un format binaire optimisé.  Les données binaires peuvent être envoyées efficacement à l'aide de la norme MTOM. Si aucun des transports ou encodages fournis ne convient à vos besoins, vous avez la possibilité de créer votre propre encodage ou transport personnalisé. Pour plus d’informations sur les transports et les encodages pris en charge par WCF, consultez [transports](./feature-details/transports.md).

- **Messages fiables et mis en file d'attente**

     WCF prend en charge l’échange de messages fiables à l’aide de sessions fiables implémentées via WS-Reliable Messaging et à l’aide de MSMQ. Pour plus d’informations sur la prise en charge de la messagerie fiable et en file d’attente dans WCF, consultez [files d’attente et sessions fiables](./feature-details/queues-and-reliable-sessions.md).

- **Messages durables**

     Un message durable est un message qui n'est jamais perdu suite à une interruption de la communication. Les messages conformes au modèle de message durable sont toujours enregistrés dans une base de données. En cas d'interruption, la base de données vous permet de reprendre l'échange de messages une fois la connexion restaurée. Vous pouvez également créer un message durable à l’aide de l’Windows Workflow Foundation (WF). Pour plus d’informations, consultez [services de flux de travail](./feature-details/workflow-services.md).

- **Transactions**

     WCF prend également en charge les transactions à l’aide de l’un des trois modèles de transaction : WS-AtomicTransactions, les API de l' <xref:System.Transactions> espace de noms et Microsoft Distributed Transaction Coordinator. Pour plus d’informations sur la prise en charge des transactions dans WCF, consultez [transactions](./feature-details/transactions-in-wcf.md).

- **Prise en charge d'AJAX et de REST**

     REST est un exemple d'une technologie évoluant vers le Web 2.0. WCF peut être configuré pour traiter des données XML « ordinaires » qui ne sont pas encapsulées dans une enveloppe SOAP. WCF peut également être étendu pour prendre en charge des formats XML spécifiques, tels qu’ATOM (une norme RSS populaire), et même des formats non XML, tels que les JavaScript Object Notation (JSON).

- **Extensibilité**

     L’architecture WCF a un certain nombre de points d’extensibilité. Si une capacité supplémentaire est requise, il existe un certain nombre de points d'entrée qui vous permettent de personnaliser le comportement d'un service. Pour plus d’informations sur les points d’extensibilité disponibles, consultez [extension de WCF](./extending/index.md).

## <a name="wcf-integration-with-other-microsoft-technologies"></a>Intégration WCF avec d'autres technologies Microsoft

WCF est une plateforme flexible. En raison de cette flexibilité extrême, WCF est également utilisé dans plusieurs autres produits Microsoft. En comprenant les principes fondamentaux de WCF, vous bénéficiez d’un avantage immédiat si vous utilisez également l’un de ces produits.

La première technologie à coupler avec WCF était la Windows Workflow Foundation (WF). Les workflows simplifient le développement d’applications en encapsulant les étapes du workflow comme des « activités ». Dans la première version de Windows Workflow Foundation, un développeur devait créer un hôte pour le Workflow. La prochaine version de Windows Workflow Foundation a été intégrée à WCF. Cela permettait à n’importe quel flux de travail d’être facilement hébergé dans un service WCF. Pour ce faire, vous pouvez choisir automatiquement le type de projet WF/WCF dans Visual Studio 2012 ou version ultérieure.

Microsoft BizTalk Server R2 utilise également WCF comme technologie de communication. BizTalk a été conçu pour recevoir et transformer des données d'un format standardisé en un autre. Les messages doivent être remis dans leur boîte de message centrale, où ils peuvent être transformés suivant un mappage strict ou à l'aide de l'une des fonctionnalités BizTalk, telles que le moteur de workflow. BizTalk peut désormais utiliser l’adaptateur LOB (Line of Business) WCF pour remettre les messages à la boîte de message.

Microsoft Silverlight est une plate-forme de création d'applications Web enrichies interopérables qui permettent aux développeurs de créer des sites Web comportant de nombreux médias (tels que la vidéo en continu). Depuis la version 2, Silverlight a intégré WCF en tant que technologie de communication pour connecter les applications Silverlight aux points de terminaison WCF.

Les fonctionnalités d’hébergement du serveur d’applications Windows Server AppFabric sont spécifiquement conçues pour le déploiement et la gestion d’applications qui utilisent WCF pour la communication. Les fonctionnalités d’hébergement incluent des outils enrichis et des options de configuration spécifiquement conçues pour les applications compatibles WCF.

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel>
- [Concepts fondamentaux de Windows Communication Foundation](fundamental-concepts.md)
- [Architecture Windows Communication Foundation](architecture.md)
- [Conseils et bonnes pratiques](guidelines-and-best-practices.md)
- [Didacticiel Prise en main](getting-started-tutorial.md)
- [Guide de la documentation](guide-to-the-documentation.md)
- [Programmation WCF de base](basic-wcf-programming.md)
- [Exemples Windows Communication Foundation](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751514%28v=vs.90%29)

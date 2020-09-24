---
title: Communication de service à service
description: Découvrez comment les microservices dorsaux Cloud-natives communiquent avec d’autres microservices back-end.
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 9761b99cd9ad076eb82a23a00ec3099e8913168b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166077"
---
# <a name="service-to-service-communication"></a>Communication de service à service

En passant par le client frontal, nous adressons maintenant les microservices back-end à communiquer entre eux.

Lors de la construction d’une application Cloud native, vous souhaiterez être sensible à la façon dont les services principaux communiquent entre eux. Dans l’idéal, la communication entre les services est moins efficace. Toutefois, l’évitement n’est pas toujours possible, car les services principaux s’appuient souvent sur un autre pour effectuer une opération.

Il existe plusieurs approches largement acceptées pour implémenter la communication entre les services. Le *type d’interaction de communication* détermine souvent la meilleure approche.

Tenez compte des types d’interaction suivants :

- *Requête* : lorsqu’un microservice appelant requiert une réponse d’un microservice appelé, par exemple « Bonjour, je me donne les informations de l’acheteur pour un ID client donné ».

- *Commande* : lorsque le microservice appelant a besoin d’un autre microservice pour exécuter une action, mais ne nécessite pas de réponse, par exemple « Bonjour, expédiez cette commande ».

- *Événement* : lorsqu’un microservice, appelé serveur de publication, déclenche un événement indiquant que l’État a changé ou qu’une action a eu lieu. D’autres microservices, appelés abonnés, peuvent réagir à l’événement de manière appropriée. Le serveur de publication et les abonnés ne sont pas conscients l’un de l’autre.

Les systèmes de microservices utilisent généralement une combinaison de ces types d’interaction lors de l’exécution d’opérations nécessitant une interaction entre les services. Jetons un coup d’œil à chacun et à la façon dont vous pouvez les implémenter.

## <a name="queries"></a>Requêtes

Bien souvent, un microservice peut avoir besoin d' *interroger* un autre, ce qui nécessite une réponse immédiate pour effectuer une opération. Un microservice de panier d’achat peut nécessiter des informations sur le produit et un prix pour ajouter un article à son panier. Il existe plusieurs approches pour implémenter des opérations de requête.

### <a name="requestresponse-messaging"></a>Messagerie demande/réponse

L’une des options d’implémentation de ce scénario est que le microservice appelant principal effectue des requêtes HTTP directes aux microservices qu’il doit interroger, comme illustré à la figure 4-8.

![Communication HTTP directe](./media/direct-http-communication.png)

**Figure 4-8**. Communication HTTP directe

Bien que les appels HTTP directs entre les microservices soient relativement simples à implémenter, il convient de veiller à réduire cette pratique. Pour démarrer, ces appels sont toujours *synchrones* et bloquent l’opération jusqu’à ce qu’un résultat soit retourné ou que la demande arrive à expiration. Ce qui était une fois autonome, les services indépendants, capables d’évoluer indépendamment et de le déployer fréquemment, sont désormais couplés entre eux. En ce qui concerne l’augmentation des microservices, leurs avantages architecturaux diminuent.

L’exécution d’une requête peu fréquente qui effectue un appel HTTP unique vers un autre microservice peut être acceptable pour certains systèmes. Toutefois, les appels de volume élevé qui appellent des appels HTTP directs à plusieurs microservices ne sont pas conseillés. Ils peuvent augmenter la latence et avoir un impact négatif sur les performances, l’évolutivité et la disponibilité de votre système. Pire encore, une longue série de communications HTTP directes peut entraîner des chaînes complexes et complexes d’appels de microservices synchrones, comme illustré à la figure 4-9 :

![Chaînage des requêtes HTTP](./media/chaining-http-queries.png)

**Figure 4-9**. Chaînage des requêtes HTTP

Vous pouvez certainement imaginer le risque dans la conception présentée dans l’image précédente. Que se passe-t-il si l’étape \# 3 échoue ? Ou l’étape \# 8 échoue-t-elle ? Comment voulez-vous récupérer ? Que se passe \# -t-il si l’étape 6 est lente parce que le service sous-jacent est occupé ? Comment continuer ? Même si tout fonctionne correctement, pensez à la latence de cet appel, qui correspond à la somme de la latence de chaque étape.

Le grand degré de couplage dans l’image précédente suggère que les services n’ont pas été modélisés de manière optimale. Il appartient l’équipe à revisiter sa conception.

### <a name="materialized-view-pattern"></a>Modèle de vue matérialisée

Une option courante pour supprimer le couplage de microservices est le [modèle de vue matérialisée](/azure/architecture/patterns/materialized-view). Avec ce modèle, un microservice stocke sa propre copie locale dénormalisée des données détenues par d’autres services. Au lieu que le microservice du panier d’achat interroge le catalogue de produits et les microservices de tarification, il gère sa propre copie locale de ces données. Ce modèle élimine le couplage inutile et améliore la fiabilité et le temps de réponse. La totalité de l’opération s’exécute à l’intérieur d’un processus unique. Nous explorons ce modèle et les autres problèmes liés aux données dans le chapitre 5.

### <a name="service-aggregator-pattern"></a>Modèle d’agrégateur de service

Une autre option permettant d’éliminer le couplage microservice à microservice est un [microservice d’agrégation](https://devblogs.microsoft.com/cesardelatorre/designing-and-implementing-api-gateways-with-ocelot-in-a-microservices-and-container-based-architecture/), illustré en violet dans la figure 4-10.

![Service d’agrégation](./media/aggregator-service.png)

**Figure 4-10**. Microservice de l’agrégateur

Le modèle isole une opération qui effectue des appels à plusieurs microservices back-end, en centralisant sa logique dans un microservice spécialisé.  Le microservice de l’agrégateur de l’extraction violette dans la figure précédente orchestre le flux de travail pour l’opération d’extraction. Il comprend des appels à plusieurs microservices principaux dans un ordre séquencé. Les données du workflow sont agrégées et retournées à l’appelant. Bien qu’elle implémente toujours des appels HTTP directs, le microservice de l’agrégateur réduit les dépendances directes entre les microservices back-end.

### <a name="requestreply-pattern"></a>Modèle de demande/réponse

Une autre approche pour découpler les messages HTTP synchrones est un [modèle demande-réponse](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RequestReply.html), qui utilise la communication de la mise en file d’attente. La communication à l’aide d’une file d’attente est toujours un canal unidirectionnel, avec un producteur qui envoie le message et le consommateur le recevant. Avec ce modèle, une file d’attente de demandes et une file d’attente de réponses sont implémentées, comme illustré dans la figure 4-11.

![Modèle demande-réponse](./media/request-reply-pattern.png)

**Figure 4-11**. Modèle demande-réponse

Ici, le producteur de message crée un message basé sur une requête qui contient un ID de corrélation unique et le place dans une file d’attente de demandes. Le service consommateur replace les messages dans la file d’attente, les traite et place la réponse dans la file d’attente de réponses avec le même ID de corrélation. Le service de producteur met le message en file d’attente, le met en correspondance avec l’ID de corrélation et continue le traitement. Nous abordons les files d’attente en détail dans la section suivante.

## <a name="commands"></a>Commandes

Un autre type d’interaction de communication est une *commande*. Un microservice peut avoir besoin d’un autre microservice pour effectuer une action. Le microservice de commande peut avoir besoin du microservice d’expédition pour créer une livraison pour un ordre approuvé. Dans la figure 4-12, un microservice, appelé producteur, envoie un message à un autre microservice, le consommateur, en le commandant pour effectuer une opération.

![Interaction de commande avec une file d’attente](./media/command-interaction-with-queue.png)

**Figure 4-12**. Interaction de commande avec une file d’attente

Le plus souvent, le producteur ne nécessite pas de réponse et peut *déclencher et oublier* le message. Si une réponse est nécessaire, le consommateur envoie un message séparé au producteur sur un autre canal. Un message de commande est le mieux envoyé de façon asynchrone avec une file d’attente de messages. pris en charge par un courtier de messages léger. Dans le diagramme précédent, Notez comment une file d’attente sépare et découple les deux services.

Une file d’attente de messages est une construction intermédiaire par le biais de laquelle un producteur et un consommateur transmettent un message. Les files d’attente implémentent un modèle de messagerie point à point asynchrone. Le producteur sait à quel endroit une commande doit être envoyée et est acheminée de manière appropriée. La file d’attente garantit qu’un message est traité par une seule instance de consommateur qui lit à partir du canal. Dans ce scénario, le service producteur ou le service consommateur peut monter en charge sans affecter l’autre. De même, les technologies peuvent être disparates de chaque côté, ce qui signifie que le microservice Java peut appeler un microservice [Golang](https://golang.org) .

Dans le chapitre 1, nous avons parlé des *services de stockage*. Les services de stockage sont des ressources auxiliaires dont dépendent les systèmes natifs du Cloud. Les files d’attente de messages sont des services de stockage. Le Cloud Azure prend en charge deux types de files d’attente de messages que vos systèmes natifs du Cloud peuvent utiliser pour implémenter la messagerie de commandes : les files d’attente de stockage Azure et les files d’attente de Azure Service Bus.

### <a name="azure-storage-queues"></a>files d’attente de stockage Azure

Les files d’attente de stockage Azure offrent une infrastructure de mise en file d’attente simple, rapide et abordable, avec les comptes de stockage Azure.

Les [files d’attente de stockage Azure](/azure/storage/queues/storage-queues-introduction) disposent d’un mécanisme de mise en file d’attente Rest avec une messagerie fiable et persistante. Ils fournissent un ensemble de fonctionnalités minimal, mais sont peu coûteux et stockent des millions de messages. Leur capacité est allant jusqu’à 500 to. Un message peut avoir une taille maximale de 64 Ko.

Vous pouvez accéder aux messages de n’importe où dans le monde via des appels authentifiés à l’aide du protocole HTTP ou HTTPs. Les files d’attente de stockage peuvent évoluer vers un grand nombre de clients simultanés pour gérer les pics de trafic.

Cela dit, il existe des limitations au service :

- L’ordre des messages n’est pas garanti.

- Un message peut uniquement être conservé pendant sept jours avant d’être automatiquement supprimé.

- La prise en charge de la gestion d’État, de la détection des doublons ou des transactions n’est pas disponible.

La figure 4-13 illustre la hiérarchie d’une file d’attente de stockage Azure.

![Hiérarchie de file d’attente de stockage](./media/storage-queue-hierarchy.png)

**Figure 4-13**. Hiérarchie de file d’attente de stockage

Dans la figure précédente, notez la manière dont les files d’attente de stockage stockent leurs messages dans le compte de stockage Azure sous-jacent.

Pour les développeurs, Microsoft fournit plusieurs bibliothèques côté client et côté serveur pour le traitement de la file d’attente de stockage. La plupart des principales plateformes sont prises en charge, y compris .NET, Java, JavaScript, Ruby, Python et Go. Les développeurs ne doivent jamais communiquer directement avec ces bibliothèques. Cela a pour effet de coupler étroitement votre code de microservice à la service de File d’attente de stockage Azure. Il est recommandé d’isoler les détails d’implémentation de l’API. Introduisez une couche d’intermédiation, ou API intermédiaire, qui expose des opérations génériques et encapsule la bibliothèque concrète. Ce couplage faible vous permet de permuter un service de mise en file d’attente pour un autre sans avoir à apporter de modifications au code du service de la principale.

Les files d’attente de stockage Azure sont une option économique pour implémenter la messagerie de commandes dans vos applications Cloud natives. En particulier, lorsqu’une taille de file d’attente dépasse 80 Go, ou un ensemble de fonctionnalités simple est acceptable. Vous payez uniquement pour le stockage des messages ; Il n’y a pas de frais fixes à l’heure fixe.

### <a name="azure-service-bus-queues"></a>Files d’attente Azure Service Bus

Pour des exigences de messagerie plus complexes, envisagez Azure Service Bus files d’attente.

Au-dessus d’une infrastructure de messages robuste, [Azure Service bus](/azure/service-bus-messaging/service-bus-messaging-overview) prend en charge un *modèle de messagerie*répartie. Les messages sont stockés de manière fiable dans un répartiteur (la file d’attente) jusqu’à leur réception par le consommateur. La file d’attente garantit la remise des messages premier entré/premier sorti (FIFO), en respectant l’ordre dans lequel les messages ont été ajoutés à la file d’attente.

La taille d’un message peut être plus importante, jusqu’à 256 Ko. Les messages sont conservés dans la file d’attente pendant une durée illimitée. Service Bus prend en charge non seulement les appels basés sur HTTP, mais fournit également une prise en charge complète du [protocole AMQP](/azure/service-bus-messaging/service-bus-amqp-overview). AMQP est une norme ouverte pour les fournisseurs qui prend en charge un protocole binaire et de plus hauts niveaux de fiabilité.

Service Bus fournit un ensemble complet de fonctionnalités, notamment la [prise en charge des transactions](/azure/service-bus-messaging/service-bus-transactions) et une [fonctionnalité de détection des doublons](/azure/service-bus-messaging/duplicate-detection). La file d’attente garantit « au plus une fois la remise » par message. Il ignore automatiquement un message qui a déjà été envoyé. Si un producteur est incertain, il peut renvoyer le même message et Service Bus garantit qu’une seule copie sera traitée. La détection des doublons vous évite d’avoir à créer des mécanismes d’infrastructure supplémentaires.

Deux autres fonctionnalités d’entreprise sont le partitionnement et les sessions. Une file d’attente de Service Bus conventionnelle est gérée par un seul courtier de messages et stockée dans une seule banque de messages. Toutefois, le [partitionnement service bus](/azure/service-bus-messaging/service-bus-partitioning) répartit la file d’attente entre plusieurs courtiers de messages et banques de messages. Le débit global n’est plus limité par les performances d’un seul courtier de messages ou d’une seule banque de messagerie. Une panne temporaire d’une banque de messagerie ne rend pas une file d’attente partitionnée indisponible.

Les [Sessions service bus](https://codingcanvas.com/azure-service-bus-sessions/) offrent un moyen de regrouper les messages liés à. Imaginez un scénario de flux de travail dans lequel les messages doivent être traités ensemble et l’opération se termine à la fin. Pour tirer parti, les sessions doivent être activées explicitement pour la file d’attente et chaque message associé doit contenir le même ID de session.

Toutefois, il existe quelques inconvénients importants : la taille de Service Bus files d’attente est limitée à 80 Go, ce qui est bien plus petit que ce qui est disponible dans les files d’attente du magasin. En outre, Service Bus files d’attente impliquent un coût de base et une facturation par opération.

La figure 4-14 présente l’architecture de haut niveau d’une file d’attente de Service Bus.

![File d’attente Service Bus](./media/service-bus-queue.png)

**Figure 4-14**. File d’attente Service Bus

Dans l’illustration précédente, notez la relation point à point. Deux instances du même fournisseur empilent des messages dans une file d’attente de Service Bus unique. Chaque message est consommé par une seule des trois instances de consommateur à droite. Ensuite, nous expliquons comment implémenter la messagerie dans laquelle les différents consommateurs peuvent être intéressés par le même message.

## <a name="events"></a>Événements

Message Queuing est un moyen efficace d’implémenter une communication dans laquelle un producteur peut envoyer un message de manière asynchrone à un consommateur. Toutefois, que se passe-t-il lorsque de *nombreux consommateurs* sont intéressés par le même message ? Une file d’attente de messages dédiée pour chaque consommateur n’est pas bien adaptée et devient difficile à gérer.

Pour traiter ce scénario, nous allons passer au troisième type d’interaction de message, l' *événement*. Un microservice annonce qu’une action s’est produite. D’autres microservices, s’ils le souhaitent, réagissent à l’action ou à l’événement.

L’événement est un processus en deux étapes. Pour un changement d’État donné, un microservice publie un événement dans un courtier de messages, ce qui le rend disponible pour tout autre microservice intéressé. Le microservice intéressé est averti en s’abonnant à l’événement dans le courtier de messages. Vous utilisez le modèle de [publication/abonnement](/azure/architecture/patterns/publisher-subscriber) pour implémenter la [communication basée sur les événements](/dotnet/standard/microservices-architecture/multi-container-microservice-net-applications/integration-event-based-microservice-communications).

La figure 4-15 montre un microservice de panier d’achat publiant un événement avec deux autres microservices s’abonnant à ce dernier.

![Messagerie pilotée par les événements](./media/event-driven-messaging.png)

**Figure 4-15**. Messagerie pilotée par les événements

Notez le composant *bus d’événements* qui se trouve au milieu du canal de communication. Il s’agit d’une classe personnalisée qui encapsule le courtier de messages et le dissocie de l’application sous-jacente. Les microservices de classement et d’inventaire opèrent indépendamment l’événement sans aucune connaissance de l’un l’autre, ni le microservice du panier d’achat. Lorsque l’événement Registered est publié dans le bus d’événements, il agit sur celui-ci.

Avec l’événement, nous passons de la technologie de mise en file d’attente aux *rubriques*. Une [rubrique](/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions) est semblable à une file d’attente, mais prend en charge un modèle de messagerie un-à-plusieurs. Un microservice publie un message. Plusieurs microservices d’abonnement peuvent choisir de recevoir et d’agir sur ce message. La figure 4-16 illustre une architecture de rubrique.

![Architecture des rubriques](./media/topic-architecture.png)

**Figure 4-16**. Architecture des rubriques

Dans la figure précédente, les éditeurs envoient des messages à la rubrique. À la fin, les abonnés reçoivent des messages des abonnements. Au milieu, la rubrique transfère les messages aux abonnements en fonction d’un ensemble de règles, affichées dans des zones bleu foncé. Les règles agissent comme un filtre qui transfère des messages spécifiques à un abonnement. Ici, un événement « GetPrice » est envoyé au prix et aux abonnements de journalisation lorsque l’abonnement à la journalisation a choisi de recevoir tous les messages.  Un événement « GetInformation » est envoyé aux informations et aux abonnements de journalisation.

Le Cloud Azure prend en charge deux services de rubrique différents : Azure Service Bus rubriques et Azure EventGrid.

### <a name="azure-service-bus-topics"></a>Rubriques Azure Service Bus

Sur le même modèle de message répartie robuste de Azure Service Bus files d’attente se trouvent [Azure Service bus rubriques](/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Une rubrique peut recevoir des messages de plusieurs éditeurs indépendants et envoyer des messages à jusqu’à 2 000 abonnés. Les abonnements peuvent être ajoutés ou supprimés de manière dynamique au moment de l’exécution sans arrêter le système ou recréer la rubrique.

De nombreuses fonctionnalités avancées des files d’attente Azure Service Bus sont également disponibles pour les rubriques, notamment la [détection des doublons](/azure/service-bus-messaging/duplicate-detection) et la [prise en charge des transactions](/azure/service-bus-messaging/service-bus-transactions). Par défaut, les rubriques de Service Bus sont gérées par un seul courtier de messages et stockées dans une seule banque de messages. Toutefois, [service bus le partitionnement](/azure/service-bus-messaging/service-bus-partitioning) met à l’échelle une rubrique en la répartissant entre plusieurs courtiers de messages et banques de messages.

La [remise planifiée des messages](/azure/service-bus-messaging/message-sequencing) marque un message avec un temps de traitement spécifique. Le message ne s’affiche pas dans la rubrique avant ce moment. Le [Report de message](/azure/service-bus-messaging/message-deferral) vous permet de différer une récupération d’un message à un moment ultérieur. Les deux sont couramment utilisés dans les scénarios de traitement de workflow où les opérations sont traitées dans un ordre particulier. Vous pouvez différer le traitement des messages reçus jusqu’à ce que le travail précédent soit terminé.

Service Bus rubriques sont une technologie robuste et éprouvée permettant d’activer la communication de publication/abonnement dans vos systèmes natifs dans le Cloud.

### <a name="azure-event-grid"></a>Azure Event Grid

Bien que Azure Service Bus soit un courtier de messagerie testé avec un ensemble complet de fonctionnalités d’entreprise, [Azure Event Grid](/azure/event-grid/overview) est le nouvel enfant du bloc.

À première vue, Event Grid peut se présenter comme un autre système de messagerie basé sur des rubriques. Toutefois, il est différent de nombreuses façons. Axé sur les charges de travail pilotées par les événements, il permet le traitement d’événements en temps réel, l’intégration Azure profonde et une infrastructure ouverte et complète sur une infrastructure sans serveur. Il est conçu pour les applications Cloud natives et sans serveur.

En tant que *fond de panier des événements*centralisés, Event Grid réagit aux événements dans les ressources Azure et à partir de vos propres services.

Les notifications d’événements sont publiées dans une rubrique Event Grid qui, à son tour, achemine chaque événement à un abonnement. Les abonnés sont mappés aux abonnements et consomment les événements. Comme Service Bus, Event Grid prend en charge un *modèle d’abonné filtré* dans lequel un abonnement définit une règle pour les événements qu’il souhaite recevoir. Event Grid fournit un débit rapide avec une garantie de 10 millions événements par seconde permettant une livraison presque en temps réel, bien plus que ce que Azure Service Bus peut générer.

Un point idéal pour Event Grid est son intégration profonde dans la structure de l’infrastructure Azure. Une ressource Azure, telle que Cosmos DB, peut publier des événements intégrés directement dans d’autres ressources Azure intéressées, sans nécessiter de code personnalisé. Event Grid pouvez publier des événements à partir d’un abonnement, d’un groupe de ressources ou d’un service Azure, ce qui permet aux développeurs de contrôler précisément le cycle de vie des ressources du Cloud. Toutefois, Event Grid n’est pas limité à Azure. Il s’agit d’une plateforme ouverte qui peut consommer des événements HTTP personnalisés publiés à partir d’applications ou de services tiers et acheminer les événements vers des abonnés externes.

Lors de la publication et de l’abonnement aux événements natifs à partir des ressources Azure, aucun codage n’est requis. Avec une configuration simple, vous pouvez intégrer des événements d’une ressource Azure à une autre, en tirant parti des fonctionnalités intégrées pour les rubriques et les abonnements. La figure 4-17 illustre l’anatomie de Event Grid.

![Event Grid anatomie](./media/event-grid-anatomy.png)

**Figure 4-17**. Event Grid anatomie

La principale différence entre EventGrid et Service Bus est le *modèle d’échange de messages*sous-jacent.

Service Bus implémente un modèle d' *extraction* de style plus ancien dans lequel l’abonné en aval interroge activement l’abonnement aux nouveaux messages. À l’envers, cette approche permet à l’abonné d’avoir un contrôle total sur le rythme de traitement des messages. Il contrôle le moment et le nombre de messages à traiter à un moment donné. Les messages non lus restent dans l’abonnement jusqu’à ce qu’ils soient traités. Une lacune importante est la latence entre le moment où l’événement est généré et l’opération d’interrogation qui extrait ce message à l’abonné pour traitement. En outre, la surcharge liée à l’interrogation constante pour l’événement suivant consomme des ressources et de l’argent.

EventGrid, toutefois, est différent. Il implémente un *modèle push* dans lequel les événements sont envoyés aux EventHandlers comme étant reçus, ce qui permet une remise d’événements en temps quasi-réel. Cela réduit également les coûts lorsque le service est déclenché uniquement lorsqu’il est nécessaire de consommer un événement, pas en permanence comme avec l’interrogation. Cela dit, un gestionnaire d’événements doit gérer la charge entrante et fournir des mécanismes de limitation afin de se protéger contre le risque de saturation. De nombreux services Azure qui consomment ces événements, tels que Azure Functions et Logic Apps fournissent des fonctionnalités de mise à l’échelle automatique pour gérer des charges accrues.  

Event Grid est un service Cloud sans serveur entièrement géré. Elle est mise à l’échelle dynamiquement en fonction de votre trafic et vous facture uniquement pour votre utilisation réelle, et non pour une capacité préachetée. Les 100 000 premières opérations par mois sont gratuites : les opérations sont définies comme entrée d’événement (notifications d’événements entrantes), tentatives de remise d’abonnement, appels de gestion et filtrage par objet. Avec une disponibilité de 99,99%, EventGrid garantit la remise d’un événement au cours d’une période de 24 heures, avec la fonctionnalité de nouvelle tentative intégrée pour la remise en échec. Les messages non remis peuvent être déplacés vers une file d’attente de lettres mortes pour la résolution.  Contrairement à Azure Service Bus, Event Grid est réglé pour des performances rapides et ne prend pas en charge les fonctionnalités telles que la messagerie, les transactions et les sessions ordonnées.

### <a name="streaming-messages-in-the-azure-cloud"></a>Diffusion en continu de messages dans le Cloud Azure

Azure Service Bus et Event Grid offrent une excellente prise en charge des applications qui exposent des événements simples et discrets tels qu’un nouveau document a été inséré dans un Cosmos DB. Mais, que se passe-t-il si votre système Cloud natif doit traiter un *flux d’événements connexes*? Les [flux d’événements](/archive/msdn-magazine/2015/february/microsoft-azure-the-rise-of-event-stream-oriented-systems) sont plus complexes. Ils sont généralement classés dans le temps, interdépendants et doivent être traités en tant que groupe.

[Azure Event Hub](https://azure.microsoft.com/services/event-hubs/) est une plateforme de diffusion de données et un service d’ingestion d’événements qui collecte, transforme et stocke des événements. Il est affiné pour capturer les données de streaming, telles que les notifications d’événements continus émises à partir d’un contexte de télémétrie. Le service est hautement évolutif et peut stocker et [traiter des millions d’événements par seconde](/azure/event-hubs/event-hubs-about). Comme illustré à la figure 4-18, il s’agit souvent d’une porte d’entrée pour un pipeline d’événements, ce qui permet de découpler le flux de réception de la consommation d’événements.

![Azure Event Hub](./media/azure-event-hub.png)

**Figure 4-18**. Azure Event Hub

Event Hub prend en charge la faible latence et la durée de rétention configurable. Contrairement aux files d’attente et aux rubriques, Event Hubs conserver les données d’événement après qu’elles ont été lues par un consommateur. Cette fonctionnalité permet à d’autres services d’analyse de données, internes et externes, de relire les données pour une analyse plus poussée. Les événements stockés dans Event Hub sont supprimés uniquement à l’expiration de la période de rétention, ce qui correspond à un jour par défaut, mais configurable.

Event Hub prend en charge les protocoles de publication d’événements courants, notamment HTTPs et AMQP. Il prend également en charge Kafka 1,0. Les [applications Kafka existantes peuvent communiquer avec Event Hub](/azure/event-hubs/event-hubs-for-kafka-ecosystem-overview) à l’aide du protocole Kafka, qui offre une alternative à la gestion des clusters Kafka volumineux. De nombreux systèmes Cloud natifs Open source intègrent Kafka.

Event Hubs implémente la diffusion de messages via un [modèle de consommateur partitionné](/azure/event-hubs/event-hubs-features) dans lequel chaque consommateur lit uniquement un sous-ensemble spécifique, ou partition, du flux de message. Ce modèle permet de disposer d'une échelle horizontale considérable pour le traitement des événements, et offre d'autres fonctionnalités axées sur le flux, qui ne sont pas disponibles dans les rubriques et les files d'attente. Une partition est une séquence ordonnée d’événements qui est conservée dans un concentrateur d’événements. Les événements les plus récents sont ajoutés à la fin de cette séquence.La figure 4-19 illustre le partitionnement dans un hub d’événements.

![Partitionnement de hub d’événements](./media/event-hub-partitioning.png)

**Figure 4-19**. Partitionnement de hub d’événements

Au lieu de lire à partir de la même ressource, chaque groupe de consommateurs lit sur un sous-ensemble, ou sur une partition, du flux de message.

Pour les applications Cloud natives qui doivent diffuser en continu un grand nombre d’événements, Azure Event Hub peut être une solution robuste et abordable.

>[!div class="step-by-step"]
>[Précédent](front-end-communication.md) 
> [Suivant](grpc.md)

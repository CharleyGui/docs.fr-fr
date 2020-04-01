---
title: Communication service-service
description: Découvrez comment les microservices natifs du cloud en arrière communiquent avec d’autres microservices back-end.
author: robvet
ms.date: 09/09/2019
ms.openlocfilehash: 926be3c2eb4513c89ebcd1f31dceb7d58639dc6f
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523559"
---
# <a name="service-to-service-communication"></a>Communication service-service

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

En passant du client front-end, nous nous attaquons maintenant aux microservices back-end communiquer les uns avec les autres.

Lors de la construction d’une application cloud-native, vous voudrez être sensible à la façon dont les services back-end communiquent les uns avec les autres. Idéalement, moins il y a de communication interspède, mieux c’est. Cependant, l’évitement n’est pas toujours possible car les services back-end comptent souvent les uns sur les autres pour effectuer une opération.

Il existe plusieurs approches largement acceptées pour mettre en œuvre la communication interseuvre. Le *type d’interaction de communication* déterminera souvent la meilleure approche.

Considérez les types d’interaction suivants :

- *Requête* - quand un microservice d’appel nécessite une réponse d’un microservice appelé, tel que, "Hey, donnez-moi les informations de l’acheteur pour un client donné Id."

- *Commandez* - lorsque le microservice d’appel a besoin d’un autre microservice pour exécuter une action, mais ne nécessite pas de réponse, comme, "Hey, il suffit d’expédier cet ordre."

- *Événement* - quand un microservice, appelé l’éditeur, soulève un événement que l’état a changé ou une action a eu lieu. D’autres microservices, appelés abonnés, qui sont intéressés, peuvent réagir de façon appropriée à l’événement. L’éditeur et les abonnés ne sont pas au courant l’un de l’autre.

Les systèmes de microservice utilisent généralement une combinaison de ces types d’interaction lors de l’exécution d’opérations qui nécessitent une interaction interservices. Examinons de près chacun d’eux et comment vous pourriez les mettre en œuvre.

## <a name="queries"></a>Requêtes

Plusieurs fois, un microservice peut avoir besoin de *poser des questions* à un autre, nécessitant une réponse immédiate pour terminer une opération. Un microservice de panier d’achat peut avoir besoin d’informations sur le produit et d’un prix pour ajouter un article à son panier. Il existe un certain nombre d’approches pour la mise en œuvre des opérations de requête.

### <a name="requestresponse-messaging"></a>Demande/messagerie d’intervention

Une option pour la mise en œuvre de ce scénario est que le microservice de retour à appel fasse des demandes directes de HTTP aux microservices qu’il doit interroger, indiqué dans la figure 4-8.

![Communication directe HTTP](./media/direct-http-communication.png)

**Figure 4-8**. Communication directe HTTP

Bien que les appels directs de HTTP entre les microservices soient relativement simples à mettre en œuvre, il faut faire attention à minimiser cette pratique. Pour commencer, ces appels sont toujours *synchrones* et bloqueront l’opération jusqu’à ce qu’un résultat soit retourné ou que les délais de demande soient dépassés. Ce qui était autrefois autonome, des services indépendants, capables d’évoluer indépendamment et de se déployer fréquemment, deviennent maintenant couplés les uns aux autres. À mesure que le couplage entre les microservices augmente, leurs avantages architecturaux diminuent.

L’exécution d’une demande peu fréquente qui fait un seul appel direct HTTP à un autre microservice pourrait être acceptable pour certains systèmes. Cependant, les appels à volume élevé qui invoquent des appels HTTP directs vers plusieurs microservices ne sont pas recommandés. Ils peuvent augmenter la latence et avoir un impact négatif sur les performances, l’évolutivité et la disponibilité de votre système. Pire encore, une longue série de communications directes http://HTTP peut mener à des chaînes profondes et complexes d’appels synchrones de microservices, indiqués dans la figure 4-9 :

![Enchaîner les requêtes HTTP](./media/chaining-http-queries.png)

**Figure 4-9**. Enchaîner les requêtes HTTP

Vous pouvez certainement imaginer le risque dans la conception montrée dans l’image précédente. Que se \#passe-t-il si l’étape 3 échoue ? Ou \#l’étape 8 échoue? Comment vous rétablissez-vous? Que se \#passe-t-il si l’étape 6 est lente parce que le service sous-jacent est occupé? Comment continuez-vous? Même si tout fonctionne correctement, pensez à la latence que cet appel encourrait, qui est la somme de la latence de chaque étape.

Le grand degré de couplage dans l’image précédente suggère que les services n’ont pas été modélisé de façon optimale. Il incomberait à l’équipe de revoir leur conception.

### <a name="materialized-view-pattern"></a>Modèle de vue matérialisée

Une option populaire pour enlever le couplage de microservice est le [modèle de vue matérialisée.](https://docs.microsoft.com/azure/architecture/patterns/materialized-view) Avec ce modèle, un microservice stocke sa propre copie locale et dénormalisée des données qui appartiennent à d’autres services. Au lieu de la microservice Shopping Basket interrogeant le catalogue de produits et les microservices de tarification, il conserve sa propre copie locale de ces données. Ce modèle élimine le couplage inutile et améliore la fiabilité et le temps de réponse. L’ensemble de l’opération s’exécute à l’intérieur d’un seul processus. Nous explorons ce modèle et d’autres préoccupations en matière de données au chapitre 5.

### <a name="service-aggregator-pattern"></a>Modèle d’agrégateur de service

Une autre option pour éliminer le couplage microservice-microservice est [un microservice d’agrégateur,](https://devblogs.microsoft.com/cesardelatorre/designing-and-implementing-api-gateways-with-ocelot-in-a-microservices-and-container-based-architecture/)indiqué en violet dans la figure 4-10.

![Service d’agrégateur](./media/aggregator-service.png)

**Figure 4-10**. Microservice d’agrégateur

Le modèle isole une opération qui fait des appels à plusieurs microservices back-end, centralisant sa logique dans un microservice spécialisé.  Le microservice d’agrégateur de caisse violet dans la figure précédente orchestre le flux de travail pour l’opération de caisse. Il comprend des appels vers plusieurs microservices back-end dans un ordre séquent. Les données du flux de travail sont agrégées et retournées à l’appelant. Bien qu’il implémente toujours des appels HTTP directs, le microservice d’agrégateur réduit les dépendances directes parmi les microservices back-end.

### <a name="requestreply-pattern"></a>Modèle de demande/réponse

Une autre approche pour découpler les messages HTTP synchrones est un [modèle de demande-réponse](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RequestReply.html), qui utilise la communication en file d’attente. La communication à l’aide d’une file d’attente est toujours un canal à sens unique, avec un producteur qui envoie le message et le consommateur qui le reçoit. Avec ce modèle, une file d’attente de demande et une file d’attente de réponse sont mises en œuvre, indiquées dans la figure 4-11.

![Modèle de demande-réponse](./media/request-reply-pattern.png)

**Figure 4-11**. Modèle de demande-réponse

Ici, le producteur de message crée un message basé sur la requête qui contient une pièce d’identité de corrélation unique et le place dans une file d’attente de demande. Le service de consommation déqueue les messages, le traite et place la réponse dans la file d’attente de réponse avec le même ID de corrélation. Le service de production déqueue le message, l’associe à l’ID de corrélation et continue le traitement. Nous couvrons les files d’attente en détail dans la section suivante.

## <a name="commands"></a>Commandes

Un autre type d’interaction de communication est une *commande*. Un microservice peut avoir besoin d’un autre microservice pour effectuer une action. Le microservice de commande peut avoir besoin du microservice d’expédition pour créer un envoi pour une commande approuvée. Dans la figure 4-12, un microservice, appelé producteur, envoie un message à un autre microservice, le consommateur, lui or commandant de faire quelque chose.

![Interaction de commande avec une file d’attente](./media/command-interaction-with-queue.png)

**Figure 4-12**. Interaction de commande avec une file d’attente

Le plus souvent, le producteur n’a pas besoin d’intervention et peut *allumer et oublier* le message. Si une réponse est nécessaire, le consommateur envoie un message distinct au producteur sur un autre canal. Un message de commande est mieux envoyé asynchrone avec une file d’attente de message. soutenu par un courtier de messages légers. Dans le diagramme précédent, notez comment une file d’attente sépare et découple les deux services.

Une file d’attente de message est une construction intermédiaire par laquelle un producteur et un consommateur passent un message. Les files d’attente implémentent un modèle de messagerie asynchrone, point à point. Le producteur sait où une commande doit être envoyée et les itinéraires appropriés. La file d’attente garantit qu’un message est traité par exactement l’un des cas de consommateurs qui lisent à partir du canal. Dans ce scénario, le fournisseur ou le service aux consommateurs peut s’étendre sans affecter l’autre. En outre, les technologies peuvent être disparates de chaque côté, ce qui signifie que nous pourrions avoir un microservice Java appelant un microservice [Golang.](https://golang.org)

Dans le chapitre 1, nous avons parlé *de services de soutien*. Les services de soutien sont des ressources accessoires dont dépendent les systèmes cloud-autochtones. Les files d’attente de messages sont des services de soutien. Le cloud Azure prend en charge deux types de files d’attente de messages que vos systèmes cloud-native peuvent consommer pour implémenter la messagerie de commande : Azure Storage Queues et Azure Service Bus Queues.

### <a name="azure-storage-queues"></a>Files d’attente Stockage Azure

Les files d’attente de stockage Azure offrent une infrastructure de file d’attente simple qui est rapide, abordable, et soutenu par des comptes de stockage Azure.

[Azure Storage Queues](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction) dispose d’un mécanisme de file d’attente basé sur REST avec messagerie fiable et persistante. Ils fournissent un ensemble de fonctionnalités minimales, mais sont peu coûteux et stockent des millions de messages. Leur capacité va jusqu’à 500 TB. Un seul message peut être jusqu’à 64 KB de taille.

Vous pouvez accéder à des messages de n’importe où dans le monde via des appels authentifiés à l’aide de HTTP ou HTTPS. Les files d’attente de stockage peuvent s’étendre à un grand nombre de clients simultanés pour gérer les pics de trafic.

Cela dit, il y a des limites au service :

- L’ordre de message n’est pas garanti.

- Un message ne peut persister que sept jours avant d’être automatiquement supprimé.

- Le support pour la gestion de l’État, la détection en double ou les transactions n’est pas disponible.

La figure 4-13 montre la hiérarchie d’une file d’attente de stockage Azure.

![Hiérarchie des files d’attente de stockage](./media/storage-queue-hierarchy.png)

**Figure 4-13**. Hiérarchie des files d’attente de stockage

Dans le chiffre précédent, notez comment les files d’attente de stockage stockent leurs messages dans le compte de stockage Azure sous-jacent.

Pour les développeurs, Microsoft fournit plusieurs bibliothèques client et serveur pour le traitement des files d’attente de stockage. La plupart des principales plates-formes sont prises en charge, y compris .NET, Java, JavaScript, Ruby, Python et Go. Les développeurs ne doivent jamais communiquer directement avec ces bibliothèques. Cela permettra de coupler étroitement votre code de microservice au service Azure Storage Queue. C’est une meilleure pratique pour isoler les détails de mise en œuvre de l’API. Introduire une couche d’intermédiation, ou API intermédiaire, qui expose les opérations génériques et encapsule la bibliothèque en béton. Ce couplage lâche vous permet d’échanger un service de file d’attente contre un autre sans avoir à apporter des modifications au code de service principal.

Les files d’attente Azure Storage sont une option économique pour implémenter la messagerie de commande dans vos applications cloud-native. Surtout quand une taille de file d’attente dépassera 80 Go, ou un ensemble de fonctionnalité simple est acceptable. Vous ne payez que pour le stockage des messages; il n’y a pas de frais horaires fixes.

### <a name="azure-service-bus-queues"></a>Files d’attente Azure Service Bus

Pour des exigences de messagerie plus complexes, envisagez les files d’attente Azure Service Bus.

Assis au sommet d’une infrastructure de message robuste, [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) prend en charge un *modèle de messagerie négocié.* Les messages sont stockés de façon fiable dans un courtier (la file d’attente) jusqu’à ce qu’ils soient reçus par le consommateur. La file d’attente garantit la livraison de messages First-In/First-Out (FIFO), en respectant l’ordre dans lequel les messages ont été ajoutés à la file d’attente.

La taille d’un message peut être beaucoup plus grande, jusqu’à 256 KB. Les messages persistent dans la file d’attente pendant une période illimitée. Service Bus prend en charge non seulement les appels basés sur HTTP, mais fournit également un soutien complet pour le [protocole AMPQ](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-amqp-overview). AMPQ est un standard ouvert entre les fournisseurs qui prend en charge un protocole binaire et des degrés de fiabilité plus élevés.

Service Bus fournit un riche ensemble de fonctionnalités, y compris [le support transactionnel](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions) et une [fonction de détection en double](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection). La file d’attente garantit « tout au plus une fois la livraison » par message. Il rejette automatiquement un message qui a déjà été envoyé. Si un producteur est en doute, il peut renvoyer le même message, et Service Bus garantit qu’une seule copie sera traitée. La détection en double vous empêche d’avoir à construire une plomberie d’infrastructure supplémentaire.

Deux autres fonctionnalités d’entreprise sont le partage et les sessions. Une file d’attente de service classique est gérée par un seul courtier de messages et stockée dans un seul magasin de messages. Mais, [Service Bus Partitioning](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) répartit la file d’attente entre plusieurs courtiers de messages et les magasins de messages. Le débit global n’est plus limité par les performances d’un courtier de messages ou d’un magasin de messagerie unique. Une panne temporaire d’un magasin de messagerie ne rend pas une file d’attente cloisonnée indisponible.

[Les sessions d’autobus](https://codingcanvas.com/azure-service-bus-sessions/) de service offrent un moyen de messages liés au groupe. Imaginez un scénario de flux de travail où les messages doivent être traités ensemble et l’opération terminée à la fin. Pour en profiter, les sessions doivent être explicitement activées pour la file d’attente et chaque message connexe doit contenir la même pièce d’identité de session.

Cependant, il ya quelques mises en garde importantes: La taille des files d’attente De bus de service est limitée à 80 Go, ce qui est beaucoup plus petit que ce qui est disponible dans les files d’attente des magasins. De plus, les files d’attente d’autobus de service entraînent un coût de base et des frais par opération.

La figure 4-14 décrit l’architecture de haut niveau d’une file d’attente d’autobus de service.

![File d’attente Service Bus](./media/service-bus-queue.png)

**Figure 4-14**. File d’attente Service Bus

Dans le chiffre précédent, notez la relation point-à-point. Deux cas du même fournisseur sont enqueuing messages dans une file d’attente d’autobus de service unique. Chaque message est consommé par seulement un des trois cas de consommateurs sur la droite. Ensuite, nous discutons de la façon de mettre en œuvre la messagerie où différents consommateurs peuvent tous être intéressés par le même message.

## <a name="events"></a>Événements

La file d’attente de message est un moyen efficace de mettre en œuvre la communication où un producteur peut envoyer asnchronement un message à un consommateur. Cependant, que se passe-t-il lorsque *de nombreux consommateurs différents* s’intéressent au même message? Une file d’attente de messages dédiée pour chaque consommateur ne serait pas bien échelle et deviendrait difficile à gérer.

Pour résoudre ce scénario, nous passons au troisième type d’interaction de message, *l’événement*. Un microservice annonce qu’une action a eu lieu. D’autres microservices, s’ils sont intéressés, réagissent à l’action ou à l’événement.

L’événementiel est un processus en deux étapes. Pour un changement d’état donné, un microservice publie un événement à un courtier de messages, le rendant disponible à tout autre microservice intéressé. Le microservice intéressé est avisé en s’abonnant à l’événement dans le courtier en messages. Vous utilisez le modèle [Publier/Abonnez-vous](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) pour mettre en œuvre [la communication basée sur l’événement](https://docs.microsoft.com/dotnet/standard/microservices-architecture/multi-container-microservice-net-applications/integration-event-based-microservice-communications).

La figure 4-15 montre un microservice de panier d’achats publiant un événement avec deux autres microservices qui s’y abonnent.

![Messagerie axée sur l’événement](./media/event-driven-messaging.png)

**Figure 4-15**. Messagerie axée sur l’événement

Notez la composante *d’autobus événementiel* qui se trouve au milieu du canal de communication. Il s’agit d’une classe personnalisée qui encapsule le courtier en message et le découple de l’application sous-jacente. Les microservices de commande et d’inventaire exploitent indépendamment l’événement sans connaissance les uns des autres, ni le microservice de panier d’achat. Lorsque l’événement enregistré est publié dans l’autobus de l’événement, ils agissent sur elle.

Avec l’événementiel, nous passons de la technologie de file d’attente à *des sujets*. Un [sujet](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions) est similaire à une file d’attente, mais prend en charge un modèle de messagerie unique à plusieurs. Un microservice publie un message. Plusieurs microservices abonnés peuvent choisir de recevoir et d’agir sur ce message. La figure 4-16 montre une architecture de sujet.

![Architecture thématique](./media/topic-architecture.png)

**Figure 4-16**. Architecture thématique

Dans le chiffre précédent, les éditeurs envoient des messages sur le sujet. À la fin, les abonnés reçoivent des messages d’abonnements. Au milieu, le sujet transmet les messages aux abonnements basés sur un ensemble de *règles,* indiquées dans des boîtes bleu foncé. Les règles agissent comme un filtre qui transmet des messages spécifiques à un abonnement. Ici, un événement "CreateOrder" serait \#envoyé à \#l’abonnement 1 \#et l’abonnement 3, mais pas à l’abonnement 2. Un événement "OrderCompleted" serait \#envoyé à \#l’abonnement 2 et à l’abonnement 3.

Le cloud Azure prend en charge deux services thématiques différents : Azure Service Bus Topics et Azure EventGrid.

### <a name="azure-service-bus-topics"></a>Rubriques Azure Service Bus

Assis au-dessus du même modèle de message négocié robuste des files d’attente Azure Service Bus sont [Azure Service Bus Topics](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Un sujet peut recevoir des messages de plusieurs éditeurs indépendants et envoyer des messages à jusqu’à 2 000 abonnés. Les abonnements peuvent être ajoutés ou supprimés dynamiquement au moment de l’exécution sans arrêter le système ou recréer le sujet.

De nombreuses fonctionnalités avancées des files d’attente Azure Service Bus sont également disponibles pour des sujets, y compris [la détection du double](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection) et le support [transactionnel](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions). Par défaut, les sujets de Service Bus sont traités par un seul courtier de messages et stockés dans un seul magasin de messages. Mais, [Service Bus Partitioning](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) échelles un sujet en le répartissant à travers de nombreux courtiers de messages et les magasins de messages.

[La livraison de messages planifiée](https://docs.microsoft.com/azure/service-bus-messaging/message-sequencing) identifie un message avec un temps spécifique pour le traitement. Le message n’apparaîtra pas dans le sujet avant cette date. [Le report de message](https://docs.microsoft.com/azure/service-bus-messaging/message-deferral) vous permet de reporter une récupération d’un message à une date ultérieure. Les deux sont couramment utilisés dans les scénarios de traitement des flux de travail où les opérations sont traitées dans un ordre particulier. Vous pouvez reporter le traitement des messages reçus jusqu’à ce que les travaux antérieurs soient terminés.

Les sujets de Service Bus sont une technologie robuste et éprouvée permettant de publier/s’abonner à la communication dans vos systèmes cloud-natives.

### <a name="azure-event-grid"></a>Azure Event Grid

Alors qu’Azure Service Bus est un courtier de messagerie éprouvé au combat avec un ensemble complet de fonctionnalités d’entreprise, [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) est le nouveau gamin sur le bloc.

À première vue, Event Grid peut ressembler à un autre système de messagerie thématique. Cependant, c’est différent à bien des égards. Axé sur les charges de travail axées sur les événements, il permet le traitement d’événements en temps réel, une intégration Azure profonde et une plate-forme ouverte - le tout sur l’infrastructure sans serveur. Il est conçu pour les applications contemporaines natives du cloud et sans serveur

En tant *qu’avion de fond*centralisé, ou tuyau, Event Grid réagit aux événements à l’intérieur des ressources Azure et de vos propres services.

Les notifications d’événements sont publiées sur un sujet de grille d’événements, qui, à son tour, achemine chaque événement vers un abonnement. Les abonnés cartographient les abonnements et consomment les événements. Comme Service Bus, Event Grid prend en charge un *modèle d’abonné filtré* où un abonnement fixe la règle des événements qu’il souhaite recevoir. Event Grid offre un débit rapide avec une garantie de 10 millions d’événements par seconde permettant une livraison en temps quasi réel - beaucoup plus que ce que Azure Service Bus peut générer.

Un point faible pour Event Grid est son intégration profonde dans le tissu de l’infrastructure Azure. Une ressource Azure, comme Cosmos DB, peut publier des événements intégrés directement à d’autres ressources Azure intéressées - sans avoir besoin de code personnalisé. Event Grid peut publier des événements à partir d’un abonnement Azure, d’un groupe de ressources ou d’un service, ce qui donne aux développeurs un contrôle limité sur le cycle de vie des ressources cloud. Cependant, Event Grid ne se limite pas à Azure. Il s’agit d’une plate-forme ouverte qui peut consommer des événements HTTP personnalisés publiés à partir d’applications ou de services tiers et d’itinéraires à des abonnés externes.

Lors de la publication et de l’abonnement à des événements autochtones à partir de ressources Azure, aucun codage n’est nécessaire. Avec une configuration simple, vous pouvez intégrer des événements d’une ressource Azure à une autre en tirant parti de la plomberie intégrée pour les sujets et les abonnements. La figure 4-17 montre l’anatomie de Event Grid.

![Anatomie de grille d’événements](./media/event-grid-anatomy.png)

**Figure 4-17**. Anatomie de grille d’événements

Une différence majeure entre EventGrid et Service Bus est le *modèle d’échange de messages*sous-jacent .

Service Bus met en œuvre un modèle de *traction* de style plus ancien dans lequel l’abonné en aval sonde activement l’abonnement au sujet pour de nouveaux messages. À la hausse, cette approche donne à l’abonné le plein contrôle du rythme auquel il traite les messages. Il contrôle le nombre de messages à traiter à un moment donné. Les messages non lus restent dans l’abonnement jusqu’à ce qu’ils soient traités. Une lacune importante est la latence entre le moment où l’événement est généré et l’opération de vote qui tire ce message à l’abonné pour le traitement. En outre, les frais généraux des sondages constants pour le prochain événement consomme des ressources et de l’argent.

EventGrid, cependant, est différent. Il met en œuvre un *modèle de poussée* dans lequel les événements sont envoyés aux EventHandlers tels qu’ils sont reçus, donnant une livraison d’événements en temps quasi réel. Il réduit également les coûts que le service est déclenché que lorsqu’il est nécessaire de consommer un événement - pas continuellement comme avec le sondage. Cela dit, un gestionnaire d’événements doit gérer la charge entrante et fournir des mécanismes de limitation pour se protéger contre le débordement. De nombreux services Azure qui consomment ces événements, tels que Azure Functions et Logic Apps fournissent des capacités automatiques d’autoscalage pour gérer des charges accrues.  

Event Grid est un service cloud sans serveur entièrement géré. Il évolue dynamiquement en fonction de votre trafic et vous facture uniquement pour votre utilisation réelle, et non la capacité pré-achetée. Les 100 000 premières opérations par mois sont gratuites , les opérations étant définies comme l’entrée d’événements (notifications d’événements entrants), les tentatives de livraison d’abonnement, les appels de gestion et le filtrage par sujet. Avec une disponibilité de 99,99 %, EventGrid garantit la livraison d’un événement dans un délai de 24 heures, avec des fonctionnalités intégrées de retentiment pour une livraison infructueuse. Les messages non livrés peuvent être déplacés vers une file d’attente de « lettre morte » pour être résolus.  Contrairement à Azure Service Bus, Event Grid est à l’écoute pour des performances rapides et ne prend pas en charge les fonctionnalités comme la messagerie commandée, les transactions et les sessions.

### <a name="streaming-messages-in-the-azure-cloud"></a>Messages en streaming dans le cloud Azure

Azure Service Bus et Event Grid fournissent un excellent soutien pour les applications qui exposent des événements simples et discrets comme un nouveau document a été inséré dans un Cosmos DB. Mais, que se passe-t-il si votre système cloud-native a besoin de traiter un *flux d’événements connexes*? [Les flux d’événements](https://docs.microsoft.com/archive/msdn-magazine/2015/february/microsoft-azure-the-rise-of-event-stream-oriented-systems) sont plus complexes. Ils sont généralement ordonnés dans le temps, interdépendants, et doivent être traités en tant que groupe.

[Azure Event Hub](https://azure.microsoft.com/services/event-hubs/) est une plateforme de streaming de données et un service d’ingestion d’événements qui collecte, transforme et stocke des événements. Il est affiné pour capturer des données en streaming, telles que les notifications d’événements continus émises par un contexte de télémétrie. Le service est très évolutif et peut stocker et [traiter des millions d’événements par seconde.](https://docs.microsoft.com/azure/event-hubs/event-hubs-about) Présenté dans la figure 4-18, il s’agit souvent d’une porte d’entrée pour un pipeline d’événements, découplant le flux d’ingérer de la consommation d’événements.

![Azure Event Hub](./media/azure-event-hub.png)

**Figure 4-18**. Azure Event Hub

Event Hub prend en charge une faible latence et une rétention de temps configurable. Contrairement aux files d’attente et aux sujets, Les centres d’événements conservent les données de l’événement après avoir été lues par un consommateur. Cette fonctionnalité permet à d’autres services d’analyse de données, internes et externes, de rejouer les données pour une analyse plus approfondie. Les événements stockés dans le hub d’événements ne sont supprimés qu’à l’expiration de la période de rétention, qui est un jour par défaut, mais configurable.

Event Hub prend en charge les protocoles communs de publication d’événements, y compris HTTPS et AMQP. Il soutient également Kafka 1.0. [Les applications Kafka existantes peuvent communiquer avec Event Hub](https://docs.microsoft.com/azure/event-hubs/event-hubs-for-kafka-ecosystem-overview) en utilisant le protocole Kafka offrant une alternative à la gestion de grands clusters Kafka. De nombreux systèmes open-source cloud-natives embrassent Kafka.

Event Hubs implémente le flux de messages à travers un [modèle de consommation divisé](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) dans lequel chaque consommateur ne lit qu’un sous-ensemble spécifique, ou partition, du flux de messages. Ce modèle permet de disposer d'une échelle horizontale considérable pour le traitement des événements, et offre d'autres fonctionnalités axées sur le flux, qui ne sont pas disponibles dans les rubriques et les files d'attente. Une partition est une séquence ordonnée d’événements qui est conservée dans un concentrateur d’événements. À mesure que de nouveaux événements arrivent, ils sont ajoutés à la fin de cette séquence.La figure 4-19 montre le partage dans un hub d’événements.

![Partitionnement de Event Hub](./media/event-hub-partitioning.png)

**Figure 4-19**. Partitionnement de Event Hub

Au lieu de lire à partir de la même ressource, chaque groupe de consommateurs lit sur un sous-ensemble, ou cloison, du flux de messages.

Pour les applications cloud-native qui doivent diffuser un grand nombre d’événements, Azure Event Hub peut être une solution robuste et abordable.

>[!div class="step-by-step"]
>[Suivant précédent](front-end-communication.md)
>[Next](grpc.md)

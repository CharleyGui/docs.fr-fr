---
title: Communication client et front-end
description: Découvrez comment les clients frontaux communiquent avec les systèmes natifs du Cloud
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: 89f13ea1c9ecbe92e959ae63a4c21bf7775f8943
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895571"
---
# <a name="front-end-client-communication"></a>Communication client et front-end

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Dans un système Cloud natif, les clients frontaux (applications mobiles, Web et de bureau) requièrent un canal de communication pour interagir avec les microservices back-end indépendants.  

Quelles sont les options ?

Pour simplifier les choses, un client frontal peut *communiquer directement* avec les microservices back-end, comme illustré à la figure 4-2.

![Communication directe entre le client et le service](./media/direct-client-to-service-communication.png)

**Figure 4-2.** Communication directe entre le client et le service

Avec cette approche, chaque microservice a un point de terminaison public accessible par les clients frontaux. Dans un environnement de production, vous devez placer un équilibreur de charge devant les microservices, en routant le trafic proportionnellement.

Bien qu’elles soient simples à implémenter, la communication directe des clients est acceptable uniquement pour les applications de microservice simples. Ce modèle associe étroitement les clients frontaux aux principaux services principaux, en ouvrant la porte à un certain nombre de problèmes, notamment :

- Sensibilité du client à la refactorisation du service principal.
- Une surface d’attaque plus étendue en tant que services principaux principaux est directement exposée.
- Duplication des préoccupations transversales dans chaque microservice.
- Code client trop complexe : les clients doivent effectuer le suivi de plusieurs points de terminaison et gérer les défaillances de manière résiliente.

Au lieu de cela, un modèle de conception de Cloud largement accepté consiste à implémenter un [service de passerelle d’API](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) entre les applications frontales et les services principaux. Le modèle est illustré dans la figure 4-3.

![Modèle de passerelle d’API](./media/api-gateway-pattern.png)

**Figure 4-3.** Modèle de passerelle d’API

Dans la figure précédente, notez la manière dont le service de passerelle d’API soustrait les microservices principaux principaux. Implémenté comme une API Web, il agit comme un *proxy inverse*, acheminant le trafic entrant vers les microservices internes.

La passerelle isole le client du partitionnement de service interne et de la refactorisation. Si vous modifiez un service principal, vous pouvez l’inclure dans la passerelle sans rompre le client. C’est également votre première ligne de défense pour les problèmes transversaux, tels que l’identité, la mise en cache, la résilience, le contrôle et la limitation. La plupart de ces problèmes de coupe croisée peuvent être déchargés à partir des services principaux de la passerelle, ce qui simplifie les services principaux.

Vous devez veiller à garder la passerelle d’API simple et rapide. En règle générale, la logique métier est conservée hors de la passerelle. Une passerelle complexe risque de devenir un goulot d’étranglement et de finir un monolithique. Les systèmes plus grands exposent souvent plusieurs passerelles d’API segmentées par type de client (mobile, Web, ordinateur de bureau) ou les fonctionnalités principales. Le modèle [backend pour les serveurs frontaux](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) fournit une direction pour l’implémentation de plusieurs passerelles. Le modèle est illustré dans la figure 4-4.

![Modèle de passerelle d’API](./media/backend-for-frontend-pattern.png)

**Figure 4-4.** Backend pour le modèle frontend

Notez dans la figure précédente Comment le trafic entrant est envoyé à une passerelle d’API spécifique basée sur le type de client : Web, mobile ou application de bureau. Cette approche est logique, car les fonctionnalités de chaque appareil diffèrent considérablement selon les limitations du facteur de forme, des performances et de l’affichage. En général, les applications mobiles exposent moins de fonctionnalités qu’une application de bureau ou de navigateur. Chaque passerelle peut être optimisée pour correspondre aux fonctionnalités et fonctionnalités de l’appareil correspondant.

Pour commencer, vous pouvez créer votre propre service de passerelle d’API. Une recherche rapide de GitHub fournit de nombreux exemples. Toutefois, il existe plusieurs infrastructures et produits de passerelle commerciaux disponibles.

## <a name="ocelot-gateway"></a>Passerelle Ocelot

Pour les applications simples en mode Cloud .NET, vous pouvez envisager la [passerelle Ocelot](https://github.com/ThreeMammals/Ocelot). Ocelot est une passerelle d’API Open source créée pour les microservices .NET qui requièrent un point d’entrée unifié dans leur système. Elle est légère, rapide et évolutive.

Comme toute passerelle d’API, ses principales fonctionnalités sont de transférer les requêtes HTTP entrantes vers les services en aval. En outre, il prend en charge un large éventail de fonctionnalités configurables dans un pipeline d’intergiciel (middleware) .NET Core. Son ensemble de fonctionnalités est présenté dans le tableau suivant.

|Fonctionnalités de Ocelot  | |
| :-------- | :-------- |
| Routage | Authentification |
| Agrégation des demandes | Autorisation |
| Découverte de service (avec consul et Eureka) | Limitation |
| Équilibrage de la charge. | Journalisation, suivi |
| Mise en cache | En-têtes/transformation de chaîne de requête |
| Transfert de corrélation | Intergiciel (middleware) personnalisé |
| Qualité de service | Stratégies de nouvelle tentative |

Chaque passerelle Ocelot spécifie les adresses en amont et en aval et les fonctionnalités configurables dans un fichier de configuration JSON. Le client envoie une requête HTTP à la passerelle ocelot. Une fois reçu, Ocelot passe l’objet HttpRequest via son pipeline en le manipulant dans l’état spécifié par sa configuration. À la fin du pipeline, Ocelot crée un nouveau HTTPResponseObject et le transmet au service en aval. Pour la réponse, Ocelot inverse le pipeline, en renvoyant la réponse au client.

Ocelot est disponible sous forme de package NuGet. Il cible le .NET standard 2,0, ce qui le rend compatible avec les runtimes .NET Core 2.0 + et .NET Framework 4.6.1 +. Ocelot s’intègre à tout ce qui parle HTTP et s’exécute sur les plateformes prises en charge par .NET Core : Linux, macOS et Windows. Ocelot est extensible et prend en charge de nombreuses plateformes modernes, y compris les conteneurs d’ancrage, les services Kubernetes Azure ou d’autres clouds publics.  Ocelot s’intègre aux packages Open source, tels que les [Eureka](https://github.com/Netflix/eureka) [consulaire](https://www.consul.io), [GraphQL](https://graphql.org)et Netflix.

Envisagez Ocelot pour les applications Cloud natives simples qui ne nécessitent pas l’ensemble complet de fonctionnalités d’une passerelle d’API commerciale.

## <a name="azure-application-gateway"></a>Azure Application Gateway

Pour les exigences de passerelle simples, vous pouvez envisager [Azure application passerelle](https://docs.microsoft.com/azure/application-gateway/overview). Disponible en tant que [service PaaS](https://azure.microsoft.com/overview/what-is-paas/)Azure, il comprend des fonctionnalités de passerelle de base telles que le routage d’URL, la terminaison SSL et un pare-feu d’applications Web. Le service prend en charge les fonctionnalités d' [équilibrage de charge de couche 7](https://www.nginx.com/resources/glossary/layer-7-load-balancing/) . Avec la couche 7, vous pouvez acheminer les demandes en fonction du contenu réel d’un message HTTP, pas seulement des paquets réseau TCP de bas niveau.

Tout au long de ce document, nous nous contribuons à l’hébergement des systèmes Cloud natifs dans [Kubernetes](https://www.infoworld.com/article/3268073/what-is-kubernetes-your-next-application-platform.html). Un Orchestrator de conteneur, Kubernetes automatise le déploiement, la mise à l’échelle et les problèmes opérationnels des charges de travail en conteneur. Azure Application passerelle peut être configurée en tant que passerelle d’API pour le cluster de [service Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/) .

Le [contrôleur](https://azure.github.io/application-gateway-kubernetes-ingress/) d’entrée Application Gateway permet à Azure application passerelle de travailler directement avec le [service Azure Kubernetes](https://azure.microsoft.com/services/kubernetes-service/). La figure 4,5 illustre l’architecture.

![Contrôleur d’entrée Application Gateway](./media/application-gateway-ingress-controller.png)

**Figure 4-5.** Contrôleur d’entrée Application Gateway

Kubernetes comprend une fonctionnalité intégrée qui prend en charge l’équilibrage de charge HTTP (niveau 7) [, appelé entrée](https://kubernetes.io/docs/concepts/services-networking/ingress/). Entrée définit un ensemble de règles sur la façon dont les instances de microservice dans AKS peuvent être exposées au monde extérieur. Dans l’image précédente, le contrôleur d’entrée interprète les règles d’entrée configurées pour le cluster et configure automatiquement la passerelle Azure Application. Sur la base de ces règles, le Application Gateway achemine le trafic vers les microservices exécutés dans AKS. Le contrôleur d’entrée écoute les modifications apportées aux règles d’entrée et apporte les modifications appropriées à la passerelle Azure Application.

## <a name="azure-api-management"></a>Gestion des API Azure

Pour les systèmes Cloud natifs modérés à grande échelle, vous pouvez envisager la [gestion des API Azure](https://azure.microsoft.com/services/api-management/). Il s’agit d’un service basé sur le Cloud qui ne résout pas uniquement vos besoins en matière de passerelle d’API, mais fournit un environnement de développement et d’administration complet. La gestion des API est illustrée dans la figure 4-6.

![Gestion des API Azure](./media/azure-api-management.png)

**Figure 4-6.** Gestion des API Azure

Pour commencer, la gestion des API expose un serveur de passerelle qui permet un accès contrôlé aux services principaux en fonction de règles et de stratégies configurables. Ces services peuvent se trouver dans le Cloud Azure, dans votre centre de données local ou dans d’autres clouds publics. Les clés API et les jetons JWT déterminent qui peut faire quoi. Tout le trafic est journalisé à des fins analytiques.

Pour les développeurs, la gestion des API offre un portail des développeurs qui permet d’accéder aux services, à la documentation et à des exemples de code pour les appeler. Les développeurs peuvent utiliser l’API Swagger/Open pour inspecter les points de terminaison de service et analyser leur utilisation. Le service fonctionne sur les principales plateformes de développement : .NET, Java, Golang et bien plus encore.

Le portail des éditeurs expose un tableau de bord de gestion dans lequel les administrateurs exposent les API et gèrent leur comportement. L’accès au service peut être accordé, surveillé par l’intégrité du service et les télémétries de service collectées. Les administrateurs appliquent des *stratégies* à chaque point de terminaison pour affecter le comportement. Les [stratégies](https://docs.microsoft.com/azure/api-management/api-management-howto-policies) sont des instructions prégénérées qui s’exécutent de façon séquentielle pour chaque appel de service.  Les stratégies sont configurées pour un appel entrant, sortant, ou appelées en cas d’erreur. Les stratégies peuvent être appliquées à différentes étendues de service pour activer l’ordonnancement déterministe lors de la combinaison de stratégies. Le produit est fourni avec un grand nombre de [stratégies](https://docs.microsoft.com/azure/api-management/api-management-policies)prédéfinies.

Voici des exemples de la façon dont les stratégies peuvent affecter le comportement de vos services Cloud natifs :  

- Limitez l’accès au service.
- Appliquer l’authentification.  
- Limiter les appels à partir d’une seule source, si nécessaire.
-  Activation de la mise en cache.
- Bloquer les appels à partir d’adresses IP spécifiques.
- Contrôler le déroulement du service.
- Convertissez les demandes de SOAP à REST ou entre des formats de données différents, par exemple de XML à JSON.

La gestion des API Azure peut exposer des services principaux qui sont hébergés n’importe où, dans le Cloud ou dans votre centre de données. Pour les services hérités que vous pouvez exposer dans vos systèmes Cloud natifs, il prend en charge les API REST et SOAP. Même les autres services Azure peuvent être exposés via la gestion des API. Vous pouvez placer une API gérée sur un service de sauvegarde Azure comme [Azure Service bus](https://azure.microsoft.com/services/service-bus/) ou [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/). La gestion des API Azure n’inclut pas la prise en charge de l’équilibrage de charge intégré et doit être utilisée conjointement avec un service d’équilibrage de charge.

La gestion des API Azure est disponible sur [quatre niveaux différents](https://azure.microsoft.com/pricing/details/api-management/):

- Développeur
- De base
- standard
- Premium

Le niveau développeur est conçu pour les charges de travail de non-production et l’évaluation. Les autres niveaux offrent progressivement plus de puissance, de fonctionnalités et de contrats de niveau de service (SLA) plus élevés. Le niveau Premium offre une [prise en charge de plusieurs régions](https://docs.microsoft.com/azure/api-management/api-management-howto-deploy-multi-region)et d’un [réseau virtuel Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) . Tous les niveaux ont un prix fixe par heure.

Le Cloud Azure offre également un [niveau sans serveur](https://azure.microsoft.com/blog/announcing-azure-api-management-for-serverless-architectures/) pour la gestion des API Azure. Appelé « niveau de *tarification*de la consommation », le service est une variante de la gestion des API conçue autour du modèle de calcul sans serveur. Contrairement aux niveaux tarifaires « pré-alloués » précédemment affichés, le niveau de consommation fournit un approvisionnement instantané et une tarification par action.

Il active les fonctionnalités de la passerelle API pour les cas d’utilisation suivants :

- Microservices implémentés à l’aide de technologies sans serveur telles que [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview) et [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/).
- Les ressources du service de sauvegarde Azure, telles que les Service Bus files d’attente et les rubriques, le stockage Azure et d’autres.
- Les microservices où le trafic a des pics de grande ampleur, mais qui reste peu la plupart du temps.

Le niveau de consommation utilise les mêmes composants de gestion des API de service sous-jacents, mais utilise une architecture entièrement différente basée sur des ressources allouées dynamiquement. Il s’aligne parfaitement avec le modèle de calcul sans serveur :

- Aucune infrastructure à gérer.
- Aucune capacité inactive.
- Haute disponibilité.
- Mise à l’échelle automatique.
- Le coût est basé sur l’utilisation réelle.
  
Le nouveau niveau de consommation est un bon choix pour les systèmes Cloud natifs qui exposent des ressources sans serveur en tant qu’API.

## <a name="real-time-communication"></a>Communication en temps réel

La communication en temps réel, ou Push, est une autre option pour les applications frontales qui communiquent avec les systèmes back-end Cloud natifs via HTTP. Les applications, telles que les cotations financières, les formations en ligne, les jeux et les mises à jour de la progression des travaux, requièrent des réponses instantanées et en temps réel du serveur principal. Avec la communication HTTP normale, le client n’a aucun moyen de savoir quand de nouvelles données sont disponibles. Le client doit continuellement *interroger* ou envoyer des demandes au serveur. Avec la communication *en temps réel* , le serveur peut envoyer de nouvelles données au client à tout moment.

Les systèmes en temps réel sont souvent caractérisés par des flux de données à fréquence élevée et un grand nombre de connexions clientes simultanées. La mise en œuvre manuelle de la connectivité en temps réel peut rapidement devenir complexe, nécessitant une infrastructure non triviale pour garantir l’évolutivité et la fiabilité de la messagerie aux clients connectés. Vous pouvez gérer une instance du cache Redims Azure et un ensemble d’équilibrages de charge configurés avec des sessions rémanentes pour l’affinité du client.

Le [service Azure signalr](https://azure.microsoft.com/services/signalr-service/) est un service Azure entièrement géré qui simplifie la communication en temps réel pour vos applications Cloud natives. Les détails de l’implémentation technique, tels que la configuration de la capacité, la mise à l’échelle et les connexions persistantes, sont extraits. Ils sont gérés pour vous avec un contrat de niveau de service de 99,9%. Vous vous concentrez sur les fonctionnalités de l’application, et non sur l’infrastructure.

Une fois activé, un service HTTP basé sur le Cloud peut envoyer des mises à jour de contenu directement à des clients connectés, y compris des applications de navigateur, mobiles et de bureau. Les clients sont mis à jour sans qu’il soit nécessaire d’interroger le serveur. Azure Signalr extrait les technologies de transport qui créent une connectivité en temps réel, notamment les WebSockets, les événements côté serveur et l’interrogation longue. Les développeurs se concentrent sur l’envoi de messages à tous ou à des sous-ensembles spécifiques de clients connectés.

La figure 4-7 illustre un ensemble de clients HTTP qui se connectent à une application Cloud native avec Azure Signalr activé.

![Azure SignalR](./media/azure-signalr-service.png)

**Figure 4-7.** Azure SignalR

Un autre avantage du service Azure Signalr est de mettre en œuvre des services Cloud natifs sans serveur. Votre code est peut-être exécuté à la demande avec des déclencheurs Azure Functions. Ce scénario peut être délicat, car votre code ne gère pas de longues connexions avec les clients. Le service Azure SignalR est en mesure de gérer cette situation, car il gère déjà les connexions à votre place.

Le service Azure Signalr s’intègre étroitement avec d’autres services Azure, tels que Azure SQL Database, Service Bus ou le cache ReDim, en ouvrant de nombreuses possibilités pour vos applications Cloud natives.

>[!div class="step-by-step"]
>[Précédent](communication-patterns.md)
>[suivant](service-to-service-communication.md)

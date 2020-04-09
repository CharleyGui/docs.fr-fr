---
title: Communication client et front-end
description: Découvrez comment les clients frontaux communiquent avec les systèmes cloud-natifs
author: robvet
ms.date: 09/08/2019
ms.openlocfilehash: af26873381509df7807db6ecb37a7d73669adb37
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989075"
---
# <a name="front-end-client-communication"></a>Communication client et front-end

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Dans un système cloud-native, les clients frontaux (applications mobiles, Web et bureau) ont besoin d’un canal de communication pour interagir avec des microservices back-end indépendants.  

Quelles sont les options?

Pour simplifier les choses, un client frontale peut *communiquer directement* avec les microservices back-end, indiqués dans la figure 4-2.

![Direct client au service de la communication](./media/direct-client-to-service-communication.png)

**Figure 4-2.** Direct client au service de la communication

Avec cette approche, chaque microservice a un point de terminaison public accessible par les clients de première ligne. Dans un environnement de production, vous placez un équilibrant de charge devant les microservices, routant le trafic proportionnellement.

Bien qu’elle soit simple à mettre en œuvre, la communication directe avec les clients ne serait acceptable que pour les applications simples de microservices. Ce modèle associe étroitement les clients front-end aux services de base back-end, ouvrant la porte à un certain nombre de problèmes, y compris:

- Susceptibilité client à la refactoration du service back-end.
- Une surface d’attaque plus large car les services back-end de base sont directement exposés.
- Duplication des préoccupations transversales dans chaque microservice.
- Code client trop complexe - les clients doivent garder une trace de plusieurs points de terminaison et gérer les défaillances d’une manière résiliente.

Au lieu de cela, un modèle de conception cloud largement accepté est de mettre en œuvre un [service de passerelle API](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md) entre les applications frontale et les services back-end. Le modèle est indiqué dans la figure 4-3.

![Modèle de passerelle API](./media/api-gateway-pattern.png)

**Figure 4-3.** Modèle de passerelle API

Dans le chiffre précédent, notez comment le service API Gateway résume les microservices de base back-end. Implémentée comme une API Web, elle agit comme un *proxy inversé,* acheminant le trafic entrant vers les microservices internes.

La passerelle isole le client du cloisonnement et du refactoring du service interne. Si vous modifiez un service back-end, vous vous y adaptez dans la passerelle sans casser le client. C’est aussi votre première ligne de défense pour les préoccupations transversales, telles que l’identité, la mise en cache, la résilience, le comptage et la limitation. Bon nombre de ces préoccupations transversales peuvent être déchargées des services de base de back-end jusqu’à la passerelle, ce qui simplifie les services de back-end.

Il faut prendre soin de garder la passerelle API simple et rapide. Typiquement, la logique d’affaires est tenue hors de la passerelle. Une passerelle complexe risque de devenir un goulot d’étranglement et éventuellement un monolithe lui-même. Les systèmes plus grands exposent souvent plusieurs passerelles API segmentées par type de client (mobile, web, bureau) ou fonctionnalités back-end. Le [modèle Backend for Frontends](https://docs.microsoft.com/azure/architecture/patterns/backends-for-frontends) fournit une orientation pour la mise en œuvre de plusieurs passerelles. Le modèle est indiqué dans la figure 4-4.

![Modèle de passerelle API](./media/backend-for-frontend-pattern.png)

**Figure 4-4.** Backend pour le modèle de frontend

Notez dans le chiffre précédent comment le trafic entrant est envoyé à une passerelle API spécifique - basée sur le type de client: web, mobile, ou application de bureau. Cette approche est logique car les capacités de chaque appareil diffèrent considérablement d’un facteur de forme, de performances et de limites d’affichage. En règle générale, les applications mobiles exposent moins de fonctionnalités qu’un navigateur ou des applications de bureau. Chaque passerelle peut être optimisée pour correspondre aux capacités et aux fonctionnalités de l’appareil correspondant.

Pour commencer, vous pouvez créer votre propre service API Gateway. Une recherche rapide de GitHub fournira de nombreux exemples. Cependant, plusieurs cadres et produits de passerelle commerciale sont disponibles.

## <a name="ocelot-gateway"></a>Porte d’entrée Ocelot

Pour les applications simples .NET cloud-native, vous pouvez considérer la [passerelle Ocelot](https://github.com/ThreeMammals/Ocelot). Ocelot est une passerelle Open Source API créée pour les microservices .NET qui nécessitent un point d’entrée unifié dans leur système. Il est léger, rapide, évolutif.

Comme toute passerelle API, sa principale fonctionnalité est de transmettre les demandes HTTP entrantes aux services en aval. En outre, il prend en charge une grande variété de capacités qui sont configurables dans un pipeline .NET Core middleware. Son ensemble de fonctionnalités est présenté dans le tableau suivant.

|Caractéristiques ocelot  | |
| :-------- | :-------- |
| Routage | Authentification |
| Demande d’agrégation | Autorisation |
| Découverte de service (avec Consul et Eureka) | Limitation |
| Équilibrage de la charge. | Enregistrement, Traçage |
| Mise en cache | En-têtes/Transformation des cordes de requête |
| Corrélation Pass-Through | Middleware personnalisé |
| Qualité de service | Politiques de réahanté( |

Chaque passerelle Ocelot spécifie les adresses en amont et en aval et les fonctionnalités configurables dans un fichier de configuration JSON. Le client envoie une demande HTTP à la passerelle Ocelot. Une fois reçu, Ocelot passe l’objet HttpRequest à travers son pipeline le manipulant dans l’état spécifié par sa configuration. À la fin du pipeline, Ocelot crée un nouvel httpsponseObject et le transmet au service en aval. Pour la réponse, Ocelot inverse le pipeline, renvoyant la réponse au client.

Ocelot est disponible sous forme de forfait NuGet. Il vise la norme NET 2.0, la rendant compatible avec les temps d’exécution .NET Core 2.0 et .NET Framework 4.6.1. Ocelot s’intègre à tout ce qui parle HTTP et s’exécute sur les plates-formes qui .NET Core prend en charge: Linux, macOS, et Windows. Ocelot est extensible et prend en charge de nombreuses plates-formes modernes, y compris les conteneurs Docker, Azure Kubernetes Services, ou d’autres nuages publics.  Ocelot s’intègre à des forfaits open-source comme [Consul](https://www.consul.io), [GraphQL](https://graphql.org), et [Eureka](https://github.com/Netflix/eureka)de Netflix .

Considérez Ocelot pour de simples applications cloud-native qui ne nécessitent pas le riche ensemble de fonctionnalités d’une passerelle API commerciale.

## <a name="azure-application-gateway"></a>Azure Application Gateway

Pour les exigences simples de passerelle, vous pouvez considérer [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/overview). Disponible en tant que service Azure [PaaS,](https://azure.microsoft.com/overview/what-is-paas/)il comprend des fonctionnalités de passerelle de base telles que le routage d’URL, la terminaison SSL et un pare-feu d’application Web. Le service prend en charge les capacités [d’équilibrage de charge de la couche-7.](https://www.nginx.com/resources/glossary/layer-7-load-balancing/) Avec la couche 7, vous pouvez acheminer les demandes en fonction du contenu réel d’un message HTTP, et pas seulement des paquets de réseau TCP de bas niveau.

Tout au long de ce livre, nous évangélisons l’hébergement de systèmes cloud-indigènes à [Kubernetes](https://www.infoworld.com/article/3268073/what-is-kubernetes-your-next-application-platform.html). Orchestrateur de conteneurs, Kubernetes automatise le déploiement, la mise à l’échelle et les préoccupations opérationnelles des charges de travail conteneurisées. Azure Application Gateway peut être configuré comme une passerelle API pour le cluster [de service Azure Kubernetes.](https://azure.microsoft.com/services/kubernetes-service/)

Le [contrôleur d’entrée d’application](https://azure.github.io/application-gateway-kubernetes-ingress/) permet à Azure Application Gateway de travailler directement avec [azure Kubernetes Service](https://azure.microsoft.com/services/kubernetes-service/). La figure 4.5 montre l’architecture.

![Contrôleur d’entrée Application Gateway](./media/application-gateway-ingress-controller.png)

**Figure 4-5.** Contrôleur d’entrée Application Gateway

Kubernetes comprend une fonctionnalité intégrée qui prend en charge l’équilibrage de charge HTTP (niveau 7), appelé [Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/). Ingress définit un ensemble de règles pour la façon dont les cas de microservice à l’intérieur de AKS peuvent être exposés au monde extérieur. Dans l’image précédente, le contrôleur d’entrée interprète les règles d’entrée configurées pour le cluster et configure automatiquement la passerelle d’application Azure. Sur la base de ces règles, la passerelle d’application assure le trafic vers les microservices qui circulent à l’intérieur d’AKS. Le contrôleur d’entrée est à l’écoute des modifications apportées aux règles d’entrée et apporte les modifications appropriées à la passerelle d’application Azure.

## <a name="azure-api-management"></a>Gestion des API Azure

Pour les systèmes cloud-natifs à grande échelle, vous pouvez envisager [Azure API Management](https://azure.microsoft.com/services/api-management/). Il s’agit d’un service basé sur le cloud qui non seulement résout vos besoins API Gateway, mais offre une expérience complète de développeur et d’administration. La gestion de l’API est indiquée à la figure 4-6.

![Gestion des API Azure](./media/azure-api-management.png)

**Figure 4-6.** Gestion des API Azure

Pour commencer, API Management expose un serveur de passerelle qui permet un accès contrôlé aux services back-end basés sur des règles et des politiques configurables. Ces services peuvent être dans le nuage Azure, votre centre de données sur le prém, ou d’autres nuages publics. Les clés API et les jetons JWT déterminent qui peut faire quoi. Tout le trafic est enregistré à des fins analytiques.

Pour les développeurs, API Management offre un portail de développeurs qui donne accès aux services, à la documentation et au code d’échantillon pour les invoquer. Les développeurs peuvent utiliser l’API Swagger/Open pour inspecter les paramètres de service et analyser leur utilisation. Le service fonctionne sur les principales plates-formes de développement: .NET, Java, Golang, et plus encore.

Le portail de l’éditeur expose un tableau de bord de gestion où les administrateurs exposent les API et gèrent leur comportement. L’accès au service peut être accordé, la santé des services surveillée et la télémétrie de service recueillies. Les administrateurs appliquent des *stratégies* à chaque critère d’évaluation pour affecter le comportement. [Les stratégies](https://docs.microsoft.com/azure/api-management/api-management-howto-policies) sont des énoncés pré-construits qui exécutent séquentiellement pour chaque appel de service.  Les stratégies sont configurées pour un appel entrant, un appel sortant ou invoquée sur une erreur. Les stratégies peuvent être appliquées à différentes étendues de service afin de permettre l’ordre déterministe lors de la combinaison des stratégies. Le produit expédie avec un grand nombre de [politiques](https://docs.microsoft.com/azure/api-management/api-management-policies)préconstrutes .

Voici des exemples de la façon dont les stratégies peuvent influer sur le comportement de vos services cloud-natives :  

- Limitez l’accès au service.
- Appliquer l’authentification.  
- Throttle appelle à partir d’une seule source, si nécessaire.
-  Activation de la mise en cache.
- Bloquez les appels à partir d’adresses IP spécifiques.
- Contrôlez le flux du service.
- Convertissez les demandes de SOAP à REST ou entre différents formats de données, comme de XML à JSON.

Azure API Management peut exposer les services back-end hébergés n’importe où, dans le cloud ou votre centre de données. Pour les services existants que vous pouvez exposer dans vos systèmes cloud-native, il prend en charge à la fois REST et SOAP API. Même d’autres services Azure peuvent être exposés par le biais de API Management. Vous pouvez placer une API gérée au-dessus d’un service de support Azure comme [Azure Service Bus](https://azure.microsoft.com/services/service-bus/) ou [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/). Azure API Management n’inclut pas de support intégré d’équilibrage des charges et doit être utilisé en conjonction avec un service d’équilibrage des charges.

Azure API Management est disponible sur [quatre niveaux différents](https://azure.microsoft.com/pricing/details/api-management/):

- Développeur
- De base
- standard
- Premium

Le niveau développeur est destiné aux charges de travail et à l’évaluation non liées à la production. Les autres niveaux offrent progressivement plus de puissance, de fonctionnalités et d’accords de niveau de service plus élevés (SLA). Le niveau Premium fournit [le réseau virtuel Azure](https://docs.microsoft.com/azure/virtual-network/virtual-networks-overview) et [le support multi-région.](https://docs.microsoft.com/azure/api-management/api-management-howto-deploy-multi-region) Tous les niveaux ont un prix fixe par heure.

Récemment, Microsoft a annoncé un [niveau sans serveur API Management](https://azure.microsoft.com/blog/announcing-azure-api-management-for-serverless-architectures/) pour Azure API Management. Appelé le niveau de prix de *consommation,* le service est une variante de la gestion API conçu autour du modèle informatique sans serveur. Contrairement aux niveaux de tarification « pré-attribués » précédemment indiqués, le niveau de consommation fournit des prix instantanés de provisionnement et de paiement par action.

Il permet aux fonctionnalités API Gateway pour les cas d’utilisation suivants :

- Microservices mis en œuvre à l’aide de technologies sans serveur telles que [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview) et [Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/).
- Ressources de service de support Azure telles que les files d’attente et les sujets de Bus de service, le stockage Azure, et d’autres.
- Microservices où le trafic a occasionnellement de grandes pointes, mais reste faible la majorité du temps.

Le niveau de consommation utilise les mêmes composants de gestion de service sous-jacents D’API, mais emploie une architecture entièrement différente basée sur des ressources attribuées dynamiquement. Il s’aligne parfaitement avec le modèle informatique sans serveur :

- Pas d’infrastructure à gérer.
- Pas de capacité de ralenti.
- Haute disponibilité.
- Mise à l’échelle automatique.
- Le coût est basé sur l’utilisation réelle.
  
Le nouveau niveau de consommation est un excellent choix pour les systèmes cloud-natifs qui exposent les ressources sans serveur comme API.

> Au moment d’écrire ces lignes, le niveau de consommation est en avant-première dans le nuage Azure.

## <a name="real-time-communication"></a>Communication en temps réel

La communication en temps réel, ou push, est une autre option pour les applications front-end qui communiquent avec les systèmes cloud-natifs back-end sur HTTP. Les applications, telles que les financiers, l’éducation en ligne, les jeux et les mises à jour du progrès de l’emploi, nécessitent des réponses instantanées en temps réel de la part du back-end. Avec la communication HTTP normale, il n’y a aucun moyen pour le client de savoir quand de nouvelles données sont disponibles. Le client doit continuellement *sonder* ou envoyer des demandes au serveur. Avec la communication *en temps réel,* le serveur peut pousser de nouvelles données vers le client à tout moment.

Les systèmes en temps réel sont souvent caractérisés par des flux de données à haute fréquence et un grand nombre de connexions clients simultanées. La mise en œuvre manuelle de la connectivité en temps réel peut rapidement devenir complexe, nécessitant une infrastructure non négligeable pour assurer l’évolutivité et la messagerie fiable aux clients connectés. Vous pouvez vous retrouver à gérer une instance d’Azure Redis Cache et un ensemble d’équilibristes de charge configurés avec des sessions collantes pour l’affinité client.

[Azure SignalR Service](https://azure.microsoft.com/services/signalr-service/) est un service Azure entièrement géré qui simplifie la communication en temps réel pour vos applications cloud-native. Les détails techniques de mise en œuvre comme l’approvisionnement en capacité, l’échelle et les connexions persistantes sont abstraits. Ils sont traités pour vous avec un contrat de service de 99,9%. Vous vous concentrez sur les fonctionnalités d’application, et non sur la plomberie d’infrastructure.

Une fois activé, un service HTTP basé sur le cloud peut pousser les mises à jour de contenu directement aux clients connectés, y compris les applications de navigateur, mobiles et de bureau. Les clients sont mis à jour sans avoir besoin de sonder le serveur. Azure SignalR résume les technologies de transport qui créent une connectivité en temps réel, y compris les WebSockets, les événements côté serveur et les sondages longs. Les développeurs se concentrent sur l’envoi de messages à tous ou sous-ensembles spécifiques de clients connectés.

La figure 4-7 montre un ensemble de clients HTTP se connectant à une application cloud-native avec Azure SignalR activé.

![Azure SignalR](./media/azure-signalr-service.png)

**Figure 4-7.** Azure SignalR

Un autre avantage du service SignalR Azure est la mise en œuvre de services cloud-native Serverless. Peut-être que votre code est exécuté à la demande avec les déclencheurs Azure Functions. Ce scénario peut être délicat parce que votre code ne maintient pas de longues connexions avec les clients. Le service Azure SignalR est en mesure de gérer cette situation, car il gère déjà les connexions à votre place.

Azure SignalR Service s’intègre étroitement à d’autres services Azure, tels qu’Azure SQL Database, Service Bus ou Redis Cache, ouvrant de nombreuses possibilités pour vos applications cloud-natives.

>[!div class="step-by-step"]
>[Suivant précédent](communication-patterns.md)
>[Next](service-to-service-communication.md)

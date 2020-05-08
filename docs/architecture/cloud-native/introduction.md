---
title: Présentation des applications cloud natives
description: En savoir plus sur l’informatique Cloud Native
author: robvet
ms.date: 08/26/2019
ms.openlocfilehash: e1f7683b6f3722bb91e611f199f2e9ce2bbefc63
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895520"
---
# <a name="introduction-to-cloud-native-applications"></a>Présentation des applications cloud natives

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Un autre jour, au bureau, en travaillant sur « la prochaine belle chose ».

Vos sonneries cellulaires. Il s’agit de votre recruteur amical, celui qui vous appelle deux fois par jour sur les nouveaux travaux.

Mais cette fois-ci, elle est différente : le démarrage, les capitaux propres et de nombreux financements.

La mention du Cloud et de la technologie de pointe vous pousse à la périphérie.

Avancez rapidement quelques semaines et vous êtes maintenant un nouvel employé dans une session de conception qui a conçu une application de commerce électronique principale. Vous allez en concurrence avec d’autres sites de commerce électronique de pointe.

Comment allez-vous le créer ?

Si vous suivez les instructions des 15 dernières années, vous créerez probablement le système illustré à la figure 1,1.

![Conception monolithique traditionnelle](./media/monolithic-design.png)

**Figure 1-1**. Conception monolithique traditionnelle

Vous construisez une grande application principale contenant l’ensemble de votre logique de domaine. Il comprend des modules tels que l’identité, le catalogue, la commande et bien plus encore. L’application principale communique avec une base de données relationnelle volumineuse. Le noyau expose les fonctionnalités via une interface HTML.

Félicitations !  Vous venez de créer une application monolithique.

Tout est incorrect. Les monolithiques offrent des avantages distincts. Par exemple, ils sont simples à...

- build
- test
- déployer
- résolution
- scale

De nombreuses applications qui existent aujourd’hui ont été créées en tant que monolithes. L’application est un accès et continue à évoluer, à l’itération après l’itération, et à ajouter de plus en plus de fonctionnalités.

À un moment donné, toutefois, vous ne vous sentez pas à l’aise. Vous perdez le contrôle de l’application. À mesure que le temps passe, le sentiment devient plus intense et vous finissez par entrer un état appelé « **cycle de crainte**».

- L’application est devenue tellement compliquée qu’aucune personne ne la comprenne.
- Vous craignez d’apporter des modifications-chaque modification a des effets secondaires inattendus et coûteux.
- Les nouvelles fonctionnalités et correctifs deviennent délicats, fastidieux et coûteux à implémenter.
- Chaque version est aussi petite qu’elle peut nécessiter un déploiement complet de l’application entière.
- Un composant instable peut bloquer l’ensemble du système.
- Les nouvelles technologies et les nouveaux frameworks ne sont pas une option.
- Il est difficile d’implémenter des méthodologies de livraison agile.
- Les jeux d’érosion de l’architecture dans, car la base de code se détériore avec des « cas spéciaux » jamais terminés.
- Les consultants vous indiquent de le réécrire.

De nombreuses organisations ont traité le cycle de crainte monolithique en adoptant une approche Cloud native pour la création de systèmes. La figure 1-2 illustre le même système généré en appliquant des techniques et des pratiques Cloud natives.

![Conception Cloud-natif](./media/cloud-native-design.png)

**Figure 1-2**. Conception Cloud-natif

Notez comment l’application est décomposée sur un ensemble de petits microservices isolés. Chaque service est autonome et encapsule son propre code, ses propres données et ses dépendances. Chaque est déployé dans un conteneur logiciel et géré par un Orchestrator de conteneur. Au lieu d’une base de données relationnelle volumineuse, chaque service possède son propre magasin de données, dont le type varie en fonction des besoins en matière de données. Notez que certains services dépendent d’une base de données relationnelle, mais d’autres sur des bases de données NoSQL. Un service stocke son état dans un cache distribué. Notez comment tout le trafic est acheminé via un service de passerelle d’API qui est responsable de l’acheminement du trafic vers les services principaux principaux et qui impose de nombreux problèmes de coupe croisée. Plus important encore, l’application tire pleinement parti des fonctionnalités d’évolutivité et de résilience disponibles dans les plateformes Cloud modernes.

### <a name="cloud-native-computing"></a>Informatique Cloud-Native

Hmm... Nous venons d’utiliser le terme «*Cloud Native*». Vous avez tout d’abord pensé que « qu’est-ce que cela signifie exactement ? » Un autre delà choisi par les éditeurs de logiciels pour commercialiser plus de choses ?»

Heureusement, il est bien différent et, à l’aide de cet ouvrage, vous vous convaincrez.

Dans un bref laps de temps, Cloud native est devenu une tendance à la hausse dans l’industrie des logiciels. Il s’agit d’une nouvelle façon de réfléchir à la création de systèmes complexes de grande taille, une approche qui tire pleinement parti des pratiques, technologies et infrastructures de développement logiciel modernes. L’approche modifie la façon dont vous concevez, implémentez, déployez et Exploitez les systèmes.

Contrairement à la bande continue qui pilote notre secteur, le Cloud native est «*for-Real*». Prenons l’exemple de CNCF ( [Cloud Native Computing Foundation](https://www.cncf.io/) ), un consortium de plus de 300 entreprises majeures disposant d’une Charte pour rendre l’informatique Cloud Native omniprésente sur la technologie et les piles de clouds. En tant qu’un des groupes Open source les plus influents, il héberge de nombreux projets open source à croissance rapide dans GitHub. Il s’agit notamment de projets tels que [Kubernetes](https://kubernetes.io/), [Prometheus](https://prometheus.io/), [Helm](https://helm.sh/), [Envoy](https://www.envoyproxy.io/)et [gRPC](https://grpc.io/).

Le CNCF favorise un écosystème de la langue Open source et de la neutralité du fournisseur. À la suite de cela, nous présentons les principes, les modèles et les meilleures pratiques Cloud natifs qui sont indépendants des technologies. En même temps, nous aborderons les services et l’infrastructure disponibles dans le Cloud Microsoft Azure pour la création de systèmes Cloud natifs.

Alors, qu’est-ce que Cloud Native ? Asseyez-vous, détendez-vous et laissez-nous vous aider à explorer ce nouveau monde.

>[!div class="step-by-step"]
>[Précédent](index.md)
>[suivant](definition.md)

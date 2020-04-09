---
title: Présentation des applications cloud natives
description: En savoir plus sur l’informatique en nuage
author: robvet
ms.date: 08/26/2019
ms.openlocfilehash: c9ffd34ec3deb04abddbbf85a9e5a6ed2b57c8f9
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989049"
---
# <a name="introduction-to-cloud-native-applications"></a>Présentation des applications cloud natives

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Un autre jour, au bureau, travaillant sur "la prochaine grande chose."

Ton portable sonne. C’est votre recruteur amical - celui qui vous appelle deux fois par jour au sujet de nouveaux emplois.

Mais cette fois, c’est différent : démarrage, équité et beaucoup de financement.

La mention du cloud et de la technologie de pointe vous pousse sur le bord.

Avance rapide de quelques semaines et vous êtes maintenant un nouvel employé dans une session de conception d’architecture d’une application eCommerce majeur. Vous allez compléter avec d’autres sites de commerce électronique de premier plan.

Comment allez-vous le construire?

Si vous suivez les directives des 15 dernières années, vous allez très probablement construire le système indiqué dans la figure 1.1.

![Conception monolithique traditionnelle](./media/monolithic-design.png)

**Figure 1-1**. Conception monolithique traditionnelle

Vous construisez une grande application de base contenant toute votre logique de domaine. Il comprend des modules tels que l’identité, le catalogue, la commande, et plus encore. L’application de base communique avec une grande base de données relationnelle. Le noyau expose la fonctionnalité via une interface HTML.

Félicitations !  Vous venez de créer une application monolithique.

Tout n’est pas mauvais. Les monolithes offrent des avantages distincts. Par exemple, ils sont simples à ...

- build
- test
- déployer
- Dépanner
- scale

Beaucoup d’applications réussies qui existent aujourd’hui ont été créées comme des monolithes. L’application est un succès et continue d’évoluer, itération après itération, ajoutant de plus en plus de fonctionnalités.

À un moment donné, cependant, vous commencez à vous sentir mal à l’aise. Vous vous retrouvez à perdre le contrôle de l’application. Comme le temps passe, le sentiment devient plus intense et vous finissez par entrer dans un état connu sous le nom de **cycle de la peur**.

- L’application est devenue si compliquée qu’aucune personne ne la comprend.
- Vous craignez d’apporter des changements - chaque changement a des effets secondaires involontaires et coûteux.
- Les nouvelles fonctionnalités/fixes deviennent délicates, longues et coûteuses à implémenter.
- Chaque version aussi petite qu’elle peut l’être nécessite un déploiement complet de l’ensemble de l’application.
- Un composant instable peut planter l’ensemble du système.
- Les nouvelles technologies et les nouveaux cadres ne sont pas une option.
- Il est difficile de mettre en œuvre des méthodologies de livraison agiles.
- L’érosion architecturale s’installe à mesure que la base de code se détériore avec des « cas spéciaux » sans fin.
- Les consultants vous disent de le réécrire.

De nombreuses organisations ont abordé le cycle de la peur monolithique en adoptant une approche cloud-native des systèmes de construction. La figure 1-2 montre le même système construit en appliquant des techniques et des pratiques cloud-natives.

![Conception Cloud-Native](./media/cloud-native-design.png)

**Figure 1-2**. Conception cloud-native

Notez comment l’application est décomposée sur un ensemble de petits microservices isolés. Chaque service est autonome et encapsule son propre code, ses données et ses dépendances. Chacun est déployé dans un conteneur logiciel et géré par un orchestrateur de conteneurs. Au lieu d’une grande base de données relationnelle, chaque service possède sa propre datastore, dont le type varie en fonction des besoins en données. Notez comment certains services dépendent d’une base de données relationnelle, mais d’autres sur les bases de données NoSQL. Un service stocke son état dans un cache distribué. Notez comment toutes les voies de circulation par le biais d’un service API Gateway qui est responsable de l’acheminement du trafic vers les services de back-end de base et l’application de nombreuses préoccupations transversales. Plus important encore, l’application tire pleinement parti des caractéristiques d’évolutivité et de résilience que l’on retrouve dans les plates-formes cloud modernes.

### <a name="cloud-native-computing"></a>Informatique en nuage

Hmm... Nous venons d’utiliser le terme,*"Cloud Native."* Vous avez d’abord pensé que ça pourrait être : "Qu’est-ce que ça veut dire ?" Un autre mot à la mode de l’industrie concocté par les fournisseurs de logiciels pour commercialiser plus de choses?

Heureusement, c’est bien différent et j’espère que ce livre vous aidera à vous convaincre.

En peu de temps, le natif du cloud est devenu une tendance moteur dans l’industrie du logiciel. C’est une nouvelle façon de penser à construire de grands systèmes complexes, une approche qui tire pleinement parti des pratiques modernes de développement de logiciels, des technologies et de l’infrastructure cloud. L’approche modifie la façon dont vous concevez, implémentez, déployez et opérationnalisez les systèmes.

Contrairement au battage médiatique continu qui anime notre industrie, le natif du cloud est «*pour le réel*». Considérez la [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF), un consortium de plus de 300 grandes sociétés avec une charte pour rendre l’informatique en nuage omniprésente à travers la technologie et les piles de nuages. En tant que l’un des groupes open-source les plus influents, il accueille de nombreux projets open source qui connaissent la croissance la plus rapide dans GitHub. Ils comprennent des projets tels que [Kubernetes](https://kubernetes.io/), [Prometheus](https://prometheus.io/), [Helm](https://helm.sh/), [Envoy](https://www.envoyproxy.io/), et [gRPC](https://grpc.io/).

La CNCF favorise un écosystème d’open source et de neutralité des fournisseurs. À la suite de cette piste, nous présentons des principes, des modèles et des pratiques exemplaires natifs du cloud qui sont agnostiques technologiques. Dans le même temps, nous discutons des services et de l’infrastructure disponibles dans le cloud Microsoft Azure pour la construction de systèmes cloud-native.

Alors, qu’est-ce que Cloud Native exactement? Asseyez-vous, détendez-vous, et laissez-nous vous aider à explorer ce nouveau monde.

>[!div class="step-by-step"]
>[Suivant précédent](index.md)
>[Next](definition.md)

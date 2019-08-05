---
title: Architecture en microservices
description: Architecture des microservices .NET pour applications .NET conteneurisées | Vue générale de l’architecture des microservices.
ms.date: 09/20/2018
ms.openlocfilehash: 3cf2a94140042d3cf76b5b63fe4e98638c56dbfe
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68672986"
---
# <a name="microservices-architecture"></a>Architecture en microservices

Comme son nom l’indique, une architecture en microservices est une approche de la création d’une application serveur sous la forme d’un ensemble de petits services. Cela signifie qu’une architecture de microservices est principalement orientée vers le back-end, même si l’approche est également utilisée pour le front-end. Chaque service s’exécute dans son propre processus et communique avec d’autres processus avec des protocoles comme HTTP/HTTPS, WebSockets ou [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Chaque microservice implémente une fonctionnalité métier ou de domaine spécifique de bout en bout dans une certaine limite de contexte, et chacun doit être développé de manière autonome et pouvoir être déployé indépendamment. Enfin, chaque microservice doit avoir son modèle de données de domaine et sa logique de domaine associés (souveraineté et gestion des données décentralisée). Il peut être basé sur différentes technologies de stockage de données (SQL, NoSQL) et sur différents langages de programmation.

De quelle taille doit être un microservice ? Quand vous développez un microservice, la taille ne doit pas être le point important. Le point important doit plutôt être de créer des services faiblement couplés, afin que le développement, le déploiement et la mise à l’échelle soient autonomes pour chaque service. Bien sûr, quand vous identifiez et concevez des microservices, vous devez essayer de les rendre les plus petits possible, tant que vous n’avez pas trop de dépendances directes avec d’autres microservices. Deux éléments sont plus importants que la taille du microservice : sa cohésion interne et son indépendance vis-à-vis d’autres services.

Pourquoi une architecture en microservices ? Pour faire court, disons qu’elle offre une agilité à long terme. Les microservices permettent une meilleure maintenabilité dans les grands systèmes complexes et hautement scalables, en vous permettant de créer des applications basées sur de nombreux services qui peuvent être déployés indépendamment, chacun ayant des cycles de vie granulaires et autonomes.

Un autre avantage est que les microservices peuvent monter en charge (scale out) de façon indépendante. Au lieu d’avoir une seule application monolithique que vous devez faire monter en charge en totalité, vous pouvez faire monter en charge des microservices spécifiques. Ainsi, vous pouvez effectuer un scale-out ciblé de la zone fonctionnelle qui nécessite plus de puissance de traitement ou plus de bande passante réseau pour satisfaire la demande, au lieu d’effectuer un scale-out d’autres zones de l’application qui n’en ont pas besoin. Cela signifie des frais réduits, car vous avez besoin de moins de matériel.

![Dans l’approche monolithique classique, la scalabilité de l’application passe par le clonage de l’ensemble de l’application sur plusieurs serveurs/machines virtuelles. Dans l’approche liée aux microservices, les fonctionnalités sont séparées en services plus petits, pour permettre à chaque service d’être scalable indépendamment.](./media/image6.png)

**Figure 4-6**. Déploiement monolithique comparé à l’approche par microservices

Comme le montre la figure 4-6, l’approche par microservices permet des modifications agiles et une itération rapide de chaque microservice, car vous pouvez changer de petites parties spécifiques de grandes applications complexes et scalables.

Le fait d’architecturer des applications basées sur des microservices à granularité fine permet des pratiques d’intégration continue et de livraison continue. Il accélère également l’ajout de nouvelles fonctions dans l’application. La composition d’applications avec une granularité fine vous permet également d’exécuter et de tester des microservices de façon isolée, et de les faire évoluer de façon autonome tout en maintenant des contrats clairs entre eux. Tant que vous ne changez pas les contrats ou les interfaces, vous pouvez changer l’implémentation interne de n’importe quel microservice ou ajouter de nouvelles fonctionnalités sans perturber le fonctionnement des autres microservices.

Voici des aspects importants pour réussir à passer en production avec un système basé sur des microservices :

- Surveillance et vérification de l’intégrité des services et de l’infrastructure.

- Infrastructure évolutive pour les services (c’est-à-dire le cloud et des orchestrateurs).

- Conception et implémentation de la sécurité à plusieurs niveaux : authentification, autorisation, gestion des secrets, communication sécurisée, etc.

- Livraison rapide des applications, généralement avec différentes équipes s’occupant des différents microservices.

- Pratiques et infrastructure DevOps et Intégration continue/livraison continue.

Parmi ces aspects, seuls les trois premiers sont couverts ou présentés dans ce guide. Les deux derniers points, qui sont liés au cycle de vie des applications, sont traités dans un autre livre électronique, [Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft](https://aka.ms/dockerlifecycleebook).

## <a name="additional-resources"></a>Ressources supplémentaires

- **Mark Russinovich. Microservices : Une révolution des applications grâce au cloud** \
  <https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/>

- **Martin Fowler. Microservices** \
  <https://www.martinfowler.com/articles/microservices.html>

- **Martin Fowler. Microservice Prerequisites** \
  <https://martinfowler.com/bliki/MicroservicePrerequisites.html>

- **Jimmy Nilsson. Chunk Cloud Computing** \
  <https://www.infoq.com/articles/CCC-Jimmy-Nilsson>

- **Cesar de la Torre. Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (livre électronique téléchargeable) \
  <https://aka.ms/dockerlifecycleebook>

>[!div class="step-by-step"]
>[Précédent](service-oriented-architecture.md)
>[Suivant](data-sovereignty-per-microservice.md)

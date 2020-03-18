---
title: Architectures courantes des applications web
description: Architecturer des applications web modernes avec ASP.NET Core et Azure | Explorer les architectures courantes des applications web
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 7ec0d9cece40ba8a99e8ab5e028f7ac491ed6f4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77450174"
---
# <a name="common-web-application-architectures"></a>Architectures courantes des applications web

> « Si vous pensez qu’une bonne architecture est coûteuse, faites l’expérience d’une mauvaise architecture. »  
> _– Brian Foote and Joseph Yoder_

La plupart des applications .NET conventionnelles sont déployées sous forme d’unités individuelles qui correspondent à un exécutable ou à une application web unique s’exécutant dans un seul domaine d’application IIS. C’est le modèle de déploiement le plus simple, qui convient parfaitement à beaucoup d’applications internes et applications publiques de petite taille. Toutefois, même avec ce déploiement en unités individuelles, la majorité des applications métier non triviales tirent avantage à avoir leur logique séparée en plusieurs couches.

## <a name="what-is-a-monolithic-application"></a>Qu’est-ce qu’une application monolithique ?

Une application monolithique est une application qui se comporte de façon totalement autonome. Elle peut avoir des interactions avec d’autres services ou magasins de données pendant son exécution, mais son comportement est fondamentalement géré en interne. L’ensemble de l’application est généralement déployée comme une seule unité. Quand une application monolithique doit faire l’objet d’une mise à l’échelle horizontale, en général, l’application entière est dupliquée sur plusieurs serveurs ou machines virtuelles.

## <a name="all-in-one-applications"></a>Applications tout-en-un

L’architecture d’une application peut se réduire à un seul projet. Dans cette architecture, toute la logique de l’application est contenue dans un seul projet, compilé dans un assembly unique et déployé comme une seule unité.

Tout nouveau projet ASP.NET Core, créé dans Visual Studio ou à partir de la ligne de commande, est au début une simple application monolithique « tout-en-un ». Le projet contient le comportement complet de l’application, y compris la logique de présentation, métier et d’accès aux données. La figure 5-1 montre la structure de fichiers d’une application à projet unique.

![Application ASP.NET Core à projet unique](./media/image5-1.png)

**Figure 5-1.** Application ASP.NET Core à projet unique.

Dans un scénario de projet unique, la séparation des préoccupations s’obtient par l’utilisation de dossiers. Le modèle par défaut inclut des dossiers distincts pour les responsabilités des modèles, vues et contrôleurs du schéma MVC, ainsi que des dossiers supplémentaires pour les services et les données. Dans cette organisation, les détails de présentation doivent être limités autant que possible au dossier Vues, et les détails d’implémentation de l’accès aux données doivent être limités aux classes stockées dans le dossier Données. La logique métier doit résider dans les services et les classes contenus dans le dossier Modèles.

La solution monolithique à projet unique est simple, mais elle présente certains inconvénients. Le nombre de fichiers et de dossiers augmente à mesure que le projet grossit et devient plus complexe. Les éléments sensibles de l’interface utilisateur (modèles, vues, contrôleurs) résident dans plusieurs dossiers qui ne sont pas regroupés par ordre alphabétique. Cela devient un réel problème quand des constructions de niveau interface utilisateur supplémentaires, telles que des filtres ou des classeurs de modèles (ModelBinder), sont ajoutées dans leurs propres dossiers. La logique métier est répartie entre les dossiers Models et Services, mais les dépendances entre les classes contenues dans ces dossiers ne sont pas clairement indiquées. Cette mauvaise organisation au niveau du projet se traduit fréquemment par la création de [code spaghetti](https://deviq.com/spaghetti-code/).

Pour résoudre ces problèmes, les applications se transforment souvent en solutions à projets multiples, où chaque projet est censé résider dans une _couche_ spécifique de l’application.

## <a name="what-are-layers"></a>Qu’est-ce qu’une architecture en couches ?

Quand une application devient complexe, un moyen de gérer cette complexité est de scinder l’application selon ses responsabilités ou préoccupations. Cela fait suite à la séparation des préoccupations principe et peut aider à maintenir une base de code croissante organisée afin que les développeurs peuvent facilement trouver où certaines fonctionnalités sont mises en œuvre. L’architecture en couches offre d’autres avantages que la simple organisation du code.

En effet, l’organisation du code en couches permet également la réutilisation des fonctionnalités communes de bas niveau dans l’ensemble de l’application. Cette possibilité est intéressante, car elle réduit la quantité de code à écrire et permet la standardisation de l’application sur une implémentation unique, selon le principe [DRY (« Ne vous répétez pas »)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself).

Avec une architecture en couches, les applications peuvent appliquer des restrictions sur les échanges autorisés entre les différentes couches. Cela contribue à améliorer l’encapsulation. De cette façon, quand une couche est modifiée ou remplacée, seules les couches qui interagissent avec elle sont impactées. En limitant l’interdépendance des couches, l’impact des modifications peut être atténué afin qu’une modification donnée n’impacte pas l’application entière.

Les couches (et l’encapsulation) facilitent le remplacement des fonctionnalités dans l’application. Par exemple, une application peut initialement utiliser sa propre base de données SQL Server pour la persistance, mais plus tard choisir d’utiliser une stratégie de persistance basée sur le cloud ou située derrière une API web. Si l’application a correctement encapsulé son implémentation de persistance au sein d’une couche logique, cette couche spécifique de SQL Server peut être remplacée par une nouvelle couche qui implémente la même interface publique.

Outre la possibilité de permuter des implémentations en réponse à des changements ultérieurs dans les exigences, les couches d’application facilitent également la permutation des implémentations pour les besoins de test. Au lieu d’écrire des tests qui s’exécutent sur la couche des données réelles ou sur la couche de l’interface utilisateur de l’application, vous pouvez remplacer ces couches durant la phase de test par des implémentations fictives qui fournissent des réponses connues aux requêtes. Cette possibilité simplifie considérablement l’écriture des tests et rend leur exécution beaucoup plus rapide par rapport aux tests effectués dans l’infrastructure réelle de l’application.

La mise en couches logiques est une technique courante pour améliorer l’organisation du code dans les applications d’entreprise. Le code peut être organisé en couches de plusieurs façons.

> [!NOTE]
 > Les _couches_ représentent une séparation logique au sein de l’application. Si la logique de l’application est répartie physiquement entre plusieurs serveurs ou processus séparés, ces différentes cibles de déploiement physiques sont appelées _niveaux_. Il est possible, et relativement courant, de déployer une application en N couches sur un seul niveau.

## <a name="traditional-n-layer-architecture-applications"></a>Applications avec une architecture en N couches conventionnelle

La figure 5-2 illustre l’organisation la plus courante d’une logique d’application en couches.

![Couches d’application typiques](./media/image5-2.png)

**Figure 5-2.** Couches d’application classiques.

Ces couches sont souvent abrégées comme ceci : UI (couche d’interface utilisateur), BLL (couche métier) et DAL (couche d’accès aux données). Avec cette architecture, les utilisateurs effectuent des requêtes par le biais de la couche UI, qui interagit uniquement avec la couche BLL. La couche BLL, à son tour, peut appeler la couche DAL pour les requêtes d’accès aux données. La couche UI ne doit pas directement adresser des requêtes à la couche DAL, ni interagir avec persistance directement par d’autres moyens. De même, la couche BLL doit uniquement interagir avec persistance en passant par la couche DAL. De cette manière, chaque couche a sa propre responsabilité connue.

Cette approche en couches classique a un inconvénient, à savoir que les dépendances de compilation s’exécutent de haut en bas. Autrement dit, la couche UI dépend de la couche BLL, qui dépend elle-même de la couche DAL. La couche BLL, qui contient généralement la logique la plus importante de l’application, est dépendante des détails d’implémentation de l’accès aux données (et souvent de l’existence d’une base de données). Il est souvent difficile de tester la logique métier dans ce type d’architecture, car il faut utiliser une base de données de test. Le principe d’inversion des dépendances peut être une solution à ce problème, comme vous le verrez dans la section suivante.

La figure 5-3 montre un exemple de solution qui scinde l’application en trois projets par responsabilité (ou couche).

![Une simple application monolithique avec trois projets](./media/image5-3.png)

**Figure 5-3.** Application monolithique simple constituée de trois projets.

Même si cette application utilise plusieurs projets à des fins d’organisation, elle reste déployée en tant qu’unité simple et ses clients interagissent avec elle en la considérant comme une application web unique. Cela simplifie nettement le processus de déploiement. La figure 5-4 montre comment une application de ce type peut être hébergée en utilisant Azure.

![Déploiement simple d’une application web Azure](./media/image5-4.png)

**Figure 5-4.** Déploiement simple d’une application web Azure

Quand l’application doit grossir, des solutions de déploiement plus complexes et robustes peuvent être nécessaires. La figure 5-5 montre un exemple de plan de déploiement plus complexe qui prend en charge des fonctionnalités supplémentaires.

![Déploiement d’une application web sur Azure App Service](./media/image5-5.png)

**Figure 5-5.** Déploiement d’une application web sur Azure App Service

En interne, l’organisation de ce projet en plusieurs projets par responsabilité facilite la maintenance de l’application.

Il est possible d’augmenter ou de diminuer la taille des instances de cette unité pour tirer parti de l’extensibilité à la demande sur le cloud. L’augmentation de la taille des instances revient à ajouter de l’UC, de la mémoire, de l’espace disque ou d’autres ressources sur le ou les serveurs qui hébergent votre application. Le scale-out revient à ajouter des instances supplémentaires de ces serveurs, qu’il s’agisse de serveurs physiques, de machines virtuelles ou de conteneurs. Quand votre application est hébergée sur plusieurs instances, un équilibreur de charge assigne les requêtes aux différentes instances de l’application.

L’approche la plus simple pour mettre à l’échelle une application web dans Azure est de configurer la mise à l’échelle manuellement dans le plan App Service de l’application. La figure 5-6 illustre le tableau de bord Azure qui permet de configurer le nombre d’instances au service d’une application.

![App Service Plan mise à l’échelle à Azure](./media/image5-6.png)

**Figure 5-6.** Mise à l’échelle du plan App Service dans Azure.

## <a name="clean-architecture"></a>Architecture propre

Les applications conçues selon le principe d’inversion des dépendances et les principes DDD (conception pilotée par le domaine) présentent au final plus ou moins la même architecture. Les noms donnés à cette architecture ont beaucoup varié au fil des années. Au début, on l’a nommée architecture hexagonale, puis architecture ports-adaptateurs. Plus récemment, on l’a appelée [architecture en oignon](https://jeffreypalermo.com/blog/the-onion-architecture-part-1/) ou [architecture propre](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html). Cette dernière désignation, architecture propre, est celle utilisée pour qualifier l’architecture utilisée dans ce livre électronique.

L’application de référence eShopOnWeb utilise l’approche Clean Architecture dans l’organisation de son code en projets. Vous pouvez trouver un modèle de solution que vous pouvez utiliser comme point de départ pour votre propre ASP.NET Core sur le référentiel [GitHub ardalis/cleanarchitecture.](https://github.com/ardalis/cleanarchitecture)

L’architecture propre met la logique métier et le modèle d’application au centre même de l’application. Au lieu que la logique métier dépende des préoccupations de l’accès aux données ou d’une autre infrastructure, cette dépendance est inversée : les détails de l’infrastructure et de l’implémentation dépendent du noyau de l’application. Cela s’obtient par la définition d’abstractions, ou interfaces, dans la couche Noyau de l’application, lesquels sont ensuite implémentés par les types définis dans la couche Infrastructure. Cette architecture est souvent représentée sous la forme d’une série de cercles concentriques, à l’image des couches d’un oignon. La figure 5-7 montre un exemple de ce style de représentation architecturale.

![Architecture propre ; représentation des couches en oignon](./media/image5-7.png)

**Figure 5-7.** Architecture propre ; représentation des couches en oignon

Dans ce diagramme, le flux des dépendances va du cercle extérieur vers le cercle le plus intérieur. La couche Noyau de l’application tire son nom de sa position au cœur de ce diagramme. Par ailleurs, comme vous pouvez constater sur le diagramme, la couche Noyau de l’application n’a aucune dépendance vis-à-vis des autres couches de l’application. Les entités et les interfaces de l’application se trouvent au centre même du diagramme. Juste après vers l’extérieur, mais toujours dans la couche Noyau de l’application, viennent les services de domaine, qui implémentent généralement les interfaces définies dans le cercle central. À l’extérieur de la couche Noyau de l’application, les couches Interface utilisateur et Infrastructure dépendent toutes deux de la couche Noyau de l’application, mais elles ne dépendent pas (nécessairement) l’une de l’autre.

La figure 5-8-X illustre un diagramme de couches horizontal plus classique, qui reflète mieux la dépendance entre la couche Interface utilisateur et les autres couches.

![Architecture propre ; représentation horizontale des couches](./media/image5-8.png)

**Figure 5-8.** Architecture propre ; représentation horizontale des couches

Notez que les flèches pleines représentent les dépendances à la compilation, tandis que la flèche en pointillé représente une dépendance à l’exécution uniquement. Dans une architecture propre, la couche Interface utilisateur interagit avec les interfaces définies dans la couche Noyau de l’application au moment de la compilation. Dans l’idéal, elle ne doit pas avoir connaissance des types d’implémentation définis dans la couche Infrastructure. Or, au moment de l’exécution, ces types d’implémentation sont nécessaires à l’exécution de l’application. Ils doivent donc être définis et transmis aux interfaces de la couche Noyau de l’application via l’injection de dépendances.

La figure 5-9 est une représentation plus détaillée de l’architecture d’une application ASP.NET Core conçue selon ces recommandations.

![ASP.NET diagramme d’architecture de base suivant l’architecture propre](./media/image5-9.png)

**Figure 5-9.** Diagramme d’une architecture ASP.NET Core propre.

Comme la couche Noyau de l’application ne dépend pas de la couche Infrastructure, il est très facile d’écrire des tests unitaires automatisés pour cette couche. Les figures 5-10 et 5-11 montrent comment les tests s’intègrent à cette architecture.

![UnitTestCore](./media/image5-10.png)

**Figure 5-10.** Tests unitaires, couche Noyau de l’application isolée.

![IntegrationTests](./media/image5-11.png)

**Figure 5-11.** Tests d’intégration, implémentations dans Infrastructure avec des dépendances externes.

Comme la couche Interface utilisateur n’a pas de dépendance directe vis-à-vis des types définis dans le projet Infrastructure, il est tout aussi simple de permuter les implémentations, que ce soit pour faciliter les tests ou pour répondre à une évolution des exigences de l’application. Grâce à la prise en charge et à l’utilisation intégrée de l’injection de dépendances dans une application ASP.NET Core, cette architecture est la plus performante pour organiser des applications monolithiques non triviales.

Dans les applications monolithiques, les projets Noyau de l’application, Infrastructure et Interface utilisateur sont tous exécutés comme une seule application. La figure 5-12 illustre un exemple d’architecture d’exécution d’une application.

![Architecture ASPNET Core 2](./media/image5-12.png)

**Figure 5-12.** Exemple d’architecture d’exécution d’une application ASP.NET Core.

### <a name="organizing-code-in-clean-architecture"></a>Organisation du code dans une architecture propre

Dans une architecture propre, les responsabilités de chaque projet sont clairement établies. À cet effet, certains types sont communs à chaque projet et vous trouverez souvent plusieurs dossiers correspondant à ces types dans le projet en question.

La couche Noyau de l’application contient le modèle métier, qui définit les entités, les services et les interfaces. Ces interfaces comprennent des abstractions pour les opérations qui seront effectuées à l’aide d’infrastructure, telles que l’accès aux données, l’accès au système de fichiers, les appels réseau, etc. Parfois, les services ou les interfaces définis à cette couche devront fonctionner avec des types non-entités qui n’ont aucune dépendance à l’assurance-chômage ou à l’infrastructure. Ils peuvent alors être définis comme objets de transfert de données (DTO).

### <a name="application-core-types"></a>Types de la couche Noyau de l’application

- Entités (classes persistantes du modèle métier)
- Interfaces
- Services
- Objets DTO

Le projet Infrastructure inclut généralement des implémentations de l’accès aux données. Dans une application web ASP.NET Core conventionnelle, ces implémentations comprennent la classe DbContext d’Entity Framework (EF), les objets `Migration` EF Core qui ont été définis, ainsi que les classes d’implémentation de l’accès aux données. La méthode la plus courante pour abstraire le code d’implémentation de l’accès aux données est d’utiliser le [modèle de conception de référentiel](https://deviq.com/repository-pattern/).

En plus des implémentations de l’accès aux données, le projet Infrastructure doit contenir les implémentations des services qui interagissent avec les préoccupations de l’infrastructure. Ces services doivent implémenter les interfaces définies dans la couche Noyau de l’application, et la couche Infrastructure doit donc référencer le projet Noyau de l’application.

### <a name="infrastructure-types"></a>Types de la couche Infrastructure

- Types EF Core (`DbContext`, `Migration`)
- Types d’implémentation de l’accès aux données (référentiels)
- Services spécifiques de l’infrastructure (par exemple, `FileLogger` ou `SmtpNotifier`)

Dans une application ASP.NET Core MVC, la couche Interface utilisateur est le point d’entrée de l’application. Ce projet doit référencer le projet Noyau de l’application, et ses types doivent interagir avec l’infrastructure uniquement par le biais des interfaces définies dans la couche Noyau de l’application. Les instanciations directes des types de la couche Infrastructure (ou les appels statiques à ces types) ne doivent pas être autorisées dans la couche Interface utilisateur.

### <a name="ui-layer-types"></a>Types de la couche Interface utilisateur

- Controllers
- Filtres
- Les vues
- ViewModels
- Démarrage

La classe Démarrage est responsable de la configuration de l’application, mais aussi de la transmission des types d’implémentation jusqu’aux interfaces, pour permettre le fonctionnement correct de l’injection de dépendances au moment de l’exécution.

> [!NOTE]
> Pour configurer l’injection de dépendances dans la section ConfigureServices du fichier Startup.cs associé au projet Interface utilisateur, celui-ci doit référencer le projet Infrastructure. Cette dépendance peut très facilement être supprimée en utilisant un conteneur d’injection de dépendances personnalisé. Dans cet exemple, l’approche la plus simple est d’autoriser le projet Interface utilisateur à référencer le projet Infrastructure.

## <a name="monolithic-applications-and-containers"></a>Conteneurs et applications monolithiques

Vous pouvez créer une application (ou service) web unique et monolithique, et la déployer en tant que conteneur. En interne, l’application peut ne pas être monolithique, mais être organisée en bibliothèques, composants ou couches. D’un point de vue externe, l’application est considérée comme un conteneur unique, de la même façon qu’un processus, une application web ou un service unique.

Pour gérer ce modèle, vous déployez un seul conteneur pour représenter l’application. Pour effectuer une mise à l’échelle, vous ajoutez simplement des copies supplémentaires avec un équilibreur de charge en frontal. Cette simplicité provient de la gestion d’un seul déploiement dans un seul conteneur ou une seule machine virtuelle.

![Figure 5-13](./media/image5-13.png)

Vous pouvez inclure plusieurs couches internes, composants ou bibliothèques dans chaque conteneur, comme illustré dans la figure 5-13. Cependant, d’après le principe des conteneurs selon lequel « _un conteneur fait une chose et la fait dans un seul processus_ », ce modèle monolithique peut être une source de conflit.

Cette approche présente des inconvénients si/quand l’application grandit, nécessitant sa mise à l’échelle. Si l’application entière est mise à l’échelle, cela n’est pas vraiment un problème. Toutefois, dans la plupart des cas, la mise à l’échelle est nécessaire pour quelques parties de l’application seulement, mais elle est inutile pour d’autres composants moins utilisés.

Dans l’exemple classique du commerce électronique, c’est probablement le composant des informations produit qui a le plus besoin d’être mis à l’échelle. Les clients qui recherchent des produits sont beaucoup plus nombreux que ceux qui en achètent. Plus de clients utilisent leur panier d’achat que ceux qui utilisent le pipeline de paiement. Moins de clients ajoutent des commentaires ou consultent leur historique d’achat. De même, seule une poignée d’employés, d’une seule région, doivent généralement gérer le contenu et les campagnes marketing. La mise à l’échelle de la conception monolithique déploie tout le code plusieurs fois.

En plus du problème de la mise à l’échelle globale, quand des modifications sont apportées à un seul composant, il faut refaire un test complet de l’application entière et redéployer intégralement toutes les instances.

L’approche architecturale monolithique est fréquemment choisie pour le développement dans les organisations. Beaucoup de ces organisations sont satisfaites des résultats obtenus, mais certaines se heurtent aux limites de ce modèle d’architecture. Les organisations ont souvent conçu leurs applications d’après ce modèle, car les outils et l’infrastructure étaient trop complexes pour concevoir des architectures orientées services (SOA). Par ailleurs, elles ne voyaient pas la nécessité de changer de modèle tant que leur application ne grossissait pas trop. Si vous vous heurtez aux limites de l’approche monolithique, la prochaine étape logique pour vous est peut-être de scinder votre application pour mieux tirer parti des conteneurs et des microservices.

![Figure 5-14](./media/image5-14.png)

Le déploiement d’applications monolithiques dans Microsoft Azure est possible en utilisant des machines virtuelles dédiées pour chaque instance. Avec [Azure Virtual Machine Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), vous pouvez facilement mettre à l’échelle les machines virtuelles. [Azure App Service](https://azure.microsoft.com/services/app-service/) peut également exécuter des applications monolithiques et facilement mettre à l’échelle des instances sans nécessiter une gestion des machines virtuelles. Azure App Service peut également exécuter des instances uniques de conteneurs Docker, ce qui simplifie le déploiement. Avec Docker, vous pouvez déployer une seule machine virtuelle comme hôte Docker et exécuter plusieurs instances. Vous pouvez gérer la mise à l’échelle à l’aide de l’équilibreur de charge Azure, comme indiqué dans la figure 5-14.

Le déploiement sur les différents hôtes peut être géré avec les techniques de déploiement traditionnelles. Les hôtes Docker peuvent être gérés à l’aide de commandes exécutées manuellement, telles que **docker run**, ou de manière automatisée, comme les pipelines de livraison continue.

### <a name="monolithic-application-deployed-as-a-container"></a>Application monolithique déployée comme conteneur

L’utilisation de conteneurs pour gérer les déploiements d’applications monolithiques présente des avantages. La mise à l’échelle des instances des conteneurs est beaucoup plus rapide et facile que le déploiement de machines virtuelles supplémentaires. Même si vous utilisez des groupes de machines virtuelles identiques pour mettre à l’échelle des machines virtuelles, leur instanciation prend du temps. Quand une machine virtuelle est déployée en tant qu’instance de l’application, la configuration de l’application est gérée en interne par la machine virtuelle.

Le déploiement de mises à jour comme images Docker est beaucoup plus rapide et efficace du point de vue du réseau. Les images Docker démarrent généralement en quelques secondes, ce qui accélère les lancements. La suppression d’une instance Docker se fait simplement en exécutant une commande `docker stop`. Cette opération prend normalement moins d’une seconde.

Comme les conteneurs sont immuables de par leur conception même, il n’y a pas de risques d’endommagement des machines virtuelles, au contraire des scripts de mise à jour qui peuvent oublier de prendre en compte une configuration ou un fichier spécifique sur le disque.

Vous pouvez utiliser des conteneurs Docker pour effectuer un déploiement monolithique d’applications web simples. Cela a pour effet d’améliorer les pipelines d’intégration continue et de déploiement continu et cela contribuer à la réussite du déploiement en production. Pas plus "Il fonctionne sur ma machine, pourquoi ne fonctionne-t-il pas en production?"

Une architecture basée sur des microservices présente de nombreux avantages, mais ces avantages se payent par une complexité accrue. Dans certains cas, les coûts l’emportent sur les avantages, de sorte qu’il est préférable d’utiliser une application à déploiement monolithique s’exécutant dans un petit nombre de conteneurs, voire dans un seul conteneur.

Il n’est pas toujours évident de décomposer une application monolithique en plusieurs microservices bien distincts. Les microservices doivent fonctionner indépendamment les uns des autres pour optimiser la résilience de l’application. Si vous ne pouvez pas proposer l’application par tranches de fonctionnalités indépendantes, la diviser ne fait qu’ajouter de la complexité.

Une application n’est pas pour autant nécessairement amenée à mettre à l’échelle les fonctionnalités de façon indépendante. Bon nombre d’applications, quand elles ont besoin d’une mise à l’échelle qui va au-delà d’une instance unique, peuvent le faire par le biais du processus relativement simple de clonage intégral de cette instance. Le travail supplémentaire que demande la séparation de l’application en services discrets offre peu d’avantages, alors que la mise à l’échelle d’instances complètes de l’application est simple et économique.

Au stade initial du développement d’une application, vous n’avez peut-être pas une idée précise de là où se trouvent les limites fonctionnelles naturelles. Même à un stade de développement où le produit est viable, il est possible que cette séparation naturelle ne se dégage toujours pas. Certaines de ces conditions peuvent être passagères. Vous pouvez commencer par créer une application monolithique et séparer par la suite certaines fonctionnalités en les développant et les déployant sous forme de microservices. D’autres conditions peuvent être essentielles à l’espace de problème de l’application, ce qui signifie que l’application risque de ne jamais être divisée en plusieurs microservices.

Séparer une application en divers processus distincts induit aussi des coûts. Il est plus complexe de séparer des fonctionnalités en différents processus. Les protocoles de communication deviennent plus complexes. Au lieu d’appeler des méthodes, vous devez utiliser des communications asynchrones entre les services. Quand il s’agit de déplacer une architecture de microservices, vous devez ajouter la plupart des blocs de construction implémentés dans la version de microservices de l’application eShopOnContainers : gestion du bus d’événements, résilience des messages et nouvelles tentatives, cohérence éventuelle, etc.

L’[application de référence eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb), bien plus simple, prend en charge l’utilisation de conteneurs monolithiques uniques. L’application inclut une application web qui inclut les vues MVC, les API web et les pages Razor traditionnelles. Cette application peut être lancée à partir de la racine de la solution à l’aide des commandes `docker-compose build` et `docker-compose up`. Cette commande configure un conteneur pour l’instance web en utilisant le `Dockerfile` situé à la racine du projet web, et exécute le conteneur sur un port spécifié. Vous pouvez télécharger la source de cette application sur GitHub et l’exécuter localement. Même cette application monolithique gagne à être déployée dans un environnement de conteneurs.

Tout d’abord, un déploiement en conteneur signifie que chaque instance de l’application s’exécute dans le même environnement. Cela inclut l’environnement de développement dans lequel les tests de la première heure et le développement ont été réalisés. L’équipe de développement peut exécuter l’application dans un environnement à conteneurs qui correspond à l’environnement de production.

De plus, la montée en charge des applications en conteneur est moins coûteuse. L’environnement à conteneurs permet un meilleur partage des ressources que les environnements à machines virtuelles classiques.

Enfin, la mise en conteneur de l’application contraint à établir une séparation entre la logique métier et le serveur de stockage. À mesure que l’application monte en charge, les différents conteneurs dépendent tous d’un même support de stockage physique. Il s’agit généralement d’un serveur à haute disponibilité exécutant une base de données SQL Server.

## <a name="docker-support"></a>Prise en charge de Docker

Le projet `eShopOnWeb` s’exécute sur .NET Core. Par conséquent, il peut s’exécuter dans des conteneurs Linux ou Windows. Notez que pour le déploiement de Docker, vous devez utiliser le même type d’hôte pour SQL Server. Les conteneurs Linux offrent un plus faible encombrement et sont à privilégier.

Vous pouvez utiliser Visual Studio 2017 ou ultérieur pour ajouter la prise en charge de Docker à une application existante en cliquant avec le bouton droit sur un projet dans l’**Explorateur de solutions** et en choisissant **Ajouter** > **Prise en charge de Docker**. Les fichiers nécessaires sont alors ajoutés et le projet est modifié pour pouvoir les utiliser. Ces fichiers sont déjà en place dans l’exemple `eShopOnWeb` actuel.

Le fichier `docker-compose.yml` au niveau de la solution contient des informations sur les images à générer et les conteneurs à lancer. Ce fichier vous permet d’utiliser la commande `docker-compose` pour lancer plusieurs applications en même temps. Dans ce cas, il lance uniquement le projet Web. Vous pouvez aussi l’utiliser pour configurer des dépendances, telles qu’un conteneur de base de données distinct.

```yml
version: '3'

services:
  eshopwebmvc:
    image: eshopwebmvc
    build:
      context: .
      dockerfile: src/Web/Dockerfile
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
    ports:
      - "5106:5106"

networks:
  default:
    external:
      name: nat
```

Le fichier `docker-compose.yml` référence le `Dockerfile` dans le projet `Web`. Le `Dockerfile` sert à spécifier le conteneur de base qui sera utilisé et la façon dont l’application sera configurée dans ce dernier. Voici le `Dockerfile` de `Web` :

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /app

COPY *.sln .
COPY . .
WORKDIR /app/src/Web
RUN dotnet restore

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS runtime
WORKDIR /app
COPY --from=build /app/src/Web/out ./

ENTRYPOINT ["dotnet", "Web.dll"]
```

### <a name="troubleshooting-docker-problems"></a>Résolution des problèmes liés à Docker

Une fois exécutée, l’application en conteneur continue de s’exécuter jusqu’à ce que vous l’arrêtiez. Vous pouvez identifier les conteneurs qui s’exécutent avec la commande `docker ps`. Vous pouvez arrêter un conteneur en cours d’exécution à l’aide de la commande `docker stop` et en spécifiant son ID.

Notez que les conteneurs Docker en cours d’exécution peuvent être liés à des ports que vous pouvez tenter d’utiliser dans votre environnement de développement. Si vous essayez d’exécuter ou de déboguer une application en utilisant le même port qu’un conteneur Docker en cours d’exécution, vous obtiendrez une erreur indiquant que le serveur ne peut pas se lier à ce port. Une fois encore, l’arrêt du conteneur devrait résoudre le problème.

Si vous voulez ajouter la prise en charge de Docker à votre application à l’aide de Visual Studio, veillez à ce que Docker Desktop s’exécute pendant l’opération. L’Assistant ne fonctionnera pas correctement si Docker Desktop n’est pas en cours d’exécution lorsque vous démarrez l’Assistant. Par ailleurs, l’Assistant examine votre choix de conteneur actuel pour ajouter la prise en charge appropriée de Docker. Si vous voulez ajouter la prise en charge des conteneurs Windows, vous devez exécuter l’Assistant pendant que Docker Desktop s’exécute avec les conteneurs Windows configurés. Si vous voulez ajouter la prise en charge des conteneurs Linux, exécutez l’Assistant pendant que Docker s’exécute avec les conteneurs Linux configurés.

### <a name="references--common-web-architectures"></a>Informations de référence sur les architectures web courantes

- **The Clean Architecture**  
  <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
- **The Onion Architecture**  
  <https://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
- **Le modèle de dépôt**  
  <https://deviq.com/repository-pattern/>
- **Modèle de solution d’architecture propre**  
  <https://github.com/ardalis/cleanarchitecture>
- **Architecting Microservices (livre électronique)**  
  <https://aka.ms/MicroservicesEbook>
- **DDD (Domain-Driven Design)**  
  <https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/>

>[!div class="step-by-step"]
>[Suivant précédent](architectural-principles.md)
>[Next](common-client-side-web-technologies.md)

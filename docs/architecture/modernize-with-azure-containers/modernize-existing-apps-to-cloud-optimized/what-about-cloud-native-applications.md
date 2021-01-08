---
title: Présentation des applications cloud natives
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Qu’en est-il des applications Cloud-Native ?
ms.date: 12/21/2020
ms.openlocfilehash: 700d23c6b44f4eb48b3f6ec20569323280682082
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025184"
---
# <a name="what-about-cloud-native-applications"></a>Présentation des applications cloud natives

Bien que les applications [Cloud natives](https://azure.microsoft.com/overview/cloudnative/) ne soient pas le sujet principal de ce guide, il est utile d’avoir une bonne compréhension de ce niveau de maturité de modernisation et de les distinguer des applications Cloud-Optimized.

Figure 4-3 positions Cloud-Native applications dans les niveaux de maturité de modernisation des applications :

![Diagramme montrant comment positionner des applications Cloud natives.](./media/what-about-cloud-native-applications/positioning-cloud-native-applications.png)

**Figure 4-3.** Positionnement des applications Cloud-Native

Le niveau de maturité de modernisation Cloud-Native nécessite généralement de nouveaux investissements en développement. Le passage au niveau de la Cloud-Native est généralement piloté par les besoins de l’entreprise pour moderniser autant que possible les applications afin d’améliorer considérablement la mise à l’échelle dans les grandes applications en créant des sous-systèmes autonomes, qui peuvent être déployés et mis à l’échelle indépendamment des autres zones de l’application, tout en réduisant les coûts à long terme et en augmentant l’agilité des parties

Les principaux piliers des applications Cloud-Native sont basés sur les approches de l’architecture des microservices, qui peuvent évoluer en fonction de l’agilité et de la mise à l’échelle vers des limites difficiles à atteindre dans une architecture monolithique, déployées dans un environnement local ou dans le Cloud.

La figure 4-4 montre les principales caractéristiques du modèle de Cloud-Native.

![Diagramme répertoriant les principales caractéristiques Cloud-natives.](./media/what-about-cloud-native-applications/cloud-native-characteristics.png)

**Figure 4-4.** Caractéristiques de Cloud-Native

En outre, vous pouvez étendre des applications Web modernes de base et des applications Cloud natives en ajoutant d’autres services, tels que l’intelligence artificielle (IA), le Machine Learning (ML) et l’IoT. Vous pouvez utiliser l’un de ces services pour étendre l’une des approches de Cloud-Optimized possibles.

La différence fondamentale dans les applications au niveau de l' Cloud-Native réside dans l’architecture de l’application. Les applications Cloud natives sont, par définition, des applications basées sur des microservices. Les applications Cloud natives nécessitent des architectures, des technologies et des plateformes spéciales, par rapport à une application Web monolithique ou à une application multiniveau traditionnelle.

## <a name="cloud-native-applications-details"></a>Détails des applications Cloud-natives

Cloud-Native est un État plus avancé ou mature pour les applications importantes et stratégiques. Les applications Cloud-Native nécessitent généralement une architecture et une conception créées à partir de zéro au lieu de moderniser les applications existantes. La principale différence entre une application Cloud-Native et une application Web Cloud-Optimized plus simple est la recommandation d’utiliser les architectures de microservices dans une approche Cloud native. Les applications Cloud-Optimized peuvent également être des applications Web monolithiques ou des applications multiniveaux.

L' [application à 12 facteurs](https://12factor.net/) (une collection de modèles étroitement liés aux approches des microservices) est également considérée comme une exigence pour les architectures d’application natives du Cloud.

[CNCF (Cloud Native Computing Foundation)](https://www.cncf.io/) est un promoteur principal des principes natifs du Cloud. Microsoft est [membre du CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Pour obtenir des instructions détaillées sur la conception et le développement d’applications Cloud natives, lisez les livres électroniques gratuits suivants :

* [Architecture des applications Cloud-Native .NET pour Azure](../../cloud-native/introduction.md)
* [Microservices .net : architecture pour les applications .net en conteneur](../../microservices/index.md).

Le facteur le plus important à prendre en compte si vous migrez une application complète vers le modèle natif du Cloud est que vous devez remanier une architecture basée sur des microservices. Cette approche nécessite clairement un investissement significatif en développement, en raison du processus de refactorisation important impliqué. Cette option est généralement choisie pour les applications stratégiques qui ont besoin de nouveaux niveaux d’évolutivité et d’agilité à long terme. Toutefois, vous pouvez commencer à passer à Cloud-Native en ajoutant des microservices pour quelques nouveaux scénarios et finalement refactoriser l’application en tant que microservices. Cette étape est une approche incrémentielle qui est la meilleure option pour certains scénarios.

## <a name="what-about-microservices"></a>Qu’en est-il des microservices ?

Il est important de comprendre les microservices et leur fonctionnement lorsque vous envisagez d’utiliser des applications Cloud natives pour votre organisation.

L’architecture de microservices est une approche avancée que vous pouvez utiliser pour les applications créées à partir de zéro ou lorsque vous faites évoluer des applications existantes vers des applications Cloud natives. Vous pouvez commencer par ajouter quelques microservices aux applications existantes pour en savoir plus sur les nouveaux paradigmes de microservices. Mais en clair, vous devez concevoir et coder, en particulier pour ce type d’approche architecturale.

Toutefois, les microservices ne sont pas obligatoires pour une application nouvelle ou moderne. Les microservices ne sont pas un « Magic Bullet », et ils ne constituent pas le moyen le plus simple de créer chaque application. La façon dont et quand vous utilisez les microservices dépend du type d’application que vous devez générer.

L’architecture de microservices devient l’approche préférée pour les applications stratégiques distribuées et volumineuses ou complexes qui sont basées sur plusieurs sous-systèmes indépendants, sous la forme de services autonomes. Dans une architecture basée sur des microservices, une application est construite sous la forme d’une collection de services qui peuvent être développés, testés, mis à niveau, déployés et mis à l’échelle indépendamment. Cette approche peut inclure toutes les bases de données autonomes et associées par Microservice.

Pour plus d’informations sur une architecture de microservices que vous pouvez implémenter à l’aide de .NET, consultez les microservices .net PDF téléchargeables [: architecture pour les applications .net en conteneur](https://aka.ms/microservicesebook). Le guide est également disponible [en ligne](../../microservices/index.md).

Toutefois, même dans les scénarios où les microservices offrent des fonctionnalités puissantes, des limites de sous-systèmes fortes et une diversité technologique, elles soulèvent également de nombreux défis. Les défis sont liés au développement d’applications distribuées, telles que les modèles de données fragmentés et indépendants. obtenir une communication résiliente entre les microservices ; la nécessité d’une cohérence éventuelle ; et de la complexité opérationnelle. Les microservices présentent un niveau de complexité supérieur par rapport aux applications monolithiques traditionnelles.

En raison de la complexité d’une architecture de microservices, seuls des scénarios spécifiques et certains types d’applications sont appropriés pour les applications basées sur des microservices. Celles-ci incluent des applications volumineuses et complexes qui ont plusieurs sous-systèmes évolutifs. Dans ce cas, il est intéressant d’investir dans une architecture logicielle plus complexe, pour une agilité à long terme accrue et une maintenance plus efficace des applications. Mais pour les scénarios moins complexes, il peut être préférable de continuer avec une approche d’application monolithique ou des approches à plusieurs niveaux plus simples.

En guise de note finale, même au risque d’être répétitif sur ce concept, vous ne devriez pas examiner l’utilisation de microservices dans vos applications en tant que « tout ou rien du tout ». Vous pouvez étendre et faire évoluer des applications monolithiques existantes en ajoutant de petits scénarios basés sur les microservices. Vous n’avez pas besoin de commencer à partir de zéro pour commencer à utiliser une approche basée sur une architecture de microservices. En fait, nous vous recommandons d’évoluer de l’utilisation d’une application monolithique ou multicouche existante en ajoutant de nouveaux scénarios. Finalement, vous pouvez décomposer l’application en composants autonomes ou en microservices. Vous pouvez commencer à évoluer vos applications monolithiques dans une direction de microservices, étape par étape.

Dans tous les cas, le reste de ce guide se concentre sur la plupart des « aucune application basée sur des microservices », car ce guide vise principalement à viser la modernisation des applications existantes qui ont généralement des architectures monolithiques ou multiniveaux.

> [!div class="step-by-step"]
> [Précédent](microsoft-technologies-in-cloud-optimized-applications.md) 
>  [Suivant](deploy-existing-net-apps-as-windows-containers.md)

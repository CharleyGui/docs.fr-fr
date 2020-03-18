---
title: Présentation des applications cloud natives
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Qu’en est-il des applications Cloud-Native?
ms.date: 04/28/2018
ms.openlocfilehash: d2a7f89e347d75ddbdae84c8eb57e32447b83297
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543545"
---
# <a name="what-about-cloud-native-applications"></a>Présentation des applications cloud natives

Bien que les applications [Cloud-Native](https://azure.microsoft.com/overview/cloudnative/) ne soient pas au centre de ce guide, il est utile de comprendre ce niveau de maturité de modernisation et de le distinguer des applications optimisées pour le Cloud.

Figure 4-3 positionne les applications Cloud-Native dans les niveaux de maturité de modernisation de l’application :

![Diagramme montrant comment positionner les applications cloud-native.](./media/what-about-cloud-native-applications/positioning-cloud-native-applications.png)

**Figure 4-3.** Positionnement des applications Cloud-Native

Le niveau de maturité de modernisation Cloud-Native nécessite généralement de nouveaux investissements dans le développement. Le passage au niveau Cloud-Native est généralement motivé par la nécessité pour les entreprises de moderniser les applications autant que possible afin d’améliorer considérablement l’échelle dans les applications de grande envergure en créant des sous-systèmes autonomes (microservices) qui peuvent être déployés et évoluer de façon indépendante d’autres domaines de l’application tout en réduisant les coûts à long terme et en accroissant l’agilité de l’évolution des pièces de ces applications autonomes qui offrent des avantages concurrentiels significatifs.

Les principaux piliers des applications Cloud-Native sont basés sur des approches d’architecture de microservices, qui peuvent évoluer avec agilité et échelle vers des limites qui seraient difficiles à atteindre dans une architecture monolithique, déployée sur place ou en nuage Environnement.

La figure 4-4 montre les principales caractéristiques du modèle Cloud-Native.

![Diagramme énumérant les principales caractéristiques cloud-native.](./media/what-about-cloud-native-applications/cloud-native-characteristics.png)

**Figure 4-4.** Caractéristiques cloud-Native

En outre, vous pouvez étendre les applications Web modernes de base et les applications cloud-native en ajoutant d’autres services, comme l’intelligence artificielle (IA), l’apprentissage automatique (ML), et IoT. Vous pouvez utiliser l’un de ces services pour étendre l’une ou l’autre des approches possibles optimisées pour le Cloud.

La différence fondamentale dans les applications au niveau Cloud-Native réside dans l’architecture de l’application. Les applications cloud-natives sont, par définition, des applications basées sur des microservices. Les applications cloud-natives nécessitent des architectures, des technologies et des plates-formes spéciales, par rapport à une application web monolithique ou une application traditionnelle N-Tier.

## <a name="cloud-native-applications-details"></a>Détails des applications cloud-native

Cloud-Native est un état plus avancé ou mature pour les applications grandes et essentielles à la mission. Les applications Cloud-Native nécessitent généralement une architecture et un design qui sont créés à partir de zéro plutôt que par la modernisation des applications existantes. La principale différence entre une application Cloud-Native et une application Web Cloud-Optimized plus simple est la recommandation d’utiliser des architectures de microservices dans une approche cloud-native. Les applications optimisées pour le cloud peuvent également être des applications Web monolithiques ou des applications N-Tier.

[L’application Twelve-Factor](https://12factor.net/) (une collection de modèles étroitement liés aux approches des microservices) est également considérée comme une exigence pour les architectures d’applications cloud-native.

La [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) est l’un des principaux promoteurs de principes cloud-natives. Microsoft est [membre de la CNCF](https://azure.microsoft.com/blog/announcing-cncf/).

Pour obtenir des conseils détaillés sur la façon de concevoir et de développer des applications cloud-native, lisez les e-books gratuits suivants :

* [Architecting Cloud-Native .NET Applications for Azure](../../cloud-native/introduction.md)
* [.NET Microservices: Architecture pour les applications conteneurisées .NET](../../microservices/index.md).

Le facteur le plus important à considérer si vous migrez une application complète vers le modèle cloud-native est que vous devez réararchitect à une architecture basée sur les microservices. Cela exige clairement un investissement important dans le développement en raison de l’important processus de refactoration en cause. Cette option est généralement choisie pour les applications essentielles à la mission qui ont besoin de nouveaux niveaux d’évolutivité et d’agilité à long terme. Mais, vous pourriez commencer à se déplacer vers le cloud-native en ajoutant des microservices pour seulement quelques nouveaux scénarios, et finalement refactor l’application entièrement comme microservices. Il s’agit d’une approche progressive qui est la meilleure option pour certains scénarios.

## <a name="what-about-microservices"></a>Qu’en est-il des microservices?

Il est important de comprendre les microservices et leur fonctionnement lorsque vous envisagez des applications cloud-natives pour votre organisation.

L’architecture des microservices est une approche avancée que vous pouvez utiliser pour des applications qui sont créées à partir de zéro ou lorsque vous évoluez applications existantes vers des applications cloud-native. Vous pouvez commencer par ajouter quelques microservices aux applications existantes pour en apprendre davantage sur les nouveaux paradigmes des microservices. Mais clairement, vous devez architecte et code, en particulier pour ce type d’approche architecturale.

Cependant, les microservices ne sont pas obligatoires pour toute application nouvelle ou moderne. Les microservices ne sont pas une « balle magique », et ils ne sont pas la seule, meilleure façon de créer chaque application. Comment et quand vous utilisez des microservices dépend du type d’application que vous devez construire.

L’architecture des microservices devient l’approche privilégiée pour les applications distribuées et importantes ou complexes de mission critiques qui sont basées sur de multiples sous-systèmes indépendants sous la forme de services autonomes. Dans une architecture basée sur les microservices, une application est conçue comme une collection de services qui peuvent être développés, testés, versions, déployés et mis à l’échelle de façon indépendante. Cela peut inclure n’importe quelle base de données autonome par microservice.

Pour un regard détaillé sur une architecture de microservices que vous pouvez mettre en œuvre en utilisant .NET Core, voir le téléchargement PDF e-book [.NET microservices: Architecture pour les applications conteneurisées .NET](https://aka.ms/microservicesebook). Le guide est également disponible [en ligne](../../microservices/index.md).

Mais même dans les scénarios dans lesquels les microservices offrent un déploiement indépendant de puissantes capacités, de solides limites de sous-systèmes et la diversité technologique, ils soulèvent également de nombreux nouveaux défis. Les défis sont liés à l’élaboration d’applications distribuées, telles que des modèles de données fragmentés et indépendants; assurer une communication résiliente entre les microservices; la nécessité d’une cohérence éventuelle; et la complexité opérationnelle. Les microservices introduisent un niveau de complexité plus élevé par rapport aux applications monolithiques traditionnelles.

En raison de la complexité d’une architecture de microservices, seuls des scénarios spécifiques et certains types d’applications conviennent aux applications basées sur le microservice. Il s’agit notamment d’applications grandes et complexes qui ont plusieurs sous-systèmes en évolution. Dans ces cas, il vaut la peine d’investir dans une architecture logicielle plus complexe, pour une agilité à long terme accrue et une maintenance d’application plus efficace. Mais pour des scénarios moins complexes, il serait peut-être préférable de poursuivre avec une approche d’application monolithique ou des approches N-Tier plus simples.

Comme une note finale, même au risque d’être répétitif au sujet de ce concept, vous ne devriez pas envisager d’utiliser les microservices dans vos applications comme «all-in ou rien du tout." Vous pouvez étendre et faire évoluer les applications monolithiques existantes en ajoutant de nouveaux petits scénarios basés sur les microservices. Vous n’avez pas besoin de partir de zéro pour commencer à travailler avec une approche d’architecture de microservices. En fait, nous vous recommandons d’évoluer à partir de l’utilisation d’une application monolithique ou N-Tier existante en ajoutant de nouveaux scénarios. Finalement, vous pouvez décomposer l’application en composants autonomes ou microservices. Vous pouvez commencer à faire évoluer vos applications monolithiques dans une direction de microservices, étape par étape.

Dans tous les cas, le reste de ces directives actuelles se concentre surtout sur "pas d’applications basées sur les microservices" parce que cette orientation vise principalement la modernisation des applications existantes qui ont généralement des architectures monolithiques ou N-Tier.

> [!div class="step-by-step"]
> [Suivant précédent](microsoft-technologies-in-cloud-optimized-applications.md)
> [Next](deploy-existing-net-apps-as-windows-containers.md)

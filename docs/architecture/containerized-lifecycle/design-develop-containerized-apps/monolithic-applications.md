---
title: Applications monolithiques
description: Comprenez les principes de base de la mise en conteneur des applications monolithiques.
ms.date: 08/06/2020
ms.openlocfilehash: c9a5baf209a47f62f421a236c0b04fe5dae37e3a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163542"
---
# <a name="monolithic-applications"></a>Applications monolithiques

Dans ce scénario, vous créez un service ou une application web unique et monolithique et le/la déployer en tant que conteneur. Au sein de l’application, la structure peut ne pas être monolithique ; elle peut être constituée de plusieurs bibliothèques, de plusieurs composants ou même de plusieurs couches (couche d’application, couche de domaine, couche d’accès aux données, etc.). D’un point de vue externe, l’application est considérée comme un conteneur unique, de la même façon qu’un processus, une application web ou un service unique.

Pour gérer ce modèle, vous déployez un seul conteneur pour représenter l’application. Pour le mettre à l’échelle, ajoutez simplement quelques copies supplémentaires avec un équilibreur de charge en frontal. Cette simplicité est liée au fait qu’un même déploiement est géré dans un seul conteneur ou une seule machine virtuelle.

En suivant le principe selon lequel un conteneur fait une seule chose à la fois et dans un processus unique, le modèle monolithique est en conflit. Vous pouvez inclure plusieurs composants/bibliothèques ou couches internes dans chaque conteneur, comme illustré dans la figure 4-1.

![Diagramme montrant une application monolithique qui se met à l’échelle en clonant l’application.](./media/monolithic-applications/monolithic-application-architecture-example.png)

**Figure 4-1.** Exemple d’architecture d’application monolithique

La plupart sinon la totalité des fonctionnalités d’une application monolithique se trouvent dans un processus ou un conteneur unique et sont organisées en composants dans des couches ou des bibliothèques internes. L’inconvénient de cette approche se manifeste si ou quand l’application grandit, ce qui nécessite une mise à l’échelle. Si l’application entière est mise à l’échelle, ce n’est pas vraiment un problème. Or, dans la plupart des cas, seules quelques parties de l’application formant les goulots d’étranglement ont besoin d’être mises à l’échelle, alors que les autres composants sont moins utilisés.

Dans l’exemple type du commerce électronique, c’est probablement le composant des informations produit qui aurait le plus besoin d’être mis à l’échelle. Les clients qui recherchent des produits sont beaucoup plus nombreux que ceux qui en achètent. Plus de clients utilisent leur panier d’achat que ceux qui utilisent le pipeline de paiement. Moins de clients ajoutent des commentaires ou consultent leur historique d’achat. De même, seule une poignée d’employés, dans une même région, doivent généralement gérer le contenu et les campagnes marketing. En mettant à l’échelle la conception monolithique, l’ensemble du code est déployé plusieurs fois.

Outre le problème de la mise à l’échelle globale, quand des modifications sont apportées à un seul composant, il faut refaire un test complet de l’application entière, mais aussi redéployer intégralement toutes les instances.

L’approche monolithique est courante, et nombreuses sont les organisations qui développent avec cette méthode architecturale. Si la plupart d’entre elles obtiennent des résultats satisfaisants, d’autres rencontrent des limites. Les organisations ont souvent conçu leurs applications selon ce modèle, car les outils et l’infrastructure étaient trop complexes pour concevoir des architectures orientées services (SOA). Par ailleurs, elles ne voyaient pas la nécessité de changer de modèle tant que leur application ne grossissait pas trop.

Du point de vue de l’infrastructure, chaque serveur peut exécuter de nombreuses applications dans le même hôte et offrir un ratio d’efficacité acceptable dans l’utilisation des ressources, comme le montre la figure 4-2.

![Diagramme montrant un hôte avec plusieurs applications dans des conteneurs distincts.](./media/monolithic-applications/host-with-multiple-apps-containers.png)

**Figure 4-2.** Hôte exécutant plusieurs applications/conteneurs

Enfin, du point de vue de la disponibilité, les applications monolithiques doivent être déployées dans leur intégralité ; autrement dit, si vous devez les *arrêter et démarrer*, toutes les fonctionnalités et tous les utilisateurs seront affectés pendant la fenêtre de déploiement. Dans certaines situations, l’utilisation d’Azure et de conteneurs peut en limiter les effets et réduire la probabilité que votre application subisse des temps d’arrêt, comme le montre la figure 4-3.

Vous pouvez déployer les applications monolithiques dans Azure en utilisant des machines virtuelles dédiées pour chaque instance. En utilisant [Azure Virtual Machine Scale Sets](/azure/virtual-machine-scale-sets/), vous pouvez facilement mettre à l’échelle les machines virtuelles.

Vous pouvez aussi utiliser [Azure App Services](https://azure.microsoft.com/services/app-service/) pour exécuter des applications monolithiques et mettre facilement à l’échelle les instances sans avoir à gérer les machines virtuelles. Azure App Services peut également exécuter des instances uniques de conteneurs Docker, ce qui simplifie le déploiement.

Vous pouvez déployer plusieurs machines virtuelles en tant qu’hôtes Docker et exécuter n’importe quel nombre de conteneurs par machine virtuelle. Ensuite, en utilisant Azure Load Balancer, comme illustré dans la Figure 4-3, vous pouvez gérer la mise à l’échelle.

![Diagramme montrant une application monolithique montée en charge sur différents hôtes.](./media/monolithic-applications/multiple-hosts-from-single-docker-container.png)

**Figure 4-3**. Plusieurs hôtes montée en charge d’une seule application d’ancrage

Vous pouvez gérer le déploiement des hôtes proprement dits via des techniques de déploiement classiques.

Vous pouvez assurer la gestion des conteneurs Docker depuis la ligne de commande en utilisant des commandes comme `docker run` et `docker-compose up`, et vous pouvez aussi l’automatiser dans des pipelines de livraison continue et effectuer un déploiement sur des hôtes Docker à partir d’Azure DevOps Services, par exemple.

## <a name="monolithic-application-deployed-as-a-container"></a>Application monolithique déployée comme conteneur

L’utilisation de conteneurs pour gérer les déploiements monolithiques présente des avantages. La mise à l’échelle des instances des conteneurs est beaucoup plus rapide et facile que le déploiement de machines virtuelles supplémentaires.

Le déploiement de mises à jour comme images Docker est beaucoup plus rapide et efficace du point de vue du réseau. Les conteneurs Docker démarrent généralement en quelques secondes, ce qui accélère les lancements. La suppression d’un conteneur Docker se fait simplement en appelant la commande `docker stop`. Cette opération prend généralement moins d’une seconde.

Les conteneurs étant immuables par conception, vous n’avez jamais à vous soucier d’un endommagement de machines virtuelles à cause d’un script de mise à jour qui aurait oublié de prendre en compte une configuration spécifique ou un fichier laissé sur le disque.

Bien que les applications monolithiques puissent tirer parti de Docker, nous n’en évoquons que les avantages les plus évidents. Les principaux avantages de la gestion des conteneurs viennent de la possibilité de déployer avec des orchestrateurs de conteneurs qui gèrent les différentes instances et le cycle de vie de chaque instance de conteneur. La décomposition de l’application monolithique en sous-systèmes qui peuvent être mis à l’échelle, développés et déployés individuellement est votre point d’entrée dans le domaine des microservices.

Pour en savoir plus sur la façon de développer des applications monolithiques avec des conteneurs et sur la façon dont vous pouvez moderniser vos applications, vous pouvez lire ce guide Microsoft supplémentaire, [moderniser les applications .NET existantes avec des conteneurs Cloud et Windows Azure](../../modernize-with-azure-containers/index.md), que vous pouvez également télécharger au format PDF à partir de <https://aka.ms/LiftAndShiftWithContainersEbook> .

## <a name="publish-a-single-docker-container-app-to-azure-app-service"></a>Publier une application conteneur Docker unique sur Azure App Service

Que vous vouliez obtenir une validation rapide d’un conteneur déployé sur Azure ou que vous disposiez d’une application à un seul conteneur, Azure App Services offre un excellent moyen de fournir des services scalables à conteneur unique.

L’utilisation d’Azure App Service s’avère intuitive et vous permet d’être rapidement opérationnel. En effet, grâce à sa parfaite intégration de Git, votre code est généré dans Microsoft Visual Studio et directement déployé dans Azure. En revanche, par le passé (avant Docker), si vous aviez besoin d’autres fonctionnalités, frameworks ou dépendances qui n’étaient pas prises en charge dans App Services, vous deviez attendre que l’équipe Azure mette à jour ces dépendances dans App Service ou vous tourner vers d’autres services comme Service Fabric, Cloud Services, voire de simples machines virtuelles, que vous pouviez mieux contrôler et sur lesquelles vous pouviez installer le composant ou le framework dont avait besoin votre application.

Désormais, comme le montre la figure 4-4, quand vous utilisez Visual Studio 2017, la prise en charge des conteneurs dans Azure App Service vous offre la possibilité d’inclure tout ce que vous voulez dans l’environnement de votre application. Si vous avez ajouté une dépendance à votre application, parce que vous l’exécutez dans un conteneur, vous avez la possibilité d’inclure ces dépendances dans votre fichier Dockerfile ou image Docker.

![Capture d’écran de la boîte de dialogue créer un App Service montrant une Container Registry.](./media/monolithic-applications/publish-azure-app-service-container.png)

**Figure 4-4**. Publication d’un conteneur dans Azure App Service à partir d’applications/conteneurs Visual Studio

La figure 4-4 montre aussi que le flux de publication pousse (push) une image via un registre de conteneurs, qui peut être Azure Container Registry (registre proche de vos déploiements dans Azure et sécurisé par des comptes et des groupes Azure Active Directory) ou tout autre registre Docker, comme Docker Hub ou des registres locaux.

>[!div class="step-by-step"]
>[Précédent](common-container-design-principles.md) 
> [Suivant](state-and-data-in-docker-applications.md)

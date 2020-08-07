---
title: Conteneurs, images et registres Docker
description: Découvrez le rôle clé que jouent globalement les registres dans la façon dont Docker déploie les applications.
ms.date: 08/06/2020
ms.openlocfilehash: 2ff6cf76b35777546b6e653d477a029296f8e496
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87915247"
---
# <a name="docker-containers-images-and-registries"></a>Conteneurs, images et registres Docker

Quand vous utilisez Docker, vous créez une application ou un service, que vous empaquetez ensuite avec les dépendances associées dans une image conteneur. Une image est une représentation statique de l’application ou du service, de leur configuration et de leurs dépendances.

Pour exécuter l’application ou le service, l’image de l’application est instanciée, créant ainsi un conteneur à exécuter sur l’hôte Docker. Les conteneurs sont initialement testés sur une machine ou un environnement de développement.

Vous stockez des images dans un registre qui agit en tant que bibliothèque d’images. Vous avez besoin d’un registre lors du déploiement sur des orchestrateurs de production. Docker gère un registre public via [Docker Hub](https://hub.docker.com/). D’autres fournisseurs proposent des registres pour différentes collections d’images, notamment [Azure Container Registry](https://azure.microsoft.com/services/container-registry/). Les entreprises peuvent également gérer un registre privé local pour stocker leurs propres images Docker.

La figure 1-4 montre les liens entre les images et registres Docker et les autres composants. Elle montre également les divers registres des autres fournisseurs.

![Diagramme montrant la taxonomie de base dans l’ancrage.](./media/docker-containers-images-and-registries/taxonomy-docker-terms-concepts.png)

**Figure 1-4**. Taxonomie des termes et concepts Docker

le registre est semblable à une bibliothèque où les images sont stockées et peuvent être extraites pour générer des conteneurs afin d’exécuter les services ou les applications web. Il existe des registres Docker privés en local et sur le cloud public. Docker Hub est un registre public géré par Docker, tout comme Docker Trusted Registry, une solution de classe d’entreprise, Azure propose Azure Container Registry. AWS, Google et d’autres ont également des registres de conteneurs.

En plaçant des images dans un registre, vous pouvez stocker les bits d’application statiques et immuables, y compris toutes les dépendances, au niveau du framework. Ensuite, vous pouvez versionner et déployer les images dans différents environnements, offrant ainsi une unité de déploiement cohérente.

L’utilisation de registres d’images privés, hébergés localement ou dans le cloud, est recommandée dans les situations suivantes :

- Vous ne voulez pas partager vos images publiquement pour des raisons de confidentialité.

- Vous souhaitez limiter la latence du réseau entre vos images et l’environnement de déploiement choisi. Par exemple, si votre environnement de production est Azure, vous souhaiterez probablement stocker vos images dans [Azure Container Registry](https://azure.microsoft.com/services/container-registry/) pour réduire au maximum la latence du réseau. De la même manière, si votre environnement de production est local, vous souhaiterez peut-être disposer d’un service Docker Trusted Registry local dans le même réseau local.

>[!div class="step-by-step"]
>[Précédent](docker-terminology.md) 
> [Suivant](road-to-modern-applications-based-on-containers.md)

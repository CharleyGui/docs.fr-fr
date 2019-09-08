---
title: Présentation de Docker
description: Cet article présente Docker et en brosse une vue d’ensemble dans le contexte d’une application .NET Core.
ms.date: 03/20/2019
ms.custom: mvc, seodec18
ms.openlocfilehash: 5da71215e3b539f10993677d23d89e2b8a49cb39
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799370"
---
# <a name="introduction-to-net-and-docker"></a>Introduction à .NET et à Docker

.NET Core peut s’exécuter sans problème dans un conteneur Docker. Les conteneurs offrent un moyen léger d’isoler une application du reste du système hôte, en partageant seulement le noyau et en utilisant les ressources attribuées à l’application. Si vous ne connaissez pas encore Docker, nous vous recommandons de lire la [documentation de présentation](https://docs.docker.com/engine/docker-overview/) de Docker.

Pour plus d’informations sur l’installation de Docker, voir la page de téléchargement de [Docker Desktop : Community Edition](https://www.docker.com/products/docker-desktop).

## <a name="docker-basics"></a>Bases de Docker

Il y a quelques concepts à connaître. Le client Docker comporte un programme d’interface de ligne de commande permettant de gérer les images et les conteneurs. Prenez bien le temps de lire la documentation de [présentation de Docker](https://docs.docker.com/engine/docker-overview/). 

### <a name="images"></a>Images

Une image est une collection ordonnée de modifications du système de fichiers qui constituent la base d’un conteneur. Elle n’a pas d’état et est en lecture seule. La plupart du temps, une image est basée sur une autre image, mais avec une certaine personnalisation. Si vous vouliez créer une image pour votre application, par exemple, vous partiriez d’une image existante contenant déjà le runtime .NET Core.

Les conteneurs étant créés à partir d’images, celles-ci comportent un ensemble de paramètres d’exécution (par exemple, un exécutable de démarrage) qui s’exécutent au démarrage du conteneur.

### <a name="containers"></a>Containers

Un conteneur est une instance exécutable d’une image. Lorsque vous générez votre image, vous déployez votre application et ses dépendances. Il est ensuite possible d’instancier plusieurs conteneurs, tous isolés les uns des autres. Chaque instance de conteneur possède son propre système de fichiers, sa propre mémoire et sa propre interface réseau.

### <a name="registries"></a>Registres

Les registres de conteneurs sont une collection de référentiels d’images. Vous pouvez baser vos images sur une image de registre. Il est possible de créer directement des conteneurs à partir d’une image d’un registre. La [relation entre les conteneurs, les images et les Registres Docker](../../architecture/microservices/container-docker-introduction/docker-containers-images-registries.md) est un concept important pour la [conception et création d’applications ou de microservices en conteneur](../../architecture/microservices/architect-microservice-container-applications/index.md). Cette approche réduit considérablement le temps nécessaire entre le développement et le déploiement.

Docker offre un registre public hébergé sur [Docker Hub](https://hub.docker.com/), où sont listées les [images associées à .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/). 

Microsoft Container Registry (MCR) est la source officielle d’images conteneur fournies par Microsoft. Il repose sur Azure CDN pour offrir des images répliquées de façon globale. Toutefois, il n’a pas de site web public ; le meilleur moyen d’en savoir plus sur les images conteneur fournie par Microsoft consiste à passer par les [pages Microsoft Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).

### <a name="dockerfile"></a>Dockerfile

Un **Dockerfile** est un fichier définissant un ensemble d’instructions qui créent une image. Chaque instruction du **Dockerfile** produit une couche de l’image. La plupart du temps, la reconstruction d’une image ne concerne que les couches modifiées. Le **Dockerfile** peut être distribué auprès d’autres personnes, qui peuvent ainsi créer une image de la même manière que la première. Si cette solution permet de diffuser les *instructions* sur la création de l’image, le principal moyen d’en distribuer une consiste à la publier dans un registre.

## <a name="net-core-images"></a>Images .NET Core

Les images Docker .NET Core officielles sont publiées dans Microsoft Container Registry (MCR) et détectables dans le [référentiel Docker Hub Microsoft .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/). Chaque référentiel contient des images pour différentes combinaisons possibles de .NET (kit de développement logiciel ou runtime) et du système d’exploitation. 

Microsoft fournit des images adaptées à des scénarios particuliers. Par exemple, celles du [référentiel ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) sont conçues pour exécuter des applications ASP.NET Core en production.

## <a name="azure-services"></a>Services Azure

Différents services Azure prennent en charge les conteneurs. Créez une image Docker pour votre application et déployez-la sur l’un des services suivants :

* [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/)\
Mettez à l’échelle et orchestrez des conteneurs Linux avec Kubernetes.

* [Azure App Service](https://azure.microsoft.com/services/app-service/containers/)\
Déployez des API ou des applications web avec des conteneurs Linux dans un environnement PaaS.

* [Azure Container Instances](https://azure.microsoft.com/services/container-instances/)\
Hébergez votre conteneur dans le cloud sans les services de gestion de niveau supérieur.

* [Azure Batch](https://azure.microsoft.com/services/batch/)\
Exécutez des tâches de calcul répétitives avec des conteneurs.

* [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/)\
Effectuez un lift-and-shift et modernisez des applications .NET en microservices avec des conteneurs Windows Server.

* [Azure Container Registry](https://azure.microsoft.com/services/container-registry/)\
Stockez et gérez des images conteneurs pour tous types de déploiements Azure.

## <a name="next-steps"></a>Étapes suivantes

* [Apprenez à conteneuriser une application .NET Core.](build-docker-netcore-container.md)
* [Apprenez à conteneuriser une application ASP.NET Core.](/aspnet/core/host-and-deploy/docker/building-net-docker-images)
* [Essayez le tutoriel Découvrir le microservice ASP.NET Core.](https://dotnet.microsoft.com/learn/web/aspnet-microservice-tutorial/intro)
* [Découvrez les outils de conteneur dans Visual Studio.](/visualstudio/containers/overview)

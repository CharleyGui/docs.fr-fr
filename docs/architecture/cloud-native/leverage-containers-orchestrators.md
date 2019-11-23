---
title: Exploitation des conteneurs et des orchestrateurs
description: Tirer parti des conteneurs et orchestrateurs Kubernetes dans Azure
ms.date: 06/30/2019
ms.openlocfilehash: 7b136ed2760ea471f42ff82d20298ff8714c6dee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087232"
---
# <a name="leveraging-containers-and-orchestrators"></a>Exploitation des conteneurs et des orchestrateurs

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Les conteneurs et orchestrateurs sont conçus pour résoudre les problèmes communs aux approches de déploiement monolithiques.

## <a name="challenges-with-monolithic-deployments"></a>Défis liés aux déploiements monolithiques

Traditionnellement, la plupart des applications ont été déployées en tant qu’unité unique. Ces applications sont appelées monolithiques. Cette approche générale du déploiement d’applications en tant qu’unités uniques, même si elles sont composées de plusieurs modules ou assemblys, est connue sous le nom d’architecture monolithique, comme le montre la figure 3-1.

![Architecture monolithique.](./media/monolithic-architecture.png)

**Figure 3-1**. Architecture monolithique.

Bien qu’ils aient l’avantage de simplifier, les architectures monolithiques font face à un certain nombre de défis :

### <a name="deployments"></a>Déploiements

Le déploiement sur des applications monolithiques requiert généralement le redémarrage de l’application entière, même si un seul petit module est remplacé. En fonction du nombre d’ordinateurs hébergeant l’application, cela peut entraîner un temps d’arrêt au cours des déploiements.

### <a name="hosting"></a>Hébergement

Les applications monolithiques sont hébergées entièrement sur une seule instance de machine. Cela peut nécessiter un matériel de plus grande capacité que n’importe quel module dans une application distribuée. En outre, si une partie de l’application devient un goulot d’étranglement, la totalité de l’application doit être déployée sur des nœuds d’ordinateur supplémentaires pour pouvoir monter en charge.

### <a name="environment"></a>Environnement

Les applications monolithiques sont généralement déployées dans un environnement d’hébergement existant (système d’exploitation, frameworks installés, etc.). Cet environnement peut ne pas correspondre à l’environnement dans lequel l’application a été développée ou testée. Les incohérences dans l’environnement de l’application constituent une source commune de problèmes pour les déploiements monolithiques.

### <a name="coupling"></a>Couplage

Les applications monolithiques sont susceptibles d’avoir une grande quantité de couplage entre les différentes parties de l’application et entre l’application et son environnement. Cela peut compliquer la factorisation d’un service particulier ou d’un problème ultérieur, afin d’augmenter son extensibilité ou son échange dans une autre implémentation. Ce couplage entraîne également des impacts potentiels plus importants pour les modifications apportées au système, nécessitant des tests approfondis dans des applications plus volumineuses.

### <a name="technology-choice"></a>Choix de la technologie

Les applications monolithiques sont générées et déployées en tant qu’unité. Cela offre une simplicité et une uniformité, mais peut être un obstacle à l’innovation. Bien qu’une nouvelle fonctionnalité ou un nouveau module du système puisse être plus adapté à une plateforme ou une infrastructure plus moderne, il est probable qu’elle soit créée à l’aide de l’approche actuelle de l’application à des fins de cohérence, ainsi qu’une facilité de développement et de déploiement.

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>Quels sont les avantages des conteneurs et des orchestrateurs ?

L’arrimeur est la plate-forme de gestion des conteneurs la plus populaire et vous permet de travailler rapidement avec des conteneurs sous Linux et Windows. Les conteneurs fournissent des environnements d’application distincts mais reproductibles qui s’exécutent de la même façon sur tous les systèmes. Cela leur permet de développer et d’héberger des applications et des composants d’application dans les applications natives du Cloud. Les conteneurs étant isolés les uns des autres, deux conteneurs sur le même matériel hôte peuvent avoir différentes versions du logiciel et même le système d’exploitation installé, sans les dépendances qui provoquent des conflits.

De plus, les conteneurs sont définis par des fichiers simples qui peuvent être archivés dans le contrôle de code source. Contrairement aux serveurs complets, même les machines virtuelles, qui nécessitent souvent un travail manuel pour appliquer des mises à jour ou installer des services supplémentaires, l’infrastructure de conteneur peut facilement être contrôlée par version. Ainsi, les applications générées pour s’exécuter dans des conteneurs peuvent être développées, testées et déployées à l’aide d’outils automatisés dans le cadre d’un pipeline de génération.

Les conteneurs sont immuables. Une fois que vous avez la définition d’un conteneur, vous pouvez recréer ce conteneur pour qu’il s’exécute exactement de la même façon. Cette immuabilité se prête à la conception basée sur les composants. Si certaines parties d’une application ne changent pas aussi souvent que d’autres, pourquoi redéployer l’application entière quand vous pouvez simplement déployer les parties qui changent le plus fréquemment ? Des fonctionnalités différentes et des problèmes de coupe croisée d’une application peuvent être divisées en unités distinctes. La figure 3-2 montre comment une application monolithique peut tirer parti des conteneurs et des microservices en déléguant certaines fonctionnalités ou fonctionnalités. Les fonctionnalités restantes de l’application elle-même ont également été en conteneur.

![le fractionnement d’une application monolithique pour utiliser des microservices dans le back end.](./media/breaking-up-monolith-with-backend-microservices.png)
**Figure 3-2**. Division d’une application monolithique pour utiliser des microservices dans le back end.

Les applications Cloud natives créées à l’aide de conteneurs distincts tirent parti de la possibilité de déployer autant ou moins d’applications que nécessaire. Les services individuels peuvent être hébergés sur des nœuds avec des ressources appropriées pour chaque service. L’environnement dans lequel chaque service s’exécute est immuable, peut être partagé entre le développement, le test et la production, et peut facilement être associé à une version. Le couplage entre les différentes zones de l’application se produit explicitement comme des appels ou des messages entre les services, et non pour les dépendances au moment de la compilation dans le monolithe. Et une partie donnée de l’application globale peut choisir la technologie qui est la plus appropriée pour cette fonctionnalité ou cette fonctionnalité sans nécessiter de modifications du reste de l’application.

## <a name="what-are-the-scaling-benefits"></a>Quels sont les avantages de la mise à l’échelle ?

Les services basés sur des conteneurs peuvent tirer parti des avantages de la mise à l’échelle proposés par les outils d’orchestration tels que Kubernetes. Par conception, les conteneurs ne savent qu’eux-mêmes. Une fois que vous avez commencé à avoir plusieurs conteneurs qui doivent fonctionner ensemble, il peut être utile de les organiser à un niveau supérieur. L’organisation d’un grand nombre de conteneurs et de leurs dépendances partagées, telles que la configuration du réseau, est l’endroit où les outils d’orchestration entrent pour gagner le jour. Kubernetes est une plateforme d’orchestration de conteneur conçue pour automatiser le déploiement, la mise à l’échelle et la gestion des applications en conteneur. Il crée une couche d’abstraction par-dessus des groupes de conteneurs et les organise en *modules*. Les POD s’exécutent sur des ordinateurs de travail désignés sous le terme de *nœuds*. L’ensemble du groupe organisé est appelé *cluster*. La figure 3-3 montre les différents composants d’un cluster Kubernetes.

![composants de cluster Kubernetes.](./media/kubernetes-cluster-components.png)
**Figure 3-3**. Composants de cluster Kubernetes.

Kubernetes offre une prise en charge intégrée de la mise à l’échelle des clusters pour répondre à la demande. Associé aux micro-services en conteneur, il offre aux applications Cloud natives la possibilité de répondre rapidement et efficacement aux pics de demande avec des ressources supplémentaires quand et où elles sont nécessaires.

### <a name="declarative-versus-imperative"></a>Déclaratifs et impératifs

Kubernetes prend en charge la configuration d’objet déclarative et impérative. L’approche impérative implique l’exécution de diverses commandes qui indiquent à Kubernetes ce qu’il faut faire chaque étape. *Exécutez* cette image. *Supprimer* ce pod. *Exposez* ce port. Avec l’approche déclarative, vous utilisez un fichier de configuration qui décrit *ce que vous souhaitez* , au lieu de savoir ce qu’il *faut faire* et Kubernetes, ce qu’il faut faire pour atteindre l’état final souhaité. Si vous avez déjà configuré votre cluster à l’aide de commandes impératives, vous pouvez exporter un manifeste déclaratif à l’aide de `kubectl get svc SERVICENAME -o yaml > service.yaml`. Cela produira un fichier manifeste comme celui-ci :

```yaml
apiVersion: v1
kind: Service
metadata:
  creationTimestamp: "2019-09-13T13:58:47Z"
  labels:
    component: apiserver
    provider: kubernetes
  name: kubernetes
  namespace: default
  resourceVersion: "153"
  selfLink: /api/v1/namespaces/default/services/kubernetes
  uid: 9b1fac62-d62e-11e9-8968-00155d38010d
spec:
  clusterIP: 10.96.0.1
  ports:
  - name: https
    port: 443
    protocol: TCP
    targetPort: 6443
  sessionAffinity: None
  type: ClusterIP
status:
  loadBalancer: {}
```

Lorsque vous utilisez la configuration déclarative, vous pouvez afficher un aperçu des modifications qui seront apportées avant de les valider à l’aide de `kubectl diff -f FOLDERNAME` sur le dossier où se trouvent vos fichiers de configuration. Une fois que vous êtes sûr de vouloir appliquer les modifications, exécutez `kubectl apply -f FOLDERNAME`. Ajoutez `-R` pour traiter de manière récursive une hiérarchie de dossiers.

En plus des services, vous pouvez utiliser la configuration déclarative pour d’autres fonctionnalités Kubernetes, telles que les *déploiements*. Les déploiements déclaratifs sont utilisés par les contrôleurs de déploiement pour mettre à jour les ressources de cluster. Les déploiements sont utilisés pour déployer de nouvelles modifications, monter en puissance pour prendre en charge davantage de charge ou revenir à une révision précédente. Si un cluster est instable, les déploiements déclaratifs fournissent un mécanisme pour ramener automatiquement le cluster à l’état souhaité.

L’utilisation de la configuration déclarative permet à l’infrastructure d’être représentée en tant que code qui peut être archivé et géré avec le code d’application. Cela permet d’améliorer le contrôle des modifications et une meilleure prise en charge du déploiement continu à l’aide d’un pipeline de génération et de déploiement lié aux modifications du contrôle de code source.

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>Quels sont les scénarios idéaux pour les conteneurs et orchestrateurs ?

Les scénarios suivants sont idéaux pour l’utilisation des conteneurs et des orchestrateurs.

### <a name="applications-requiring-high-uptime-and-scalability"></a>Applications nécessitant une disponibilité et une évolutivité élevées

Les applications individuelles qui ont des exigences élevées en termes de temps de fonctionnement et d’évolutivité sont des candidats idéaux pour les architectures natives du Cloud utilisant des microservices, des conteneurs et des orchestrateurs. Ces applications peuvent être développées dans des conteneurs à l’aide d’environnements avec version, peuvent être testées de manière intensive avant de passer en production et peuvent être déployées en production sans temps d’arrêt. L’utilisation de clusters Kubernetes garantit que ces applications peuvent également être mises à l’échelle à la demande et récupérées automatiquement à partir des défaillances de nœud.

### <a name="large-numbers-of-applications"></a>Grand nombre d’applications

Les organisations qui déploient et doivent gérer par la suite un grand nombre d’applications bénéficient des conteneurs et des orchestrateurs. L’effort initial de la configuration des environnements en conteneur et des clusters Kubernetes est essentiellement un coût fixe. Le déploiement, la maintenance et la mise à jour d’applications individuelles ont un coût qui varie selon le nombre d’applications qui doivent être gérées. Au-delà d’un certain nombre d’applications, la complexité de la gestion manuelle des applications personnalisées dépasse le coût de l’implémentation d’une solution utilisant des conteneurs et des orchestrateurs.

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>Quand devez-vous éviter d’utiliser des conteneurs et des orchestrateurs ?

Si vous n’êtes pas en mesure de créer votre application à l’aide des principes d’application à douze facteurs, vous aurez probablement intérêt à éviter les conteneurs et orchestrateurs. Dans ce cas, il peut être préférable d’utiliser une plateforme d’hébergement basée sur une machine virtuelle, voire un système hybride dans lequel vous pouvez faire tourner certains éléments de fonctionnalité dans des conteneurs distincts ou même des fonctions sans serveur.

## <a name="development-resources"></a>Ressources de développement

Cette section présente une liste succincte de ressources de développement qui peuvent vous aider à commencer à utiliser des conteneurs et orchestrateurs pour votre prochaine application. Si vous recherchez des conseils sur la façon de concevoir votre application d’architecture de microservices Native Cloud, lisez le Guide de ce manuel, [microservices .net : architecture pour les applications .net en conteneur](https://aka.ms/microservicesebook).

### <a name="local-kubernetes-development"></a>Développement Kubernetes local

Les déploiements Kubernetes fournissent une valeur ajoutée dans les environnements de production, mais vous pouvez également les exécuter localement. Bien que la plupart du temps, il est judicieux de pouvoir travailler sur des applications ou des microservices individuels, il est parfois judicieux de pouvoir exécuter l’ensemble du système localement de la même manière qu’il s’exécutera en cas de déploiement en production. Il existe plusieurs façons d’y parvenir, dont deux sont Minikube et bureau d’ancrage. Visual Studio fournit également des outils pour le développement de l’ancrage.

### <a name="minikube"></a>Minikube

Qu’est-ce que Minikube ? Le projet Minikube indique « Minikube implémente un cluster Kubernetes local sur macOS, Linux et Windows ». Ses principaux objectifs sont les meilleurs outils pour le développement d’applications Kubernetes locales et pour la prise en charge de toutes les fonctionnalités Kubernetes. L’installation de Minikube est distincte de Dockr, mais Minikube prend en charge d’autres hyperviseurs que le Bureau de l’arrimeur prend en charge. Les fonctionnalités Kubernetes suivantes sont actuellement prises en charge par Minikube :

- DNS
- Noexclusions
- ConfigMaps et secrets
- Tableaux de bord
- Runtimes de conteneur : docker, RKT, élément de rapport personnalisé-O et conteneur
- Activation de l’interface réseau du conteneur (CNI)
- Pénètre

Après avoir installé Minikube, vous pouvez commencer rapidement à l’utiliser en exécutant la commande `minikube start`, qui télécharge une image et démarre le cluster Kubernetes local. Une fois le cluster démarré, vous interagissez avec lui à l’aide des commandes standard Kubernetes `kubectl`.

### <a name="docker-desktop"></a>Bureau de l’ancrage

Vous pouvez également utiliser Kubernetes directement à partir du Bureau de l’ancrage sur Windows. Il s’agit de votre seule option si vous utilisez des conteneurs Windows. il s’agit d’un bon choix pour les conteneurs non Windows. L’application de configuration du Bureau de l’arrimeur standard est utilisée pour configurer Kubernetes en cours d’exécution à partir du Bureau de l’ancrage.

![Configuration de Kubernetes dans le Bureau de l’arrimeur](./media/docker-desktop-kubernetes.png)

**Figure 3-4**. Configuration de Kubernetes dans le Bureau de l’ancrage.

Le Bureau de l’arrimeur est déjà l’outil le plus populaire pour configurer et exécuter des applications en conteneur localement. Lorsque vous travaillez avec le Bureau de l’Ancreur, vous pouvez développer localement sur le même ensemble d’images de conteneur d’ancrage que vous allez déployer en production. Le Bureau de l’arrimeur est conçu pour créer, tester et expédier des applications en conteneur localement. Une fois que les images ont été expédiées à un registre d’images comme Azure Container Registry ou le hub d’ancrage, les services comme Azure Kubernetes service (AKS) gèrent l’application en production.

### <a name="visual-studio-docker-tooling"></a>Outils de l’ancrage de Visual Studio

Visual Studio prend en charge le développement de l’ancrage pour les applications Web. Lorsque vous créez une application de ASP.NET Core, vous avez la possibilité de la configurer avec la prise en charge de l’ancrage dans le cadre du processus de création du projet, comme illustré dans la figure 3-5.

![Visual Studio permet la prise en charge de l’ancrage](./media/visual-studio-enable-docker-support.png)

**Figure 3-5**. Visual Studio permet la prise en charge de l’ancrage

Lorsque cette option est sélectionnée, le projet est créé avec un `Dockerfile` dans sa racine, qui peut être utilisé pour générer et héberger l’application dans un conteneur Dockr. Un exemple de fichier dockerfile est illustré dans la figure 3-6.

```docker
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.0-stretch AS build
WORKDIR /src
COPY ["WebApplication3/WebApplication3.csproj", "WebApplication3/"]
RUN dotnet restore "WebApplication3/WebApplication3.csproj"
COPY . .
WORKDIR "/src/WebApplication3"
RUN dotnet build "WebApplication3.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication3.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication3.dll"]
```

**Figure 3-6**. Fichier dockerfile généré par Visual Studio

Le comportement par défaut lors de l’exécution de l’application est également configuré pour utiliser l’Ancreur. La figure 3-7 montre les différentes options d’exécution disponibles à partir d’un nouveau projet de ASP.NET Core créé avec la prise en charge de l’ancrage ajouté.

![Options d’exécution de l’Ancreur Visual Studio](./media/visual-studio-docker-run-options.png)

**Figure 3-7**. Options d’exécution de l’Ancreur Visual Studio

En plus du développement local, [Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/) offre un moyen pratique à plusieurs développeurs de travailler avec leurs propres configurations Kubernetes dans Azure. Comme vous pouvez le voir dans la figure 3-7, vous pouvez également exécuter l’application dans Azure Dev Spaces.

Si vous n’ajoutez pas la prise en charge de l’ancrage à votre application ASP.NET Core lorsque vous la créez, vous pouvez toujours l’ajouter ultérieurement. Dans le Explorateur de solutions Visual Studio, cliquez avec le bouton droit sur le projet et sélectionnez **ajouter** > **prise en charge**de l’ancrage, comme illustré à la figure 3-8.

![Ajout de la prise en charge de l’ancrage à Visual Studio](./media/visual-studio-add-docker-support.png)

**Figure 3-8**. Ajout de la prise en charge de l’ancrage à Visual Studio

En plus de la prise en charge de l’ancrage, vous pouvez également ajouter la prise en charge de l’orchestration de conteneur, également illustrée dans la figure 3-8. Par défaut, l’orchestrateur utilise Kubernetes et Helm. Une fois que vous avez choisi l’orchestrateur, un fichier `azds.yaml` est ajouté à la racine du projet et un dossier `charts` est ajouté, contenant les graphiques Helm utilisés pour configurer et déployer l’application sur Kubernetes. La figure 3-9 montre les fichiers résultants dans un nouveau projet.

![Ajout de la prise en charge d’Orchestrator à Visual Studio](./media/visual-studio-add-orchestrator-support.png)

**Figure 3-9**. Ajout de la prise en charge d’Orchestrator à Visual Studio

## <a name="references"></a>Références

- [Qu’est-ce que Kubernetes ?](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [Installation de Kubernetes avec Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube et bureau de l’ancrage](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Visual Studio Tools pour Docker](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)

>[!div class="step-by-step"]
>[Précédent](scale-applications.md)
>[Suivant](leverage-serverless-functions.md)

---
title: Exploitation des conteneurs et des orchestrateurs
description: Tirer parti des conteneurs Docker et des orchestrateurs de Kubernetes en Azure
ms.date: 06/30/2019
ms.openlocfilehash: 44b2fff8c9c88717d83e41a421b9817e2cc68135
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989036"
---
# <a name="leveraging-containers-and-orchestrators"></a>Exploitation des conteneurs et des orchestrateurs

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Les conteneurs et les orchestrateurs sont conçus pour résoudre des problèmes communs aux approches de déploiement monolithiques.

## <a name="challenges-with-monolithic-deployments"></a>Défis avec des déploiements monolithiques

Traditionnellement, la plupart des applications ont été déployées en tant qu’unité unique. Ces applications sont appelées monolithes. Cette approche générale du déploiement d’applications en tant qu’unités individuelles, même si elles sont composées de plusieurs modules ou assemblages est connue sous le nom d’architecture monolithique, comme le montre la figure 3-1.

![Architecture monolithique.](./media/monolithic-architecture.png)

**Figure 3-1**. Architecture monolithique.

Bien qu’elles aient l’avantage de la simplicité, les architectures monolithiques font face à un certain nombre de défis :

### <a name="deployments"></a>Déploiements

Le déploiement d’applications monolithiques nécessite généralement le redémarrage de l’application entière, même si un seul petit module est remplacé. Selon le nombre de machines hébergeant l’application, cela peut entraîner des temps d’arrêt pendant les déploiements.

### <a name="hosting"></a>Hébergement

Les applications monolithiques sont hébergées entièrement sur une seule instance de machine. Cela peut nécessiter du matériel plus haute capacité que n’importe quel module d’une application distribuée. En outre, si une partie de l’application devient un goulot d’étranglement, l’application entière doit être déployée sur des nœuds machine supplémentaires afin de mettre à l’échelle.

### <a name="environment"></a>Environnement

Les applications monolithiques sont généralement déployées dans un environnement d’hébergement existant (système d’exploitation, cadres installés, etc.). Cet environnement peut ne pas correspondre à l’environnement dans lequel l’application a été développée ou testée. Les incohérences dans l’environnement de l’application sont une source commune de problèmes pour les déploiements monolithiques.

### <a name="coupling"></a>Couplage

Les applications monolithiques sont susceptibles d’avoir beaucoup de couplage entre les différentes parties de l’application, et entre l’application et son environnement. Cela peut rendre difficile de tenir compte d’un service ou d’une préoccupation particulier plus tard, afin d’accroître son évolutivité ou de l’échange dans une autre implémentation. Ce couplage entraîne également des impacts potentiels beaucoup plus importants pour les changements apportés au système, ce qui nécessite des tests approfondis dans des applications plus importantes.

### <a name="technology-choice"></a>Choix de la technologie

Les applications monolithiques sont construites et déployées en tant qu’unité. Cela offre simplicité et uniformité, mais peut être un obstacle à l’innovation. Bien qu’une nouvelle fonctionnalité ou module dans le système puisse être mieux adapté à une plate-forme ou un cadre plus moderne, il est susceptible d’être construit en utilisant l’approche actuelle de l’application pour des raisons de cohérence ainsi que la facilité de développement et de déploiement.

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>Quels sont les avantages des conteneurs et des orchestrateurs?

Docker est la plate-forme de gestion et d’imagerie de conteneurs la plus populaire et vous permet de travailler rapidement avec des conteneurs sur Linux et Windows. Les conteneurs fournissent des environnements d’application séparés mais reproductibles qui fonctionnent de la même manière sur n’importe quel système. Cela les rend parfaits pour le développement et l’hébergement d’applications et de composants d’applications dans des applications cloud-natives. Les conteneurs sont isolés les uns des autres, de sorte que deux conteneurs sur le même matériel d’hôte peuvent avoir différentes versions de logiciels et même système d’exploitation installés, sans les dépendances causant des conflits.

De plus, les conteneurs sont définis par des fichiers simples qui peuvent être contrôlés dans le contrôle source. Contrairement aux serveurs complets, même les machines virtuelles, qui nécessitent fréquemment un travail manuel pour appliquer des mises à jour ou installer des services supplémentaires, l’infrastructure des conteneurs peut facilement être contrôlée par la version. Ainsi, les applications conçues pour fonctionner dans des conteneurs peuvent être développées, testées et déployées à l’aide d’outils automatisés dans le cadre d’un pipeline de construction.

Les conteneurs sont immuables. Une fois que vous avez la définition d’un conteneur, vous pouvez recréer ce conteneur et il fonctionnera exactement de la même façon. Cette immuabilité se prête à la conception basée sur les composants. Si certaines parties d’une application ne changent pas aussi souvent que d’autres, pourquoi redéployer l’application entière alors que vous pouvez simplement déployer les pièces qui changent le plus fréquemment ? Différentes fonctionnalités et préoccupations transversales d’une application peuvent être divisées en unités distinctes. La figure 3-2 montre comment une application monolithique peut tirer parti des conteneurs et des microservices en déléguant certaines fonctionnalités ou fonctionnalités. Les fonctionnalités restantes dans l’application elle-même ont également été conteneurisées.

![Démantèlement d’une application monolithique pour utiliser les microservices à l’arrière. ](./media/breaking-up-monolith-with-backend-microservices.png)
 **Figure 3-2**. Démantèlement d’une application monolithique pour utiliser les microservices à l’arrière.

Les applications cloud-natives construites à l’aide de conteneurs distincts bénéficient de la possibilité de déployer autant ou aussi peu d’application que nécessaire. Les services individuels peuvent être hébergés sur des nœuds avec des ressources appropriées à chaque service. L’environnement dans lequel chaque service s’exécute est immuable, peut être partagé entre le dev, le test et la production, et peut facilement être versionné. Le couplage entre les différentes zones de l’application se produit explicitement sous forme d’appels ou de messages entre les services, et non de dépendances dans le monolithe. Et n’importe quelle partie donnée de l’application globale peut choisir la technologie qui fait le plus de sens pour cette fonctionnalité ou capacité sans nécessiter des changements au reste de l’application.

## <a name="what-are-the-scaling-benefits"></a>Quels sont les avantages de mise à l’échelle?

Les services construits sur des conteneurs peuvent tirer parti des avantages d’échelle fournis par des outils d’orchestration comme Kubernetes. Par la conception des conteneurs ne savent que sur eux-mêmes. Une fois que vous commencez à avoir plusieurs conteneurs qui ont besoin de travailler ensemble, il peut être utile de les organiser à un niveau supérieur. L’organisation d’un grand nombre de conteneurs et de leurs dépendances communes, comme la configuration du réseau, est l’endroit où les outils d’orchestration entrent pour sauver la journée! Kubernetes est une plate-forme d’orchestration de conteneurs conçue pour automatiser le déploiement, la mise à l’échelle et la gestion d’applications conteneurisées. Il crée une couche d’abstraction au-dessus de groupes de conteneurs et les organise en *gousses.* Les gousses fonctionnent sur des machines de travailleurs appelées *nœuds.* L’ensemble du groupe organisé est appelé un *cluster*. La figure 3-3 montre les différents composants d’un cluster Kubernetes.

![Composants de cluster Kubernetes. ](./media/kubernetes-cluster-components.png)
 **Figure 3-3**. Composants de cluster Kubernetes.

Kubernetes a intégré le soutien aux clusters à l’échelle pour répondre à la demande. Combiné avec des micro-services conteneurisés, cela permet aux applications cloud-natives de répondre rapidement et efficacement aux pics de demande avec des ressources supplémentaires quand et où elles sont nécessaires.

### <a name="declarative-versus-imperative"></a>Déclaratif contre impératif

Kubernetes prend en charge la configuration des objets déclaratifs et impératives. L’approche impérative consiste à exécuter diverses commandes qui indiquent à Kubernetes ce qu’il faut faire à chaque étape du chemin. *Exécutez* cette image. *Supprimez* cette gousse. *Exposez* ce port. Avec l’approche déclarative, vous utilisez un fichier de configuration qui décrit ce que *vous voulez* au lieu de *ce qu’il faut faire* et Kubernetes figure sur ce qu’il faut faire pour atteindre l’état final souhaité. Si vous avez déjà configuré votre cluster à l’aide de `kubectl get svc SERVICENAME -o yaml > service.yaml`commandes impératives, vous pouvez exporter un manifeste déclaratif en utilisant . Cela produira un fichier manifeste comme celui-ci:

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

Lors de l’utilisation de la configuration déclarative, vous pouvez `kubectl diff -f FOLDERNAME` prévisualiser les modifications qui seront apportées avant de les engager en les utilisant contre le dossier où vos fichiers de configuration sont situés. Une fois que vous êtes sûr que `kubectl apply -f FOLDERNAME`vous voulez appliquer les modifications, exécuter . Ajouter `-R` pour traiter de façon récursive une hiérarchie de dossiers.

En plus des services, vous pouvez utiliser la configuration déclarative pour d’autres fonctionnalités Kubernetes, telles que *les déploiements*. Les déploiements déclaratifs sont utilisés par les contrôleurs de déploiement pour mettre à jour les ressources du cluster. Les déploiements sont utilisés pour déployer de nouveaux changements, prendre de l’ampleur pour supporter plus de charge, ou revenir à une révision précédente. Si un cluster est instable, les déploiements déclaratifs fournissent un mécanisme permettant de ramener automatiquement le cluster à un état souhaité.

L’utilisation de configuration déclarative permet d’être représenté l’infrastructure comme code qui peut être enregistré et versionné à côté du code d’application. Cela permet d’améliorer le contrôle des changements et d’améliorer le soutien au déploiement continu à l’aide d’un pipeline de construction et de déploiement lié aux changements de contrôle des sources.

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>Quels scénarios sont idéaux pour les conteneurs et les orchestrateurs?

Les scénarios suivants sont idéaux pour l’utilisation de conteneurs et d’orchestrateurs.

### <a name="applications-requiring-high-uptime-and-scalability"></a>Applications nécessitant une disponibilité et une évolutivité élevées

Les applications individuelles qui ont des exigences élevées en matière de disponibilité et d’évolutivité sont des candidats idéaux pour les architectures cloud-natives utilisant des microservices, des conteneurs et des orchestrateurs. Ces applications peuvent être développées dans des conteneurs à l’aide d’environnements en version, peuvent être testées intensivement avant d’aller à la production, et peuvent être déployées à la production avec zéro temps d’arrêt. L’utilisation des clusters Kubernetes garantit que ces applications peuvent également évoluer sur la demande et se remettre automatiquement des défaillances de nœuds.

### <a name="large-numbers-of-applications"></a>Un grand nombre d’applications

Les organisations qui se déploient et doivent par la suite maintenir un grand nombre d’applications bénéficient de conteneurs et d’orchestrateurs. L’effort d’avant-plan de la mise en place d’environnements conteneurisés et de clusters Kubernetes est avant tout un coût fixe. Le déploiement, l’entretien et la mise à jour d’applications individuelles ont un coût qui varie selon le nombre d’applications qui doivent être maintenues. Au-delà d’un certain nombre assez restreint d’applications, la complexité de la maintenance manuelle des applications personnalisées dépasse manuellement le coût de mise en œuvre d’une solution à l’aide de conteneurs et d’orchestrateurs.

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>Quand devriez-vous éviter d’utiliser des conteneurs et des orchestrateurs?

Si vous n’êtes pas disposé ou incapable de construire votre application selon les principes de l’application Douze Facteurs, vous serez probablement mieux d’éviter les conteneurs et les orchestrateurs. Dans ces cas, il peut être préférable d’aller de l’avant avec une plate-forme d’hébergement basée sur VM, ou peut-être un système hybride dans lequel vous pouvez spin off certains morceaux de fonctionnalité dans des conteneurs séparés ou même des fonctions sans serveur.

## <a name="development-resources"></a>Ressources de développement

Cette section affiche une courte liste de ressources de développement qui peuvent vous aider à commencer à utiliser des conteneurs et des orchestrateurs pour votre prochaine application. Si vous êtes à la recherche de conseils sur la façon de concevoir votre application d’architecture de microservices cloud-native, lisez le compagnon de ce livre, [.NET Microservices: Architecture for Containerized .NET Applications](https://aka.ms/microservicesebook).

### <a name="local-kubernetes-development"></a>Développement local de Kubernetes

Les déploiements de Kubernetes offrent une grande valeur dans les environnements de production, mais vous pouvez également les exécuter localement. Bien que la plupart du temps, il est bon d’être en mesure de travailler sur des applications individuelles ou des microservices indépendamment, parfois il est bon d’être en mesure d’exécuter l’ensemble du système localement tout comme il fonctionnera lorsqu’il sera déployé à la production. Il existe plusieurs façons d’y parvenir, dont deux sont Minikube et Docker Desktop. Visual Studio fournit également l’outillage pour le développement Docker.

### <a name="minikube"></a>Minikube

Qu’est-ce que Minikube? Le projet Minikube indique que «Minikube implémente un cluster local Kubernetes sur macOS, Linux et Windows." Ses principaux objectifs sont « d’être le meilleur outil pour le développement local d’applications Kubernetes et de prendre en charge toutes les fonctionnalités de Kubernetes qui s’adaptent ». L’installation de Minikube est séparée de Docker, mais Minikube prend en charge différents hyperviseurs que les supports Docker Desktop. Les fonctionnalités suivantes de Kubernetes sont actuellement prises en charge par Minikube :

- DNS
- NodePorts (nodePorts)
- ConfigMaps et secrets
- Tableaux de bord
- Durée des conteneurs : Docker, rkt, CRI-O et conteneurs
- Permettant l’interface réseau de conteneurs (CNI)
- Entrée

Après l’installation de Minikube, vous pouvez `minikube start` rapidement commencer à l’utiliser en exécutant la commande, qui télécharge une image et démarre le cluster local Kubernetes. Une fois le cluster démarré, vous interagissez `kubectl` avec lui à l’aide des commandes Kubernetes standard.

### <a name="docker-desktop"></a>Docker Desktop

Vous pouvez également travailler avec Kubernetes directement depuis Docker Desktop sur Windows. C’est votre seule option si vous utilisez windows Containers, et est un excellent choix pour les conteneurs non Windows ainsi. L’application de configuration Docker Desktop standard est utilisée pour configurer Kubernetes en cours d’exécution à partir de Docker Desktop.

![Configurer Kubernetes dans Docker Desktop](./media/docker-desktop-kubernetes.png)

**Figure 3-4**. Configurer Kubernetes dans Docker Desktop.

Docker Desktop est déjà l’outil le plus populaire pour configurer et exécuter localement des applications conteneurisées. Lorsque vous travaillez avec Docker Desktop, vous pouvez développer localement contre le même ensemble exact d’images de conteneurs Docker que vous déployez à la production. Docker Desktop est conçu pour « construire, tester et expédier » localement des applications conteneurisées. Une fois que les images ont été expédiées à un registre d’images comme Azure Container Registry ou Docker Hub, des services comme Azure Kubernetes Service (AKS) gèrent l’application en production.

### <a name="visual-studio-docker-tooling"></a>Outil Visual Studio Docker

Visual Studio prend en charge le développement de Docker pour des applications web. Lorsque vous créez une nouvelle application ASP.NET Core, vous avez la possibilité de la configurer avec le support Docker dans le cadre du processus de création de projet, comme le montre la figure 3-5.

![Visual Studio Active Docker Support (en)](./media/visual-studio-enable-docker-support.png)

**Figure 3-5**. Visual Studio Active Docker Support (en)

Lorsque cette option est sélectionnée, le `Dockerfile` projet est créé avec un dans sa racine, qui peut être utilisé pour construire et héberger l’application dans un conteneur Docker. Un exemple Dockerfile est montré dans la figure 3-6.

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

**Figure 3-6**. Visual Studio a généré Dockerfile

Le comportement par défaut lorsque l’application s’exécute est configuré pour utiliser Docker ainsi. La figure 3-7 montre les différentes options d’exécution offertes par un nouveau projet ASP.NET Core créé avec le soutien de Docker ajouté.

![Visual Studio Docker Run Options](./media/visual-studio-docker-run-options.png)

**Figure 3-7**. Visual Studio Docker Run Options

En plus du développement local, [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/) offre un moyen pratique pour plusieurs développeurs de travailler avec leurs propres configurations Kubernetes au sein d’Azure. Comme vous pouvez le voir dans la figure 3-7, vous pouvez également exécuter l’application dans Azure Dev Spaces.

Si vous n’ajoutez pas de support Docker à votre application ASP.NET Core lorsque vous la créez, vous pouvez toujours l’ajouter plus tard. De l’Explorer De solution Visual Studio, cliquez à droite sur le projet et **sélectionnez Add** > **Docker Support**, comme indiqué dans la figure 3-8.

![Visual Studio Ajouter le soutien Docker](./media/visual-studio-add-docker-support.png)

**Figure 3-8**. Visual Studio Ajouter le soutien Docker

En plus du support Docker, vous pouvez également ajouter Container Orchestration Support, également indiqué dans la figure 3-8. Par défaut, l’orchestrateur utilise Kubernetes et Helm. Une fois que vous avez `azds.yaml` choisi l’orchestrateur, un `charts` fichier est ajouté à la racine du projet et un dossier est ajouté contenant les graphiques Helm utilisés pour configurer et déployer l’application à Kubernetes. La figure 3-9 indique les fichiers qui en résultent dans un nouveau projet.

![Visual Studio Ajouter le support orchestrateur](./media/visual-studio-add-orchestrator-support.png)

**Figure 3-9**. Visual Studio Ajouter le support orchestrateur

## <a name="references"></a>References

- [Présentation de Kubernetes](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [Installation de Kubernetes avec Minikube](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube vs Bureau Docker](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Outils de studio visuel pour Docker](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)

>[!div class="step-by-step"]
>[Suivant précédent](scale-applications.md)
>[Next](leverage-serverless-functions.md)

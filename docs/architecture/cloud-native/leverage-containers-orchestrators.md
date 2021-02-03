---
title: Exploitation des conteneurs et des orchestrateurs
description: Tirer parti des conteneurs et orchestrateurs Kubernetes dans Azure
ms.date: 01/19/2021
ms.openlocfilehash: 63ac91b05a88dc13b7c62e6e04eecb0550cd4652
ms.sourcegitcommit: f2ab02d9a780819ca2e5310bbcf5cfe5b7993041
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505745"
---
# <a name="leveraging-containers-and-orchestrators"></a>Exploitation des conteneurs et des orchestrateurs

Les conteneurs et orchestrateurs sont conçus pour résoudre les problèmes communs aux approches de déploiement monolithiques.

## <a name="challenges-with-monolithic-deployments"></a>Défis liés aux déploiements monolithiques

Traditionnellement, la plupart des applications ont été déployées en tant qu’unité unique. Ces applications sont appelées monolithiques. Cette approche générale du déploiement d’applications en tant qu’unités uniques, même si elles sont composées de plusieurs modules ou assemblys, est connue sous le nom d’architecture monolithique, comme le montre la figure 3-1.

![Architecture monolithique.](./media/monolithic-design.png)

**Figure 3-1**. Architecture monolithique.

Bien qu’ils aient l’avantage de simplifier, les architectures monolithiques font face à un certain nombre de défis :

### <a name="deployment"></a>Déploiement

En outre, ils nécessitent un redémarrage de l’application, ce qui peut avoir un impact temporaire sur la disponibilité si aucune technique de temps d’arrêt n’est appliquée lors du déploiement.

### <a name="scaling"></a>Mise à l'échelle

Une application monolithique est hébergée entièrement sur une seule instance de machine, ce qui nécessite souvent du matériel à capacité élevée. Si une partie du monolithe requiert une mise à l’échelle, une autre copie de l’application entière doit être déployée sur un autre ordinateur. Avec un monolithique, vous ne pouvez pas mettre à l’échelle des composants d’application individuellement. c’est tout ou rien. La mise à l’échelle des composants qui ne nécessitent pas de mise à l’échelle entraîne une utilisation inefficace et coûteuse des ressources.

### <a name="environment"></a>Environnement

Les applications monolithiques sont généralement déployées dans un environnement d’hébergement avec un système d’exploitation, un Runtime et des dépendances de bibliothèque préinstallés. Cet environnement peut ne pas correspondre à celui sur lequel l’application a été développée ou testée. Les incohérences entre les environnements d’application constituent une source commune de problèmes pour les déploiements monolithiques.

### <a name="coupling"></a>Couplage

Une application monolithique est susceptible d’avoir un couplage élevé sur ses composants fonctionnels. Sans limites physiques, les modifications du système entraînent souvent des effets secondaires inattendus et coûteux. Les nouvelles fonctionnalités et correctifs deviennent délicats, fastidieux et coûteux à implémenter. Les mises à jour nécessitent un test approfondi. Le couplage complique également la refactorisation des composants ou l’échange dans d’autres implémentations. Même s’ils sont construits avec une séparation stricte des préoccupations, les ensembles d’érosions de l’architecture dans comme la base de code monolithique se détériorent avec des « cas spéciaux » jamais terminés.

### <a name="platform-lock-in"></a>Verrouillage de la plateforme

Une application monolithique est construite avec une seule pile technologique. Tout en offrant une uniformité, cet engagement peut devenir un obstacle à l’innovation. De nouveaux composants et fonctionnalités seront créés à l’aide de la pile actuelle de l’application, même si des technologies plus modernes peuvent être un meilleur choix. Un risque à plus long terme est que votre pile de technologies devient obsolète et obsolète. La réorganisation d’une application entière vers une nouvelle plateforme plus moderne est au mieux coûteuse et risquée.

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>Quels sont les avantages des conteneurs et des orchestrateurs ?

Nous avons introduit les conteneurs dans le chapitre 1. Nous avons mis en évidence comment la CNCF (Cloud Native Computing Foundation) classe le conteneur comme la première étape de leur [carte de piste Cloud Native](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) pour les entreprises qui commencent leur parcours Cloud-native. Dans cette section, nous aborderons les avantages des conteneurs.

L’arrimeur est la plateforme de gestion des conteneurs la plus populaire. Il fonctionne avec les conteneurs sur Linux ou Windows. Les conteneurs fournissent des environnements d’application distincts mais reproductibles qui s’exécutent de la même façon sur tous les systèmes. Cet aspect les rend parfaitement adaptés au développement et à l’hébergement des services Cloud natifs. Les conteneurs sont isolés les uns des autres. Deux conteneurs sur le même matériel hôte peuvent avoir différentes versions de logiciels, sans provoquer de conflits.

Les conteneurs sont définis par des fichiers texte simples qui deviennent des artefacts de projet et sont archivés dans le contrôle de code source. Bien que les serveurs complets et les machines virtuelles requièrent un effort manuel pour la mise à jour, les conteneurs sont facilement contrôlés par contrôle de version. Les applications générées pour s’exécuter dans des conteneurs peuvent être développées, testées et déployées à l’aide d’outils automatisés dans le cadre d’un pipeline de génération.

Les conteneurs sont immuables. Une fois que vous avez défini un conteneur, vous pouvez le recréer et l’exécuter exactement de la même façon. Cette immuabilité se prête à la conception basée sur les composants. Si certaines parties d’une application évoluent différemment des autres, pourquoi redéployer l’application entière quand vous pouvez simplement déployer les parties qui changent le plus fréquemment ? Des fonctionnalités différentes et des problèmes de coupe croisée d’une application peuvent être divisées en unités distinctes. La figure 3-2 montre comment une application monolithique peut tirer parti des conteneurs et des microservices en déléguant certaines fonctionnalités ou fonctionnalités. Les fonctionnalités restantes de l’application elle-même ont également été en conteneur.

![Division d’une application monolithique pour utiliser des microservices dans le back end.](./media/cloud-native-design.png)

**Figure 3-2**. Décomposition d’une application monolithique pour adopter des microservices.

Chaque service Cloud natif est généré et déployé dans un conteneur distinct. Chaque peut être mis à jour en fonction des besoins. Les services individuels peuvent être hébergés sur des nœuds avec des ressources appropriées pour chaque service. L’environnement dans lequel chaque service s’exécute est immuable, partagé entre les environnements de développement, de test et de production, et facilement géré par un contrôle de version. Le couplage entre les différentes zones de l’application se produit explicitement comme des appels ou des messages entre les services, et non pour les dépendances au moment de la compilation dans le monolithe. Vous pouvez également choisir la technologie qui correspond le mieux à une fonctionnalité donnée sans avoir à modifier le reste de l’application.

Les services en conteneur requièrent une gestion automatisée. Il n’est pas possible d’administrer manuellement un grand ensemble de conteneurs déployés de manière indépendante. Par exemple, considérez les tâches suivantes :

- Comment les instances de conteneur seront-elles approvisionnées sur un cluster de plusieurs ordinateurs ?
- Une fois le déploiement terminé, comment les conteneurs découvrent et communiquent les uns avec les autres ?
- Comment les conteneurs peuvent-ils être mis à l’échelle ou sortants à la demande ?
- Comment surveiller l’intégrité de chaque conteneur ?
- Comment protéger un conteneur contre les défaillances matérielles et logicielles ?
- Comment mettre à niveau des conteneurs pour une application active sans temps d’arrêt ?

Les orchestrateurs de conteneurs adressent et automatisent ces problèmes et d’autres.

Dans le système Eco Cloud-native, Kubernetes est devenu le conteneur de facto Orchestrator. Il s’agit d’une plateforme open source gérée par Cloud Native Computing Foundation (CNCF). Kubernetes automatise le déploiement, la mise à l’échelle et les problèmes opérationnels des charges de travail en conteneur sur un cluster d’ordinateurs. Toutefois, l’installation et la gestion de Kubernetes sont notoirement complexes.

Une meilleure approche consiste à tirer parti de Kubernetes en tant que service géré à partir d’un fournisseur de Cloud. Le Cloud Azure est doté d’une plateforme Kubernetes entièrement gérée [, intitulée Azure Kubernetes service (AKS)](https://azure.microsoft.com/services/kubernetes-service/). AKS fait abstraction de la complexité et de la surcharge opérationnelle de la gestion des Kubernetes. Vous consommez Kubernetes en tant que service Cloud. Microsoft est responsable de la gestion et de la prise en charge. AKS s’intègre également étroitement avec d’autres services Azure et des outils de développement.

AKS est une technologie basée sur les clusters. Un pool de machines virtuelles fédérées, ou nœuds, est déployé dans le Cloud Azure. Ensemble, ils forment un environnement hautement disponible ou un cluster. Le cluster apparaît comme une entité unique et transparente pour votre application Cloud-native. En coulisse, AKS déploie vos services en conteneur sur ces nœuds en suivant une stratégie prédéfinie qui répartit équitablement la charge.

## <a name="what-are-the-scaling-benefits"></a>Quels sont les avantages de la mise à l’échelle ?

Les services basés sur des conteneurs peuvent tirer parti des avantages de la mise à l’échelle proposés par les outils d’orchestration tels que Kubernetes. Par conception, les conteneurs ne savent qu’eux-mêmes. Une fois que vous avez plusieurs conteneurs qui doivent fonctionner ensemble, vous devez les organiser à un niveau supérieur. L’organisation d’un grand nombre de conteneurs et de leurs dépendances partagées, telles que la configuration du réseau, est l’endroit où les outils d’orchestration entrent pour gagner le jour. Kubernetes crée une couche d’abstraction sur des groupes de conteneurs et les organise en *Pod*. Les POD s’exécutent sur des ordinateurs de travail désignés sous le terme de *nœuds*. Cette structure organisée est appelée *cluster*. La figure 3-3 montre les différents composants d’un cluster Kubernetes.

![Composants de cluster Kubernetes. ](./media/kubernetes-cluster-components.png)
 **Figure 3-3**. Composants de cluster Kubernetes.

La mise à l’échelle des charges de travail en conteneur est une fonctionnalité clé des orchestrateurs de conteneurs. AKS prend en charge la mise à l’échelle automatique sur deux dimensions : les instances de conteneur et les nœuds de calcul. Ensemble, ils offrent à AKS la possibilité de répondre rapidement et efficacement aux pics de demande et d’ajouter des ressources supplémentaires. Nous aborderons la mise à l’échelle dans AKS plus loin dans ce chapitre.

### <a name="declarative-versus-imperative"></a>Déclaratifs et impératifs

Kubernetes prend en charge les configurations déclaratives et impératives. L’approche impérative implique l’exécution de diverses commandes qui indiquent à Kubernetes ce qu’il faut faire chaque étape. Exécutez cette image. Supprimer ce pod. Exposez ce port. Avec l’approche déclarative, vous créez un fichier de configuration, appelé manifeste, pour décrire ce que vous souhaitez. Kubernetes lit le manifeste et transforme l’état final souhaité en état final réel.

Les commandes impératives sont très utiles pour l’apprentissage et l’expérimentation interactive. Toutefois, vous souhaiterez créer de manière déclarative des fichiers manifestes Kubernetes pour adopter une infrastructure en tant qu’approche de code, en fournissant des déploiements fiables et reproductibles. Le fichier manifeste devient un artefact de projet et est utilisé dans votre pipeline CI/CD pour automatiser les déploiements de Kubernetes.

Si vous avez déjà configuré votre cluster à l’aide de commandes impératives, vous pouvez exporter un manifeste déclaratif à l’aide de `kubectl get svc SERVICENAME -o yaml > service.yaml` . Cette commande génère un manifeste similaire à celui illustré ci-dessous :

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

Lorsque vous utilisez la configuration déclarative, vous pouvez afficher un aperçu des modifications qui seront apportées avant de les valider à l’aide de `kubectl diff -f FOLDERNAME` sur le dossier où se trouvent vos fichiers de configuration. Une fois que vous êtes sûr de vouloir appliquer les modifications, exécutez `kubectl apply -f FOLDERNAME` . Ajoutez `-R` pour traiter de manière récursive une hiérarchie de dossiers.

Vous pouvez également utiliser la configuration déclarative avec d’autres fonctionnalités Kubernetes, dont l’un est un déploiement. Les déploiements déclaratifs aident à gérer les mises à jour, les mises à jour et la mise à l’échelle. Ils indiquent au contrôleur de déploiement Kubernetes comment déployer de nouvelles modifications, monter en charge la charge ou revenir à une révision précédente. Si un cluster est instable, un déploiement déclaratif rétablit automatiquement le cluster à un état souhaité. Par exemple, si un nœud doit se bloquer, le mécanisme de déploiement redéploiera un remplacement pour atteindre l’état souhaité.

L’utilisation de la configuration déclarative permet à l’infrastructure d’être représentée en tant que code qui peut être archivé et géré avec le code d’application. Il offre un contrôle amélioré des modifications et une meilleure prise en charge du déploiement continu à l’aide d’un pipeline de build et de déploiement.

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>Quels sont les scénarios idéaux pour les conteneurs et orchestrateurs ?

Les scénarios suivants sont idéaux pour l’utilisation des conteneurs et des orchestrateurs.

### <a name="applications-requiring-high-uptime-and-scalability"></a>Applications nécessitant une disponibilité et une évolutivité élevées

Les applications individuelles qui ont des exigences élevées en termes de temps de fonctionnement et d’évolutivité sont des candidats idéaux pour les architectures natives du Cloud utilisant des microservices, des conteneurs et des orchestrateurs. Elles peuvent être développées dans des conteneurs, testées sur des environnements avec version et déployées en production sans temps d’arrêt. L’utilisation de clusters Kubernetes garantit que ces applications peuvent également être mises à l’échelle à la demande et récupérées automatiquement à partir des défaillances de nœud.

### <a name="large-numbers-of-applications"></a>Grand nombre d’applications

Les organisations qui déploient et maintiennent un grand nombre d’applications bénéficient des conteneurs et des orchestrateurs. L’effort initial de la configuration des environnements en conteneur et des clusters Kubernetes est essentiellement un coût fixe. Le déploiement, la maintenance et la mise à jour d’applications individuelles ont un coût qui varie selon le nombre d’applications. Au-delà d’un petit nombre d’applications, la complexité de la gestion manuelle des applications personnalisées dépasse le coût d’implémentation d’une solution à l’aide de conteneurs et d’orchestrateurs.

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>Quand devez-vous éviter d’utiliser des conteneurs et des orchestrateurs ?

Si vous ne parvenez pas à créer votre application en suivant les principes de l’application Twelve-Factor, vous devez envisager d’éviter les conteneurs et les orchestrateurs. Dans ce cas, envisagez une plateforme d’hébergement basée sur une machine virtuelle, voire un système hybride. Avec elle, vous pouvez toujours faire tourner certains fragments de fonctionnalités dans des conteneurs distincts ou même des fonctions sans serveur.

## <a name="development-resources"></a>Ressources de développement

Cette section présente une liste succincte de ressources de développement qui peuvent vous aider à commencer à utiliser des conteneurs et orchestrateurs pour votre prochaine application. Si vous recherchez des conseils sur la façon de concevoir votre application d’architecture de microservices Native Cloud, lisez le Guide de ce manuel, [microservices .net : architecture pour les applications .net en conteneur](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook).

### <a name="local-kubernetes-development"></a>Développement Kubernetes local

Les déploiements Kubernetes fournissent une valeur ajoutée dans les environnements de production, mais peuvent également être exécutés localement sur votre ordinateur de développement. Si vous pouvez travailler sur des microservices individuels, il peut arriver que vous deviez exécuter le système tout entier localement, exactement comme s’il s’exécutait en production. Il existe plusieurs outils qui peuvent vous aider : Minikube et docker Desktop. Visual Studio fournit également des outils pour le développement de l’ancrage.

### <a name="minikube"></a>Minikube

Qu’est-ce que Minikube ? Le projet Minikube indique « Minikube implémente un cluster Kubernetes local sur macOS, Linux et Windows ». Ses principaux objectifs sont les meilleurs outils pour le développement d’applications Kubernetes locales et pour la prise en charge de toutes les fonctionnalités Kubernetes. L’installation de Minikube est distincte de Dockr, mais Minikube prend en charge d’autres hyperviseurs que le Bureau de l’arrimeur prend en charge. Les fonctionnalités Kubernetes suivantes sont actuellement prises en charge par Minikube :

- DNS
- Noexclusions
- ConfigMaps et secrets
- Tableaux de bord
- Runtimes de conteneur : docker, RKT, élément de rapport personnalisé-O et conteneur
- Activation de l’interface réseau du conteneur (CNI)
- Entrée

Après avoir installé Minikube, vous pouvez commencer rapidement à l’utiliser en exécutant la `minikube start` commande, qui télécharge une image et démarre le cluster Kubernetes local. Une fois le cluster démarré, vous interagissez avec lui à l’aide des commandes Kubernetes standard `kubectl` .

### <a name="docker-desktop"></a>Docker Desktop

Vous pouvez également utiliser Kubernetes directement à partir du Bureau de l’ancrage sur Windows. C’est votre seule option si vous utilisez des conteneurs Windows et est un excellent choix pour les conteneurs non Windows. La figure 3-4 montre comment activer la prise en charge des Kubernetes locaux lors de l’exécution de l’ordinateur de bureau de station d’accueil.

![Configuration de Kubernetes dans le Bureau de l’arrimeur](./media/docker-desktop-kubernetes.png)

**Figure 3-4**. Configuration de Kubernetes dans le Bureau de l’ancrage.

Le Bureau de l’arrimeur est l’outil le plus populaire pour configurer et exécuter des applications en conteneur localement. Lorsque vous travaillez avec le Bureau de l’Ancreur, vous pouvez développer localement sur le même ensemble d’images de conteneur d’ancrage que vous allez déployer en production. Le Bureau de l’arrimeur est conçu pour créer, tester et expédier des applications en conteneur localement. Il prend en charge les conteneurs Linux et Windows. Une fois que vous avez envoyé vos images vers un registre d’images, comme Azure Container Registry ou Hub Dockr, AKS peut les extraire et les déployer en production.

### <a name="visual-studio-docker-tooling"></a>Outils de l’ancrage de Visual Studio

Visual Studio prend en charge le développement de l’ancrage pour les applications Web. Lorsque vous créez une application de ASP.NET Core, vous avez la possibilité de la configurer avec la prise en charge de l’ancrage, comme illustré dans la figure 3-5.

![Visual Studio permet la prise en charge de l’ancrage](./media/visual-studio-enable-docker-support.png)

**Figure 3-5**. Visual Studio permet la prise en charge de l’ancrage

Lorsque cette option est sélectionnée, le projet est créé avec un `Dockerfile` à sa racine, qui peut être utilisé pour générer et héberger l’application dans un conteneur d’ancrage. Un exemple de fichier dockerfile est illustré à la figure 3 -6. git.

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:5.0-buster-slim AS build
WORKDIR /src
COPY ["eShopWeb/eShopWeb.csproj", "eShopWeb/"]
RUN dotnet restore "eShopWeb/eShopWeb.csproj"
COPY . .
WORKDIR "/src/eShopWeb"
RUN dotnet build "eShopWeb.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "eShopWeb.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "eShopWeb.dll"]
```

**Figure 3-6**. Fichier dockerfile généré par Visual Studio

Le comportement par défaut lors de l’exécution de l’application est également configuré pour utiliser l’Ancreur. La figure 3-7 montre les différentes options d’exécution disponibles à partir d’un nouveau projet de ASP.NET Core créé avec la prise en charge de l’ancrage ajouté.

![Options d’exécution de l’Ancreur Visual Studio](./media/visual-studio-docker-run-options.png)

**Figure 3-7**. Options d’exécution de l’Ancreur Visual Studio

En plus du développement local, [Azure dev Spaces](/azure/dev-spaces/) offre un moyen pratique à plusieurs développeurs de travailler avec leurs propres configurations Kubernetes dans Azure. Comme vous pouvez le voir dans la figure 3-7, vous pouvez également exécuter l’application dans Azure Dev Spaces.

En outre, à tout moment, vous pouvez ajouter la prise en charge de l’ancrage à une application de ASP.NET Core existante. À partir de l’Explorateur de solutions Visual Studio, cliquez avec le bouton droit sur le projet et sélectionnez **Ajouter** la  >  **prise en charge** de l’ancrage, comme illustré à la figure 3-8.

![Ajout de la prise en charge de l’ancrage à Visual Studio](./media/visual-studio-add-docker-support.png)

**Figure 3-8**. Ajout de la prise en charge de l’ancrage à Visual Studio

Vous pouvez également ajouter la prise en charge de l’orchestration de conteneur, également illustrée dans la figure 3-8. Par défaut, l’orchestrateur utilise Kubernetes et Helm. Une fois que vous avez choisi l’orchestrateur, un `azds.yaml` fichier est ajouté à la racine du projet et un `charts` dossier contenant les graphiques Helm utilisés pour configurer et déployer l’application sur Kubernetes est ajouté. La figure 3-9 montre les fichiers résultants dans un nouveau projet.

![Ajout de la prise en charge d’Orchestrator à Visual Studio](./media/visual-studio-add-orchestrator-support.png)

**Figure 3-9**. Ajout de la prise en charge de l’orchestration à Visual Studio

### <a name="visual-studio-code-docker-tooling"></a>Outils de l’ancrage Visual Studio Code

Un certain nombre d’extensions sont disponibles pour Visual Studio Code qui prennent en charge le développement de l’ancrage.

Microsoft fournit la [station d’accueil pour l’extension de Visual Studio code](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker). Cette extension simplifie le processus d’ajout de la prise en charge des conteneurs aux applications. Il élabore les fichiers requis, génère des images de l’ancrage et vous permet de déboguer votre application à l’intérieur d’un conteneur. L’extension présente un explorateur visuel qui permet d’effectuer facilement des actions sur des conteneurs et des images tels que Démarrer, arrêter, inspecter, supprimer, etc. L’extension prend également en charge les Docker Compose vous permettant de gérer plusieurs conteneurs en cours d’exécution en tant qu’unité unique.

>[!div class="step-by-step"]
>[Précédent](scale-applications.md) 
> [Suivant](leverage-serverless-functions.md)

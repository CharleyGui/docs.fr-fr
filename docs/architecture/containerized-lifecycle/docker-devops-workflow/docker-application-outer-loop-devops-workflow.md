---
title: Étapes du workflow DevOps de la boucle externe pour une application Docker
description: Découvrez les étapes de la « boucle externe » du workflow DevOps
ms.date: 02/15/2019
ms.openlocfilehash: fdda1b6a2deb08ed97867583fcc8048d4dba880c
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988971"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Étapes du workflow DevOps de la boucle externe pour une application Docker

La Figure 5-1 décrit de bout en bout les étapes du workflow DevOps de la boucle externe. Il montre la "boucle extérieure" de DevOps. Quand du code est poussé (push) vers le dépôt, un pipeline d’intégration continue (CI) est démarré, puis il commence le pipeline de déploiement continu (CD), où l’application est déployée. Les métriques collectées à partir d’applications déployées sont renvoyées à la charge de travail de développement, où la « boucle interne » se produit. Les équipes de développement disposent ainsi de données réelles pour répondre aux besoins des utilisateurs et des entreprises.

![Diagramme montrant les 6 étapes du flux de travail de la boucle extérieure DevOps.](./media/docker-application-outer-loop-devops-workflow/overview-dev-ops-outter-loop-workflow.png)

**Figure 5-1**. Workflow DevOps de la boucle externe pour les applications Docker avec des outils Microsoft

Maintenant, nous allons examiner chacune de ces étapes plus en détail.

## <a name="step-1-inner-loop-development-workflow"></a>Étape 1 : Flux de travail de développement en boucle intérieure

Cette étape est expliquée en détail au chapitre 4, mais, pour résumer, c’est là que commence la boucle externe, à savoir le moment auquel un développeur pousse (push) le code vers le système de gestion de contrôle de code source (comme Git), lançant ainsi les actions du pipeline CI.

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>Étape 2 : Intégration et gestion du contrôle des codes de la source avec Azure DevOps Services et Git

À cette étape, vous devez disposer d’un système de gestion de versions pour collecter une version consolidée de tout le code provenant des différents développeurs de l’équipe.

Même si le contrôle de code source (SCC, Source-Code Control) et la gestion de code source peuvent sembler naturels à la plupart des développeurs, quand vous créez des applications Docker dans un cycle de vie DevOps, gardez à l’esprit que vous ne devez pas pousser (push) les images Docker avec l’application directement vers le registre Docker global (comme Azure Container Registry ou Docker Hub) à partir de la machine du développeur. Au contraire, les images Docker à publier et à déployer sur les environnements de production doivent uniquement être créées sur le code source en cours d’intégration à votre pipeline CI ou de build global en fonction de votre dépôt de code source (comme Git).

Les images locales, générées par les développeurs, doivent uniquement être utilisées par ces derniers lors des tests sur leurs propres machines. C’est pourquoi il est essentiel que votre pipeline DevOps soit activé à partir du code SCC.

Azure DevOps Services et Team Foundation Server prennent en charge Git et Team Foundation Version Control. Vous pouvez choisir l’un d’eux et l’utiliser pour une expérience Microsoft de bout en bout. Toutefois, vous pouvez également gérer votre code dans des dépôts externes (tels que GitHub, des dépôts Git locaux ou Subversion) et être toujours en mesure de vous y connecter et d’obtenir le code comme point de départ pour votre pipeline CI DevOps.

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>Étape 3 : Construire, CI, intégrer et tester avec Azure DevOps Services et Docker

L’intégration continue est devenue un standard pour le test et la livraison de logiciels modernes. La solution Docker maintient une séparation claire des responsabilités entre les équipes de développement et des opérations. L’immuabilité des images Docker garantit un déploiement reproductible entre ce qui a été développé, testé par le biais de l’intégration continue et exécuté en production. Le moteur Docker déployé sur les ordinateurs portables des développeurs et l’infrastructure de test rend les conteneurs portables entre les environnements.

À ce stade, une fois que vous disposez d’un système de gestion de versions avec le bon code, vous avez besoin d’un *service de build* pour récupérer le code et exécuter la build et les tests globaux.

Le workflow interne de cette étape (CI, build, test) concerne la construction d’un pipeline CI constitué de votre dépôt de code (Git, etc.), de votre serveur de builds (Azure DevOps Services), du moteur Docker et d’un registre Docker.

Vous pouvez vous appuyer sur Azure DevOps Services pour générer vos applications et définir votre pipeline CI ainsi que pour publier les « artefacts » générés sur un « dépôt d’artefacts », comme l’explique la prochaine étape.

Quand vous utilisez Docker pour le déploiement, les « artefacts finaux » à déployer sont des images Docker comportant vos application ou services. Ces images sont poussées vers, ou publiées sur, un *registre Docker* (un dépôt privé comme ceux que vous pouvez avoir dans Azure Container Registry ou un dépôt public tel que le registre Docker Hub, qui est couramment utilisé pour les images de base officielles).

Voici le concept de base : le pipeline CI sera lancé par un engagement à un référentiel SCC comme Git. Le commit amène Azure DevOps Services à exécuter une tâche de build dans un conteneur Docker et, si cette tâche réussit, à pousser (push) une image Docker vers le registre Docker, comme illustré dans la Figure 5-2. La première partie de la boucle extérieure implique des étapes 1 à 3, à partir du code, exécuter, déboguer et valider, puis le code répo jusqu’à l’étape CI de construction et de test.

![Diagramme montrant les trois étapes impliquées dans le flux de travail de CI.](./media/docker-application-outer-loop-devops-workflow/continuous-integration-steps.png)

**Figure 5-2**. Étapes impliquées dans l’intégration continue

Voici les étapes du workflow CI avec Docker et Azure DevOps Services :

1. Le développeur pousse (push) un commit à un dépôt SCC (Git/Azure DevOps Services, GitHub, etc.).

2. Si vous utilisez Azure DevOps Services ou Git, l’intégration continue est intégrée ; vous avez uniquement besoin de cocher une case dans Azure DevOps Services. Si vous utilisez un contrôle de code source externe (comme GitHub), un `webhook` avertit Azure DevOps Services de la mise à jour ou de la poussée (push) vers Git/GitHub.

3. Azure DevOps Services tire (pull) le dépôt SCC, notamment le fichier Dockerfile décrivant l’image ainsi que le code d’application et de test.

4. Azure DevOps Services génère une image Docker et l’étiquette avec un numéro de build.

5. Azure DevOps Services instancie le conteneur Docker dans l’hôte Docker provisionné et exécute les tests appropriés.

6. Si les tests réussissent, l’image est réétiquetée avec un nom significatif afin que vous sachiez qu’il s’agit d’une « build consacrée » (comme « /1.0.0 » ou n’importe quelle autre étiquette), puis poussée vers votre registre Docker (Docker Hub, Azure Container Registry, DTR, etc.).

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Mise en œuvre du pipeline CI avec Azure DevOps Services et l’extension Docker pour Azure DevOps Services

Visual Studio Azure DevOps Services contient des modèles de build et de mise en production que vous pouvez utiliser dans votre pipeline CI/CD, pour générer des images Docker, pousser (push) des images Docker vers un registre Docker authentifié, exécuter des images Docker ou exécuter d’autres opérations disponibles depuis l’interface CLI de Docker. Il ajoute également une tâche Docker Compose que vous pouvez utiliser pour générer, pousser et exécuter des applications Docker multiconteneurs ou exécuter d’autres opérations disponibles depuis l’interface CLI de Docker Compose, comme illustré dans la Figure 5-3.

![Capture d’écran du pipeline Docker CI à Azure DevOps.](./media/docker-application-outer-loop-devops-workflow/docker-ci-pipeline-azure-devops.png)

**Figure 5-3**. Pipeline d’intégration continue Docker dans Azure DevOps Services incluant les modèles de build et de mise en production et les tâches associées.

Vous pouvez utiliser ces modèles et tâches pour construire les artefacts CI/CD à générer, tester et déployer dans Azure Service Fabric, Azure Kubernetes Service et des offres similaires.

Avec ces tâches Visual Studio Team Services, une machine virtuelle ou un hôte Linux-Docker de build provisionné dans Azure et le registre Docker de votre choix (Azure Container Registry, Docker Hub, DTR Docker privé ou tout autre registre Docker), vous pouvez assembler votre pipeline CI Docker de façon très cohérente.

***Conditions requises :***

- Azure DevOps Services ou, pour les installations locales, Team Foundation Server 2015 Update 3 ou version ultérieure

- Un agent Azure DevOps Services ayant les binaires Docker

  Un moyen facile de créer un de ces agents consiste à utiliser Docker pour exécuter un conteneur basé sur l’image Docker de l’agent Azure DevOps Services.

> [!INFORMATIONS] Pour en savoir plus sur l’assemblage d’un pipeline CI Docker Azure DevOps Services et voir les procédures pas à pas, consultez ces sites :
>
> - Exécution d’un agent Visual Studio Team Services (maintenant Azure DevOps Services) en tant que conteneur Docker : \
>   <https://hub.docker.com/_/microsoft-azure-pipelines-vsts-agent>
>
> - Génération d’images Docker Linux .NET Core avec Azure DevOps Services : \
>   <https://docs.microsoft.com/archive/blogs/stevelasker/building-net-core-linux-docker-images-with-visual-studio-team-services>
>
> - Génération d’une machine de build Visual Studio Team Services basée sur Linux avec prise en charge de Docker : \
>   <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>Intégrer, tester et valider des applications Docker multiconteneurs

En règle générale, la plupart des applications Docker sont composées de plusieurs conteneurs plutôt que d’un seul. Un bon exemple est une application orientée microservices pour laquelle vous auriez un conteneur par microservice. Toutefois, même sans suivre strictement les modèles d’approche des microservices, il est probable que votre application Docker soit composée de plusieurs conteneurs ou services.

Ainsi, après avoir généré les conteneurs de l’application dans le pipeline CI, vous devez également déployer, intégrer et tester l’application dans son ensemble avec tous ses conteneurs au sein d’un hôte Docker d’intégration ou même dans un cluster de test auquel vos conteneurs sont distribués.

Si vous utilisez un seul hôte, vous pouvez recourir à des commandes Docker telles que docker-compose pour générer et déployer des conteneurs associés afin de tester et valider l’environnement Docker dans une seule machine virtuelle. Toutefois, si vous utilisez un cluster orchestrateur tel que DC/OS, Kubernetes ou Docker Swarm, vous devez déployer vos conteneurs par le biais d’un mécanisme ou orchestrateur différent, en fonction du cluster/planificateur sélectionné.

Voici plusieurs types de tests que vous pouvez exécuter contre des conteneurs Docker :

- Tests unitaires pour conteneurs Docker

- Test de groupes d’applications ou de microservices liés entre eux

- Test dans les versions de production et de contrôle de validité

Le point important est que quand vous exécutez des tests d’intégration et fonctionnels, vous devez le faire en dehors des conteneurs. Les tests ne sont pas contenus ou exécutés dans les conteneurs que vous déployez, car les conteneurs sont basés sur des images statiques qui doivent être des répliques exactes de celles que vous allez déployer en production.

Lors du test de scénarios plus avancés, tels que l’inclusion de plusieurs clusters (cluster de test, cluster de préproduction et cluster de production), une option pratique consiste à publier les images sur un registre afin de pouvoir opérer le test dans différents clusters.

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>Pousser l’image Docker d’application personnalisée à votre registre Docker global

Une fois les images Docker testées et validées, vous pouvez les étiqueter et les publier sur votre registre Docker. Le registre Docker est un élément essentiel du cycle de vie des applications Docker, car c’est l’emplacement central où vous stockez votre test personnalisé (également appelé « images consacrées ») en vue de son déploiement sur des environnements d’assurance qualité et de production.

De la même manière que le code d’application stocké dans votre dépôt SCC (Git, etc.) est votre « source de vérité », le registre Docker est la « source de vérité » pour vos bits ou application binaire à déployer sur les environnements de production ou d’assurance qualité.

En règle générale, vous souhaiterez peut-être que les dépôts privés de vos images personnalisées se trouvent dans un dépôt privé au sein d’Azure Container Registry ou d’un registre local comme Docker Trusted Registry ou dans un registre cloud public avec accès restreint (tel que Docker Hub), bien que dans ce dernier cas vous deviez approuver la sécurité du fournisseur si votre code n’est pas open source. Dans les deux cas, la méthode que vous utilisez est similaire et est basée sur la commande `docker push`, comme indiqué dans la Figure 5-4.

![Diagramme montrant la poussée des images personnalisées à un registre de conteneurs.](./media/docker-application-outer-loop-devops-workflow/docker-push-custom-images.png)

**Figure 5-4**. Publication des images personnalisées sur un registre Docker

À l’étape 3, pour la génération, l’intégration et les tests (CI), vous pouvez publier les images Docker résultantes sur un registre privé ou public. Les fournisseurs de cloud proposent diverses offres de registres Docker telles qu’Azure Container Registry, Amazon Web Services Container Registry, Google Container Registry et Quay Registry.

À l’aide des tâches Docker, vous pouvez pousser un ensemble d’images de service définies par un fichier `docker-compose.yml`, avec plusieurs étiquettes, à un registre Docker authentifié (tel qu’Azure Container Registry), comme illustré dans la Figure 5-5.

![Capture d’écran montrant l’étape pour publier des images à un registre.](./media/docker-application-outer-loop-devops-workflow/publish-custom-image-to-docker-registry.png)

**Figure 5-5**. Utilisation d’Azure DevOps Services pour publier des images personnalisées sur un registre Docker

> [!INFORMATIONS] Pour plus d’informations sur Azure Container Registry, consultez <https://aka.ms/azurecontainerregistry>.

## <a name="step-4-cd-deploy"></a>Étape 4 : CD, Déploiement

L’immuabilité des images Docker garantit un déploiement reproductible avec ce qui a été développé, testé par le biais de l’intégration continue et exécuté en production. Une fois les images Docker d’application publiées sur votre registre Docker (privé ou public), vous pouvez les déployer sur les différents environnements dont vous disposez (production, assurance qualité, préproduction, etc.) à partir de votre pipeline CD en utilisant Azure DevOps Services Release Management ou des tâches de pipeline Azure DevOps Services.

Toutefois, à ce stade, la nature du déploiement dépend du type d’application Docker à déployer. Le déploiement d’une application simple (du point de vue de la composition et du déploiement), telle qu’une application monolithique comprenant quelques conteneurs ou services, sur quelques serveurs ou machines virtuelles diffère du déploiement d’une application plus complexe, telle qu’une application orientée microservices dotée de fonctionnalités d’hyperscale. Ces deux scénarios sont expliqués dans les sections suivantes.

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>Déploiement d’applications Docker composées sur plusieurs environnements Docker

Examinons d’abord le scénario moins complexe : déploiement sur des hôtes Docker simples (machines virtuelles ou serveurs) dans un seul environnement ou dans plusieurs environnements (assurance qualité, préproduction et production). Dans ce scénario, en interne, votre pipeline CD peut utiliser docker-compose (à partir de vos tâches de déploiement Azure DevOps Services) pour déployer les applications Docker avec l’ensemble de conteneurs ou de services connexe, comme illustré dans la Figure 5-6.

![Diagramme montrant le CD déployer l’étape de déploiement à trois environnements.](./media/docker-application-outer-loop-devops-workflow/deploy-app-containers-to-docker-host-environments.png)

**Figure 5-6**. Déploiement de conteneurs d’application sur un registre d’environnements hôtes Docker simple

La figure 5-7 met en évidence la façon dont vous pouvez connecter l’intégration continue de la build aux environnements de test et d’assurance qualité via Azure DevOps Services en cliquant sur Docker Compose dans la boîte de dialogue Ajouter des tâches. Toutefois, quand vous effectuez un déploiement sur des environnements de préproduction ou de production, vous utilisez généralement des fonctionnalités Release Management gérant plusieurs environnements (assurance qualité, préproduction et production, par exemple). Si vous effectuez un déploiement sur des hôtes Docker uniques, vous recourez à la tâche « Docker Compose » d’Azure DevOps Services (qui, en coulisses, appelle la commande `docker-compose up`). Si vous effectuez un déploiement sur Azure Kubernetes Service (AKS), c’est la tâche Déployer sur Kubernetes qui est utilisée, comme expliqué dans la section qui suit.

![Capture d’écran montrant Add tâches dialogue de la tâche Docker Compose.](./media/docker-application-outer-loop-devops-workflow/add-tasks-docker-compose.png)

**Figure 5-7**. Ajout d’une tâche Docker Compose dans un pipeline Azure DevOps Services

Quand vous créez une mise en production dans Azure DevOps Services, elle prend un ensemble d’artefacts d’entrée. Ces artefacts sont destinés à être immuables pour la durée de vie de la mise en production, dans tous les environnements. Quand vous introduisez des conteneurs, les artefacts d’entrée identifient les images dans un registre à déployer. Suivant la manière dont ces images sont identifiées, il n’est pas garanti qu’elles restent les mêmes pendant toute la durée de la mise en production, en particulier si vous référencez `myimage:latest` à partir d’un fichier `docker-compose`.

Les modèles Azure DevOps Services vous donnent la possibilité de générer des artefacts de build contenant des condensats d’image de registre spécifiques qui identifient de manière unique le même binaire d’image. Ce sont ceux-là qu’il convient d’utiliser comme entrée pour une mise en production.

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>Gestion des mises en production dans les environnements Docker à l’aide d’Azure DevOps Services Release Management

À l’aide des modèles Azure DevOps Services, vous pouvez générer une nouvelle image, la publier sur un registre Docker, l’exécuter sur des hôtes Linux ou Windows et utiliser des commandes telles que `docker-compose` pour déployer plusieurs conteneurs sous la forme d’une application entière, le tout grâce aux fonctionnalités Azure DevOps Services Release Management destinées à plusieurs environnements, comme illustré dans la Figure 5-8.

![Capture d’écran montrant la configuration des versions Docker composer.](./media/docker-application-outer-loop-devops-workflow/configure-docker-compose-release.png)

**Figure 5-8**. Configuration de tâches Docker Compose Azure DevOps Services à partir d’Azure DevOps Services Release Management

Toutefois, gardez à l’esprit que le scénario illustré dans la Figure 5-6 et implémenté dans la Figure 5-8 est un scénario simple (déploiement sur des machines virtuelles et hôtes Docker uniques, à raison d’un conteneur ou instance par image) et qui ne doit probablement être utilisé que dans le cadre d’un développement ou de tests. Dans la plupart des scénarios de production d’entreprise, vous souhaitez obtenir une haute disponibilité (HA) et une scalabilité facile à gérer en équilibrant la charge entre plusieurs nœuds, serveurs et machines virtuelles ainsi que des « basculements intelligents » afin que, si un serveur ou un nœud tombe en panne, ses services et conteneurs soient déplacés vers un autre serveur hôte ou machine virtuelle. Dans ce cas, vous avez besoin de technologies plus avancées telles que les clusters de conteneurs, les orchestrateurs et les planificateurs. Ainsi, la façon d’effectuer un déploiement sur ces clusters passe par la maîtrise des scénarios avancés expliqués dans la section suivante.

### <a name="deploying-docker-applications-to-docker-clusters"></a>Déploiement d’applications Docker sur des clusters Docker

La nature des applications distribuées nécessite des ressources de calcul qui sont également distribuées. Pour bénéficier de fonctionnalités de niveau production, vous devez disposer de fonctionnalités de clustering qui fournissent une haute scalabilité et une haute disponibilité basées sur le regroupement de ressources.

Vous pourriez déployer des conteneurs manuellement sur ces clusters à partir d’un outil CLI ou d’une interface utilisateur web, mais vous devez réserver ce genre de travail manuel à l’identification d’objectifs de gestion et de test de déploiement tels que la réalisation d’un scale-out ou d’une supervision.

Du point de vue du déploiement continu, et notamment d’Azure DevOps Services, vous pouvez exécuter à partir de vos environnements Azure DevOps Services Release Management des tâches de déploiement spécifiques destinées à déployer vos applications conteneurisées sur des clusters distribués dans Container Service, comme illustré dans la Figure 5-9.

![Diagramme montrant le CD déployer l’étape de déploiement aux orchestrateurs.](./media/docker-application-outer-loop-devops-workflow/cd-deploy-to-orchestrators.png)

**Figure 5-9**. Déploiement d’applications distribuées sur Container Service

Pour effectuer un déploiement sur certains clusters ou orchestrateurs, vous utilisez probablement des mécanismes et des scripts de déploiement spécifiques suivant chaque orchestrateur (en d’autres termes, Kubernetes et Service Fabric ont des mécanismes de déploiement différents) au lieu de l’outil convivial `docker-compose` basé sur le fichier de définition `docker-compose.yml`. Cependant, grâce à la tâche Azure DevOps Services Docker Deploy, indiquée dans la figure 5-10, vous pouvez maintenant également vous déployer aux orchestrateurs pris en charge en utilisant simplement votre fichier familier `docker-compose.yml` parce que l’outil effectue cette «traduction» pour vous (de votre `docker-compose.yml` fichier au format requis par l’orchestrateur).

![Capture d’écran montrant la tâche Deploy to Kubernetes.](./media/docker-application-outer-loop-devops-workflow/add-deploy-to-kubernetes-task.png)

**Figure 5-10**. Ajout de la tâche Déployer sur Kubernetes à votre environnement

La Figure 5-11 montre comment vous pouvez modifier la tâche Déployer sur Kubernetes avec les sections disponibles pour la configuration. Cette tâche est chargée de récupérer vos images Docker personnalisées prêtes à l’emploi à déployer en tant que conteneurs dans le cluster.

![Capture d’écran montrant la configuration de tâche Deploy to Kubernetes.](./media/docker-application-outer-loop-devops-workflow/edit-deploy-to-kubernetes-task.png)

**Figure 5-11**. Déploiement de la définition de la tâche Déployer sur Kubernetes sur ACS DC/OS

> [!INFORMATIONS] Pour en savoir plus sur le pipeline CD avec Azure DevOps Services et Docker, visitez <https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>Étape 5 : Exécuter et gérer

Étant donné que l’exécution et la gestion des applications au niveau de la production en entreprise constituent en elles-mêmes un sujet majeur et en raison du type d’opérations et des personnes qui travaillent à ce niveau (opérations informatiques) ainsi que de la grande étendue de ce domaine, le chapitre suivant est consacré à leur explication.

## <a name="step-6-monitor-and-diagnose"></a>Étape 6 : Surveiller et diagnostiquer

Ce sujet est également couvert dans le prochain chapitre dans le cadre des tâches effectuées par l’équipe informatique au sein des systèmes de production ; toutefois, il est important de souligner que les insights obtenus au cours de cette étape doivent parvenir à l’équipe de développement afin que l’application soit améliorée en permanence. De ce point de vue, DevOps est également impliqué, bien que les tâches et les opérations soient couramment effectuées par l’équipe informatique.

Ce n’est que quand la supervision et les diagnostics relèvent en totalité du domaine de DevOps que les processus de supervision et l’analytique sont effectués par l’équipe de développement par rapport à des environnements de test ou bêta. Ces opérations impliquent la réalisation de test de charge ou la supervision d’environnements bêta ou d’assurance qualité, où les bêta-testeurs essaient les nouvelles versions.

>[!div class="step-by-step"]
>[Suivant précédent](index.md)
>[Next](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)

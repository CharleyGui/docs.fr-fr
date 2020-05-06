---
title: Présentation de la plateforme et des outils Microsoft pour les applications en conteneur
description: Familiarisez-vous avec les offres de Microsoft visant à prendre en charge le cycle de vie des applications Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 84f4136c6b6c284dd5ecb3fc174ac825857a567e
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158500"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Présentation de la plateforme et des outils Microsoft pour les applications en conteneur

*Vision : créez un cycle de vie d’application en conteneur adaptable, adapté à l’entreprise qui couvre votre développement, vos opérations informatiques et la gestion de la production.*

La figure 3-1 illustre les principaux piliers du cycle de vie des applications Docker, classés selon le type de travail fourni par plusieurs équipes (développement d’applications, processus d’infrastructure DevOps, gestion et opérations informatiques). Dans l’entreprise, les profils du « persona » en charge de chaque zone sont généralement différents. Ses compétences varient aussi.

:::image type="complex" source="./media/index/microsoft-tools-contanerized-docker-app.png" alt-text="Diagramme montrant les outils Microsoft nécessaires à la gestion des applications de l’ancrage.":::
Outils Microsoft. Pour la charge de travail de développement/conception : le moteur d’ancrage pour Windows, Visual Studio et Visual Studio Code, .NET Core, service Azure Kubernetes. Pour la charge de travail Build/test/Ship : Azure DevOps, Team Foundation Server, CLI CLI, service Kubernetes Azure. Pour la charge de travail exécuter/surveiller/gérer : Azure Monitor, Portail Azure, Azure Kubernetes services, Service Fabric et d’autres orchestrateurs.
:::image-end:::

**Figure 3-1.** Principaux piliers du cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft

Un workflow de cycle de vie Docker en conteneur peut être initialement normalisé selon les « choix des produits par défaut », ce qui facilite et accélère le démarrage des développeurs. Toutefois, sous le capot, l’existence d’une infrastructure ouverte est fondamentale pour garantir un workflow flexible capable de s’adapter aux différents contextes de chaque organisation ou entreprise. L’infrastructure de workflow (composants et produits) doit être suffisamment flexible pour prendre en charge le futur environnement de chaque entreprise. Elle doit notamment permettre le remplacement de produits de développement ou DevOps par d’autres. Ces caractéristiques, à savoir la flexibilité, l’ouverture et le vaste choix de technologies d’infrastructure et de plateforme, sont précisément les priorités de Microsoft pour les applications Docker en conteneur, comme l’expliquent les chapitres qui suivent.

Comme le montre le tableau 3-1, l’intention de Microsoft DevOps pour les applications Docker en conteneur est de fournir un workflow DevOps ouvert qui permet de choisir les produits à utiliser pour chaque phase (Microsoft ou tiers) tout en bénéficiant d’un workflow simplifié avec des « produits par défaut » déjà connectés. Vous pouvez donc vous lancer rapidement dans votre workflow DevOps au niveau de l’entreprise pour les applications Docker.

**Tableau 3-1.** Workflows DevOps, ouverts à toute technologie

| Host | Technologies Microsoft | Technologies tierces, enfichables dans Azure |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Plateforme pour applications Docker   | • Microsoft Visual Studio et Visual Studio Code<br /> • .NET<br /> • Microsoft Azure Kubernetes Service (AKS)<br /> • Azure Service Fabric<br /> • Azure Container Registry<br /> | • N’importe quel éditeur de code (par exemple, Sublime)<br /> • N’importe quel langage (Node.js, Java, Go, etc.)<br /> • N’importe quel orchestrateur/planificateur<br /> • N’importe quel registre Docker<br /> |
| DevOps pour applications Docker     | • Azure DevOps Services<br /> • Microsoft Team Foundation Server<br /> • Azure Kubernetes Service (AKS)<br /> • Azure Service Fabric<br /> | • GitHub, Git, Subversion, etc.<br /> • Jenkins, Chef, Puppet, Velocity, CircleCI, TravisCI, etc.<br /> • Centre de données Docker local, Docker Swarm, Mesos DC/OS, Kubernetes, etc.<br /> |
| Gestion et surveillance  | • Azure Monitor | • Marathon, Chronos, etc.<br />|

La plateforme et les outils Microsoft pour les applications Docker en conteneur, tels que définis dans le tableau 3-1, comprennent les composants suivants :

- **Plateforme pour le développement d’applications Docker** Développement d’un service ou d’une collection de services constituant une « application ». La plateforme de développement permet aux développeurs d’effectuer tout le travail nécessaire avant d’envoyer (push) leur code dans un dépôt de code partagé. Le processus de développement de services déployés comme conteneurs est similaire à celui d’applications ou de services sans Docker. Vous pouvez continuer d’utiliser votre langage par défaut (.NET, Node.js, Go, etc.) et votre éditeur ou IDE préféré comme Visual Studio ou Visual Studio Code. Toutefois, plutôt que de considérer Docker comme destination du déploiement, vous développez vos services dans l’environnement Docker. Vous générez, exécutez, testez et déboguez votre code dans des conteneurs au niveau local, et vous indiquez l’environnement de destination au moment du développement. L’environnement de destination étant fourni au niveau local, les conteneurs Docker mettent en place ce qu’il faut pour améliorer considérablement votre cycle de vie DevOps. Visual Studio et Visual Studio Code offrent des extensions permettant d’intégrer les conteneurs Docker à votre processus de développement.

- **DevOps pour les applications Docker** Les développeurs qui créent des applications Docker peuvent utiliser [Azure DevOps Services](https://azure.microsoft.com/services/devops/) ou tout autre produit tiers, tel que Jenkins, pour générer une solution ALM (Application Lifecycle Management) automatisée complète.

  Les développeurs peuvent utiliser Azure DevOps Services pour créer une solution DevOps axée sur les conteneurs en vue d’établir un processus itératif rapide qui couvre le contrôle de code source, quelle que soit son origine (Azure DevOps Services-Git, GitHub, dépôt Git distant quelconque ou Subversion), l’intégration continue (CI), les tests unitaires internes, les tests d’intégration interconteneur/interservice, la livraison continue (CD) et la gestion des versions (RM). Les développeurs peuvent également automatiser leurs versions de l’application Dockr dans Azure Kubernetes service (AKS), du développement aux environnements intermédiaires et de production.

- **Gestion et supervision** Les informaticiens peuvent gérer et superviser des applications et services de production de plusieurs façons, en intégrant ces deux perspectives dans une expérience consolidée.

  - **Portail Azure** si vous utilisez des orchestrateurs Open source, Azure Kubernetes service (AKS), service fabric et d’autres orchestrateurs vous aident à configurer et à gérer vos environnements d’ancrage. Si vous utilisez Azure Service Fabric, l’outil Service Fabric Explorer vous permet de visualiser et de configurer votre cluster.

  - **Outils de l’arrimeur** vous pouvez gérer vos applications de conteneur à l’aide d’outils familiers. Il est inutile de changer vos méthodes de gestion Docker existantes pour déplacer les charges de travail de conteneur dans le cloud. Utilisez les outils de gestion d’application que vous connaissez déjà et connectez-vous par le biais des points de terminaison d’API standards de l’orchestrateur de votre choix. Vous pouvez également utiliser d’autres outils tiers pour gérer vos applications de station d’accueil, telles que le centre de gestion de l’ancrage ou même les outils d’ancrage de l’interface CLI.

    Même si vous connaissez bien les commandes Linux, vous pouvez gérer vos applications de conteneur à l’aide de Microsoft Windows et PowerShell avec une ligne de commande du sous-système Linux et les clients des produits (Docker, Kubernetes...) s’exécutant sur cette fonctionnalité de sous-système Linux. Vous allez en savoir plus sur l’utilisation de ces outils dans le sous-système Linux en utilisant votre système d’exploitation Microsoft Windows favori plus loin dans cet ouvrage.

  - **Outils open source** étant donné que AKS expose les points de terminaison d’API standard pour le moteur d’orchestration, les outils les plus populaires sont compatibles avec AKS et, dans la plupart des cas, ils fonctionnent dès le début, y compris les visualiseurs, la surveillance, les outils en ligne de commande et même les futurs outils dès qu’ils sont disponibles.

  - **Azure Monitor** Il s’agit de la solution d’Azure pour superviser tous les angles de votre environnement de production. Vous pouvez superviser les applications Docker de production en configurant simplement leur SDK dans vos services de manière à récupérer les données de journal générées par le système depuis les applications.

Microsoft offre donc une base complète pour un cycle de vie d’application Docker en conteneur de bout en bout. Toutefois, il s’agit d’une *collection de produits et de technologies qui vous permettent de sélectionner et d’intégrer des outils et processus existants*. La flexibilité d’une approche large et la profondeur des fonctionnalités offertes confèrent à Microsoft un positionnement avantageux dans le domaine du développement d’applications Docker en conteneur.

>[!div class="step-by-step"]
>[Précédent](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[suivant](../design-develop-containerized-apps/index.md)

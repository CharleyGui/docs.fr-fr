---
title: Présentation de la plateforme et des outils Microsoft pour les applications en conteneur
description: Découvrez les offres de Microsoft pour prendre en charge le cycle de vie des applications Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 6907528a5d7ff354a312e7575531b9c608cb479f
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195596"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Introduction à la plate-forme Microsoft et les outils pour les applications en conteneur

*Vision : Créer un adaptable, entreprise, en conteneur cycle de vie d’application qui s’étend sur votre développement, opérations informatiques et gestion de production.*

La figure 3-1 illustre les principaux piliers du cycle de vie des applications Docker, classés selon le type de travail fourni par plusieurs équipes (développement d’applications, processus d’infrastructure DevOps, gestion et opérations informatiques). Dans l’entreprise, les profils du « persona » en charge de chaque zone sont généralement différents. Ses compétences varient aussi.

![Outils de Microsoft. Pour la charge de travail de développement/conception : Moteur docker pour Windows, Visual Studio et Visual Studio Code, .NET Core, Azure Kubernetes Service. Pour la charge de travail de Test/Build/livraison : Azure DevOps, Team Foundation Server, Docker CLI, Azure Kubernetes Service. Pour la charge de travail d’exécution/analyse/gérer : Azure Monitor, Azure Portal Azure Kubernetes Services, Service Fabric, autres orchestrateurs.](./media/image1.png)

**Figure 3-1** : Principaux piliers du cycle de vie pour les applications Docker en conteneur avec la plate-forme Microsoft et outils

Un flux de travail du cycle de vie Docker en conteneur peut être initialement normalisé selon « par défaut produit choix, » ce qui facilite pour les développeurs démarrer plus rapidement, mais il est fondamental que sous le capot il doit être une infrastructure ouverte afin qu’il soit un flux de travail flexible capable de s’adapter aux différents contextes de chaque organisation ou d’une entreprise. L’infrastructure de workflow (composants et produits) doit être suffisamment flexible pour prendre en charge le futur environnement de chaque entreprise. Elle doit notamment permettre le remplacement de produits de développement ou DevOps par d’autres. Ces caractéristiques, à savoir la flexibilité, l’ouverture et le vaste choix de technologies d’infrastructure et de plateforme, sont précisément les priorités de Microsoft pour les applications Docker en conteneur, comme l’expliquent les chapitres qui suivent.

Comme le montre le tableau 3-1, l’intention de Microsoft DevOps pour les applications Docker en conteneur est de fournir un workflow DevOps ouvert qui permet de choisir les produits à utiliser pour chaque phase (Microsoft ou tiers) tout en bénéficiant d’un workflow simplifié avec des « produits par défaut » déjà connectés. Vous pouvez donc vous lancer rapidement dans votre workflow DevOps au niveau de l’entreprise pour les applications Docker.

**Tableau 3-1.** Flux de travail DevOps, ouvert à n’importe quelle technologie

| Hôte | Technologies Microsoft | Technologies tierces, enfichables dans Azure |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Plateforme pour applications Docker   | • Microsoft Visual Studio et Visual Studio Code<br /> • .NET<br /> • Microsoft Azure Kubernetes Service (AKS)<br /> • Azure Service Fabric<br /> • Azure Container Registry<br /> | • N’importe quel éditeur de code (par exemple, Sublime)<br /> • N’importe quel langage (Node.js, Java, Go, etc.)<br /> • N’importe quel orchestrateur/planificateur<br /> • N’importe quel registre Docker<br /> |
| DevOps pour applications Docker     | • Les Services azure DevOps<br /> • Microsoft Team Foundation Server<br /> • Azure Kubernetes Service (AKS)<br /> • Azure Service Fabric<br /> | • GitHub, Git, Subversion, etc.<br /> • Jenkins, Chef, Puppet, Velocity, CircleCI, TravisCI, etc.<br /> • Centre de données Docker local, Docker Swarm, Mesos DC/OS, Kubernetes, etc.<br /> |
| Gestion et surveillance  | • Azure Monitor | • Marathon, Chronos, etc.<br />|

La plateforme et les outils Microsoft pour les applications Docker en conteneur, tels que définis dans le tableau 3-1, comprennent les composants suivants :

- **Plateforme pour le développement d’applications Docker** Développement d’un service ou d’une collection de services constituant une « application ». La plateforme de développement permet aux développeurs d’effectuer tout le travail nécessaire avant d’envoyer (push) leur code dans un dépôt de code partagé. Développement de services déployés en tant que conteneurs, est similaires pour le développement des applications ou des services sans Docker même. Vous continuez à utiliser votre langage préféré (.NET, Node.js, Go, etc.) et un éditeur favori ou un IDE comme Visual Studio ou Visual Studio Code. Toutefois, plutôt que de considérer Docker comme destination du déploiement, vous développez vos services dans l’environnement Docker. Vous générez, exécutez, testez et déboguez votre code dans des conteneurs au niveau local, et vous indiquez l’environnement de destination au moment du développement. L’environnement de destination étant fourni au niveau local, les conteneurs Docker mettent en place ce qu’il faut pour améliorer considérablement votre cycle de vie DevOps. Visual Studio et Visual Studio Code offrent des extensions permettant d’intégrer les conteneurs Docker à votre processus de développement.

- **DevOps pour les applications Docker** permet aux développeurs qui créent des applications Docker [Azure DevOps Services](https://azure.microsoft.com/services/devops/) ou tout autre produit tiers, tels que Jenkins, pour générer un cycle de vie d’application automatisée complète Management (ALM).

  Avec Azure DevOps Services, les développeurs peuvent créer axée sur le conteneur de contrôler le DevOps pour un processus itératif rapide qui couvre le code source à partir de n’importe où (Azure DevOps Services-Git, GitHub, n’importe quel référentiel Git distant ou Subversion), intégration continue (CI) , tests unitaires internes, inter-container service/tests d’intégration, livraison continue (CD) et la gestion des versions (RM). Les développeurs peuvent également automatiser leurs versions d’application Docker dans Azure Kubernetes Service (AKS), du développement pour les environnements intermédiaire et de production.

- **Gestion et surveillance** informatique peuvent gérer et surveiller des applications de production et les services de plusieurs façons, l’intégration de ces deux perspectives dans une expérience consolidée.

  - **Portail Azure** si vous utilisez des orchestrateurs open source, Azure Kubernetes Service (AKS), Service Fabric et autres orchestrateurs vous aident à configurer et à gérer vos environnements Docker. Si vous utilisez Azure Service Fabric, l’outil Service Fabric Explorer vous permet de visualiser et de configurer votre cluster.

  - **Outils Docker** Vous pouvez gérer vos applications conteneur à l’aide d’outils familiers. Il est inutile de changer vos méthodes de gestion Docker existantes pour déplacer les charges de travail de conteneur dans le cloud. Utilisez les outils de gestion d’application que vous connaissez déjà et connectez-vous par le biais des points de terminaison d’API standards de l’orchestrateur de votre choix. Vous pouvez également utiliser d’autres outils tiers pour gérer vos applications Docker, notamment Docker Datacenter ou même les outils CLI Docker. 

    Même si vous êtes familiarisé avec les commandes Linux, vous pouvez gérer vos applications de conteneur à l’aide de Microsoft Windows et PowerShell avec une ligne de commande du sous-système de Linux et les produits (Docker, Kubernetes...) clients s’exécutant sur cette fonctionnalité de sous-système de Linux. Vous allez en savoir plus sur l’utilisation de ces outils dans le sous-système de Linux à l’aide de votre système d’exploitation de Windows Microsoft favoris plus loin dans ce livre.

  - **Outils Open source** , car ACS expose les points de terminaison de l’API standards pour le moteur d’orchestration, les outils les plus populaires sont compatibles avec ACS et, dans la plupart des cas, ne fonctionnera prêts à l’emploi, y compris les visualiseurs, surveillance, outils de ligne de commande et même futurs outils dès qu’elles deviennent disponibles.

  - **Azure Monitor** solution d’Azure est pour surveiller tous les angles de votre environnement de production. Vous pouvez surveiller des applications Docker de production en configurant simplement le SDK dans vos services afin que vous pouvez obtenir des données de journal générés par le système à partir des applications.

Microsoft offre donc une base complète pour un cycle de vie d’application Docker en conteneur de bout en bout. Toutefois, il est *une collection de produits et technologies qui vous permettent de sélectionner et d’intégrer avec existant, outils et processus*. La flexibilité d’une approche large et la profondeur des fonctionnalités offertes confèrent à Microsoft un positionnement avantageux dans le domaine du développement d’applications Docker en conteneur.

>[!div class="step-by-step"]
>[Précédent](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[Suivant](../design-develop-containerized-apps/index.md)

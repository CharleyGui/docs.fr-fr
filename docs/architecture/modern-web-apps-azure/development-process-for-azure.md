---
title: Processus de développement pour Azure
description: Architecturer des applications web modernes avec ASP.NET Core et Azure | Processus de développement pour Azure
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 7a641c1b6665af6e9e78ef182174b360041d74aa
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450039"
---
# <a name="development-process-for-azure"></a>Processus de développement pour Azure

> _« Avec le cloud, particuliers et petites entreprises peuvent configurer des services d’entreprise en un clin d’œil. »_  
> _- Roy Stephan_

## <a name="vision"></a>Vision

> *Développez comme vous voulez des applications ASP .NET Core bien conçues avec Visual Studio ou l’interface CLI dotnet et Visual Studio Code ou l’éditeur de votre choix.*

## <a name="development-environment-for-aspnet-core-apps"></a>Environnement de développement pour les applications ASP.NET Core

### <a name="development-tools-choices-ide-or-editor"></a>Choix des outils de développement : IDE ou éditeur

Que vous préfériez un IDE complet et puissant ou un éditeur léger et agile, Microsoft met à votre disposition tout ce dont vous avez besoin pour développer des applications ASP.NET Core.

**Visual Studio 2019.** Visual Studio 2019 est l’IDE idéal pour le développement d’applications pour ASP.NET Core. Il offre un hôte de fonctionnalités qui améliorent la productivité des développeurs. Vous pouvez l’utiliser pour développer l’application, puis analyser ses performances et d’autres caractéristiques. Le débogueur intégré vous permet de suspendre l’exécution du code et d’effectuer un pas à pas détaillé dans le code à la volée lors de son exécution. Test Runner intégré vous permet d’organiser vos tests et leurs résultats, et peut même effectuer des tests unitaires en direct pendant le codage. À l’aide de Live Share, vous pouvez collaborer en temps réel avec d’autres développeurs, en partageant votre session de code en toute transparence sur le réseau. Et quand vous êtes prêt, Visual Studio inclut tout ce dont vous avez besoin pour publier votre application sur Azure ou à l’endroit où vous pouvez l’héberger.

[Télécharger Visual Studio 2019](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

**Visual Studio Code et interface CLI dotnet** (outils multiplateformes pour Mac, Linux et Windows). Si vous préférez un éditeur léger et multiplateforme prenant en charge n’importe quel langage de développement, vous pouvez utiliser Microsoft Visual Studio Code et l’interface CLI dotnet. Ces produits proposent une expérience simple mais robuste qui simplifie le flux de travail du développeur. De plus, Visual Studio Code prend en charge des extensions pour le développement web et C\#, ce qui donne accès à Intellisense et à des tâches raccourcies dans l’éditeur.

[Télécharger le SDK .NET Core](https://dotnet.microsoft.com/download)

[Télécharger Visual Studio Code](https://code.visualstudio.com/download)

## <a name="development-workflow-for-azure-hosted-aspnet-core-apps"></a>Flux de travail de développement pour les applications ASP.NET Core hébergées par Azure

Le cycle de vie du développement d’une application débute sur une machine de développeur, là où le développeur programme l’application dans le langage de son choix et où il la teste localement. Les développeurs peuvent choisir leur système de contrôle de code source par défaut et peuvent configurer l’intégration continue (CI) et/ou la livraison/le déploiement continu(e) (CD) à l’aide d’un serveur de builds ou en fonction des fonctionnalités Azure intégrées.

Pour commencer à développer une application ASP.NET Core à l’aide de CI/CD, vous pouvez utiliser Azure DevOps Services ou le serveur TFS (Team Foundation Server) de votre organisation.

### <a name="initial-setup"></a>Configuration initiale

Pour créer un pipeline de mise en production pour votre application, vous devez avoir votre code d’application dans le contrôle de code source. Configurez un référentiel local et connectez-le à un référentiel distant dans un projet d’équipe. Suivez ces instructions :

- [Partager votre code avec Git et Visual Studio](https://docs.microsoft.com/azure/devops/git/share-your-code-in-git-vs) ou

- [Partager votre code avec TFVC et Visual Studio](https://docs.microsoft.com/azure/devops/tfvc/share-your-code-in-tfvc-vs)

Créez un service d’application Azure où vous déploierez votre application. Créez une application web en accédant au panneau App Services dans le portail Azure. Cliquez sur +Ajouter, sélectionnez le modèle Application web, cliquez sur Créer et spécifiez un nom et d’autres détails. L’application web sera accessible à partir de {nom}.azurewebsites.net.

![AzureWebApp](./media/image10-2.png)

**Figure 10-1.** Création d’une application web Azure App Service dans le portail Azure.

Votre processus de génération CI effectue une génération automatique chaque fois que du nouveau code est validé dans le référentiel de contrôle de code source du projet. Ainsi, vous savez immédiatement que le code a été généré (et, dans l’idéal, réussit les tests automatisés) et peut être déployé. Cette build CI génère un artefact de package de déploiement web et le publie en vue de sa consommation par votre processus CD.

[Définir votre processus de build CI](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#ci)

Veillez à activer l’intégration continue afin que le système mette en file d’attente une build chaque fois qu’un membre de votre équipe valide du nouveau code. Testez la build et vérifiez qu’elle produit un package de déploiement web comme l’un de ses artefacts.

Quand une build réussit, votre processus CD déploie les résultats de votre build CI sur votre application web Azure. Pour configurer cela, créez et configurez une *Mise en production*, qui sera déployée sur votre service d’application Azure.

[Définir votre processus de mise en production CD](https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core#cd)

Une fois que votre pipeline CI/CD est configuré, vous pouvez simplement effectuer des mises à jour de votre application web et les valider dans le contrôle de code source afin de les déployer.

### <a name="workflow-for-developing-azure-hosted-aspnet-core-applications"></a>Flux de travail de développement d’applications ASP.NET Core hébergées par Azure

Une fois que vous avez configuré votre compte Azure et votre processus CI/CD, le développement d’applications ASP.NET Core hébergées par Azure est simple. Voici les étapes de base que vous prenez habituellement lors de la création d’une application ASP.NET Core, hébergée dans Azure App Service en tant qu’application Web, comme illustré dans la figure 10-2.

![EndToEndDevDeployWorkflow](./media/image10-3.png)

**Figure 10-2.** Flux de travail pas à pas pour la création d’applications ASP.NET Core et leur hébergement dans Azure

#### <a name="step-1-local-dev-environment-inner-loop"></a>Étape 1. Boucle interne d’environnement de développement local

Le développement d’une application ASP.NET Core pour le déploiement sur Azure ne diffère en aucune manière d’un développement ordinaire. Utilisez l’environnement de développement local avec lequel vous êtes à l’aise, que ce soit Visual Studio 2017 ou l’interface CLI dotnet et Visual Studio Code ou votre éditeur favori. Vous pouvez écrire du code, exécuter et déboguer vos modifications, exécuter des tests automatisés et effectuer des validations locales dans le contrôle de code source jusqu’à ce que vous soyez prêt à envoyer vos modifications dans votre référentiel de contrôle de code source partagée.

#### <a name="step-2-application-code-repository"></a>Étape 2. Référentiel de code d’application

Chaque fois que vous êtes prêt à partager votre code avec votre équipe, vous devez envoyer vos modifications de votre référentiel de code source local vers le référentiel de code source partagé de votre équipe. Si vous travaillez dans une branche personnalisée, cette étape nécessite généralement la fusion de votre code dans une branche partagée (par exemple au moyen d’une [demande de tirage (pull request)](https://docs.microsoft.com/azure/devops/git/pull-requests)).

#### <a name="step-3-build-server-continuous-integration-build-test-package"></a>Étape 3. Serveur de builds : Intégration continue. Générer, tester, empaqueter

Une nouvelle build est déclenchée sur le serveur de builds chaque fois qu’une nouvelle validation est effectuée dans le référentiel de code d’application partagé. Dans le cadre du processus CI, cette build doit compiler entièrement l’application et exécuter des tests automatisés afin de confirmer que tout fonctionne comme prévu. Le résultat final du processus CI doit être une version empaquetée de l’application web, prête pour le déploiement.

#### <a name="step-4-build-server-continuous-delivery"></a>Étape 4. Serveur de builds : Livraison continue

Une fois qu’une build a réussi, le processus CD prend en charge les artefacts de build générés, qui comprennent notamment un package de déploiement web. Le serveur de builds déploie ce package sur Azure App Service, en remplaçant tout service existant par celui qui vient d’être créé. En général, cette étape cible un environnement de préproduction, mais certaines applications sont déployées directement en production par le biais d’un processus CD.

#### <a name="step-5-azure-app-service-web-app"></a>Étape 5. Application web Azure App Service

Une fois déployée, l’application ASP.NET Core s’exécute dans le contexte d’une application web Azure App Service. Cette application web peut être surveillée et configurée davantage dans le portail Azure.

#### <a name="step-6-production-monitoring-and-diagnostics"></a>Étape 6. Surveillance de la production et diagnostics

Pendant l’exécution de l’application web, vous pouvez surveiller son intégrité et recueillir des données de diagnostic et de comportement de l’utilisateur. Application Insights, qui est fourni avec Visual Studio, offre une instrumentation automatique pour les applications ASP.NET. Il peut vous fournir des informations sur l’utilisation, les exceptions, les requêtes, les performances et les journaux.

## <a name="references"></a>References

**Générer et déployer votre application ASP.NET Core sur Azure**  
<https://docs.microsoft.com/azure/devops/build-release/apps/aspnet/build-aspnet-core>

>[!div class="step-by-step"]
>[Précédent](test-asp-net-core-mvc-apps.md)
>[Suivant](azure-hosting-recommendations-for-asp-net-web-apps.md)

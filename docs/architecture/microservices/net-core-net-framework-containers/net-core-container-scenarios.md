---
title: Quand choisir .NET Core pour les conteneurs Docker
description: Architecture de microservices .NET pour les applications .NET en conteneur | Quand choisir .NET Core pour les conteneurs Docker
ms.date: 01/30/2020
ms.openlocfilehash: f784512af3f520f96d499ab002eda58071b3c284
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147373"
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Quand choisir .NET Core pour les conteneurs Docker

La modularité et la légèreté de .NET Core en font l’outil idéal pour les conteneurs. Quand vous déployez ou démarrez un conteneur, son image est beaucoup plus petite avec .NET Core qu’avec le .NET Framework. En revanche, pour utiliser le .NET Framework pour un conteneur, vous devez baser votre image sur l’image Windows Server Core, qui est beaucoup plus lourde que les images Windows Nano Server ou Linux que vous utilisez pour .NET Core.

De plus, .NET Core étant multiplateforme, vous pouvez déployer des applications serveur avec des images de conteneur Linux ou Windows. Cependant, si vous utilisez le .NET Framework classique, vous pouvez déployer uniquement des images basées sur Windows Server Core.

Vous trouverez ci-dessous une explication plus détaillée des raisons de choisir .NET Core.

## <a name="developing-and-deploying-cross-platform"></a>Développement et déploiement multiplateformes

Il va de soi que si votre objectif est de disposer d’une application (application ou service web) capable de s’exécuter sur plusieurs plateformes prises en charge par Docker (Linux et Windows), .NET Core est le bon choix, car le .NET Framework prend uniquement en charge Windows.

.NET Core prend aussi en charge macOS comme plateforme de développement. Cependant, quand vous déployez des conteneurs sur un hôte Docker, celui-ci doit (à ce moment-là) être basé sur Windows ou Linux. Par exemple, dans un environnement de développement, vous pouvez utiliser une machine virtuelle Linux s’exécutant sur un Mac.

[Visual Studio](https://www.visualstudio.com/vs/) propose un environnement de développement intégré (IDE) pour Windows et prend en charge le développement Docker.

[Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/) est un IDE, une évolution de Xamarin Studio, qui s’exécute sur macOS et prend en charge le développement d’applications Docker. Ce choix est recommandé pour les développeurs qui travaillent sur des ordinateurs Mac et qui veulent utiliser un IDE puissant.

Vous pouvez également utiliser [Visual Studio Code](https://code.visualstudio.com/) sur macOS, Linux et Windows. Visual Studio Code prend en charge entièrement .NET Core, y compris IntelliSense et débogage. Parce que VS Code est un éditeur léger, vous pouvez l’utiliser pour développer des applications conteneurisées sur le Mac en conjonction avec le Docker CLI et le [CLI .NET Core](../../../core/tools/index.md). Vous pouvez aussi cibler .NET Core avec la plupart des éditeurs tiers comme Sublime, Emacs, vi et le projet open source OmniSharp, qui assure aussi une prise en charge d’IntelliSense.

En plus des IDE et des éditeurs, vous pouvez utiliser le [CLI .NET Core](../../../core/tools/index.md) pour toutes les plates-formes prises en charge.

## <a name="using-containers-for-new-green-field-projects"></a>Utilisation de conteneurs pour les nouveaux projets (« green-field »)

Les conteneurs sont couramment utilisés avec une architecture de microservices, même s’ils peuvent aussi servir à organiser en conteneurs les services ou applications web qui suivent un modèle d’architecture. Vous pouvez utiliser le .NET Framework dans les conteneurs Windows, mais par sa modularité et sa légèreté, .NET Core est parfait pour les conteneurs et les architectures de microservices. Quand vous créez et déployez un conteneur, son image est beaucoup plus petite avec .NET Core qu’avec le .NET Framework.

## <a name="create-and-deploy-microservices-on-containers"></a>Créer et déployer des microservices sur des conteneurs

Vous pouvez utiliser le .NET Framework classique pour créer des applications basées sur des microservices (sans conteneurs) en suivant des processus ordinaires. De cette façon, comme .NET Framework est déjà installé et partagé entre les processus, ceux-ci démarrent rapidement du fait de leur légèreté. En revanche, si vous utilisez des conteneurs, l’image pour le .NET Framework classique est aussi basée sur Windows Server Core, ce qui la rend trop lourde pour une approche de microservices dans des conteneurs. Cependant, les équipes ont été à la recherche d’opportunités pour améliorer l’expérience pour les utilisateurs du Cadre .NET ainsi. Récemment, la taille des [images de conteneurs Windows Server Core ont été réduites à >40% plus petit](https://devblogs.microsoft.com/dotnet/we-made-windows-server-core-container-images-40-smaller).

D’autre part, .NET Core est le meilleur candidat si vous adoptez un système axé sur les microservices qui est basé sur des conteneurs, parce que .NET Core est léger. En outre, ses images de conteneurs connexes, pour Linux ou Windows Nano Server, sont maigres et petits, ce qui rend les conteneurs légers et rapides à démarrer.

Un microservice doit être le petit possible de façon à être léger pendant son exécution, à offrir un faible encombrement, à présenter un contexte limité réduit (voir DDD, [Conception pilotée par le modèle](https://en.wikipedia.org/wiki/Domain-driven_design)), à ne pas être une source de problèmes et à démarrer et à s’arrêter rapidement. Pour remplir ces conditions, vous devez utiliser des images de conteneur petites et rapides à instancier à l’instar de l’image de conteneur .NET Core.

Une architecture de microservices permet aussi de combiner des technologies au-delà des limites d’un service. Une migration progressive vers .NET Core devient ainsi possible pour les nouveaux microservices qui fonctionnent conjointement avec d’autres microservices ou services développés avec Node.js, Python, Java, GoLang ou d’autres technologies.

## <a name="deploying-high-density-in-scalable-systems"></a>Déploiement de la haute densité dans des systèmes scalables

Quand votre système basé sur des conteneurs a besoin d’une densité, d’une granularité et de performances optimales, .NET Core et ASP.NET Core constituent les meilleures options. ASP.NET Core est jusqu’à dix fois plus rapide qu’ASP.NET dans le .NET Framework classique et il devance les autres technologies courantes pour les microservices, telles que les servlets Java, Go et Node.js.

Cela est particulièrement intéressant pour les architectures de microservices dans lesquelles plusieurs centaines de microservices (conteneurs) peuvent s’exécuter simultanément. Avec des images ASP.NET Core (basées sur le runtime .NET Core) sur Linux ou Windows Nano, vous pouvez exécuter votre système avec beaucoup moins de serveurs ou de machines virtuelles, ce qui en fin de compte vous permet de réaliser des économies en infrastructure et hébergement.

>[!div class="step-by-step"]
>[Suivant précédent](general-guidance.md)
>[Next](net-framework-container-scenarios.md)

---
title: Quand choisir .NET 5 pour les conteneurs de l’ancrage
description: Architecture des microservices .NET pour les applications .NET en conteneur | Quand choisir .NET pour les conteneurs d’ancrage
ms.date: 01/13/2021
ms.openlocfilehash: 61909c91d795582af499456c65ae0d7b4f2911e2
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189276"
---
# <a name="when-to-choose-net-for-docker-containers"></a>Quand choisir .NET pour les conteneurs d’ancrage

La modularité et la nature légère de .NET 5 le rendent parfait pour les conteneurs. Lorsque vous déployez et démarrez un conteneur, son image est beaucoup plus petite avec .NET 5 qu’avec .NET Framework. En revanche, pour utiliser .NET Framework pour un conteneur, vous devez baser votre image sur l’image Windows Server Core, ce qui est beaucoup plus lourd que les images Windows nano Server ou Linux que vous utilisez pour .NET 5.

En outre, .NET 5 est multiplateforme, ce qui vous permet de déployer des applications serveur avec des images de conteneur Linux ou Windows. Cependant, si vous utilisez le .NET Framework classique, vous pouvez déployer uniquement des images basées sur Windows Server Core.

Vous trouverez ci-dessous une explication plus détaillée de la raison pour laquelle choisir .NET 5.

## <a name="developing-and-deploying-cross-platform"></a>Développement et déploiement multiplateformes

En clair, si votre objectif est de disposer d’une application (application Web ou service) qui peut s’exécuter sur plusieurs plateformes prises en charge par l’arrimeur (Linux et Windows), le bon choix est .NET 5, car .NET Framework prend en charge uniquement Windows.

.NET 5 prend également en charge macOS comme plate-forme de développement. Cependant, quand vous déployez des conteneurs sur un hôte Docker, celui-ci doit (à ce moment-là) être basé sur Windows ou Linux. Par exemple, dans un environnement de développement, vous pouvez utiliser une machine virtuelle Linux s’exécutant sur un Mac.

[Visual Studio](https://www.visualstudio.com/vs/) propose un environnement de développement intégré (IDE) pour Windows et prend en charge le développement Docker.

[Visual Studio pour Mac](https://www.visualstudio.com/vs/visual-studio-mac/) est un IDE, une évolution de Xamarin Studio, qui s’exécute sur macOS et prend en charge le développement d’applications Docker. Cet outil doit être le choix privilégié pour les développeurs qui travaillent sur des ordinateurs Mac qui souhaitent également utiliser un IDE puissant.

Vous pouvez également utiliser [Visual Studio code](https://code.visualstudio.com/) sur MacOS, Linux et Windows. Visual Studio Code prend entièrement en charge .NET 5, y compris IntelliSense et le débogage. Étant donné que VS Code est un éditeur léger, vous pouvez l’utiliser pour développer des applications en conteneur sur l’ordinateur conjointement avec l’interface CLI et l' [interface CLI .net](../../../core/tools/index.md). Vous pouvez également cibler .NET 5 avec la plupart des éditeurs tiers, comme sublime, Emacs, VI et le projet OmniSharp Open source, qui fournit également la prise en charge d’IntelliSense.

Outre les IDE et les éditeurs, vous pouvez utiliser l' [interface de commande .net](../../../core/tools/index.md) pour toutes les plateformes prises en charge.

## <a name="using-containers-for-new-green-field-projects"></a>Utilisation de conteneurs pour les nouveaux projets (« green-field »)

Les conteneurs sont couramment utilisés avec une architecture de microservices, même s’ils peuvent aussi servir à organiser en conteneurs les services ou applications web qui suivent un modèle d’architecture. Vous pouvez utiliser .NET Framework sur des conteneurs Windows, mais la modularité et la nature légère de .NET 5 le rendent parfait pour les architectures de conteneurs et de microservices. Quand vous créez et déployez un conteneur, son image est beaucoup plus petite avec .NET Core qu’avec le .NET Framework.

## <a name="create-and-deploy-microservices-on-containers"></a>Créer et déployer des microservices sur des conteneurs

Vous pouvez utiliser le .NET Framework classique pour créer des applications basées sur des microservices (sans conteneurs) en suivant des processus ordinaires. De cette façon, comme .NET Framework est déjà installé et partagé entre les processus, ceux-ci démarrent rapidement du fait de leur légèreté. En revanche, si vous utilisez des conteneurs, l’image pour le .NET Framework classique est aussi basée sur Windows Server Core, ce qui la rend trop lourde pour une approche de microservices dans des conteneurs. Toutefois, les équipes cherchent des opportunités pour améliorer l’expérience des utilisateurs .NET Framework. Récemment, la taille des [images de conteneur Windows Server Core a été réduite à >40% plus petite](https://devblogs.microsoft.com/dotnet/we-made-windows-server-core-container-images-40-smaller).

En revanche, .NET 5 est le meilleur candidat si vous adoptez un système orienté microservices basé sur des conteneurs, car .NET 5 est léger. En outre, les images de conteneur associées, pour Linux ou Windows nano Server, sont légères et petites, ce qui rend les conteneurs clairs et rapides à démarrer.

Un microservice doit être le petit possible de façon à être léger pendant son exécution, à offrir un faible encombrement, à présenter un contexte limité réduit (voir DDD, [Conception pilotée par le modèle](https://en.wikipedia.org/wiki/Domain-driven_design)), à ne pas être une source de problèmes et à démarrer et à s’arrêter rapidement. Pour ces exigences, vous pouvez utiliser des images de conteneur petites et rapides à instancier comme l’image de conteneur .NET 5.

Une architecture de microservices permet aussi de combiner des technologies au-delà des limites d’un service. Cette approche permet une migration progressive vers .NET 5 pour les nouveaux microservices qui fonctionnent conjointement avec d’autres microservices ou avec des services développés avec Node.js, Python, Java, GoLang ou d’autres technologies.

## <a name="deploying-high-density-in-scalable-systems"></a>Déploiement de la haute densité dans des systèmes scalables

Lorsque votre système basé sur des conteneurs a besoin d’une densité, d’une granularité et de performances optimales, .NET et ASP.NET Core sont vos meilleures options. ASP.NET Core est jusqu’à 10 fois plus rapide que ASP.NET dans le .NET Framework traditionnel, et il dirige d’autres technologies populaires du secteur pour les microservices, comme les servlets Java, Go et Node.js.

Cette approche est particulièrement pertinente pour les architectures de microservices, où vous pouvez exécuter des centaines de microservices (conteneurs). Avec les images ASP.NET Core (basées sur le Runtime .NET) sur Linux ou Windows nano, vous pouvez exécuter votre système avec un nombre bien plus faible de serveurs ou de machines virtuelles, ce qui permet d’économiser des coûts dans l’infrastructure et l’hébergement.

>[!div class="step-by-step"]
>[Précédent](general-guidance.md) 
> [Suivant](net-framework-container-scenarios.md)

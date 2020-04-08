---
title: .NET Core et Open-Source
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: 4d9d42304c58c631020d8b12bec5c038bc0c07ab
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888239"
---
# <a name="net-core-and-open-source"></a>.NET Core et l’open source

Cet article fournit un bref aperçu de ce que .NET Core est et montre comment vous pouvez trouver plus d’informations. Pour trouver la liste complète de la documentation pour .NET Core, visitez le [guide .NET Core](../../core/index.yml).

## <a name="what-is-net-core"></a>Qu'est-ce que le .NET Core ?  

.NET Core est un objectif général, modulaire, multiplateforme, et la mise en œuvre open-source de la norme .NET. Il contient plusieurs des mêmes API que le cadre .NET (mais .NET Core est un ensemble plus petit) et comprend le temps d’exécution, le cadre, le compilateur et les composants d’outils qui prennent en charge une variété de systèmes d’exploitation et de cibles de puces. L’implémentation .NET Core a été essentiellement motivée par les charges de travail ASP.NET Core, mais aussi par la nécessité et l’envie d’avoir une implémentation plus moderne. Il peut être utilisé dans les scénarios de périphériques, de nuages et d’images intégrées/IoT.  
  
Pour commencer avec .NET Core, visitez le tutoriel .NET [Bonjour Monde en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).  
  
Les principales caractéristiques de .NET Core sont les :
  
- **Multiplateforme.** .NET Core fournit des fonctionnalités clés permettant d’implémenter les composants d’application dont vous avez besoin et de réutiliser le code, quelle que soit votre plateforme cible. Il prend actuellement en charge trois principaux systèmes d’exploitation (OS) : Windows, Linux et macOS. Vous pouvez écrire des applications et des bibliothèques qui s’exécutent telles quelles sur les systèmes d’exploitation pris en charge. Pour afficher la liste des systèmes d’exploitation pris en charge, consultez la [feuille de route .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md).
  
- **Open source.** .NET Core est l’un des nombreux projets placés sous l’intendance de [.NET Foundation](https://www.dotnetfoundation.org/) et disponible sur [GitHub](https://github.com/). En tant que projet open-source, .NET Core promeut un processus de développement plus transparent et une communauté active et engagée.  
  
- **Déploiement flexible.** Il existe deux méthodes principales pour déployer votre application : le déploiement dépendant du framework ou le déploiement autonome. Avec le déploiement dépendant du framework, seules vos dépendances d’application et tierces sont installées. Votre application dépend de la présence d’une version de .NET Core à l’échelle du système. Avec le déploiement autonome, la version .NET Core utilisée pour construire votre application est également déployée avec votre application et dépendances tierces et peut fonctionner côte à côte avec d’autres versions. Pour plus d’informations, voir [.NET Core Application Deployment](../../core/deploying/index.md).

- **Modulaire :** .NET Core est modulaire, car il est publié via NuGet dans des packages d’assembly plus petits. Plutôt qu’un grand assemblage qui contient la plupart des fonctionnalités de base, .NET Core est disponible sous forme de paquets plus petits et centrés sur les fonctionnalités. Cette modularité permet un modèle de développement plus agile pour nous et vous permet d’optimiser votre application pour inclure uniquement les paquets NuGet dont vous avez besoin. Les avantages d’une petite zone de surface d’application offrent une sécurité accrue, une maintenance réduite, des performances améliorées et une réduction des coûts dans un modèle de paiement basé uniquement sur votre utilisation.  
  
## <a name="the-net-core-platform"></a>La plate-forme .NET Core
  
La plate-forme .NET Core est composée de plusieurs composants, y compris les compilateurs gérés, l’heure d’exécution, les bibliothèques de classe de base, et de nombreux modèles d’application, tels que ASP.NET Core. Vous pouvez en apprendre davantage sur les différents composants et vous engager en visitant le repos [suivant GitHub:](https://github.com/)  
  
- [.NET Maison de base](https://github.com/dotnet/core)  
  
- [Runtime - plate-forme .NET Core et runtime](https://github.com/dotnet/runtime)  
  
- [CLI – Outils en ligne de commande .NET Core](https://github.com/dotnet/cli)  
  
- [Roslyn – .NET Compiler Platform](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a>Voir aussi

- [.NET tutoriel - Bonjour monde en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [Guide .NET Core](../../core/index.yml)
- [ASP.NET docs de base](/aspnet/core/)

---
title: .NET Core et Open-Source
description: Lisez une vue d’ensemble de .NET Core, qui est une implémentation à usage général, modulaire, multiplateforme et open source de l' .NET Standard.
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: 08d30d047c25b3b6d681d72b46b81a0cb21f8e0a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622755"
---
# <a name="net-core-and-open-source"></a>.NET Core et l’open source

Cet article fournit une brève présentation de .NET Core et montre comment trouver plus d’informations. Pour obtenir la liste complète de la documentation de .NET Core, consultez le [Guide .net Core](../../core/index.yml).

## <a name="what-is-net-core"></a>Qu'est-ce que le .NET Core ?  

.NET Core est une implémentation à usage général, modulaire, multiplateforme et open source de l' .NET Standard. Il contient un grand nombre des mêmes API que le .NET Framework (mais .NET Core est un ensemble plus petit) et comprend des composants d’exécution, d’infrastructure, de compilateur et d’outils qui prennent en charge une variété de systèmes d’exploitation et de cibles de puces. L’implémentation .NET Core a été essentiellement motivée par les charges de travail ASP.NET Core, mais aussi par la nécessité et l’envie d’avoir une implémentation plus moderne. Il peut être utilisé dans des scénarios d’appareil, de Cloud et d’intégration/IoT.  
  
Pour vous familiariser avec .NET Core, consultez le didacticiel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).  
  
Les principales caractéristiques de .NET Core sont les suivantes :
  
- **Multiplateforme.** .NET Core fournit des fonctionnalités clés permettant d’implémenter les composants d’application dont vous avez besoin et de réutiliser le code, quelle que soit votre plateforme cible. Il prend actuellement en charge trois principaux systèmes d’exploitation : Windows, Linux et macOS. Vous pouvez écrire des applications et des bibliothèques qui s’exécutent telles quelles sur les systèmes d’exploitation pris en charge. Pour afficher la liste des systèmes d’exploitation pris en charge, consultez la [feuille de route .NET Core](https://github.com/dotnet/core/blob/master/roadmap.md).
  
- **Open source.** .NET Core est l’un des nombreux projets placés sous l’intendance de [.NET Foundation](https://www.dotnetfoundation.org/) et disponible sur [GitHub](https://github.com/). En tant que projet open source, .NET Core encourage un processus de développement plus transparent et une communauté active et engagée.  
  
- **Déploiement flexible.** Il existe deux méthodes principales pour déployer votre application : le déploiement dépendant du framework ou le déploiement autonome. Avec le déploiement dépendant du framework, seules vos dépendances d’application et tierces sont installées. Votre application dépend de la présence d’une version de .NET Core à l’échelle du système. Avec le déploiement autonome, la version de .NET Core utilisée pour générer votre application est également déployée avec votre application et les dépendances tierces et peut s’exécuter côte à côte avec d’autres versions. Pour plus d’informations, consultez [déploiement d’applications .net Core](../../core/deploying/index.md).

- **Modulaire :** .NET Core est modulaire, car il est publié via NuGet dans des packages d’assembly plus petits. Au lieu d’un assembly volumineux qui contient la plupart des fonctionnalités principales, .NET Core est disponible sous la forme de packages plus petits et centrés sur les fonctionnalités. Cette modularité permet un modèle de développement plus agile pour nous et vous permet d’optimiser votre application pour inclure uniquement les packages NuGet dont vous avez besoin. Les avantages d’une petite zone de surface d’application offrent une sécurité accrue, une maintenance réduite, des performances améliorées et une réduction des coûts dans un modèle de paiement basé uniquement sur votre utilisation.  
  
## <a name="the-net-core-platform"></a>La plateforme .NET Core
  
La plateforme .NET Core est constituée de plusieurs composants, y compris les compilateurs managés, le runtime, les bibliothèques de classes de base et de nombreux modèles d’application, tels que ASP.NET Core. Vous pouvez en savoir plus sur les différents composants et vous familiariser en visitant les [GitHub](https://github.com/) suivantes :  
  
- [Page d’hébergement de .NET Core](https://github.com/dotnet/core)  
  
- [Runtime-plateforme .NET Core et Runtime](https://github.com/dotnet/runtime)  
  
- [CLI – Outils en ligne de commande .NET Core](https://github.com/dotnet/cli)  
  
- [Roslyn – .NET Compiler Platform](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a>Voir aussi

- [Didacticiel .NET-Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [Guide .NET Core](../../core/index.yml)
- [Documentation ASP.NET Core](/aspnet/core/)

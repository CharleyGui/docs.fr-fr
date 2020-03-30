---
title: Vue d’ensemble de .NET Core
description: Découvrez les caractéristiques et la composition de .NET Core, et comparez-le à d’autres implémentations .NET.
ms.date: 03/26/2020
ms.openlocfilehash: c9a63ddba14cf176be529e9520027c0610cfc087
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391167"
---
# <a name="net-core-overview"></a>Vue d’ensemble de .NET Core

.NET Core a les caractéristiques suivantes :

- **Plateforme transversale :** S’exécute sur windows, macOS, et [les systèmes d’exploitation](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Linux .
- **Open source:** Le cadre .NET Core est [open source](https://github.com/dotnet/core), en utilisant les licences MIT et Apache 2. .NET Core est un projet [.NET Foundation](https://dotnetfoundation.org/).
- **Moderne:** Il met en œuvre des paradigmes modernes comme la programmation asynchrone, les modèles sans copie à l’aide de structs, et la gouvernance des ressources pour les conteneurs.
- **Performance:**  Offre [des performances élevées](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-core-3-0/) avec des fonctionnalités comme le matériel [intrinsèque](https://devblogs.microsoft.com/dotnet/hardware-intrinsics-in-net-core/), compilation à [plusieurs niveaux](https://github.com/dotnet/coreclr/blob/master/Documentation/design-docs/tiered-compilation.md), et Span [\<T>](../standard/memory-and-spans/index.md).
- **Cohérent entre les environnements :** Exécute votre code avec le même comportement sur plusieurs systèmes d’exploitation et architectures, y compris x64, x86, et ARM.
- **Outils de ligne de commandement :**  Inclut des outils de ligne de commande faciles à utiliser qui peuvent être utilisés pour le développement local et pour l’intégration continue.
- **Déploiement flexible :** Vous pouvez inclure .NET Core dans votre application ou l’installer côte à côte (installations à l’échelle de l’utilisateur ou à l’échelle du système). Peut être utilisé avec des [conteneurs Docker](docker/introduction.md).

## <a name="languages"></a>Languages

Les langues [C,](../csharp/index.yml) [Visual Basic](../visual-basic/index.yml)et [F peuvent](../fsharp/index.yml) être utilisées pour écrire des applications et des bibliothèques pour .NET Core. Ces langues peuvent être utilisées dans votre éditeur de texte préféré ou environnement de développement intégré (IDE), y compris :

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Code de studio visuel](https://code.visualstudio.com/download)

L’intégration des éditeurs est assurée, en partie, par les contributeurs des projets [OmniSharp](https://www.omnisharp.net/) et [Ionide.](http://ionide.io)

## <a name="apis"></a>API

.NET Core expose des cadres pour la construction de tout type d’application :

* Applications Cloud avec [ASP.NET Core](/aspnet/core/)
* Applications mobiles avec [Xamarin](/xamarin)
* Applications IoT avec [System.Device.GPIO](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)
* Applications client Windows avec [formulaires WPF](../desktop-wpf/overview/index.md) et Windows
* [ML.NET](../machine-learning/index.yml) d’apprentissage automatique

De nombreuses API sont incluses qui répondent à des besoins communs :

- Types primitifs, tels que <xref:System.Boolean?displayProperty=nameWithType> et <xref:System.Int32?displayProperty=nameWithType>.
- Collections, comme <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> et <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Types d’utilitaire, comme <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> et <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Types de données, tels que <xref:System.Data.DataSet?displayProperty=nameWithType>, et <xref:System.Data.Entity.DbSet?displayProperty=nameWithType>.
- Types de haute performance, tels que <xref:System.Span%601?displayProperty=nameWithType>, <xref:System.Numerics.Vector?displayProperty=nameWithType>, et [pipelines](../standard/io/pipelines.md).

.NET Core assure la compatibilité avec les API .NET Framework et Mono en implémentant la spécification [.NET Standard](../standard/net-standard.md).

## <a name="composition"></a>Composition

.NET Core est constitué des composants suivants :

- Le [runtime .NET Core](https://github.com/dotnet/runtime/tree/master/src/coreclr), qui fournit un système de type, le chargement d’assemblage, un éboueur, interop natif, et d’autres services de base. [.NET Les bibliothèques-cadres de base](https://github.com/dotnet/runtime/tree/master/src/libraries) fournissent des types de données primitifs, des types de composition d’applications et des services publics fondamentaux.
- Le [ASP.NET Core runtime](https://github.com/dotnet/aspnetcore), qui fournit un cadre pour la construction d’applications modernes, basées sur le cloud, connectées à Internet, telles que les applications Web, les applications IoT et les backends mobiles.
- Le [.NET Core SDK](https://github.com/dotnet/sdk) et les compilateurs de langue ([Roslyn](https://github.com/dotnet/roslyn) et [F )](https://github.com/microsoft/visualfsharp)qui permettent l’expérience développeur .NET Core.
- La [commande dotnet](./tools/dotnet.md), qui est utilisé pour lancer des applications .NET Core et des commandes CLI. Il sélectionne et héberge l’heure d’exécution, fournit une stratégie de chargement d’assemblage et lance des applications et des outils.

### <a name="open-source"></a>Open source

[.NET Core](about.md) est une plate-forme de développement [open-source,](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)polyvalente. Vous pouvez créer des applications .NET Core pour windows, macOS et Linux pour les processeurs x64, x86, ARM32 et ARM64. Cadres et API sont fournis pour [le cloud](/aspnet/core/), [IoT](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [l’interface utilisateur client](../desktop-wpf/overview/index.md), et [l’apprentissage automatique](../machine-learning/index.yml).

## <a name="support"></a>Support

.NET Core est [pris en charge par Microsoft](https://dotnet.microsoft.com/platform/support/policy) sur Windows, macOS et Linux. Il est mis à jour pour la sécurité et la qualité régulièrement (le deuxième mardi de chaque mois).

.NET Core distributions binaires de Microsoft sont construits et testés sur des serveurs Microsoft-maintenus dans Azure et suivre Microsoft ingénierie et les pratiques de sécurité.

[Red Hat prend en charge .NET Core](http://redhatloves.net/) sur Red Hat Enterprise Linux (RHEL). Red Hat génère .NET Core à partir de la source et le rend disponible dans les [collections logicielles Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat et Microsoft collaborent pour s’assurer que .NET Core fonctionne correctement sur RHEL.

[Tizen prend en charge .NET Core](https://developer.tizen.org/development/training/.net-application) sur les plates-formes Tizen.

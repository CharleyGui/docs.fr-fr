---
title: Vue d’ensemble de .NET Core
description: Découvrez les caractéristiques et la composition de .NET Core et comparez-les à d’autres implémentations de .NET.
ms.date: 03/26/2020
ms.openlocfilehash: e99939cf85cc441fd473e4d033e22b1a5d053638
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539006"
---
# <a name="net-core-overview"></a>Vue d’ensemble de .NET Core

> [!div class="button"]
> [Télécharger .NET Core](https://dotnet.microsoft.com/download)

.NET Core a les caractéristiques suivantes :

- **Multiplateforme :** S’exécute sur les [systèmes d’exploitation](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, MacOS et Linux.
- **Open Source :** L’infrastructure .NET Core est [Open source](https://github.com/dotnet/core)et utilise des licences mit et Apache 2. .NET Core est un projet [.NET Foundation](https://dotnetfoundation.org/).
- **Moderne :** Il implémente des paradigmes modernes tels que la programmation asynchrone, des modèles sans copie utilisant des structs et la gouvernance des ressources pour les conteneurs.
- **Performances :**  Offre des [performances élevées](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-core-3-0/) avec des fonctionnalités telles que les [intrinsèques matérielles](https://devblogs.microsoft.com/dotnet/hardware-intrinsics-in-net-core/), la [compilation à plusieurs niveaux](https://github.com/dotnet/coreclr/blob/master/Documentation/design-docs/tiered-compilation.md)et l' [étendue \<T> ](../standard/memory-and-spans/index.md).
- **Cohérence entre les environnements :** Exécute votre code avec le même comportement sur plusieurs systèmes d’exploitation et architectures, y compris x64, x86 et ARM.
- **Outils en ligne de commande :**  Comprend des outils en ligne de commande faciles à utiliser qui peuvent être utilisés pour le développement local et pour une intégration continue.
- **Déploiement flexible :** Vous pouvez inclure .NET Core dans votre application ou l’installer côte à côte (installations à l’utilisateur ou à l’ensemble du système). Peut être utilisé avec des [conteneurs Docker](docker/introduction.md).

## <a name="languages"></a>Langages

Les langages [C#](../csharp/index.yml), [Visual Basic](../visual-basic/index.yml)et [F #](../fsharp/index.yml) peuvent être utilisés pour écrire des applications et des bibliothèques pour .net core. Ces langues peuvent être utilisées dans votre éditeur de texte ou votre environnement de développement intégré (IDE), notamment :

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://code.visualstudio.com/download)

L’intégration de l’éditeur est fournie, en partie, par les contributeurs des projets [OmniSharp](https://www.omnisharp.net/) et [Ionide](https://ionide.io) .

## <a name="apis"></a>API

.NET Core expose des frameworks pour créer tout type d’application :

* Applications Cloud avec [ASP.net Core](/aspnet/core/)
* Applications mobiles avec [Xamarin](/xamarin)
* Applications IoT avec [System. Device. GPIO](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)
* Applications clientes Windows avec [WPF](../desktop-wpf/overview/index.md) et Windows Forms
* Machine learning [ml.net](../machine-learning/index.yml)

De nombreuses API sont incluses qui répondent aux besoins courants :

- Types primitifs, tels que <xref:System.Boolean?displayProperty=nameWithType> et <xref:System.Int32?displayProperty=nameWithType> .
- Collections, comme <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> et <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Types d’utilitaire, comme <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> et <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Types de données, tels que <xref:System.Data.DataSet?displayProperty=nameWithType> et <xref:System.Data.Entity.DbSet?displayProperty=nameWithType> .
- Types hautes performances, tels que les <xref:System.Span%601?displayProperty=nameWithType> <xref:System.Numerics.Vector?displayProperty=nameWithType> [pipelines](../standard/io/pipelines.md), et.

.NET Core assure la compatibilité avec les API .NET Framework et Mono en implémentant la spécification [.NET Standard](../standard/net-standard.md).

## <a name="composition"></a>Composition

.NET Core est constitué des composants suivants :

- Le [Runtime .net Core](https://github.com/dotnet/runtime/tree/master/src/coreclr), qui fournit un système de type, un chargement d’assembly, un récupérateur de mémoire, une interopérabilité native et d’autres services de base. Les [bibliothèques .net Core Framework](https://github.com/dotnet/runtime/tree/master/src/libraries) fournissent des types de données primitifs, des types de composition d’applications et des utilitaires fondamentaux.
- Le [ASP.net Core Runtime](https://github.com/dotnet/aspnetcore), qui fournit une infrastructure pour la création d’applications modernes, basées sur le Cloud et connectées à Internet, telles que les applications Web, les applications IOT et les backends mobiles.
- Le [Kit SDK .net Core](https://github.com/dotnet/sdk) et les compilateurs de langage ([Roslyn](https://github.com/dotnet/roslyn) et [F #](https://github.com/microsoft/visualfsharp)) qui permettent l’expérience de développement .net core.
- La [commande dotnet](./tools/dotnet.md), qui sert à lancer les applications .net Core et les commandes CLI. Il sélectionne et héberge le runtime, fournit une stratégie de chargement d’assembly et lance des applications et des outils.

### <a name="open-source"></a>Open source

[.Net Core](about.md) est une plateforme de développement [Open source à](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)usage général. Vous pouvez créer des applications .NET Core pour Windows, macOS et Linux pour les processeurs x64, x86, ARM32 et ARM64. Les frameworks et les API sont fournis pour le [Cloud](/aspnet/core/), l' [IOT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [l’interface utilisateur du client](../desktop-wpf/overview/index.md)et les [machine learning](../machine-learning/index.yml).

## <a name="support"></a>Support

.NET Core est [pris en charge par Microsoft](https://dotnet.microsoft.com/platform/support/policy) sur Windows, MacOS et Linux. Il est mis à jour pour la sécurité et la qualité régulièrement (le deuxième mardi de chaque mois).

Les distributions binaires .NET Core de Microsoft sont générées et testées sur des serveurs gérés par Microsoft dans Azure et suivent les pratiques d’ingénierie et de sécurité de Microsoft.

[Red Hat prend en charge .NET Core](https://developers.redhat.com/topics/dotnet/) sur Red Hat Enterprise Linux (RHEL). Red Hat génère .NET Core à partir de la source et le rend disponible dans les [collections logicielles Red Hat](https://developers.redhat.com/products/softwarecollections/overview/). Red Hat et Microsoft collaborent pour s’assurer que .NET Core fonctionne correctement sur RHEL.

[Tizen prend en charge .net Core](https://developer.tizen.org/development/training/.net-application) sur les plateformes Tizen.

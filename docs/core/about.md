---
title: À propos de .NET Core
description: Découvrez plus en détail .NET Core.
ms.date: 09/17/2019
ms.openlocfilehash: e5460fd1d968a49478a1bdc5f18962de2c7cbbe0
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920957"
---
# <a name="about-net-core"></a>À propos de .NET Core

.NET Core a les caractéristiques suivantes :

- **Multiplateforme :** S’exécute sur les [systèmes d’exploitation](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Windows, MacOS et Linux.
- **Cohérent entre architectures :** Exécute votre code avec le même comportement sur plusieurs architectures, notamment x64, x86 et ARM.
- **Outils de ligne de commande :** Intègre des outils de ligne de commande faciles qui peuvent être utilisés pour le développement local et dans des scénarios d’intégration continue.
- **Déploiement flexible :** Peut être inclus dans votre application ou installé côte à côte (installations à l’ensemble de l’utilisateur ou de l’ensemble du système). Peut être utilisé avec des [conteneurs Docker](docker/introduction.md).
- **Compatible :** .net Core est compatible avec .NET Framework, Xamarin et mono, via [.NET standard](../standard/net-standard.md).
- **Open Source :** la plateforme .NET Core est open source et utilise des licences MIT et Apache 2. .NET Core est un projet [.NET Foundation](https://dotnetfoundation.org/).
- **Pris en charge par Microsoft :** Le .NET Core est pris en charge par Microsoft, via le [Support .NET Core](https://dotnet.microsoft.com/platform/support/policy).

## <a name="languages"></a>Langages

Vous pouvez utiliser les langages C#, Visual Basic et F# pour écrire des applications et des bibliothèques pour .NET Core. Ces langues peuvent être utilisées dans votre éditeur de texte ou votre environnement de développement intégré (IDE), notamment :

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)
- Texte sous-vert
- Vim

Cette intégration est fournie, en partie, par les contributeurs des projets [OmniSharp](https://www.omnisharp.net/) et [Ionide](http://ionide.io) .

## <a name="apis"></a>API

.NET Core expose des API pour de nombreux scénarios, en voici quelques-uns :

- Types primitifs, tels que <xref:System.Boolean?displayProperty=nameWithType> et <xref:System.Int32?displayProperty=nameWithType>.
- Collections, comme <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> et <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Types d’utilitaire, comme <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> et <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Types de données, comme <xref:System.Data.DataSet?displayProperty=nameWithType> et [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/).
- Types haute performance, tels que les <xref:System.Numerics.Vector?displayProperty=nameWithType> et les [pipelines](../standard/io/pipelines.md).

.NET Core assure la compatibilité avec les API .NET Framework et Mono en implémentant la spécification [.NET Standard](../standard/net-standard.md).

## <a name="frameworks"></a>Infrastructures

Plusieurs frameworks ont été construits à partir de .NET Core :

- [ASP.NET Core](/aspnet/core/)
- [Plateforme Windows universelle (UWP) Windows 10](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>composition

.NET Core est constitué des composants suivants :

- Le [Runtime .net Core](https://github.com/dotnet/runtime/tree/master/src/coreclr), qui fournit un système de type, un chargement d’assembly, un récupérateur de mémoire, une interopérabilité native et d’autres services de base. Les [bibliothèques .net Core Framework](https://github.com/dotnet/runtime/tree/master/src/libraries) fournissent des types de données primitifs, des types de composition d’applications et des utilitaires fondamentaux.
- Le [Runtime d’ASP.net Core](https://github.com/dotnet/aspnetcore), qui fournit une infrastructure pour la création d’applications modernes connectées à Internet Cloud, telles que les applications Web, les applications IOT et les backends mobiles.
- Le [Kit SDK .net Core](https://github.com/dotnet/sdk) et les compilateurs de langage[Roslyn](https://github.com/dotnet/roslyn) (Roslyn [F#](https://github.com/microsoft/visualfsharp)et) qui permettent l’expérience de développement .net core.
- La [commande dotnet](./tools/dotnet.md), qui sert à lancer les applications .net Core et les commandes CLI. Il sélectionne le runtime et héberge le runtime, fournit une stratégie de chargement d’assembly et lance des applications et des outils.

Ces composants sont distribués de la façon suivante :

- [Runtime .NET Core](https://dotnet.microsoft.com/download) : inclut le runtime .NET Core et des bibliothèques de framework.
- [Runtime ASP.NET Core](https://dotnet.microsoft.com/download) : inclut le runtime ASP.NET Core et .NET Core, et des bibliothèques de framework.
- [Kit SDK .net Core](https://dotnet.microsoft.com/download) --comprend le CLI .net Core, le runtime ASP.net Core et le runtime et le Framework .net core.

### <a name="open-source"></a>Ouvrir la source

[.NET Core](https://github.com/dotnet/core) est open source ([licence MIT](https://github.com/dotnet/core/blob/master/LICENSE.TXT)) et a été introduit dans [.NET Foundation](https://dotnetfoundation.org) par Microsoft en 2014. Il s’agit désormais de l’un des projets .NET Foundation les plus actifs. Il peut être utilisé par des individus et des sociétés, y compris à des fins personnelles, universitaires ou commerciales. Plusieurs entreprises utilisent .NET Core dans le cadre d’applications, d’outils, de nouvelles plateformes et de services d’hébergement. Certaines de ces sociétés contribuent de façon significative à .NET Core sur GitHub et fournissent des conseils sur l’orientation des produits dans le cadre du groupe de travail appelé le [.NET Foundation Technical Steering Group](https://dotnetfoundation.org/blog/tsg-welcome).

### <a name="designed-for-adaptability"></a>Conçu pour l’adaptabilité

.NET Core a été créé comme un produit très similaire mais unique par rapport aux autres produits .NET. Il a été conçu pour offrir une adaptabilité étendue aux nouvelles plates-formes et charges de travail, et il dispose de plusieurs ports de système d’exploitation et processeur disponibles (et peut être porté à plusieurs autres).

Le produit est divisé en plusieurs composants, ce qui permet d’adapter les différentes parties à de nouvelles plateformes, à différents moments. Le runtime et les bibliothèques de base spécifiques à la plateforme doivent être portés individuellement. Les bibliothèques indépendantes de la plateforme doivent fonctionner en l’état sur toutes les plateformes, de par leur construction. Il existe un décalage entre le projet et la réduction des implémentations spécifiques à la plateforme pour améliorer l’efficacité des C# développeurs, en préférant le code indépendant de la plateforme chaque fois qu’un algorithme ou une API peut être implémentée en totalité ou en partie de cette façon.

Il est fréquent que des personnes s’interrogent sur la façon dont .NET Core est implémenté afin de prendre en charge plusieurs systèmes d’exploitation. Elles demandent généralement s’il existe des implémentations distinctes ou si la [compilation conditionnelle](https://en.wikipedia.org/wiki/Conditional_compilation) est utilisée. La réponse est les deux à la fois, avec une forte préférence pour la compilation conditionnelle.

Vous pouvez voir dans le graphique suivant que la grande majorité des [bibliothèques .net Core](https://github.com/dotnet/runtime/tree/master/src/libraries) est un code indépendant de la plateforme qui est partagé entre toutes les plateformes. Le code indépendant de la plateforme peut être implémenté en tant qu’assembly portable unique et utilisé sur toutes les plateformes.

![CoreFX : lignes de code par plateforme](../images/corefx-platforms-loc.png)

Les implémentations Windows et Unix sont de taille équivalente. Windows a une implémentation plus importante, car les bibliothèques .NET Core implémentent des fonctionnalités propres à Windows, telles que [Microsoft. Win32. Registry](https://github.com/dotnet/runtime/tree/master/src/libraries/Microsoft.Win32.Registry) , mais n’implémentent pas encore de nombreux concepts propres à UNIX. Vous verrez également que la majorité des implémentations de Linux et macOS sont partagées dans une implémentation UNIX, tandis que les implémentations spécifiques à Linux et à macOS sont à peu près similaires.

Dans .NET Core, il existe une combinaison de bibliothèques spécifiques à la plateforme et de plateformes indépendantes de la plateforme. Cette caractéristique peut être illustrée à travers les exemples suivants :

- [CoreCLR](https://github.com/dotnet/runtime/tree/master/src/coreclr) est spécifique à la plateforme. Il s’appuie sur des sous-systèmes de système d’exploitation, comme le gestionnaire de mémoire et le planificateur de threads.
- [System.IO](https://github.com/dotnet/runtime/tree/master/src/libraries/System.IO) et [System.Security.Cryptography.Algorithms](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Security.Cryptography.Algorithms) sont propres à la plateforme, puisque les API de stockage et de chiffrement sont très différentes sur chaque système d’exploitation.
- [System.Collections](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Collections) et [System.Linq](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Linq) sont indépendants de la plateforme, vu qu’ils créent et exploitent des structures de données.

## <a name="comparisons-to-other-net-implementations"></a>Comparaison avec les autres implémentations .NET

Il est probablement plus facile de comprendre la taille et la forme de .NET Core en le comparant aux implémentations .NET existantes.

### <a name="comparison-with-net-framework"></a>Comparaison avec le .NET Framework

.NET a été annoncé pour la première fois par Microsoft en 2000 et a depuis évolué. Le .NET Framework a été la principale implémentation .NET à avoir été conçue par Microsoft durant cette période de presque 20 ans.

Les principales différences entre .NET Core et le .NET Framework sont les suivantes :

- Les **modèles d’application** --. net Core ne prennent pas en charge tous les modèles d’application .NET Framework. En particulier, il ne prend pas en charge ASP.NET Web Forms et ASP.NET MVC, mais il prend en charge ASP.NET Core MVC. À compter de .NET Core 3,0, .NET Core prend également en charge WPF et Windows Forms sur Windows uniquement.
- **API** : .NET Core contient une grande partie de la bibliothèque de classes de base de .NET Framework, avec une factorisation différente (les noms d’assembly sont différents, les membres exposés sur les types diffèrent selon les cas). Dans certains cas, ces différences requièrent des modifications de la source du port pour .NET Core. Pour plus d’informations, consultez [l’analyseur de portabilité .net](../standard/analyzers/portability-analyzer.md). .NET Core implémente la spécification d’API [.NET Standard](../standard/net-standard.md).
- **Sous-systèmes** : .NET Core implémente un sous-ensemble des sous-systèmes du .NET Framework, avec l’objectif d’une implémentation et d’un modèle de programmation plus simples. Par exemple, la sécurité d’accès du code (CAS) n’est pas prise en charge, tandis que la réflexion est prise en charge.
- **Plateformes** : le .NET Framework prend en charge Windows et Windows Server, tandis que .NET Core prend aussi en charge macOS et Linux.
- **Open Source** : .NET Core est open source, alors que seul un [sous-ensemble en lecture seule du .NET Framework](https://github.com/microsoft/referencesource) l’est.

Bien que .NET Core soit unique et présente des différences significatives au .NET Framework et à d’autres implémentations .NET, il est simple de partager du code entre ces implémentations, à l’aide de techniques de partage source ou binaire.

Étant donné que .NET Core prend en charge l’installation côte à côte et que son runtime est complètement indépendant de .NET Framework, il peut être installé sur des machines avec .NET Framework installé sans aucun problème.

### <a name="comparison-with-mono"></a>Comparaison avec Mono

[Mono](https://www.mono-project.com/) est l’implémentation multiplateforme d’origine de .net. Il a commencé comme une alternative [Open source](https://github.com/mono/mono) à .NET Framework et a migré vers le ciblage des appareils mobiles, car les appareils iOS et Android sont devenus populaires. Elle peut être considérée comme un clone communautaire du .NET Framework. L’équipe de projet mono s’est appuyée sur les [normes .net](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) ouvertes (notamment ECMA 335) publiées par Microsoft pour fournir une implémentation compatible.

Les principales différences entre .NET Core et Mono sont les suivantes :

- **Modèles d’application** : mono prend en charge un sous-ensemble des modèles d’application .NET Framework (par exemple, Windows Forms) et d’autres pour le développement mobile (par exemple, [Xamarin. iOS](https://www.xamarin.com/platform)) via le produit Xamarin. .NET Core ne prend pas en charge Xamarin.
- **API** : Mono prend en charge un [sous-ensemble étendu](http://docs.go-mono.com/?link=root%3a%2fclasslib) des API du .NET Framework, en utilisant les mêmes noms d’assembly et la même factorisation.
- **Plateformes** : Mono prend en charge un grand nombre de plateformes et de processeurs.
- **Open Source** : Mono et .NET Core utilisent tous deux une licence MIT et sont des projets .NET Foundation.
- **Priorité** : Les plateformes mobiles sont la principale priorité de Mono depuis quelques années, alors que .NET Core se concentre sur les charges de travail cloud et de bureau.

## <a name="the-future"></a>Le futur

Il a été annoncé que .NET 5 sera la prochaine version de .NET Core et représente une unification de la plate-forme. Le projet a pour but d’améliorer .NET en quelques points clés :

- Produisez une infrastructure et un Runtime .NET uniques qui peuvent être utilisés partout et qui ont des comportements d’exécution et des expériences de développement uniformes.
- Développez les fonctionnalités de .NET en utilisant le meilleur de .NET Core, .NET Framework, Xamarin et mono.
- Générez ce produit en dehors d’une base de code unique que les développeurs (Microsoft et la Communauté) peuvent utiliser et développent ensemble, ce qui améliore tous les scénarios.

Pour plus d’informations sur ce qui est planifié pour .NET 5, consultez [Présentation de .net 5](https://devblogs.microsoft.com/dotnet/introducing-net-5/).

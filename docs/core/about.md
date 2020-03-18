---
title: À propos de .NET Core
description: Découvrez plus en détail .NET Core.
ms.date: 09/17/2019
ms.openlocfilehash: 89740b67b294650f78cf36361548c2fe24ac80cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147358"
---
# <a name="about-net-core"></a>À propos de .NET Core

.NET Core a les caractéristiques suivantes :

- **Plateforme croisée :** S’exécute sur windows, macOS, et [les systèmes d’exploitation](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)Linux .
- **Cohérent entre architectures :** Exécute votre code avec le même comportement sur plusieurs architectures, notamment x64, x86 et ARM.
- **Outils de ligne de commande :** Intègre des outils de ligne de commande faciles qui peuvent être utilisés pour le développement local et dans des scénarios d’intégration continue.
- **Déploiement flexible :** Peut être inclus dans votre application ou installé côte à côte (installations à l’échelle de l’utilisateur ou à l’échelle du système). Peut être utilisé avec des [conteneurs Docker](docker/introduction.md).
- **Compatible:** .NET Core est compatible avec .NET Framework, Xamarin, et Mono, via [.NET Standard](../standard/net-standard.md).
- **Open Source :** la plateforme .NET Core est open source et utilise des licences MIT et Apache 2. .NET Core est un projet [.NET Foundation](https://dotnetfoundation.org/).
- **Pris en charge par Microsoft :** Le .NET Core est pris en charge par Microsoft, via le [Support .NET Core](https://dotnet.microsoft.com/platform/support/policy).

## <a name="languages"></a>Languages

Vous pouvez utiliser les langages C#, Visual Basic et F# pour écrire des applications et des bibliothèques pour .NET Core. Ces langues peuvent être utilisées dans votre éditeur de texte préféré ou environnement de développement intégré (IDE), y compris :

- [Studio visuel](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Code de studio visuel](https://code.visualstudio.com/download)
- Sublime Text
- Vim

Cette intégration est assurée, en partie, par les contributeurs des projets [OmniSharp](https://www.omnisharp.net/) et [Ionide.](http://ionide.io)

## <a name="apis"></a>API

.NET Core expose des API pour de nombreux scénarios, en voici quelques-uns :

- Types primitifs, tels que <xref:System.Boolean?displayProperty=nameWithType> et <xref:System.Int32?displayProperty=nameWithType>.
- Collections, comme <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> et <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Types d’utilitaire, comme <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> et <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Types de données, comme <xref:System.Data.DataSet?displayProperty=nameWithType> et [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/).
- Types de haute performance, tels que <xref:System.Numerics.Vector?displayProperty=nameWithType> et [pipelines](../standard/io/pipelines.md).

.NET Core assure la compatibilité avec les API .NET Framework et Mono en implémentant la spécification [.NET Standard](../standard/net-standard.md).

## <a name="frameworks"></a>Frameworks

Plusieurs frameworks ont été construits à partir de .NET Core :

- [ASP.NET Core](/aspnet/core/)
- [Plateforme Windows universelle (UWP) Windows 10](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Composition

.NET Core est constitué des composants suivants :

- Le [runtime .NET Core](https://github.com/dotnet/runtime/tree/master/src/coreclr), qui fournit un système de type, le chargement d’assemblage, un éboueur, interop natif, et d’autres services de base. [.NET Les bibliothèques-cadres de base](https://github.com/dotnet/runtime/tree/master/src/libraries) fournissent des types de données primitifs, des types de composition d’applications et des services publics fondamentaux.
- Le [ASP.NET Core runtime](https://github.com/dotnet/aspnetcore), qui fournit un cadre pour la construction d’applications modernes connectées à Internet basées sur le cloud, telles que les applications Web, les applications IoT et les backends mobiles.
- Le [.NET Core SDK](https://github.com/dotnet/sdk) et les compilateurs de langue ([Roslyn](https://github.com/dotnet/roslyn) et [F )](https://github.com/microsoft/visualfsharp)qui permettent l’expérience développeur .NET Core.
- La [commande dotnet](./tools/dotnet.md), qui est utilisé pour lancer des applications .NET Core et des commandes CLI. Il sélectionne l’heure d’exécution et héberge l’heure d’exécution, fournit une stratégie de chargement d’assemblage et lance des applications et des outils.

Ces composants sont distribués de la façon suivante :

- [Runtime .NET Core](https://dotnet.microsoft.com/download) : inclut le runtime .NET Core et des bibliothèques de framework.
- [Runtime ASP.NET Core](https://dotnet.microsoft.com/download) : inclut le runtime ASP.NET Core et .NET Core, et des bibliothèques de framework.
- [.NET Core SDK](https://dotnet.microsoft.com/download) -- comprend le .NET Core CLI, ASP.NET Core runtime, et .NET Core runtime et cadre.

### <a name="open-source"></a>Open source

[.NET Core](https://github.com/dotnet/core) est open source ([licence MIT](https://github.com/dotnet/core/blob/master/LICENSE.TXT)) et a été introduit dans [.NET Foundation](https://dotnetfoundation.org) par Microsoft en 2014. C’est maintenant l’un des projets les plus actifs de la Fondation NET. Il peut être utilisé par des particuliers et des entreprises, y compris à des fins personnelles, académiques ou commerciales. Plusieurs entreprises utilisent .NET Core dans le cadre d’applications, d’outils, de nouvelles plates-formes et de services d’hébergement. Certaines de ces sociétés contribuent de façon significative à .NET Core sur GitHub et fournissent des conseils sur l’orientation des produits dans le cadre du groupe de travail appelé le [.NET Foundation Technical Steering Group](https://dotnetfoundation.org/blog/tsg-welcome).

### <a name="designed-for-adaptability"></a>Conçu pour l’adaptabilité

.NET Core a été construit comme un produit similaire mais unique par rapport à d’autres produits .NET. Il a été conçu pour permettre une large adaptabilité aux nouvelles plates-formes et charges de travail et il dispose de plusieurs ports OS et CPU disponibles (et il peut être porté à beaucoup plus).

Le produit est divisé en plusieurs composants, ce qui permet d’adapter les différentes parties à de nouvelles plateformes, à différents moments. Le runtime et les bibliothèques de base spécifiques à la plateforme doivent être portés individuellement. Les bibliothèques indépendantes de la plateforme doivent fonctionner en l’état sur toutes les plateformes, de par leur construction. Il y a un biais de projet vers la réduction des implémentations spécifiques à la plate-forme afin d’accroître l’efficacité des développeurs, préférant le code Cmd neutre sur la plate-forme chaque fois qu’un algorithme ou un API peut être implémenté de cette façon.

Il est fréquent que des personnes s’interrogent sur la façon dont .NET Core est implémenté afin de prendre en charge plusieurs systèmes d’exploitation. Elles demandent généralement s’il existe des implémentations distinctes ou si la [compilation conditionnelle](https://en.wikipedia.org/wiki/Conditional_compilation) est utilisée. La réponse est les deux à la fois, avec une forte préférence pour la compilation conditionnelle.

Vous pouvez voir dans le tableau suivant que la grande majorité des [bibliothèques .NET Core](https://github.com/dotnet/runtime/tree/master/src/libraries) est un code neutre sur la plate-forme qui est partagé sur toutes les plates-formes. Le code indépendant de la plateforme peut être implémenté en tant qu’assembly portable unique et utilisé sur toutes les plateformes.

![CoreFX : lignes de code par plateforme](../images/corefx-platforms-loc.png)

Les implémentations Windows et Unix sont de taille équivalente. Windows a une implémentation plus grande depuis .NET Core bibliothèques implémente certaines fonctionnalités Windows-seulement, tels que [Microsoft.Win32.Registry,](https://github.com/dotnet/runtime/tree/master/src/libraries/Microsoft.Win32.Registry) mais ne met pas encore en œuvre de nombreux concepts Unix-seulement. Vous verrez également que la majorité des implémentations Linux et macOS sont partagées sur une implémentation Unix, tandis que les implémentations spécifiques à Linux et macOS sont à peu près similaires.

Il ya un mélange de bibliothèques spécifiques à la plate-forme et neutre plate-forme dans .NET Core. Cette caractéristique peut être illustrée à travers les exemples suivants :

- [CoreCLR](https://github.com/dotnet/runtime/tree/master/src/coreclr) est spécifique à la plateforme. Il s’appuie sur des sous-systèmes de système d’exploitation, comme le gestionnaire de mémoire et le planificateur de threads.
- [System.IO](https://github.com/dotnet/runtime/tree/master/src/libraries/System.IO) et [System.Security.Cryptography.Algorithms](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Security.Cryptography.Algorithms) sont propres à la plateforme, puisque les API de stockage et de chiffrement sont très différentes sur chaque système d’exploitation.
- [System.Collections](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Collections) et [System.Linq](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Linq) sont indépendants de la plateforme, vu qu’ils créent et exploitent des structures de données.

## <a name="comparisons-to-other-net-implementations"></a>Comparaison avec les autres implémentations .NET

Il est probablement plus facile de comprendre la taille et la forme de .NET Core en le comparant à des implémentations .NET existantes.

### <a name="comparison-with-net-framework"></a>Comparaison avec le .NET Framework

.NET a été annoncé pour la première fois par Microsoft en 2000 et a depuis évolué. Le .NET Framework a été la principale implémentation .NET à avoir été conçue par Microsoft durant cette période de presque 20 ans.

Les principales différences entre .NET Core et le .NET Framework sont les suivantes :

- **App-modèles** -- .NET Core ne prend pas en charge tous les modèles d’applications .NET Framework. En particulier, il ne prend pas en charge ASP.NET Web Forms et ASP.NET MVC, mais il prend en charge ASP.NET Core MVC. Et à partir de .NET Core 3.0, .NET Core prend également en charge WPF et Windows Forms sur Windows seulement.
- **API** : .NET Core contient une grande partie de la bibliothèque de classes de base de .NET Framework, avec une factorisation différente (les noms d’assembly sont différents, les membres exposés sur les types diffèrent selon les cas). Dans certains cas, ces différences nécessitent des modifications de la source portuaire à .NET Core. Pour plus d’informations, voir [The .NET Portability Analyzer](../standard/analyzers/portability-analyzer.md). .NET Core implémente la spécification d’API [.NET Standard](../standard/net-standard.md).
- **Sous-systèmes** : .NET Core implémente un sous-ensemble des sous-systèmes du .NET Framework, avec l’objectif d’une implémentation et d’un modèle de programmation plus simples. Par exemple, la sécurité d’accès au code (CAS) n’est pas prise en charge, tandis que la réflexion est soutenue.
- **Plateformes** : le .NET Framework prend en charge Windows et Windows Server, tandis que .NET Core prend aussi en charge macOS et Linux.
- **Open Source** : .NET Core est open source, alors que seul un [sous-ensemble en lecture seule du .NET Framework](https://github.com/microsoft/referencesource) l’est.

Bien que .NET Core est unique et a des différences significatives avec le cadre .NET et d’autres implémentations .NET, il est simple de partager du code entre ces implémentations, en utilisant des techniques de partage source ou binaire.

Étant donné que .NET Core prend en charge l’installation côte à côte et que son runtime est complètement indépendant de .NET Framework, il peut être installé sur des machines avec .NET Framework installé sans aucun problème.

### <a name="comparison-with-mono"></a>Comparaison avec Mono

[Mono](https://www.mono-project.com/) est la mise en œuvre multiplateforme originale de .NET. Il a commencé comme une alternative [open-source](https://github.com/mono/mono) à .NET Framework et la transition vers le ciblage des appareils mobiles que les appareils iOS et Android est devenu populaire. Elle peut être considérée comme un clone communautaire du .NET Framework. L’équipe du projet Mono s’est appuyée sur les [normes ouvertes .NET](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) (notamment ECMA 335) publiées par Microsoft pour fournir une implémentation compatible.

Les principales différences entre .NET Core et Mono sont les suivantes :

- **Modèles d’applications** -- Mono prend en charge un sous-ensemble des modèles d’applications .NET Framework (par exemple, Windows Forms) et quelques modèles supplémentaires pour le développement mobile (par exemple, [Xamarin.iOS](https://www.xamarin.com/platform)) à travers le produit Xamarin. .NET Core ne prend pas en charge Xamarin.
- **API** : Mono prend en charge un [sous-ensemble étendu](http://docs.go-mono.com/?link=root%3a%2fclasslib) des API du .NET Framework, en utilisant les mêmes noms d’assembly et la même factorisation.
- **Plateformes** : Mono prend en charge un grand nombre de plateformes et de processeurs.
- **Open Source** : Mono et .NET Core utilisent tous deux une licence MIT et sont des projets .NET Foundation.
- **Priorité** : Les plateformes mobiles sont la principale priorité de Mono depuis quelques années, alors que .NET Core se concentre sur les charges de travail cloud et de bureau.

## <a name="the-future"></a>L’avenir

Il a été annoncé que .NET 5 sera la prochaine version de .NET Core et représente une unification de la plate-forme. Le projet vise à améliorer .NET de quelques façons clés:

- Produisez un temps d’exécution unique .NET et un cadre qui peut être utilisé partout et qui a des comportements de temps d’exécution uniformes et des expériences de développeur.
- Élargir les capacités de .NET en prenant le meilleur de .NET Core, .NET Framework, Xamarin, et Mono.
- Construisez ce produit à partir d’une base de code unique sur laquelle les développeurs (Microsoft et la communauté) peuvent travailler et développer ensemble, ce qui améliore tous les scénarios.

Pour plus de détails sur ce qui est prévu pour .NET 5, voir [Introducing .NET 5](https://devblogs.microsoft.com/dotnet/introducing-net-5/).

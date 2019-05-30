---
title: À propos de .NET Core
description: Découvrez plus en détail .NET Core.
author: richlander
ms.date: 08/01/2018
ms.openlocfilehash: fb6088bcadcdc9c28699446df035b899485c406d
ms.sourcegitcommit: 11deacc8ec9f229ab8ee3cd537515d4c2826515f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66003757"
---
# <a name="about-net-core"></a>À propos de .NET Core

.NET Core a les caractéristiques suivantes :

- **Multiplateforme :** s’exécute sur les [systèmes d’exploitation](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md) Windows, macOS et Linux.
- **Cohérent entre architectures :** exécute votre code avec le même comportement sur plusieurs architectures, notamment x64, x86 et ARM.
- **Outils de ligne de commande :**  intègre des outils de ligne de commande faciles qui peuvent être utilisés pour le développement local et dans des scénarios d’intégration continue.
- **Souplesse de déploiement :** Peut être inclus dans votre application ou installé côte à côte (installations à l’échelle de l’utilisateur ou à l’échelle du système). Peut être utilisé avec des [conteneurs Docker](docker/index.md).
- **Compatibilité :** .NET Core est compatible avec le .NET Framework, Xamarin et Mono via [.NET Standard](../standard/net-standard.md).
- **Open Source :** la plateforme .NET Core est open source et utilise des licences MIT et Apache 2. .NET Core est un projet [.NET Foundation](https://dotnetfoundation.org/).
- **Pris en charge par Microsoft :** Le .NET Core est pris en charge par Microsoft, via le [Support .NET Core](https://www.microsoft.com/net/core/support/).

## <a name="languages"></a>Langages

Vous pouvez utiliser les langages C#, Visual Basic et F# pour écrire des applications et des bibliothèques pour .NET Core. Ces langages sont ou peuvent être intégrés dans vos éditeurs de texte et IDE préférés, notamment [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp), Sublime Text et Vim. Nous devons en partie cette intégration aux créateurs des projets [OmniSharp](https://www.omnisharp.net/) et [Ionide](http://ionide.io).

## <a name="apis"></a>API

.NET Core expose des API pour de nombreux scénarios, en voici quelques-uns :

- Types primitifs, comme [bool](../csharp/language-reference/keywords/bool.md) et [int](../csharp/language-reference/keywords/int.md).
- Collections, comme <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> et <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Types d’utilitaires, comme <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> et <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Types de données, comme <xref:System.Data.DataSet?displayProperty=nameWithType> et [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/).
- Types hautes performances, comme <xref:System.Numerics.Vector?displayProperty=nameWithType> et [Pipelines](https://devblogs.microsoft.com/dotnet/system-io-pipelines-high-performance-io-in-net/).

.NET Core assure la compatibilité avec les API .NET Framework et Mono en implémentant la spécification [.NET Standard](../standard/net-standard.md).

## <a name="frameworks"></a>Frameworks

Plusieurs frameworks ont été construits à partir de .NET Core :

- [ASP.NET Core](/aspnet/core/)
- [Plateforme Windows universelle (UWP) Windows 10](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Composition

.NET Core est constitué des composants suivants :

- Le [runtime .NET Core](https://github.com/dotnet/coreclr), qui fournit un système de type, un chargement d’assembly, un récupérateur de mémoire, une interopérabilité native et d’autres services de base. Des [bibliothèques de frameworks .NET Core](https://github.com/dotnet/corefx), qui fournissent des types de données primitives, des types de composition d’applications et des utilitaires essentiels.
- Le [runtime ASP.NET](https://github.com/aspnet/home), qui fournit un framework pour créer des applications cloud modernes connectées à Internet, comme les applications web, les applications IoT et les backends mobiles.
- Les [outils .NET Core CLI](https://github.com/dotnet/cli) et les compilateurs de langage ([Roslyn](https://github.com/dotnet/roslyn) et [F#](https://github.com/microsoft/visualfsharp)) qui permettent d’assurer une expérience de développement .NET Core.
- [L’outil dotnet](https://github.com/dotnet/core-setup), utilisé pour lancer les applications .NET Core et les outils CLI. Il sélectionne et héberge le runtime, fournit une stratégie de chargement d’assembly et lance les applications et les outils.

Ces composants sont distribués de la façon suivante :

- [Runtime .NET Core](https://www.microsoft.com/net/download/dotnet-core/2.1) : inclut le runtime .NET Core et des bibliothèques de framework.
- [Runtime ASP.NET Core](https://www.microsoft.com/net/download/dotnet-core/2.1) : inclut le runtime ASP.NET Core et .NET Core, et des bibliothèques de framework.
- [SDK .NET Core](https://www.microsoft.com/net/download/dotnet-core/2.1) : inclut les outils CLI .NET, le runtime ASP.NET Core ainsi que le runtime et le framework .NET Core.

### <a name="open-source"></a>Open source

[.NET Core](https://github.com/dotnet/core) est open source ([licence MIT](https://github.com/dotnet/core/blob/master/LICENSE.TXT)) et a été introduit dans [.NET Foundation](https://dotnetfoundation.org) par Microsoft en 2014. Il compte parmi les projets les plus actifs de .NET Foundation. Les particuliers et les entreprises sont libres de l’adopter, que ce soit à des fins personnelles, éducatives ou commerciales. Diverses sociétés utilisent .NET Core à travers des applications, des outils, de nouvelles plateformes et des services d’hébergement. Certaines de ces sociétés contribuent de façon significative à .NET Core sur GitHub et fournissent des conseils sur l’orientation des produits dans le cadre du groupe de travail appelé le [.NET Foundation Technical Steering Group](https://dotnetfoundation.org/blog/tsg-welcome).

### <a name="designed-for-adaptability"></a>Conçu pour l’adaptabilité

.NET Core a été créé comme un produit très similaire aux autres produits .NET mais aussi unique. Il a été conçu pour offrir une grande capacité d’adaptation aux nouvelles plateformes et charges de travail. Le portage sur plusieurs systèmes d’exploitation et processeurs est disponible, et d’autres projets de portage vont probablement suivre.

Le produit est divisé en plusieurs composants, ce qui permet d’adapter les différentes parties à de nouvelles plateformes, à différents moments. Le runtime et les bibliothèques de base spécifiques à la plateforme doivent être portés individuellement. Les bibliothèques indépendantes de la plateforme doivent fonctionner en l’état sur toutes les plateformes, de par leur construction. Il existe une tendance à vouloir réduire le nombre d’implémentations spécifiques à la plateforme pour optimiser l’efficacité des développeurs, qui préfèrent utiliser du code C# indépendant de la plateforme chaque fois que tout ou partie d’un algorithme ou d’une API peut être implémentée de cette façon.

Il est fréquent que des personnes s’interrogent sur la façon dont .NET Core est implémenté afin de prendre en charge plusieurs systèmes d’exploitation. Elles demandent généralement s’il existe des implémentations distinctes ou si la [compilation conditionnelle](https://en.wikipedia.org/wiki/Conditional_compilation) est utilisée. La réponse est les deux à la fois, avec une forte préférence pour la compilation conditionnelle.

Comme le montre le graphique ci-dessous, l’essentiel de [CoreFX](https://github.com/dotnet/corefx) est constitué de code indépendant de la plateforme partagé entre toutes les plateformes. Le code indépendant de la plateforme peut être implémenté en tant qu’assembly portable unique et utilisé sur toutes les plateformes.

![CoreFX : lignes de code par plateforme](../images/corefx-platforms-loc.png)

Les implémentations Windows et Unix sont de taille équivalente. L’implémentation Windows est plus grande, car CoreFX implémente des fonctionnalités propres à Windows, comme [Microsoft.Win32.Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry), mais n’implémente pas encore de concepts propres à Unix. Vous pouvez aussi constater que la majorité des implémentations Linux et macOS sont partagées dans une implémentation Unix, alors que les implémentations spécifiques à Linux et macOS sont à peu près de taille équivalente.

.NET Core contient à la fois des bibliothèques spécifiques aux plateformes et des bibliothèques indépendantes des plateformes. Cette caractéristique peut être illustrée à travers les exemples suivants :

- [CoreCLR](https://github.com/dotnet/coreclr) est spécifique à la plateforme. Il s’appuie sur des sous-systèmes de système d’exploitation, comme le gestionnaire de mémoire et le planificateur de threads.
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) et [System.Security.Cryptography.Algorithms](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) sont propres à la plateforme, puisque les API de stockage et de chiffrement sont très différentes sur chaque système d’exploitation.
- [System.Collections](https://github.com/dotnet/corefx/tree/master/src/System.Collections) et [System.Linq](https://github.com/dotnet/corefx/tree/master/src/System.Linq) sont indépendants de la plateforme, vu qu’ils créent et exploitent des structures de données.

## <a name="comparisons-to-other-net-implementations"></a>Comparaison avec les autres implémentations .NET

Il est peut-être plus facile d’appréhender la taille et la forme de .NET Core en le comparant aux implémentations .NET existantes.

### <a name="comparison-with-net-framework"></a>Comparaison avec le .NET Framework

.NET a été annoncé pour la première fois par Microsoft en 2000 et a depuis évolué. Le .NET Framework a été la principale implémentation .NET à avoir été conçue par Microsoft durant cette période de presque 20 ans.

Les principales différences entre .NET Core et le .NET Framework sont les suivantes :

- **Modèles d’application** : .NET Core ne prend pas en charge tous les modèles d’application .NET Framework. En particulier, il ne prend pas en charge ASP.NET Web Forms et ASP.NET MVC, mais il prend en charge ASP.NET Core MVC. Il a été annoncé que [.NET Core 3 prendra en charge WPF et Windows Forms](https://devblogs.microsoft.com/dotnet/net-core-3-and-support-for-windows-desktop-applications/).
- **API** : .NET Core contient une grande partie de la bibliothèque de classes de base de .NET Framework, avec une factorisation différente (les noms d’assembly sont différents, les membres exposés sur les types diffèrent selon les cas). Ces différences nécessitent des changements pour porter la source vers .NET Core dans certains cas (consultez [microsoft/dotnet-apiport](https://github.com/microsoft/dotnet-apiport)). .NET Core implémente la spécification d’API [.NET Standard](../standard/net-standard.md).
- **Sous-systèmes** : .NET Core implémente un sous-ensemble des sous-systèmes du .NET Framework, avec l’objectif d’une implémentation et d’un modèle de programmation plus simples. Par exemple, la sécurité d’accès du code (CAS) n’est pas prise en charge, alors que la réflexion l’est.
- **Plateformes** : le .NET Framework prend en charge Windows et Windows Server, tandis que .NET Core prend aussi en charge macOS et Linux.
- **Open Source** : .NET Core est open source, alors que seul un [sous-ensemble en lecture seule du .NET Framework](https://github.com/microsoft/referencesource) l’est.

Bien que .NET Core soit unique et présente des différences de taille par rapport au .NET Framework et aux autres implémentations .NET, il permet de partager facilement du code entre ces implémentations, que ce soit au moyen de techniques de partage de source ou de fichiers binaires.

Étant donné que .NET Core prend en charge l’installation côte à côte et que son runtime est complètement indépendant de .NET Framework, il peut être installé sur des machines avec .NET Framework installé sans aucun problème.

### <a name="comparison-with-mono"></a>Comparaison avec Mono

[Mono](https://www.mono-project.com/) est la première implémentation .NET multiplateforme et [open source](https://github.com/mono/mono) ; elle a vu le jour en 2004. Elle peut être considérée comme un clone communautaire du .NET Framework. L’équipe du projet Mono s’est appuyée sur les [normes .NET](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) libres (notamment ECMA 335) publiées par Microsoft pour proposer une implémentation compatible.

Les principales différences entre .NET Core et Mono sont les suivantes :

- **Modèles d’application** : Mono ne prend en charge qu’un sous-ensemble des modèles d’application du .NET Framework (par exemple, Windows Forms) et quelques autres (par exemple, [Xamarin.iOS](https://www.xamarin.com/platform)) via le produit Xamarin. .NET Core ne les prend pas en charge.
- **API** : Mono prend en charge un [sous-ensemble étendu](http://docs.go-mono.com/?link=root%3a%2fclasslib) des API du .NET Framework, en utilisant les mêmes noms d’assembly et la même factorisation.
- **Plateformes** : Mono prend en charge un grand nombre de plateformes et de processeurs.
- **Open Source** : Mono et .NET Core utilisent tous deux une licence MIT et sont des projets .NET Foundation.
- **Priorité** : Les plateformes mobiles sont la principale priorité de Mono depuis quelques années, alors que .NET Core se concentre sur les charges de travail cloud et de bureau.
